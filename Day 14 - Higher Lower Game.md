In this day I had to create the Higher Lower Game.
### Game Description
The Higher or Lower game is a fun and simple guessing game where players compare the follower counts of two social media accounts (e.g., celebrities, brands, or influencers). The game presents two accounts, one with its follower count revealed and the other hidden. The player's goal is to guess whether the second account has a higher or lower follower count than the first. Each correct guess earns a point, and the game continues with new comparisons until the player makes a wrong guess. It's a test of pop culture knowledge and intuition, often featuring accounts from platforms like Instagram, TikTok, or Twitter.

Next the code:
There is a module called game_data where it is stored a list with dictionaries.

![image](https://github.com/user-attachments/assets/88dca598-471f-4535-8559-5d83109dec54)

```python
from game_data import data
from random import randint


def generate_opponent(data):
    """
     Generates dictionary item from the data list
    :param data:
    :return: dictionary item
    """
    random_account = randint(0,len(data) - 1)
    print(f"{data[random_account]['name']}, "
          f"{data[random_account]['follower_count']}, "
          f"{data[random_account]['description']}, "
          f"{data[random_account]['country']}")
    return data[random_account]


def get_greater(A,B):
    if A['follower_count'] > B['follower_count']:
        return A
    else:
        return B


print('Welcome to the higher/lower game')
choice_is_correct = True
score = 0
B = generate_opponent(data)
while choice_is_correct:
    A = B
    B = generate_opponent(data)
    print('vs')
    B = generate_opponent(data)
    choice = input('Who has more followers? Type \'A\' or \'B\': ')
    if choice == 'A':
        choice = A
    else:
        choice = B

    if choice['name'] == get_greater(A,B)['name']:
        score += 1
        print('\n' *100 + f'You did good. Current Score: {score}')
    else:
        print('You did bad')
        choice_is_correct = False


   # if A['follower_count'] > B['follower_count']:
       # print(f'{A['name']} has more followers than {B['name']}')

```
