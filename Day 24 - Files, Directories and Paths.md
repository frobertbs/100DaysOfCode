# Files, Directories and Paths

* Relative and Absolute paths
* File Opening and Writing
* Multiple Email Sending for differents names Exercise
---
Exercise Code
```python
#TODO: Create a letter using starting_letter.txt 
#for each name in invited_names.txt
#Replace the [name] placeholder with the actual name.
#Save the letters in the folder "ReadyToSend".
    
#Hint1: This method will help you: https://www.w3schools.com/python/ref_file_readlines.asp
    #Hint2: This method will also help you: https://www.w3schools.com/python/ref_string_replace.asp
        #Hint3: THis method will help you: https://www.w3schools.com/python/ref_string_strip.asp

def guests():
    with open('Input/Names/invited_names.txt') as file:
        names = file.readlines()
    return names


def send_email(name):
    with open(f'Output/ReadyToSend/letter_for_{name}', 'w') as email:
        email.write(f'''
        Dear {name},
        You are invited to my birthday this Saturday.
        Hope you can make it!
        Robert
''')

guests = guests()

for guest in guests:
    send_email(guest)


```
