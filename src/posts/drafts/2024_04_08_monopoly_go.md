---  
title: Monopoly Go - Heist Simulation  
description: Sometimes you just play with things  
date: 2024-04-08  
tags:  
    - python  
    - programming  
    - softwaredevelopment  
    - ai  
layout: layouts/post.njk  
---  


My wife and I enjoy playing Monopoly Go, and I often find myself wanting to simulate different parts of the game just to run analysis on different aspects of gameplay. Today I found myself questioning the possibile differences in selection strategy for the Bank Heist minigame. I wanted to do this quickly so that it didn't distract me from work for too long. Let's walk through my process.

## The Premise

In this minigame there is a 3x4 grid of bank vault doors for you to open. Behind each door is one of three items. The diamond ring corresponds with the max award, the stack of money is 2/3 of the max award, and the coin is 1/3 of the max award. Once you have matched three of the same item then you receive the corresponding award. 

When I play this game I'd previously theorized that using the same selection sequence every time would reduce variability and maximize winnings. Ultimately I have no clue, and it seems like it would be pretty straight forward to simulate. There are 12 items of three varieties, you can select max 7 doors, and all items are displayed after you complete the minigame so the number of each item can easily be seen.

## Let's Make a Simulation

After getting a python file opened for the simulation, I begin with this comment up top. 

```python
"""
I want to test strategy on monopoly go heist.
There are 12 positions and three possible items
once you collect three of a given item then you get the score associated with the item

There are 3 of the lowest, and 4 each of the highest items.
These items are placed in random order

The strategies to be tested will be
1. a fixed order of selection
2. a random order of selection
"""
```

My next step was to open a new chat in ChatGPT. I'm using the free tier because I haven't been able to justify paying yet. One assumption that I made was to order the items as integers with increasing value. 

### Arrange the Items

Prompt: 
```
I want a python function that will randomly order a set of repeating items. 
The items in the collection are 3 items of value 1, 5 items of value 2, and 4 items of value 3. 
The function should generate a list of 12 items consisting of those described and ordered randomly. 
```

ChatGPT then gives a bit of other information with the centerpiece being this snippet. 

```python
import random

def random_order():
    items = [1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3, 3]  # Define the items
    random.shuffle(items)  # Shuffle the items randomly
    return items

random_list = random_order()
print(random_list)
```

After distilling this down, I have a working function.

```python
import random
def get_heist_items():
    items = [0, 0, 0, 1, 1, 1, 1, 1, 2, 2, 2, 2]
    random.shuffle(items)
    return items
```

That will do it. 

### Get the Selection Order


Prompt:
```
I would now like a python function that will select 7 items. The items being selected will be the indexes of a list with a given length.
```

The ChatGPT solution is this.

```python
def select_indexes(list_length, num_items):
    if num_items > list_length:
        raise ValueError("Number of items to select cannot be greater than the length of the list.")
    indexes = list(range(list_length))  # Generate a list of indexes from 0 to list_length - 1
    selected_indexes = random.sample(indexes, num_items)  # Select num_items indexes randomly
    return selected_indexes

list_length = 12  # Length of the list
num_items = 7  # Number of items to select
selected_indexes = select_indexes(list_length, num_items)
print("Selected indexes:", selected_indexes)
```

I then distilled that into something I like better.

```python
def get_random_selection_order():
    selection_list = list(range(12))
    return random.sample(selection_list, 7)
```

Since I'm going to be comparing the random selection to my personal fixed selection, I took the time to figure out the indexes I normally pick. These are the corners top right, top left, bottom left, and bottom right. And that's followed by the center row from third item back to the left. (At some point I decided that I believed the corners and middle-most two had higher occurance of max value item, but I know that's likely a lie). Those indexes are easily returned as a list. 

```python
def get_fixed_selection_order():
    return [3, 0, 8, 11, 6, 5, 4]
```

### Simulate!

I proceeded to write this bit to walk through how to simulate asserting a selection order on a randomly ordered group of items. For good measure I added an optional argument for whether or not to use random selection strategy.

```python
def single_simulation(random_selection=True):
    counts = [0, 0, 0]
    bank = get_heist_items()
    print(bank)
    selection_order = get_random_selection_order() if random_selection else get_fixed_selection_order()
    print(selection_order)
    selected_items = list()
    for position in selection_order:
        item_value = bank[position]
        selected_items.append(item_value)
        counts[item_value] += 1
        if counts[item_value] == 3:
            print(selected_items, item_value)
            return item_value
```


I did a few initial tests as such.

```python
if __name__ == '__main__':
    single_simulation()
```

Great, now I can start simulating multiple runs of each!

```python
if __name__ == '__main__':
    simulation_count = 100
    random_sum = [single_simulation(random_selection=True) for _ in range(simulation_count)]
    fixed_sum = [single_simulation(random_selection=False) for _ in range(simulation_count)]
    print('Random:', random_sum)
    print('Fixed:', fixed_sum)
```
I went on to run this for 1k and 1M simulations of each selection type and it's becoming quite obvious that the selection strategy doesn't matter. The odds are pretty even. But, I've gone through making this thing and would like to clean up the execution a bit, and wouldn't it be cool if I could test both selection methods on the same item set. 


### Refactor

In order to run both selections on the same game/item set I needed to refactor this a little bit. The evaluation of a selection set needs to be separate from where it's being generated. 

```python
def single_simulation(random_selection=True):
    bank = get_heist_items()
    # print('Bank:', bank)
    selection_order = get_random_selection_order() if random_selection else get_fixed_selection_order()
    # print('Selection Order:', selection_order)
    return simulation_selection(bank, selection_order)


def simulation_selection(bank, selection_order):
    counts = [0, 0, 0]
    selected_items = list()
    for position in selection_order:
        item_value = bank[position]
        selected_items.append(item_value)
        counts[item_value] += 1
        if counts[item_value] == 3:
            # print(selected_items, item_value)
            return item_value
```

And now I can test both selection types and evaluate which wins on a given game. 

```python
def complex_simulation():
    bank = get_heist_items()

    random_selection = get_random_selection_order()
    random_score =  simulation_selection(bank, random_selection)

    fixed_selection = get_fixed_selection_order()
    fixed_score = simulation_selection(bank, fixed_selection)

    if random_score == fixed_score:
        return 'TIE'
    if random_score > fixed_score:
        return 'RANDOM'
    return 'FIXED'
```

After doing a few runs to ensure that this simulation is working correctly to evaluate a winner of the game, I need to run it a bunch of times and get the results. I also ask Chat GPT to give me a quick way to count the recurring elements of a list. It proposes a couple of solutions and I opt to use `collections.Counter`. I wind up with this.

```python
from collections import Counter
if __name__ == '__main__':
    simulation_count = 1_000
    print(dict(Counter([complex_simulation() for _ in range(simulation_count)])))
```

output:
```
{'RANDOM': 293, 'TIE': 421, 'FIXED': 286}
```

I like it. Now is there a way to clean up the print out? I'd like to have the numbers include American order of magnitude separators as a comma. I can iterate over the items in the dictionary and use an f-string to format the numbers with desired commas.

```python
if __name__ == '__main__':
    simulation_count = 1_000_000
    winning_results = dict(Counter([complex_simulation() for _ in range(simulation_count)]))
    print([f'{k}: {v:,};' for k, v in winning_results.items()])
```
output:
```
['TIE: 437,737;', 'FIXED: 281,375;', 'RANDOM: 280,888;']
```

And now the commas between the items in that list are a bit annoying among the numerical commas. I'll use a string join to get rid of them.

```python
if __name__ == '__main__':
    simulation_count = 1_000_000
    winning_results = dict(Counter([complex_simulation() for _ in range(simulation_count)]))
    print(" ".join([f'{k}: {v:,}' for k, v in winning_results.items()]))
```

### Results

In the end I determined that there's not a significant difference in the selection strategies, but I enjoyed the process and decided to share it with you.

```
TIE: 436,321 RANDOM: 281,926 FIXED: 281,753
```


And if you'd like to see the completed code then here you are:

```python
"""
I want to test strategy on monopoly go heist.
There are 12 positions and three possible items
once you collect three of a given item then you get the score associated with the item

There are 3 of the lowest, and 4 each of the highest items.
These items are placed in random order

The strategies to be tested will be
1. a fixed order of selection
2. a random order of selection
"""
import random
from collections import Counter


def get_heist_items():
    items = [0, 0, 0, 1, 1, 1, 1, 1, 2, 2, 2, 2]
    random.shuffle(items)
    return items


def get_random_selection_order():
    selection_list = list(range(12))
    return random.sample(selection_list, 7)


def get_fixed_selection_order():
    return [3, 0, 8, 11, 6, 5, 4]


def single_simulation(random_selection=True):
    bank = get_heist_items()
    # print('Bank:', bank)
    selection_order = get_random_selection_order() if random_selection else get_fixed_selection_order()
    # print('Selection Order:', selection_order)
    return simulation_selection(bank, selection_order)


def simulation_selection(bank, selection_order):
    counts = [0, 0, 0]
    selected_items = list()
    for position in selection_order:
        item_value = bank[position]
        selected_items.append(item_value)
        counts[item_value] += 1
        if counts[item_value] == 3:
            # print(selected_items, item_value)
            return item_value


def complex_simulation():
    bank = get_heist_items()

    random_selection = get_random_selection_order()
    random_score = simulation_selection(bank, random_selection)

    fixed_selection = get_fixed_selection_order()
    fixed_score = simulation_selection(bank, fixed_selection)

    if random_score == fixed_score:
        return 'TIE'
    if random_score > fixed_score:
        return 'RANDOM'
    return 'FIXED'


if __name__ == '__main__':
    simulation_count = 1_000_000
    winning_results = dict(Counter([complex_simulation() for _ in range(simulation_count)]))
    print(" ".join([f'{k}: {v:,}' for k, v in winning_results.items()]))
```
