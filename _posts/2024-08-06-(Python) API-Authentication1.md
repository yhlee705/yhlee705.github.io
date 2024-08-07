---
categories: 
 - Python
layout: single
title: "(Python) API 인증 - Openweather에서 날씨정보 가져오기"
---

발급받은 API를 Parameter에 넣어 호출하기

(1) `request` 모듈 import <br/>
(2) `request.get` : API 호출하여 응답 내용을 `response`에 저장 <br/>
(3) `response.raise_for_status()` : 정상적으로 응답하였는지 여부 확인 <br/>
(4) `response.json()` : 응답 내용을 json 양식으로 반환

```python
import requests
import pprint
import datetime as dt

OWM_ENDPOINT = "https://api.openweathermap.org/data/2.5/forecast"
API_KEY = [API_KEY]

WEATHER_PARAMS = {
    "lat": 25.032969,
    "lon": 121.565414,
    "appid": API_KEY,
    "lang": "kr",
}

response = requests.get(OWM_ENDPOINT, params = WEATHER_PARAMS)
response.raise_for_status()
weather_data = response.json()
```
