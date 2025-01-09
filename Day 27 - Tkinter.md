# Tkinter - Python GUI Module

### *args positional arguments
```python
def my_function(*args):
    print(type(args))  # Output: <class 'tuple'>
    for arg in args:
        print(arg)

my_function(1, 2, 3, "hello")


def my_function(**kwargs):
    print(type(kwargs))  # Output: <class 'dict'>
    for key, value in kwargs.items():
        print(f"{key}: {value}")

my_function(name="Alice", age=30, city="New York")



def my_function(*args, **kwargs):
    print("Positional arguments (args):")
    for arg in args:
        print(arg)

    print("\nKeyword arguments (kwargs):")
    for key, value in kwargs.items():
        print(f"{key}: {value}")

my_function(1, 2, 3, name="Bob", age=25, city="London")
```
Output:
Positional arguments (args):
1
2
3

Keyword arguments (kwargs):
name: Bob
age: 25
city: London

* *args devuelve una tupla de valores
* **kwargs funciona a través de keywords, devuelve un diccionario
