---
title:        "HTML and CSS, but without Javascript"
author:       "sarbull"
---

Scenario: Create a form that has two steps for reading user input and you don't want to hide and show elements with javascript. You can still do it with plain HTML and CSS.

```html
<div class="container">
  <div class="rating">
    <input name="rating" type="radio" /> 1
    <input name="rating" type="radio" /> 2
    <input name="rating" type="radio" /> 3
    <input name="rating" type="radio" /> 4
    <input name="rating" type="radio" /> 5
  </div>
  
  <textarea name="feedback"></textarea>
</div>
```

```css
.container textarea { display:none; }
.container:has(.rating > input:checked) .rating { display:none; }
.container:has(.rating > input:checked) textarea { display:block; }
```

## Demo

![demo](https://github.com/user-attachments/assets/eadd4df0-69c2-4ad0-bb29-a67e40576c3f)
