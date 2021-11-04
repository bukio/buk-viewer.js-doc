---
layout: default
title: BukViewerElement
permalink: /bukviewerelement
has_children: true
nav_order: 2
---

# BukViewerElement

buk-viewer.js를 로드하여 커스텀 엘리먼트 형태로 제공되는 `<buk-viewer>` 요소를 사용할 수 있다

```html
<html>
  <body>
    <buk-viewer></buk-viewer>
    <script src="buk-viewer.js"></script>
    <script>
      const viewer = document.querySelector('buk-viewer');
      
      viewer.addEventListener('bookLoad', ({ detail: event }) => {
        console.log(event.book);
      });
      
      viewer.init(...);
      viewer.openBook('bid');
    </script>
  </body>
</html>
```