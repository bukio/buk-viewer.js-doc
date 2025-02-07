---
layout: default
title: Methods
permalink: /methods
parent: BukViewerElement
nav_order: 1
---

# Methods
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

# 초기화

## init(config)

뷰어를 초기화한다.

### Parameters
{: .no_toc }

| Name     | Type                      | Description |
| -------- | ------------------------- | ----------- |
| `config` | [`LibConfig`]({{ "/libconfig#libconfig-1" | prepend: site.baseurl }}) | 초기화 옵션           |

### Returns
{: .no_toc }

[`LibConfig`]({{ "/libconfig#libconfig-1" | prepend: site.baseurl }})

---

# 책 로드 및 페이지 이동

## openBook(bid, iid?, anchor?, query?)

책을 로드하거나 지정한 페이지로 이동한다.

### Parameters
{: .no_toc }

| Name           | Type                     | Description                                                                                                |
| -------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| `bid`          | `string`                 | 책 아이디                                                                                                  |
| `iid`          | `string`                 | 아이템 아이디                                                                                   |
| `anchor` | `string | number`       | 아이템 내 위치<br /><br />- 페이지 `0\.\d+`<br />- 텍스트 범위 `\d+-\d+`<br />- 요소 아이디 |
| `query`        | `{ [key: string]: any }` | 페이지 표시에 필요한 기타 파라미터<br>[Address]({{ "/address#query-parameters" | prepend: site.baseurl }}) 참고                           |

## openBookWithURL(url)

북이오 콘텐츠 주소 체계에 해당하는 URL을 이용하여 책을 로드하거나 지정한 페이지로 이동한다.

### Parameters
{: .no_toc }

| Name  | Type     | Description |
| ----- | -------- | ----------- |
| `url` | `string` |       |

## prevPage()

이전 페이지로 이동한다.

## nextPage()

다음 페이지로 이동한다.

## goToPrintPage(page)

EPUB의 [Page List](https://www.w3.org/TR/epub-33/#sec-nav-pagelist)에 명시된 종이책 페이지로 이동한다. EPUB에 [Page List](https://www.w3.org/TR/epub-33/#sec-nav-pagelist)가 없는 경우 아무런 동작도 하지 않는다.

### Parameters
{: .no_toc }

| Name   | Type     | Description          |
| ------ | -------- | -------------------- |
| `page` | `string` | 이동할 종이책 페이지 |

---

# 주소 파싱

## parseBukURL(url)

북이오 콘텐츠 주소 체계를 따르는 URL을 파싱하여 Address 객체를 리턴한다.

### Parameters
{: .no_toc }

| Name   | Type | Description |
| - | - | - |
| `url` | `string` | 북이오 콘텐츠 주소 체계를 따르는 URL |

### Returns
{: .no_toc }

[`Address`]({{ "/address#address-1" | prepend: site.baseurl }})

---

# 현재 상태 가져오기

## getCurrentAddress()

현재 표시중인 페이지의 주소를 가져온다.

### Returns
{: .no_toc }

`Address | undefined`

## getCurrentSettings()

현재 읽기 설정을 가져온다.

### Returns
{: .no_toc }

[`Settings`]({{ "/settings#settings-1" | prepend: site.baseurl }})

## getFontsCurrentlyAvailable()

LibConfig에 명시된 폰트 중 현재 책에 적용 가능한 font-family 목록을 가져온다.

### Returns
{: .no_toc }

`string[]`

---

# 읽기 설정 변경

## updateSettings(key, value)

읽기 설정을 변경한다.

### Parameters
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `key` | [`keyof Settings`]({{ "/settings#settings" | prepend: site.baseurl }}) | 변경할 설정 항목 |
| `value` | `any` | 변경할 값 |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## changeTheme(theme)
{: .mt-2 }

테마를 변경한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name    | Type                           | Description |
| ------- | ------------------------------ | ----------- |
| `theme` | [`Theme`]({{ "/settings#theme" | prepend: site.baseurl }}) |             |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## changeFontFace(fontFace)
{: .mt-2 }

폰트를 변경한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name       | Type     | Description                                                        |
| ---------- | -------- | ------------------------------------------------------------------ |
| `fontFace` | `string` | `'default'` 또는 `LibConfig.fonts`에 정의된 `fontFamilies` 중 하나 |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## changeFontSize(value, isAbsolute?)
{: .mt-2 }

폰트 사이즈를 변경한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용, 기존 메서드에서 `isAbsolute`를 `true`로 호출한 것과 같이 동작한다.

### Parameters
{: .no_toc }

| Name         | Type      | Description                                                                                                      |
| ------------ | --------- | ---------------------------------------------------------------------------------------------------------------- |
| `value`      | `number`  | `isAbsolute`가 `false`일 경우 두 가지 값 `축소: -1, 확대: 1`<br/>`isAbsolute`가 `true`일 경우 퍼센트 값 `50~500` |
| `isAbsolute` | `boolean` |                                                                                                       |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## changeLineHeight(value, isAbsolute?)
{: .mt-2 }

줄 간격을 변경한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용, 기존 메서드에서 `isAbsolute`를 `true`로 호출한 것과 같이 동작한다.

### Parameters
{: .no_toc }

| Name         | Type      | Description                                                                                                      |
| ------------ | --------- | ---------------------------------------------------------------------------------------------------------------- |
| `value`      | `number`  | `isAbsolute`가 `false`일 경우 두 가지 값 `좁게: -1, 넓게: 1`<br/>`isAbsolute`가 `true`일 경우 퍼센트 값 `50~150` |
| `isAbsolute` | `boolean` |                                                                                                       |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## changePagingMode(pagingMode)
{: .mt-2 }

페이지/스크롤 모드를 설정한다. Reflowable 책에서만 동작한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name         | Type                                     | Description |
| ------------ | ---------------------------------------- | ----------- |
| `pagingMode` | [`PagingMode`]({{ "/settings#pagingmode" | prepend: site.baseurl }}) |             |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## setPageAnimation(isActive)
{: .mt-2 }

페이지 넘김 애니메이션을 사용할지 여부를 설정한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name       | Type      | Description |
| ---------- | --------- | ----------- |
| `isActive` | `boolean` |             |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## setMultiColumn(isActive)
{: .mt-2 }

한 페이지/두 페이지 보기 모드를 설정한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name       | Type      | Description                                       |
| ---------- | --------- | ------------------------------------------------- |
| `isActive` | `boolean` | `false` 한 페이지 보기<br />`true` 두 페이지 보기 |

Deprecated
{: .label .label-red .m-0 .mt-5 }

## setClickToPlayMediaOverlay(isActive)
{: .mt-2 }

미디어 오버레이 요소를 클릭하여 재생을 시작할 지 여부를 설정한다.

{: .deprecated }
updateSettings(key, value) 메서드 사용

### Parameters
{: .no_toc }

| Name       | Type      | Description |
| ---------- | --------- | ----------- |
| `isActive` | `boolean` |             |

---

# 콘텐츠 CSS 스타일 변경

## setContentsStyles(styles)

콘텐츠에 추가되는 CSS 스타일을 지정하는 `LibConfig.contentsStyles`를 새로운 값으로 교체한다.

### Parameters
{: .no_toc }

| Name       | Type      | Description |
| ---------- | --------- | ----------- |
| `styles` | `string[]` | CSS 문자열의 배열 |

---

# 책 내 검색

## search(keyword, callback)

현재 책 내에서 주어진 키워드로 검색하고, 결과를 담아 콜백을 호출한다.

### Parameters
{: .no_toc }

| Name       | Type                                       | Description    |
| ---------- | ------------------------------------------ | -------------- |
| `keyword`  | `string`                                   | 키워드         |
| `callback` | `(result: ContentsSearchResult[]) => void` | 검색 완료 콜백 |

### Returns
{: .no_toc }

`() => void`

검색 중단 시 호출할 함수 

---

# 어노테이션(하이라이트 및 북마크)

## setAnnotations(annotations)

뷰어가 표시할 어노테이션 목록을 셋팅한다. 셋팅 즉시 페이지의 하이라이트 및 북마크 상태도 함께 업데이트 된다.

### Parameters
{: .no_toc }

| Name          | Type                              | Description |
| ------------- | --------------------------------- | ----------- |
| `annotations` | [`Annotation[]`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) |             |

## toggleBookmark()

북마크를 토글한다. 기존 북마크 상태에 따라 [`annotationCreated`]({{ "/events#annotationcreated" | prepend: site.baseurl }}), [`annotationRemoved`]({{ "/events#annotationremoved" | prepend: site.baseurl }}) 이벤트가 발생한다.

## getHighlightsFromRange(range)

`range`를 포함하고 있는 하이라이트에 대한 정보를 가져온다. 텍스트 선택 시 컨텍스트 메뉴 표시에 이용한다.

### Parameters
{: .no_toc }

| Name    | Type    | Description |
| ------- | ------- | ----------- |
| `range` | `Range` |             |

### Returns
{: .no_toc }

하이라이트에 해당하는 Range 및 Annotation 목록

`{ range: Range; annotation: Annotation }[]`

## createHighlight(range, styleClass, options?)

`range`에 하이라이트를 생성한다.

### Parameters
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `range` | `Range | string` | 하이라이트할 Range 또는 범위 URL |
| `styleClass` | `string` | 하이라이트 스타일 클래스 |
| `options` | `{ expandToWord?: boolean; mergeWith?: string[], emitEvent?: boolean }` | 하이라이트 동작 옵션<br>- expandToWord: `range`를 단어 단위까지 확장하여 하이라이트 (기본값: `true`)<br>- mergeWith: 머지할 겹치는 하이라이트의 스타일 클래스 (기본값: `[]`)<br>- emitEvent: 'annotationCreated' 이벤트 발생 여부 (기본값: `true`) |

### Returns
{: .no_toc }

`{ annotation: Annotation; mergedAnnotations: Annotation[] }` \| `null`

하이라이트를 통해 생성된 어노테이션, 머지된 어노테이션 목록. 하이라이트 실패 시 `null`.

## changeHighlight(rangeURL, currStyleClass, newStyleClass, options?)

하이라이트의 스타일을 변경한다.

### Parameters
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `rangeURL` | `string` | 변경할 하이라이트의 URL |
| `currStyleClass` | `string` | 변경할 하이라이트의 스타일 클래스 |
| `newStyleClass` | `string` | 새로운 스타일 클래스 |
| `options` | `{ emitEvemt?: boolean }` | 하이라이트 동작 옵션<br>- emitEvent: 'annotationChanged' 이벤트 발생 여부 (기본값: `true`) |

### Returns
{: .no_toc }

[`Annotation`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) \| `null`

변경된 어노테이션 (변경 후 데이터). 화면에 표시중인 페이지 내에 `rangeURL`에 해당하는 하이라이트가 없거나 변경 실패 시 `null`.

## removeHighlight(rangeURL, styleClass, options?)

하이라이트를 삭제한다.

### Parameters
{: .no_toc }

| Name | Type | Description |
| ------- | ------- | ------------ |
| `rangeURL` | `string` | 삭제할 하이라이트의 URL |
| `styleClass` | `string` | 삭제할 하이라이트의 스타일 클래스 |
| `options` | `{ emitEvemt?: boolean }` | 하이라이트 동작 옵션<br>- emitEvent: 'annotationRemoved' 이벤트 발생 여부 (기본값: `true`) |

### Returns
{: .no_toc }

[`Annotation`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) \| `null`

삭제된 어노테이션. `range`에 해당하는 하이라이트가 없거나 삭제 실패 시 `null`.

&nbsp;

{: .note }
`toggleBookmark`, `createHighlight`, `changeHighlight`, `removeHighlight`는 페이지에 북마크 및 하이라이트를 **표시**하며, `setAnnotations`를 통해 전달받은 Annotation 목록은 업데이트**하지 않는다**. 해당 목록에 포함되어 있지 않은 Annotation은 아이템이 변경되면 페이지에서 삭제된다. 따라서 책을 보는동안 아이템 변경에 관계 없이 북마크 및 하이라이트를 유지하려면 위 메서드들에 의해 업데이트된 어노테이션 목록을 `setAnnotations`를 통해 뷰어에 전달해주어야 한다.

---

## getSelection()

현재 선택된 텍스트에 대한 정보 가져온다.

### Returns
{: .no_toc }

[`ContentsSelection`]({{ "/misc#contentsselection" | prepend: site.baseurl }}) \| `null`

현재 선택된 텍스트에 대한 정보. 선택된 텍스트가 없는 경우 `null`.

## clearSelection()

현재 선택된 텍스트 선택 해제

---

# 미디어 오버레이

## playMediaOverlay(prevOrNext)

이전 또는 다음 미디어 오버레이 요소를 재생한다.

### Parameters
{: .no_toc }

| Name         | Type      | Description                         |
| ------------ | --------- | ----------------------------------- |
| `prevOrNext` | `1 | -1` | 이전 또는 다음 트랙 재생 |

## playMediaOverlayFromRange(range)

Range에 포함된 미디어 오버레이 요소를 재생한다. Range에 미디어 오버레이 요소가 포함되어 있지 않으면 아무런 동작도 하지 않는다.

### Parameters
{: .no_toc }

| Name    | Type    | Description                 |
| ------- | ------- | --------------------------- |
| `range` | `Range` |  |

## pauseMediaOverlay()

미디어 오버레이 재생을 중지한다.

## isPlayingMediaOverlay()

현재 미디어 오버레이가 재생중인지 여부를 가져온다.

### Returns
{: .no_toc }

`boolean`

## setMediaOverlayPlaybackRate(value)

미디어 오버레이 재생 배속을 설정한다.

### Parameters
{: .no_toc }

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| `value` | `number` | 배속 값     |

## canPlayMediaOverlayFromRange(range)

`range`를 이용해 미디어 오버레이를 재생할 수 있는지 여부를 가져온다(`range`와 겹치는 미디어 오버레이 요소가 있는지 체크). `true`이면 해당 `range`를 `playMediaOverlayFromRange`에 파라미터로 넘겨 미디어 오버레이를 재생할 수 있다.

### Parameters
{: .no_toc }

| Name    | Type    | Description |
| ------- | ------- | ----------- |
| `range` | `Range` |             |

### Returns
{: .no_toc }

`boolean`

---

# 페이지 확대/축소

## zoom(scale)

페이지를 확대/축소 한다. EPUB3 Fixed Layout 및 PDF 책에서만 동작한다.

### Parameters
{: .no_toc }

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| `scale` | `number` | 확대/축소 스케일을 나타내는 퍼센트 값 |

{: .note }
데스크탑 환경에 최적화하여 개발되었으며, 터치 디바이스에서는 브라우저 네이티브 핀치 줌 사용 권장.

---

# Range

## createRangeFromElements(startId, endId, iid?)

요소의 id를 이용해 시작 요소, 끝 요소를 포함하는 Range를 가져온다. iid 파라미터는 한 페이지에 여러 아이템이 표시되고 있을 때 사용할 수 있다. 요소가 없거나 iid가 잘못된 경우 에러를 던진다.

### Parameters
{: .no_toc }

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| `startId` | `string` | 시작 요소의 id |
| `endId` | `string` | 끝 요소의 id |
| `iid` | `string` | 요소를 찾을 아이템의 iid |

### Returns
{: .no_toc }

[`Range`](https://developer.mozilla.org/en-US/docs/Web/API/Range)

## getVisibleRanges()

현재 페이지에 보여지고 있는 내용의 범위를 나타내는 Range를 가져온다. 리턴되는 배열의 길이는 현재 화면에 표시되고 있는 아이템의 개수와 같다.

### Returns
{: .no_toc }

[`Range[]`](https://developer.mozilla.org/en-US/docs/Web/API/Range)

## getAddressFromRange(range)

Range로 부터 텍스트 범위를 가져와 해당 위치를 가리키는 Address 객체를 가져온다. Range로 부터 텍스트 범위를 가져올 수 없는 경우 `null`을 리턴한다

### Parameters
{: .no_toc }

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| `range` | [`Range`](https://developer.mozilla.org/en-US/docs/Web/API/Range) | |

### Returns
{: .no_toc }

[`Address`]({{ "/address#address-1" | prepend: site.baseurl }}) \| `null`