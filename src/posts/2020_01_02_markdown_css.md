---  
title: Markdown Style  
description: This is what I use for markdown in VSCode  
date: 2020-01-14  
tags:  
  - markdown  
  - css
  - vscode  
layout: layouts/post.njk  
---  

While writing about [using Markdown to boost productivity in note taking]({{ '../2020_01_02_markdown_for_notes' | url }}) I thought that maybe some people might be interested. in this configuration.


```css
:root {
  /* from https://www.behance.net/gallery/8482091/Flat-Bold-UI-Kit */
  --black: #333333;
  --light-gray: #B3B8BC;
  --dark-gray: #656565;
  --blue: #46BDDF;
  --green: #52D273;
  --red: #E95065;
  --orange: #E57255;
  --yellow: #E5C453;
  --background: #484848;
  
  /* Other Sources */
  --other-background: #252525;
  --white: #FFF;
  
  background-color: var(--other-background);
} 
h1, h2, h3, h4, h5, h6{
  font-weight: bolder;
}

h1{
  color: var(--blue);
}
h2{
  color: var(--green);
}
h3{
  color: var(--yellow);
}
h4{
  color: var(--orange);
}
h5{
  color: var(--red);
}
h6{
  color: var(--white);
}
a:link {
  color: skyblue;
  font-weight: bolder;
}
a:visited {
  color: lightskyblue;
  font-weight: bolder;
}
p, ul, ol, li{
  color: var(--light-gray);
}
pre{
    background-color: #000 !important; 
}
strong {
  color: var(--white);
}
```

