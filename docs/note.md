---
layout: default
title: 참고
permalink: /note
nav_order: 9
---

# 참고

## 보기 설정 복원

- 브라우저 `localStorage`를 이용하여 보기 설정을 저장한다.
- 뷰어 초기화 시 `LibConfig.initialSettings` 값을 지정하지 않으면 `localStorage`에 저장했던 값을 이용해 복원한다.

## 종이책 페이지

페이지 라벨은 숫자만 허용하며 숫자 이외의 텍스트가 포함되면 해당 항목은 무시된다.

```html
<nav epub:type="page-list" hidden="hidden">
  <ol>
    <li><a href="georgia.xhtml#page752">Page 752</a></li> <!-- X -->
    <li><a href="georgia.xhtml#page753">753</a></li> <!-- O -->
    ...
```