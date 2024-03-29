---
layout: default
title: Miscellaneous
permalink: /misc
nav_order: 8
---

# Miscellaneous

Interface
{: .label .m-0 .mt-6 }

## ContentsSearchResult
{: .mt-2 }

| Name   | Type     | Description            |
| ------ | -------- | ---------------------- |
| `text` | `string` | 검색어가 포함된 책 내 텍스트 |
| `url`  | `string` | 해당 위치의 URL        |


Interface
{: .label .m-0 .mt-6 }

## ContentsSelection
{: .mt-2 }

현재 선택된 텍스트에 대한 정보

| Name | Type | Description |
| - | - | - |
| `rect`  | `Rect` | 선택 영역의 모든 Rect들을 포함하는 뷰포트 상대적인 Rect |
| `rects`  | `Rect[]` | 선택 영역의 모든 뷰포트 상대적인 Rect들 |
| `range` | `Range` | 선택된 Range |
| `url`   | `string | null` | 선택에 해당하는 URL, 북이오 주소 체계로 나타낼 수 없는 경우 `null` |


Interface
{: .label .m-0 .mt-6 }

## Rect
{: .mt-2 }

크기와 위치를 나타냄

| Name | Type | Description |
| - | - | - |
| `x`  | `number` | x 좌표 |
| `y`  | `number` | y 좌표 |
| `width`  | `number` | 너비 |
| `height`  | `number` | 높이 |


Enum
{: .label .m-0 .mt-6 }

## Direction
{: .mt-2 }

| Name | Value | Description |
| - | - | - |
| `Prev` | `-1` | 이전 |
| `Next` | `1` | 다음 |