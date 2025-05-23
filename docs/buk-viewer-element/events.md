---
layout: default
title: Events
permalink: /events
parent: BukViewerElement
nav_order: 2
---

# Events
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# 책 및 아이템 로드

## bookLoad

buk.json 로드 완료 시 발생

### BookLoadEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name   | Type      | Description                                                           |
| ------ | --------- | --------------------------------------------------------------------- |
| `book` | `BukJSON` | 불러온 buk.json 내용<br />책 메타데이터, 목차, 아이템 정보 등을 담고있음 |

## bookLoadError

buk.json 로드 실패 시 발생

### BookLoadErrorEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name   | Type                                      | Description |
| ------ | ----------------------------------------- | ----------- |
| `code` | [`BookLoadErrorCode`](#bookloaderrorcode) | 에러 코드   |
| `raw`  | `any`                          |             |

### BookLoadErrorCode
{: .no_toc }

##### Constants
{: .no_toc }

| Name      | Value | Description          |
| --------- | ----- | -------------------- |
| `Unknown` | `0`   | 알 수 없는 에러 발생 |
| `Network` | `1`   | 네트워크 에러        |

## itemLoadStart

아이템의 html 로드 시작 시 발생

### ItemLoadStartEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name      | Type                      | Description |
| --------- | ------------------------- | ----------- |
| `address` | [`Address`]({{ "/address#address-1" | prepend: site.baseurl }}) | 현재 주소   |

## itemLoad

아이템의 html이 로드되고, html이 페이지에 모두 표시되면 발생

### ItemLoadEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `address` | [`Address`]({{ "/address#address-1" | prepend: site.baseurl }}) | 현재 주소 |
| `items` | [`BookItem[]`]({{ "/bukjson#bookitem" | prepend: site.baseurl }}) | 로드된 아이템 |

## itemLoadError

아이템의 html 로드 실패 시 발생

### ItemLoadErrorEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `address` | [`Address`]({{ "/address#address-1" | prepend: site.baseurl }}) | 현재 주소 |
| `item` | [`BookItem`]({{ "/bukjson#bookitem" | prepend: site.baseurl }})`| undefined` | 에러가 발생한 아이템 |
| `code` | [`ItemLoadErrorCode`](#itemloaderrorcode) | 에러 코드 |
| `raw` | `any` | |

### ItemLoadErrorCode
{: .no_toc }

##### Constants
{: .no_toc }

| Name                       | Value | Description                        |
| -------------------------- | ----- | ---------------------------------- |
| `Unknown`                  | `0`   | 알 수 없는 에러 발생               |
| `ItemNotFound`             | `1`   | 요청한 아이템이 존재하지 않음      |
| `PermissionDenied`         | `2`   | 해당 아이템을 볼 수 있는 권한 없음 (deprecated) |
| `ContentsLoadFailed`       | `3`   | html 파일 로드 중 에러 발생        |
| `ContentsProcessingFailed` | `4`   | 콘텐츠 처리 중 에러 발생           |

---

# 상태 변경

## addressChange

주소가 변경될 때 발생, 주소는 뷰어가 표시하고 있는 페이지에 대한 위치 정보를 주로 나타낸다.

### AddressChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name      | Type                      | Description |
| --------- | ------------------------- | ----------- |
| `address` | [`Address`]({{ "/address#address-1" | prepend: site.baseurl }}) | 새로운 주소 |

## settingsChange

읽기 설정이 변경될 때 발생

### SettingsChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name       | Type                        | Description         |
| ---------- | --------------------------- | ------------------- |
| `settings` | [`Settings`]({{ "/settings#settings-1" | prepend: site.baseurl }}) | 변경된 Settings |

## pageInfoChange

페이지(전체 페이지, 현재 페이지)가 변경될 때 발생

### PageInfoChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name                   | Type             | Description                                            |
| ---------------------- | ---------------- | ------------------------------------------------------ |
| `pageCount`       | `number`         | 아이템 내 전체 페이지 수                               |
| `page`          | `number`         | 아이템 내 현재 페이지 번호                             |
| `printPages`    | `string[]`       | 현재 페이지에 보여지는 종이책 페이지 번호              |
| `tocIndex` | `number` | 현재 보여지는 페이지에 해당하는 목차의 인덱스, 해당하는 목차가 없는 경우 -1 |
| `printPageRange` | `{ start: { pct: number }, end: { pct: number } }` | 현재 페이지가 종이책에서 어느 범위에 해당하는지에 대한 데이터 |

## bookmarkStateChange

현재 페이지의 북마크 상태가 변경될 때 발생

### BookmarkStateChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name       | Type      | Description               |
| ---------- | --------- | ------------------------- |
| `isActive` | `boolean` | 현재 페이지의 북마크 상태 |

## mediaOverlayPlayStateChange

미디어 오버레이 재생 상태가 변경될 때 발생

### MediaOverlayPlayStateChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name        | Type      | Description                    |
| ----------- | --------- | ------------------------------ |
| `isPlaying` | `boolean` | 현재 미디어 오버레이 재생 중 여부 |

---

# 텍스트 및 하이라이트 선택

## selectionChange

텍스트 선택이 변경되었을 때 발생

### SelectionChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `selection` | [`ContentsSelection`]({{ "/misc#contentsselection" | prepend: site.baseurl }})`| null` | 현재 선택된 텍스트에 대한 정보, 선택된 텍스트가 없으면 `null` |
| `doc` | `Document` | 변경이 발생한 Document |

## highlightClick

유저가 하이라이트를 클릭했을 때 발생

### HighlightClickEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `highlights` | `{ rect: Rect, rects: Rect[], range: Range, annotation: Annotation }[]` | 클릭된 하이라이트들에 대한 정보 |
| `offsetX` | `number` | 뷰어 내에서 클릭의 X 좌표 |
| `offsetY` | `number` | 뷰어 내에서 클릭의 Y 좌표 |

---

# 어노테이션 변경

## annotationCreated

북마크, 하이라이트 액션에 의해 어노테이션이 생성되었을 때 발생

### AnnotationCreatedEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name                | Type                              | Description            |
| ------------------- | --------------------------------- | ---------------------- |
| `annotation`        | [`Annotation`]({{ "/annotation#annotation-1" | prepend: site.baseurl }})   | 생성된 어노테이션      |
| `mergedAnnotations` | [`Annotation[]`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) | 머지된 어노테이션 목록 |

## annotationChanged

하이라이트 액션에 의해 어노테이션이 변경되었을 때 발생

### AnnotationChangedEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `annotation` | [`Annotation`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) | 변경된 어노테이션 |
| `oldStyleClass` | `string` | 변경 전 어노테이션의 styleClass |

## annotationRemoved

북마크, 하이라이트 액션에 의해 어노테이션이 삭제되었을 때 발생

### AnnotationRemovedEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name          | Type                              | Description            |
| ------------- | --------------------------------- | ---------------------- |
| `annotations` | [`Annotation[]`]({{ "/annotation#annotation-1" | prepend: site.baseurl }}) | 삭제된 어노테이션 목록 |

---
# 페이지 확대/축소

## zoomScaleChange

### ZoomScaleChangeEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `scale` | `number` | 확대/축소 스케일을 나타내는 퍼센트 값 |

---

# 기타

## pageTap

콘텐츠 내 상호작용 가능한 요소를 클릭한 경우를 제외하고 페이지가 클릭됐을 때 발생

### PageTapEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name                  | Type          | Description                                                                    |
| --------------------- | ------------- | ------------------------------------------------------------------------------ |
| `target`              | `EventTarget` | 이벤트 타겟                                                                    |
| `offsetX`             | `number`      | 뷰어 내에서 탭의 X 좌표                                                        |
| `offsetY`             | `number`      | 뷰어 내에서 탭의 Y 좌표                                                        |
| `isPageChangeGesture` | `boolean`     | 현재 탭에 의해 페이지 이동이 일어날 수 있는지 (페이지 좌, 우 영역을 탭한 경우) |

## pageChangeCanceled

이전, 다음 페이지로 이동하려고 할 때 [`PageChangeCancelCode`](#pagechangecancelcode)에 의해 이동이 취소된 경우 발생

### PageChangeCanceledEvent
{: .no_toc }

##### Properties
{: .no_toc }

| Name | Type | Description |
| - | - | - |
| `direction` | [`Direction`]({{ "/misc#direction" | prepend: site.baseurl }}) | 이동하려고 했던 방향 |
| `code` | [`PageChangeCancelCode`](#pagechangecancelcode) | 취소 사유 |

### PageChangeCancelCode
{: .no_toc }

##### Constants
{: .no_toc }

| Name      | Value | Description          |
| --------- | ----- | -------------------- |
| `OutOfPreviewBounds` | `0`   | 미리보기 모드에서 볼 수 없는 페이지로 이동 (deprecated) |
| `NoNextItem` | `1`   | 다음 아이템이 없음 (책의 시작 또는 끝에서 발생)        |

## pageTransitionEnd

페이지 전환이 완료되면 발생. 스크롤에 의해 페이지 전환이 일어나거나 페이지 전환 시에 페이지 넘김 애니메이션이 동작하는 경우 해당 동작이 끝난 후에 발생한다.