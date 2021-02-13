---
title: Simple Blog Post 3
description: Just a simple blog post
img: post-3.jpg
alt: my second blog post
---

## Javascript

```js{1,3-5}[script.js]
const http = require('http')
const bodyParser = require('body-parser')

http.createServer((req, res) => {
  bodyParser.parse(req, (error, body) => {
    res.end(body)
  })
}).listen(3000)
```

## CSS

```css[style.css]
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
```

## HTML

```html[index.html]
<div class="nuxt-content-highlight">
  <span class="filename">server.js</span>
  <pre class="language-js" data-line="1,3-5">
    <code>
      ...
    </code>
  </pre>
</div>
```
