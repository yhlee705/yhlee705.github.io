---
categories: 
 - Python
layout: single
title: "(Python) API 인증 - Openweather에서 날씨정보 가져오기"
---


```python
import requests
import pprint
import datetime as dt
```


```python
OWM_ENDPOINT = "https://api.openweathermap.org/data/2.5/forecast"
API_KEY = [API_KEY]

WEATHER_PARAMS = {
    "lat": 25.032969,
    "lon": 121.565414,
    "appid": API_KEY,
    "lang": "kr",
}

```


```python
response = requests.get(OWM_ENDPOINT, params = WEATHER_PARAMS)
response.raise_for_status()
weather_data = response.json()
```

![alt text](image.png)

```python
weather_slice = weather_data['list'][:4]
will_rain = False

for hour3_data in weather_slice:
    weather_code = hour3_data['weather'][0]['id']
    if weather_code < 700:
        will_rain = True
```


```python
if will_rain:
    print("Bring an Umbrella.")
```

            Bring an Umbrella.
    


