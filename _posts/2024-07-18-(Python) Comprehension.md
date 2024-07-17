---
categories: 
 - Python
layout: single
title: "(Python) Comprehension"
---

## <b>List Comprehension</b>

기본 양식
```python
new_list = [new_item for item in list]
```

  ### List comprehension 기본 예


```python
numbers = [num for num in range(1,5)]
numbers
```




    [1, 2, 3, 4]



### List comprehension에 조건문 적용
아래 예시는 길이가 5보다 작은 이름을 추출


```python
names = ['Alex', 'Beth', 'Caroline', 'Dave', 'Eleanor', 'Freddie']
short_names = [name for name in names if len(name) < 5]
short_names
```




    ['Alex', 'Beth', 'Dave']



### 함수 적용
아래 예시는 길이가 5보다 큰 이름을 추출하고 대문자로 변환


```python
names = ['Alex', 'Beth', 'Caroline', 'Dave', 'Eleanor', 'Freddie']
long_names = [name.upper() for name in names if len(name) > 5]
long_names
```




    ['CAROLINE', 'ELEANOR', 'FREDDIE']



## <b>Dictionary Comprehension</b>

기본 양식
```python
new_dict = {new_key : new_value for item in list}
new_dict = {new_key : new_value for (key, value) in dict.items()}
```

### List로부터 dictionary 생성


```python
import random

names = ['Alex', 'Beth', 'Caroline', 'Dave', 'Eleanor', 'Freddie']
students_score = {student : random.randint(1,100) for student in names}
students_score
```




    {'Alex': 20,
     'Beth': 52,
     'Caroline': 15,
     'Dave': 4,
     'Eleanor': 81,
     'Freddie': 16}



### Dictionary로부터 dictionary 생성


```python
passed_students = {student : score for (student, score) in students_score.items() if score > 50}
passed_students
```




    {'Beth': 52, 'Eleanor': 81}




```python

```
