---
categories: 
 - Python
layout: single
title: "(Python) 문자열 좌우 여백 삭제"
---

## strip()

- 이 <code>strip()</code> 메서드는 앞뒤의 공백을 제거
- 선행은 문자열의 시작 부분을 의미하고, 후행은 문자열의 끝 부분을 의미
- 제거할 문자를 지정할 수 있으며, 지정하지 않으면 모든 공백이 제거

```python
txt = "     banana     "
x = txt.strip()
print("of all fruits", x, "is my favorite")

```
<br>
