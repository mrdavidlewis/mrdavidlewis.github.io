---
title: "CSS Selectors"
date: 2022-11-02T16:03:24Z
draft: false
---

### Element selector:
```css
h1 {
  font-size: 4rem;
}
```

### ID selector:
```css
#main {
  color: red;
}
```

### Class selector:
```css
.nav {
  background-color: blue;
}
```

### Compound selectors

Match all ```h1``` elements with a class of ```front-page```
```css
h1.front-page {
  letter-spacing: 0.05rem;
}
```
Match all ```h1``` elements with a class of both ```front-page``` and ```head-line```
```css
h1.front-page.head-line {
  line-spacing: 1rem;
} 