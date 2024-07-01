---
layout: single
title: "이미지 파일로부터 Color를 추출하는 Library"
---

'image.jpg' 파일로부터 30개의 Color를 추출하는 Library

```python
import colorgram

rgb_colors = []
colors = colorgram.extract('image.jpg', 30)
for color in colors:
    rgb_colors.append(color.rgb)

print(rgb_colors)
print(len(rgb_colors))
```

<em>colorgram.Color</em>의 properties는 아래와 같음

```python
colorgram.Color

Color.rgb        # r, g, b = 0 ~ 255
Color.hsl        # h, s, l = 0 ~ 255
Color.proportion # 0 ~ 1.0
```
