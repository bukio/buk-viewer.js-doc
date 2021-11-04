---
layout: default
title: Annotation
permalink: /annotation
parent: Interfaces
nav_order: 7
---

# Annotation

Interface
{: .label .m-0 .mt-6 }

## Annotation
{: .mt-2 }

북마크, 하이라이트 등 어노테이션

### Properties

| Name         | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| `type`       | `AnnotationType` | 어노테이션 타입, 북마크 또는 하이라이트                                                    |
| `url`        | `string`         | 어노테이션의 URL                                                                             |
| `text`       | `string`         | 어노테이션 텍스트                                                                  |
| `styleClass` | `string | null` | 어노테이션의 스타일 클래스,<br/>`type`이 `AnnotationType.Bookmark` 인 경우 `null` |


Enum
{: .label .m-0 .mt-6 }

## AnnotationType
{: .mt-2 }

어노테이션 타입

| Name        | Value         | Description |
| ----------- | ------------- | ----------- |
| `Bookmark`  | `'bookmark'`  | 북마크      |
| `Highlight` | `'highlight'` | 하이라이트  |
