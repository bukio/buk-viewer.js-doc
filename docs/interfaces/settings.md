---
layout: default
title: Settings
permalink: /settings
parent: Interfaces
nav_order: 5
---

# Settings

Interface
{: .label .m-0 .mt-6 }

## Setting\<T\>
{: .mt-2 }

### Properties

| Name         | Type      | Description                                                                                           |
| ------------ | --------- | ----------------------------------------------------------------------------------------------------- |
| `isDisabled` | `boolean` | 현재 설정 불가능한 항목인지, 예를 들어 Fixed Layout 책의 경우 `fontFace`, `fontSize` 등은 설정 불가함 |
| `value`      | `T`       | 설정 값                                                                                               |



Type Alias
{: .label .m-0 .mt-6 }

## Settings
{: .mt-2 }

읽기 설정 값들과 상태를 나타냄

### Properties

| Name                      | Type                  | Description |
| ------------------------- | --------------------- | -|
| `theme`                   | `Setting<Theme>`      | 테마 |
| `fontFace`                | `Setting<string>`     | 폰트 |
| `fontSize`                | `Setting<number>`     | 폰트 사이즈 |
| `lineHeight`              | `Setting<number>`     | 줄 간격 |
| `pagingMode`              | `Setting<PagingMode>` | 페이지/스크롤 모드 |
| `pageAnimation`           | `Setting<boolean>`    | 페이지 넘김 애니메이션 |
| `multiColumn`             | `Setting<boolean>`    | 한 페이지/두 페이지 보기 |
| `clickToPlayMediaOverlay` | `Setting<boolean>`    | 미디어 오버레이 요소를 클릭하여 재생 |


Enum
{: .label .m-0 .mt-6 }

## Theme
{: .mt-2 }

| Name    | Value     | Description |
| ------- | --------- | ----------- |
| `Light` | `'light'` |             |
| `Dark`  | `'dark'`  |             |
| `Sepia` | `'sepia'` |             |


Enum
{: .label .m-0 .mt-6 }

## PagingMode
{: .mt-2 }

| Name     | Value      | Description      |
| -------- | ---------- | ---------------- |
| `Page`   | `'page'`   | 가로 페이지 모드   |
| `Scroll` | `'scroll'` | 세로 스크롤 모드 |
