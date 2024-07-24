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

```python
# Catch the exception and make sure the code runs without crashing.
fruits = ["Apple", "Pear", "Orange"]
def make_pie(index):
  try:
    fruit = fruits[index]
  except IndexError:
    print("Fruit pie")
  else:
    print(fruit + " pie")

make_pie(4) # Raises IndexError on list with less than 5 items.
```

Result
```
Fruit pie
```


### KeyError 처리 예제

```python
facebook_posts = [{'Likes': 21, 'Comments': 2}, 
                  {'Likes': 13, 'Comments': 2, 'Shares': 1}, 
                  {'Likes': 33, 'Comments': 8, 'Shares': 3}, 
                  {'Comments': 4, 'Shares': 2},
                  {'Comments': 1, 'Shares': 1}, 
                  {'Likes': 19, 'Comments': 3}]

total_likes = 0

# Catching the KeyError exception in the dictionary

for post in facebook_posts:
  try:
    total_likes = total_likes + post['Likes']
  except KeyError:
    pass 

print(total_likes)
```

Result
```
86
```
