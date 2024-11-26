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




# Blind Auction Project
from art import logo
print(logo)


def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
        if bid_amount > highest_bid:
            highest_bid = bid_amount
            winner = bidder
    print(f"The winner is {winner} with a bid of ${highest_bid}")


bids = {}
continue_bidding = True
while continue_bidding:
    name = input("What is your name?: ")
    price = int(input("What is your bid?: $"))
    bids[name] = price
    should_continue = input("Are there any other bidders? Type 'yes or 'no'.\n")
    if should_continue == "no":
        continue_bidding = False
        find_highest_bidder(bids)
    elif should_continue == "yes":
        print("\n" * 20)


