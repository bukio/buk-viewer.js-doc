---
layout: default
title: Home
permalink: /
nav_order: 1
---

# buk-viewer.js

북이오 콘텐츠 뷰어 자바스크립트 라이브러리.

## 기능

- 읽기 설정 (테마, 폰트, 두 페이지 보기 등)
- 하이라이트 및 북마크
- 책 내 검색
- [미디어 오버레이](https://www.w3.org/publishing/epub3/epub-mediaoverlays.html)
- [종이책 페이지](https://www.w3.org/publishing/epub3/epub-packages.html#sec-nav-pagelist)

## 장점

- 메뉴, 컨텍스트 메뉴 등을 자유롭게 개발 가능하도록 관련 API를 지원
- 커스텀 엘리먼트 형태로 제공되어 간단하게 사용 가능
- 타입스크립트 개발 환경 지원

## 용어

- 아이템: EPUB OPF의 spine에 속한 itemref (linear="no" 제외)
- buk.json: 책 메타데이터, 목차, 아이템 정보를 포함하고 있는 파일
- bid: 책 아이디
- iid: 아이템 아이디

## 콘텐츠 주소 체계

> /`bid`(/`iid`(/`pageOrAnchor`))

- `pageOrAnchor`: 아이템 내 위치를 나타내는 값. 진행률 `(0\.\d+)`, 하이라이트 범위 `(\d+-\d+)`, 요소 아이디
