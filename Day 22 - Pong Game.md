In this day, I had to code and develop the pong game.
For more information about how the game is played:https://en.wikipedia.org/wiki/Pong
To do this OOP was used as a way of using the clean code and methodology.

```python


"""
    1.Create the screen - DONE
    2.Create and move the paddle
    3.Create another paddle
    4.Create the ball and make it move
    5.Detect collision with wall and bounce
    6.Detect collision with paddle
    7.Detect when the paddle misses the ball
    8.Keep Score
"""

from turtle import Turtle, Screen
from paddle import Paddle
from ball import Ball
from scoreboard import Scoreboard
import time

screen = Screen()
screen.setup(width=800, height=600)
screen.bgcolor('black')
screen.title('Pong')

left_paddle = Paddle(350, 0)
right_paddle = Paddle(-350, 0)
ball = Ball()
scoreboard = Scoreboard()

screen.listen()
screen.onkey(left_paddle.moveUp, 'Up')
screen.onkey(right_paddle.moveUp(), 'w')
screen.onkey(left_paddle.moveDown, 'Down')
screen.onkey(right_paddle.moveDown, 's')

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()
    ball.move()

    # detect colision with wall:
    if ball.ycor() > 280 or ball.ycor() < -280:
        # needs to bounce
        ball.bounce_y()

    # detect colision with paddle:
    if ball.distance(right_paddle) < 50 and ball.xcor() > 340:
        ball.bounce_x()

    # Detect right paddle misses
    if ball.xcor() > 380:
        ball.reset_position()

    # Detect left paddle misses:
        if ball.xcor() < -380:
            ball.reset_position()
screen.mainloop()



from turtle import Turtle

class Scoreboard(Turtle):
    def __init__(self):
        super().__init__()
        self.color('white')
        self.penup()
        self.hideturtle()
        self.l_score = 0
        self.r_score = 0

    def update_scoreboard(self):
        self.clear()
        self.goto(-100, 200)
        self.write(self.l_score, align='center', font=('Courier', 80, 'normal'))
        self.goto(100, 200)
        self.write(self.r_score, align='center', font=('Courier', 80, 'normal'))

    def l_point(self):
        self.l_score += 1
        self.update_scoreboard()

    def r_point(self):
        self.r_score += 1
        self.update_scoreboard()

from turtle import Turtle

class Paddle(Turtle):
    def __init__(self, x_position, y_position):
        super().__init__()
        self.shape('square')
        self.color('white')
        self.penup()
        self.resizemode("user")
        self.shapesize(stretch_wid=5, stretch_len=1)
        self.goto(x=x_position, y=y_position)

    def moveUp(self):
        new_y = self.ycor() + 20
        self.setposition(self.xcor(), new_y)

    def moveDown(self):
        new_y = self.ycor() - 20
        self.setposition(self.xcor(), new_y)
from turtle import Turtle
from paddle import Paddle

class Ball(Turtle):
    def __init__(self):
        super().__init__()
        self.shape('circle')
        self.penup()
        self.goto(0,0)
        self.color('white')
        self.x_move = 10
        self.y_move = 10

    def move(self):
        new_x = self.xcor() + self.x_move
        new_y = self.ycor() + self.y_move
        self.goto(new_x, new_y)

    def bounce_y(self):
        self.y_move *= -1

    def bounce_x(self):
        self.x_move *= -1

    def reset_position(self):
        self.goto(0,0)
        self.bounce_x()




```
