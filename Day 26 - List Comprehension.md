```python
# list comprehension

# first example
numbers = [1, 2, 3]
new_list = [n + 1 for n in numbers]
print(new_list)

# second example
name = "Robert"
name_letters = [letter for letter in name]
print(name_letters)

# third example
doubled_numbers = [number * 2 for number in range(1, 5)]
print(doubled_numbers)

# fourth example
names = ['Alex', 'Beth', 'Caroline', 'Dave', 'Eleanor', 'Freddie']
short_names = [name for name in names if len(name) < 5]
upper_case_names = [name.upper() for name in names if len(name) >= 5]
print(upper_case_names)


```



```Data Overlap

💪 This exercise is HARD 💪 

Take a look inside file1.txt and file2.txt. They each contain a bunch of numbers, each number on a new line. 

You are going to create a list called result which contains the numbers that are common in both files. 

e.g. if file1.txt contained: 

1 

2 

3

and file2.txt contained: 

2

3

4

result = [2, 3]


IMPORTANT:  The output should be a list of integers and not strings!

Try to use List Comprehension instead of a Loop.
```

```python
with open('file1.txt') as file1:
    content_file_1 = file1.readlines()
    list_file_1 = [int(number) for number in content_file_1]

with open('file2.txt') as file2:
    content_file_2 = file2.readlines()
    list_file_2 = [int(number) for number in content_file_2]
    

print(list_file_1)
print(list_file_2)

result = [number for number in list_file_1 if number in list_file_2]

print(result)
```
