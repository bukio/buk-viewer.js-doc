---
layout: default
title: Address
permalink: /address
nav_order: 6
---

# Address


Class
{: .label .m-0 .mt-6 }

## Address
{: .mt-2 }

북이오 콘텐츠 주소를 표현하는 객체

### Properties

| Name     | Type                                                  | Description                                                                      |
| -------- | ----------------------------------------------------- | -------------------------------------------------------------------------------- |
| `bid`    | `string`                                              | 책 아이디                                                                        |
| `iid`    | `string | undefined`                                 | 아이템 아이디                                                                    |
| `anchor` | `number | string | undefined`                                 | 아이템 내 위치 (페이지, 범위, 요소 아이디 셋 중 하나로 나타냄)                       |
| `page` | `number | undefined`                                 | 아이템 내 페이지                       |
| `range` | `string | undefined`                                 | 아이템 내 텍스트 범위                       |
| `fragment` | `string | undefined`                                 | 아이템 내 요소 아이디                       |
| `query`  | `{ [key: string]: string | undefined } | undefined` | 페이지 표시에 필요한 기타 파라미터 <br>[사용 가능한 파라미터](#query-parameters) |

### Constructor

### new Address(bid, iid?, anchor?, query?)

### Methods

### clone()

현재 인스턴스를 복제하여 새로운 Address 인스턴스 반환

##### Returns

`Address`

### toString()

Address를 북이오 콘텐츠 주소 체계를 따르는 URL로 변환

##### Returns

`string`

---

# Query Parameters

## highlight

이동하려는 주소가 하이라이트 범위면 해당 범위를 하이라이트 함. 값으로 `'true'` 또는 하이라이트 배경색을 지정할 수 있음.

| Value                                                                        | Description                                                      |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| `true`                                                                       | 기본 색상으로 하이라이트 함                                      |
| [CSS color value](https://developer.mozilla.org/ko/docs/Web/CSS/color_value) | 해당 색상으로 하이라이트 함 (16진수 표기법 사용시 '#' 생략 가능) |

```javascript
Viewer.openBook('bid', 'iid', '1-10', { highlight: 'yellow' });
Viewer.openBook('bid', 'iid', '1-10', { highlight: '#FFFF00' });
Viewer.openBookWithURL('/bid/iid/1-10?highlight=yellow');
Viewer.openBookWithURL('/bid/iid/1-10?highlight=ff0');
```

## force

현재 주소와 상관 없이 무조건 책을 새로 연다. (buk.json을 새로 불러온다)

| Value    | Description                                              |
| -------- | -------------------------------------------------------- |
| `true` | |

