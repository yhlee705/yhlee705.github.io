---
categories: 
 - Python
layout: single
title: "(Python) 파일 읽기, 쓰기"
---

## 파일 읽기

1. `open()`/`close()` 사용하기 <br>

```python
file = open("my_file.txt")
contents = file.read()
print(contents)
file.close()
```
<br>

2. `with open()` 사용하기<br>

```python
with open("my_file.txt") as file:
  contents = file.read()
  print(contents)
```
<br>

3. 읽기/쓰기 모드<br>

mode 파라미터 : r(읽기), w(쓰기), a(추가)<br>

```python
with open("my_file.txt", mode = "r") as file:
  contents = file.read()
  print(contents)
```
<br>

## 파일 쓰기

```python
with open("my_file.txt", mode = "w") as file:
  file.write("New text.")
```
