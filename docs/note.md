---
layout: default
title: 참고
permalink: /note
nav_order: 9
---

# 참고
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

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

## `buk-viewer` 요소 타입 정의

```typescript
import { NgElement, WithProperties } from '@angular/elements'; // 설치 필요
import { BukViewer } from 'buk-viewer';

declare global {
  interface HTMLElementTagNameMap {
    'buk-viewer': NgElement & WithProperties<BukViewer>;
  }
}
```

## 콘텐츠 기본 스타일 및 테마 수정

다음의 CSS 변수들을 오버라이드하여 일부 콘텐츠 기본 스타일 및 테마를 수정할 수 있다.

`<buk-viewer>` 요소 및 하위 요소들에서 사용하는 변수

- 여백 관련
  - `--bukv-contents-padding-top`
  - `--bukv-contents-padding-bottom`
- 테마 관련
  - `--bukv-contents-bg-color-light`
  - `--bukv-contents-bg-color-sepia`
  - `--bukv-contents-bg-color-dark`
  
콘텐츠에 삽입되는 뷰어 기본 스타일에서 사용하는 변수

- 여백 관련
  - `--bukv-padding-left`
  - `--bukv-padding-right`
  - `--bukv-padding-top`
  - `--bukv-padding-bottom`
- 테마 관련
  - `--bukv-text-color`
  - `--bukv-bg-color`
  - `--bukv-column-rule-img`