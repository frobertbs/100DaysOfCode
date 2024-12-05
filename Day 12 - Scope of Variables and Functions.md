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
