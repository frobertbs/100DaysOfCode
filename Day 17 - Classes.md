# How to create classes
```python
class Car:
  # constructor
  def __init__(self, brand, model, year):
    self.brand = brand
    self.model = model
    self.year = year
    self.kilometers = 0
```

self keyword references the object itself

In the day 17 I learnt about the modularity of OOP. The use of an API data and how OOP can mean minor changes when adding new data or changing it.

Next I attach the code of the python files of the quiz game coded.

## data.py
```python
question_data = [
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "It&#039;s not possible to format a write-protected DVD-R Hard Disk.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "The common software-programming acronym &quot;I18N&quot; comes from the term &quot;Interlocalization&quot;.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "Early RAM was directly seated onto the motherboard and could not be easily removed.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "To bypass US Munitions Export Laws, the creator of the PGP published all the source code in book form. ",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "Android versions are named in alphabetical order.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "FLAC stands for &quot;Free Lossless Audio Condenser&quot;&#039;",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "The last Windows operating system to be based on the Windows 9x kernel was Windows 98.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "The open source program Redis is a relational database server.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "AMD created the first consumer 64-bit processor.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Science: Computers",
        "question": "All program codes have to be compiled into an executable file in order to be run. This file can then be executed on any machine.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    }
]
```

## Quiz Brain.py
```python
class QuizBrain:
    def __init__(self, question_list):
        self.question_number = 0
        self.question_list = question_list
        self.score = 0

    def still_has_question(self):
        return self.question_number < len(self.question_list)

    def next_question(self):
        current_question = self.question_list[self.question_number] # Devuelve el objeto de la pregunta
        self.question_number += 1
        user_answer = input(f'Q.{self.question_number}: {current_question.text}. (True/False)?:')
        self.check_answer(user_answer,current_question.answer)

    def check_answer(self, user_answer, correct_answer):
        if user_answer.lower() == correct_answer.lower():
            print('You got it right')
            self.score += 1
        else:
            print('You got it wrong')
        print(f'The correct answer was: {correct_answer}')
        print(f'Your current score is {self.score}/{self.question_number}')
        print('\n')

```

## Question Model
```python
class Question:
    def __init__(self, text, answer):
        self.text = text
        self.answer = answer
```

## main.py
```python
from question_model import Question
from data import question_data
from quiz_brain import QuizBrain

question_bank = []

for i in question_data:
    question_bank.append(Question(i['question'], i['correct_answer']))

quiz = QuizBrain(question_bank)
while quiz.still_has_question():
   quiz.next_question()
```

