---
categories: 
 - Python
layout: single
title: "(100days Python) Day17_OOP(Quiz game)"
---

## 프로그램 실행 구조

* question_data.py로부터 data를 읽어 question_model.py의 구조체 형태로 Q/A의 List를 question_bank에 저장
* question_bank를 quiz_brain.py의 QuizBrain에 전달하여 quiz 인스턴스 생성
* quiz.still_has_questions()가 True인 경우 quiz.next_question()을 실행하여 문제 제출
* QuizBrain 클래스 내에 정답을 맞히면 정답수를 계산하는 함수(check_answer(self, user_answer, correct_answer)) 동작

|Tree|Description|
|---|---|
|📦Root | |
| ┣ 📜main.py           | |
| ┣ 📜data.py           | Question/Answer를 포함하는 Dataset|
| ┣ 📜question_model.py | Question/Answer 구조를 포함하는 Class(구조체)|
| ┗ 📜quiz_brain.py     | 문제를 내고 정답 여부를 확인하는 Class|

### main.py

```python
from question_model import Question
from data import question_data
from quiz_brain import QuizBrain

question_bank = []
for question in question_data:
    question_text = question["question"]
    question_answer = question["correct_answer"]
    new_question = Question(question_text, question_answer)
    question_bank.append(new_question)

quiz = QuizBrain(question_bank)

while quiz.still_has_questions():
    quiz.next_question()

print("You've completed the quiz")
print(f"Your final score was: {quiz.score}/{quiz.question_number}")
```

### data.py

```python
question_data = [
    {
        "category": "Science: Computers",
        "type": "boolean",
        "difficulty": "medium",
        "question": "The HTML5 standard was published in 2014.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
]
```

### question_model.py

```python
class Question:

    def __init__(self, q_text, q_answer):
        self.text = q_text
        self.answer = q_answer
```

### quiz_brain.py

```python
class QuizBrain:

    def __init__(self, q_list):
        self.question_number = 0
        self.score = 0
        self.question_list = q_list

    def still_has_questions(self):
        return self.question_number < len(self.question_list)

    def next_question(self):
        current_question = self.question_list[self.question_number]
        self.question_number += 1
        user_answer = input(f"Q.{self.question_number}: {current_question.text} (True/False): ")
        self.check_answer(user_answer, current_question.answer)

    def check_answer(self, user_answer, correct_answer):
        if user_answer.lower() == correct_answer.lower():
            self.score += 1
            print("You got it right!")
        else:
            print("That's wrong.")
        print(f"The correct answer was: {correct_answer}.")
        print(f"Your current score is: {self.score}/{self.question_number}")
        print("\n")
```
