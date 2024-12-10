### Local Scope vs Global
In this day I have learnt about the scope of variables.
```python
# global scope
my_global_variable = "Content of the variable"
def my_function_with_var_declaration():
  # local scope
  local_var = "Content of local variable"

print(local_var) # error because the variable can only be acccessed from inside the function
print(my_global_variable) # Ouputs: Content of the variable
```
In Python does not exist the Block Scope. For example:
```python
  if 1 == 1:
    new_variable = True
  else:
    else_variable = False

  print(new_variable) # will be printed
  print(else_variable) # will not be printed
```

```python
 # Guessing Game
import random
print('Welcome to the guessing game')
generated_number = random.randint(1,100)
print(generated_number)
difficulty = input('Choose your difficulty, easy or hard: ').lower()
attempts = int()

guessed = False

if difficulty == 'easy':
    attempts = 10
elif difficulty == 'hard':
    attempts = 5

print(f'You have {attempts} remaining to guess the number.')

while guessed is not True and attempts != 0:

    guess = int(input('Make a guess: '))
    if guess < generated_number:
        print('Too low.\n Guess again.')
        attempts -= 1
        print(f"You have {attempts} remaining to guess the number")
    elif guess > generated_number:
        print('Too high.\n Guess again.')
        attempts -= 1
        print(f"You have {attempts} remaining to guess the number")
    elif guess == generated_number:
        print(f'You got it! The answer was {generated_number}')
        guessed = True

```
