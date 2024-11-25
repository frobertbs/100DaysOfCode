# Dictionary in Python
{Key:Value}
```python
programming_dictionary = {
    "Bug": "An error in a program that prevents the program from running as expected.",
    "Function": "A piece of code that you can easily call over and over again.",
    "Loop": "The action of doing something over and over again"
}

print(programming_dictionary["Bug"])

# loop through the dictionary
for thing in programming_dictionary:
    print(thing) # only gives you the keys
    print(programming_dictionary[thing]) # the value of the key

my_dictionary = {
    "key1":[],
    "key2":str()
}

travel_log = {
    "France": {
        'cities_visited':["Paris", 'Lille', 'Dijon'],
        'total_visits':12
    },
    "Germany":{
        'cities_visited': ['Berlin','Munich','Suttgart'],
        'total_visits':5
    }
}
# print out Stuttgart
print(travel_log['Germany']['cities_visited'][2])


nested_list = ['A','B',['C','D']]
print(nested_list[2][1])

