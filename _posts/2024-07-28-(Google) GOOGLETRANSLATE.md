---
categories: 
 - Google
layout: single
title: "(Google) GOOGLETRANSLATE"
---

## <b>GOOGLETRANSLATE</b>

* Text를 다른 언어로 번역 ([Link](https://support.google.com/docs/answer/3093331?hl=en-GB&ref_topic=3105411&sjid=2162334432427783619-AP))

### 예시
```
GOOGLETRANSLATE('Hello world','en','es')

GOOGLETRANSLATE(A2,B2,C2)

GOOGLETRANSLATE(A2)
```

### 문법

```
GOOGLETRANSLATE(text, [source_language, target_language])

   - text : 번역할 텍스트
   - source_language : 선택사항(기본값 - 'auto'), 영어 'en', 한국어 'ko', 일본어 'ja'
   - target_language : 선택사항(기본값 - 기본 시스템 언어)
```
