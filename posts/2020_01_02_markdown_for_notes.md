---
title: Using Markdown for Notes
description: Increasing Productivity with Markup Language
date: 2020-01-02
tags:
  - productivity
  - markdown
  - vscode
  - css
layout: layouts/post.njk
---

I recently found myself with four different files opened long term in Notepad++ that all centered around one set of changes that I was working on, and that seemed a bit absurd.  I was keeping one file open for schema definitions, another for java snippets, another for meeting notes, and another for the actual requirement description. I decided that I should be able to consolidate these notes in a meaningful way, and spent several hours walking through formatting these things together as YAML and then XML before settling on Markdown.

If you aren't familiar with Markdown, [Wikipedia](https://en.wikipedia.org/wiki/Markdown) says this:

> Markdown is a lightweight markup language with plain text formatting syntax. Its design allows it to be converted to many output formats, but the original tool by the same name only supports HTML.[9] Markdown is often used to format readme files, for writing messages in online discussion forums, and to create rich text using a plain text editor.

You are likely familiar with Markdown already as it is used on Github (README.md), Reddit comments, Discord, Slack and others. It has functionality to include code blocks with language specific highlighting, links, bullet lists, numbered lists, six levels of headers, not to mention **different** *text* ~~decorations~~.

# Example
This code
```markdown
# Heading 1
information
+ **bold**
+ *italic*
+ ***bold/italic***
  + nested
## Heading 2
stuff and things
1. [ ] Unchecked box
2. [x] Checked box
```

Looks like this:

# Heading 1
information
+ **bold**
+ *italic*
+ ***bold/italic***
  + nested
## Heading 2
stuff and things
1. [ ] Unchecked box
2. [x] Checked box

---

My primary goal when I set out on this journey was to have support to fold sections that I'm not currently looking at, but what I got with Markdown is so much more. I usually keep notes open in Notepad++, but for some reason I decided to use VSCode. I'm pretty glad that I did, in hindsight because what I currently have configured works significantly better than anything I've ever gotten in Notepad++.

Through the last week I've wound up with a few customizations that make life a bit better for me. I got a few plugins and wrote some custom CSS, and now I'm really happy with the whole thing.

## Markdown All in One plugin
Helps alot, with live preview, formatting lists, toggling styles, generating linked table of contents, print to html, format tables, and pretty math symbols.
[The repository can be found here](https://github.com/yzhang-gh/vscode-markdown)

## Custom CSS
This relates directly to the live preview which by default does not differentiate the headers from the primary text (although it does color the code blocks).  markdown.styles setting allows you to define a css file to apply to the preview.  I then used the markdown.extension.print.onFileSave setting to figure out how to select the bits that I wanted to cutomize. The parts that I thought to be important were having different colors for the different header levels, code block backgrounds that are visibly distinct from the other text,

## Insert Date String
To quickly insert date or dateTime into my notes this plugin is helpful.  I added a keybind to `Ctrl+Shift+i+d` to insert date without time. The formatting is configurable to your needs. [The repository can be found here](https://github.com/jsynowiec/vscode-insertdatestring)

## Snippets
For my personal usage I also wanted to include information for frontmatter/header.  This one is specifically for my 11ty blog entries which is also written in markdown.

```json
	"frontmatter": {
		"scope": "markdown",
		"prefix": "frontmatter",
		"body": [
			"---  ",
			"title: ${1:title}  ",
			"description: ${2:description}  ",
			"date: ${3:Ctrl+Shift+i+d}  ",
			"tags:  ",
			"	- ${4:first}  ",
			"	- ${5:second}  ",
			"layout: layouts/post.njk  ",
			"---  "
			],
			"description": "front-matter for 11ty blog post"
	}
```
which get's pasted in like this, and i can tab through the variables easily.
```yaml
---
title: title
description: description
date: Ctrl+Shift+i+d
tags:
  - first
  - second
layout: layouts/post.njk
---
```

I'd also love to hear thoughts and experiences that you may have with markdown or other languages for taking your notes.  Editor/plugin recommendations, tips, and tricks are all welcome as well.
