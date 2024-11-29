### The Tenth Day deals with functions that return values

One of the challenges is the leap year function
```python
def is_leap_year(year):
    # Write your code here. 
    # Don't change the function name.
    result = True
    if year % 4 == 0:
        if year % 100 == 0:
            if year % 400 == 0:
                result = True
            else:
                result = False
        else:
            result = True
    else:
        result = False
    
    return result
```

#### Docstrings concept
Docstrings is a way of creating documentation as we code along.
The docstring has to go after the first line of the declaration of the function
example:
def my_function():
    """Documentation for the function"""


As a project for this day I had to code a calculator that takes as input two numbers and one operation. After the result, the user is asked if he wants to continue calculating with another number maintaining the previous result. Here I had to use dictionaries, functions, while loops and recursion.

```python
import art


def add(n1, n2):
    return n1 + n2


def subtract(n1, n2):
    return n1 - n2


def multiply(n1, n2):
    return n1 * n2


def divide(n1, n2):
    return n1 / n2


operations = {
    "+": add,
    "-": subtract,
    "*": multiply,
    "/": divide,
}

# print(operations["*"](4, 8))


def calculator():
    print(art.logo)
    should_accumulate = True
    num1 = float(input("What is the first number?: "))

    while should_accumulate:
        for symbol in operations:
            print(symbol)
        operation_symbol = input("Pick an operation: ")
        num2 = float(input("What is the next number?: "))
        answer = operations[operation_symbol](num1, num2)
        print(f"{num1} {operation_symbol} {num2} = {answer}")

        choice = input(f"Type 'y' to continue calculating with {answer}, or type 'n' to start a new calculation: ")

        if choice == "y":
            num1 = answer
        else:
            should_accumulate = False
            print("\n" * 20)
            calculator()


calculator()
```

