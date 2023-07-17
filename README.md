# week-10
Scripts for week 10
import turtle
import math

def drawCircle(turtle_obj, center_x, center_y, radius):
    circumference_distance = 2.0 * math.pi * radius / 120.0

    turtle_obj.penup()
    turtle_obj.goto(center_x, center_y - radius)
    turtle_obj.pendown()

    for _ in range(120):
        turtle_obj.forward(circumference_distance)
        turtle_obj.left(3)

# Example usage
my_turtle = turtle.Turtle()
drawCircle(my_turtle, 0, 0, 100)

turtle.done()

import turtle

def drawFractalLine(turtle_obj, distance, angle, level):
    if level == 0:
        turtle_obj.forward(distance)
    else:
        distance /= 3
        drawFractalLine(turtle_obj, distance, angle, level - 1)
        turtle_obj.left(angle)
        drawFractalLine(turtle_obj, distance, angle, level - 1)
        turtle_obj.right(angle * 2)
        drawFractalLine(turtle_obj, distance, angle, level - 1)
        turtle_obj.left(angle)
        drawFractalLine(turtle_obj, distance, angle, level - 1)

def drawKochSnowflake(turtle_obj, initial_distance, level):
    for _ in range(3):
        drawFractalLine(turtle_obj, initial_distance, 120, level)
        turtle_obj.right(120)

# Example usage
my_turtle = turtle.Turtle()
my_turtle.speed(0)  # Set the turtle's speed to the fastest

drawKochSnowflake(my_turtle, 200, 3)

turtle.done()

import turtle
import random

def drawCCurve(turtle_obj, length, depth):
    if depth == 0:
        turtle_obj.forward(length)
    else:
        angle = random.randint(10, 90)  # Generate a random angle between 10 and 90 degrees

        drawCCurve(turtle_obj, length / 2, depth - 1)
        turtle_obj.right(angle)
        drawCCurve(turtle_obj, length / 2, depth - 1)
        turtle_obj.left(angle * 2)
        drawCCurve(turtle_obj, length / 2, depth - 1)
        turtle_obj.right(angle)
        drawCCurve(turtle_obj, length / 2, depth - 1)

def main():
    my_turtle = turtle.Turtle()
    my_turtle.speed(0)  # Set the turtle's speed to the fastest

    length = 400
    depth = 4

    # Set the turtle's pen colors to random RGB values
    my_turtle.pencolor(random.random(), random.random(), random.random())

    drawCCurve(my_turtle, length, depth)

    turtle.done()

if __name__ == '__main__':
    main()
