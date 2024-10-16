---
layout: post
title: "Tic Tac Toe Step2"
date: 2024-10-16
categories: blog
tags: [學習, 益智遊戲, Pygame]
---


```python

# Write your code here :-)

import pygame
from pygame.locals import *

pygame.init()

# set screen size and windows name
screen_width = 300
screen_height = 300
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Tic Tac Toe ")

# define variable
mark_list = []
line_width = 6
clicked = False
player = 1
gameover = False
winner = 0

# define color
red = (255, 0, 0)
green = (0, 255, 0)

def draw_grird():
    bg = (255, 255, 200)
    grid = (50, 50, 50)
    screen.fill(bg)
    for line in range(1, 3):
        pygame.draw.line(
            screen, grid, (0, line * 100), (screen_width, line * 100), line_width
        )
        pygame.draw.line(
            screen, grid, (line * 100, 0), (line * 100, screen_height), line_width
        )

def draw_markers():
    x_pos = 0
    for x in mark_list:
        y_pos = 0
        for y in x:
            if(y == 1):
                pygame.draw.line(screen, red, (x_pos * 100 + 15, y_pos * 100 + 15), (x_pos * 100 + 85, y_pos * 100 + 85), line_width)
                pygame.draw.line(screen, red, (x_pos * 100 + 85, y_pos * 100 + 15), (x_pos * 100 + 15, y_pos * 100 + 85), line_width)
            if(y == -1):
                pygame.draw.circle(screen, green, (x_pos * 100 + 50, y_pos * 100 + 50), 38, line_width)
            y_pos+=1
        x_pos+=1

def check_winner():
    for x in mark_list:
        if(sum(x) == 3):
            winner = 1
            gameover = True
            print(winner)
        elif(sum(x) == -3):
            winner = 2
            gameover = True
            print(winner)



for x in range(3):
    row = [0] * 3
    mark_list.append(row)



#main loop
run = True
while run:
    draw_grird()
    # add event handlers
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        if event.type == pygame.MOUSEBUTTONDOWN and clicked == False:
            clicked = True
        if event.type == pygame.MOUSEBUTTONUP and clicked == True:
            clicked = False
            pos = pygame.mouse.get_pos()
            mouse_x = pos[0]//100
            mouse_y = pos[1]//100
            #if array is empty, can put on player mark, and change player.
            if mark_list[mouse_x][mouse_y] == 0:
                mark_list[mouse_x][mouse_y] = player
                player = player * -1
    draw_markers()
    pygame.display.update()

pygame.quit()

