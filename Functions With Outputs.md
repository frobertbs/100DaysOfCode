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

