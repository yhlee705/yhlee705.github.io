---
categories: 
 - Python
layout: single
title: "(Python) Error Handling"
---

## <b>Error Handling</b>

try: - 예외를 유발할 수 있는 실행 코드

except: - 예외가 있는 경우 실행 코드(2개 이상 연속으로 사용 가능)

else: - 예외가 없을 때 실행하는 코드

finally: - 성공여부와 무관하게 무조건 실행

```python
try:
    file = open("a_file.txt")
    a_dictionary = {"key": "value"}
    print(a_dictionary["key"])
except FileNotFoundError:
    file = open("a_file.txt", "w")
    file.write("Something")
except KeyError as error_message:
    print(f"The key {error_message} does not exist.")
else:
    content = file.read()
    print(content)
finally:
    raise TypeError("This is an error that I made up.")
```

### IndexError 처리




### KeyError 처리



