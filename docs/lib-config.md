---
layout: default
title: LibConfig
permalink: /libconfig
nav_order: 3
---

# LibConfig

Interface
{: .label .m-0 .mt-6 }

## LibConfig
{: .mt-2 }

뷰어 초기화에 사용되는 값

### Properties

| Name | Type | Description |
| - | - | - |
| `contentsBaseURL` | `string` | 아이템 로드 및 아이템 내 리소스 요청시 사용할 주소를 설정 |
| `bukJSONBaseURL` | `string | undefined` | buk.json 요청시 사용할 주소를 설정, 없으면 `contentsBaseURL` 사용 |
| `fonts` | [`FontConfig`](#fontconfig)`| undefined` | 뷰어에서 지원할 폰트 |
| `highlightStyles` | [`HighlightStyle[]`](#highlightstyle)`| undefined` | 하이라이트 스타일 |
| `initialSettings` | [`SettingValues`](#settingvalues)`| undefined` | 읽기 설정 초기값 |
| `updateHTTPRequest` | [`UpdateHTTPRequestFn`](#updatehttprequestfn)`| undefined` | 뷰어에서 일어나는 요청을 수정하는 함수 |
| `canChangeAddress` | [`CanChangeAddressFn`](#canchangeaddressfn)`| undefined` | 새로운 주소로 변경되기 전 호출되는 함수. 리턴값으로 뷰어의 주소 변경 동작을 제어할 수 있음. |


Interface
{: .label .m-0 .mt-6 }

## HighlightStyle
{: .mt-2 }

페이지 내에서 하이라이트에 사용할 스타일 클래스 이름과 스타일

### Properties

| Name         | Type     | Description                          |
| ------------ | -------- | ------------------------------------ |
| `styleClass` | `string` | 하이라이트에 사용할 클래스 이름 |
| `style`      | `string` | 클래스에 적용될 스타일               |


Interface
{: .label .m-0 .mt-6 }

## SettingValues
{: .mt-2 }

읽기 설정 값

### Properties

| Name                      | Type                                     | Description                          |
| ------------------------- | ---------------------------------------- | ------------------------------------ |
| `theme`                   | [`Theme`]({{ "/settings#theme" | prepend: site.baseurl }})           | 테마                                 |
| `fontFace`                | `string`                                 | 폰트                                 |
| `fontSize`                | `number`                                 | 폰트 사이즈                          |
| `lineHeight`              | `number`                                 | 줄 간격                          |
| `pagingMode`              | [`PagingMode`]({{ "/settings#pagingmode" | prepend: site.baseurl }}) | 페이지/스크롤 모드     |
| `pageAnimation`           | `boolean`                                | 페이지 넘김 애니메이션               |
| `multiColumn`             | `boolean`                                | 한 페이지/두 페이지 보기       |
| `clickToPlayMediaOverlay` | `boolean`                                | 미디어 오버레이 요소를 클릭하여 재생 |


Type Alias
{: .label .m-0 .mt-6 }

## FontConfig
{: .mt-2 }

책 언어에 따라 지원할 폰트 정의. 언어 코드(ISO 639)를 키값으로 하는 오브젝트, 언어 코드당 아래 속성을 가지고 있음.

| Name           | Type       | Description                            |
| -------------- | ---------- | -------------------------------------- |
| `fontFaces`    | `string[]` | @font-face가 지정된 css 파일 경로 배열 |
| `fontFamilies` | `string[]` | font-family 배열                       |

```typescript
{
  [languageCode: string]: {
    fontFaces: string[];
    fontFamilies: string[];
  };
};
```

Type Alias
{: .label .m-0 .mt-6 }

## UpdateHTTPRequestFn
{: .mt-2 }

뷰어에서 일어나는 HTTP 요청을 수정하는 함수

```typescript
(url: string) => { // 요청 URL
  url?: string; // 요청 URL 자체를 변경해야 하는 경우 변경할 요청 URL
  withCredentials?: boolean;
  setParams?: { [param: string]: string }; // 추가 파라미터
  setHeaders?: { [name: string]: string }; // 추가 헤더
};
```

Type Alias
{: .label .m-0 .mt-6 }

## CanChangeAddressFn
{: .mt-2 }

새로운 주소로 변경되기 전 호출되는 함수. 리턴값으로 뷰어의 주소 변경 동작을 제어할 수 있음.

```typescript
(newAddress: Address) => boolean; // true: 주소 변경을 계속한다, false: 주소 변경을 중단한다
```