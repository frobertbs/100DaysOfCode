In the day number 23, as a capstone project, I had to think and divide subproblems of how to create a turtle crossing project. 

# About
This project is a Mini-Game in Python, following OOP and using the Turtle module. The goal of this game is to help a turtle to cross the street.

# Game instructions
Use the arrow up key to move the turtle to the other side of the street without getting hit by a car. Be careful as the cars will be moving faster, each time you level up.

# Example
![image](https://github.com/user-attachments/assets/8847d267-7004-4aa5-9656-d6b352710321)

# Code

```python
import time
from turtle import Screen
from player import Player
from car_manager import CarManager
from scoreboard import Scoreboard
import random

screen = Screen()
screen.setup(width=600, height=600)
screen.tracer(0)
screen.listen()

player = Player()
car_manager = CarManager()
scoreboard = Scoreboard()
screen.onkey(player.move, 'Up')

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()
    car_manager.create_car()
    car_manager.move_cars()

    # detect collision with the car
    for car in car_manager.all_cars:
        if car.distance(player) < 20:
            game_is_on = False
            scoreboard.game_over()
    # detect when the player has reached the other side
    if player.player_is_at_line():
        player.go_to_start()
        car_manager.level_up()
        scoreboard.increase_level()





import random
from turtle import Turtle
from random import choice
COLORS = ["red", "orange", "yellow", "green", "blue", "purple"]
STARTING_MOVE_DISTANCE = 5
MOVE_INCREMENT = 10


class CarManager():
    def __init__(self):
        self.all_cars = []
        self.car_speed = STARTING_MOVE_DISTANCE

    def create_car(self):
        random_chance = random.randint(1,6)
        if random_chance == 1:
            new_car = Turtle()
            new_car.shape('square')
            new_car.penup()
            new_car.color(random.choice(COLORS))
            new_car.shapesize(stretch_wid=1, stretch_len=2.5)
            new_car.goto(x=300, y=random.randint(-280, 280))
            self.all_cars.append(new_car)

    def move_cars(self):
        for car in self.all_cars:
            new_x = car.xcor() - self.car_speed
            car.setposition(new_x, car.ycor())

    def level_up(self):
        self.car_speed += MOVE_INCREMENT


from turtle import Turtle
STARTING_POSITION = (0, -280)
MOVE_DISTANCE = 10
FINISH_LINE_Y = 280


class Player(Turtle):
    def __init__(self):
        super().__init__()
        self.shape('turtle')
        self.penup()
        self.color('black')
        self.go_to_start()
        self.setheading(90)

    def move(self):
        new_y = self.ycor() + 10
        self.setposition(x=self.xcor(), y=new_y)

    def player_is_at_line(self):
        if self.ycor() > FINISH_LINE_Y:
            return True
        else:
            return False

    def go_to_start(self):
        self.goto(STARTING_POSITION)

from turtle import Turtle
FONT = ("Courier", 24, "normal")


class Scoreboard(Turtle):
    def __init__(self):
        super().__init__()
        self.color('black')
        self.penup()
        self.hideturtle()
        self.level = 1
        self.score = 0
        self.goto(-270,250)
        self.write(f'Level: {self.level}', align='left', font=FONT)

    def update_scoreboard(self):
        self.clear()
        self.write(f'Level: {self.level}', align='left', font=FONT)

    def increase_level(self):
        self.level += 1
        self.update_scoreboard()

    def game_over(self):
        self.goto(0, 0)
        self.write(f'Game Over')


```
