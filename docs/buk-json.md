---
layout: default
title: BukJSON
permalink: /bukjson
nav_order: 4
---

# BukJSON

Interface
{: .label .m-0 .mt-6 }

## BukJSON
{: .mt-2 }

책의 메타데이터, 목차, 아이템 정보를 담고있음

### Properties

| Name        | Type                              | Dscription         |
| ----------- | --------------------------------- | ------------------ |
| `meta`      | [`BookMeta`](#bookmeta)           | 메타데이터         |
| `items`     | [`BookItem[]`](#bookitem)         | 아이템 목록        |
| `toc`       | [`TOCItem[]`](#tocitem)           | 목차               |
| `page_list` | [`PageListItem[]`](#pagelistitem) | 종이책 페이지 정보 |


Interface
{: .label .m-0 .mt-6 }

## BookMeta
{: .mt-2 }

책 메타데이터

### Properties

| Name        | Type                                               | Description                                                |
| ----------- | -------------------------------------------------- | ---------------------------------------------------------- |
| `bid`       | `string`                                           | 책 아이디                                                  |
| `type`      | [`BookType`](#booktype)                            | 책 타입 |
| `cover`     | `string`                                           | 커버 이미지 URL                                            |
| `title`     | `string`                                           | 제목                                                       |
| `subtitle`  | `string`                                           | 부제목                                                     |
| `author`    | `string`                                           | 작가                                                       |
| `languages` | `string[]`                                         | 책 언어 목록                                               |
| `media`     | [`MediaOverlayMeta`](#mediaoverlaymeta)`| undefined` | 미디어 오버레이 관련 메타데이터                            |


Interface
{: .label .m-0 .mt-6 }

## MediaOverlayMeta
{: .mt-2 }

미디어 오버레이 관련 메타데이터

### Properties

| Name                    | Type                  | Description                                                            |
| ----------------------- | --------------------- | ---------------------------------------------------------------------- |
| `playback_active_class` | `string | undefined`   | 미디어 오버레이가 재생중일 때 document 요소에 적용되는 CSS 클래스 이름 |
| `active_class`          | `string | undefined`   | 현재 재생중인 요소에 적용되는 CSS 클래스 이름                          |
| `duration`              | `string`              | 미디어 오버레이 전체 길이                                              |
| `narrator`              | `string[] | undefined` | 내레이터                                                               |


Interface
{: .label .m-0 .mt-6 }

## BookItem
{: .mt-2 }

아이템

### Properties

| Name  | Type     | Description     |
| ----- | -------- | --------------- |
| `iid` | `string` | 아이템 아이디   |
| `url` | `string` | 콘텐츠 파일 URL |
| `thumbnail` | `string | undefined` | 썸네일 이미지 URL (책 타입이 PDF인 경우에만 존재) |


Interface
{: .label .m-0 .mt-6 }

## TOCItem
{: .mt-2 }

목차 아이템

### Properties

| Name      | Type     | Description                           |
| --------- | -------- | ------------------------------------- |
| `address` | `string` | 책 내에서 목차의 위치를 나타내는 주소 |
| `title`   | `string` | 제목                                  |
| `depth`   | `number` |                                       |


Interface
{: .label .m-0 .mt-6 }

## PageListItem
{: .mt-2 }

종이책 페이지 정보

### Properties

| Name     | Type     | Description                                          |
| -------- | -------- | ---------------------------------------------------- |
| `anchor` | `string | undefined` | 아이템 내에서 종이책 페이지를 나타내는 요소의 아이디 |
| `iid`    | `string` | 아이템 아이디                                        |
| `page`   | `number` | 종이책 페이지 번호                                   |


Enum
{: .label .m-0 .mt-6 }

## BookType
{: .mt-2 }

| Name       | Value        | Description                             |
| ---------- | ------------ | --------------------------------------- |
| `Buk`      | `'buk'`      | EPUB을 스트리밍 가능한 형태로 변환한 책 |
| `PDF`      | `'pdf'`      | PDF를 스트리밍 가능한 형태로 변환한 책  |
| `Document` | `'document'` | 단일 챕터로 이루어진 문서                                    |
| `Wiki`     | `'wiki'`     | 위키피디아                              |
