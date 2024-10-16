---
layout: post
title: "Tic Tac Toe Step1"
date: 2024-10-03
categories: blog
tags: [學習, 益智遊戲, Pygame]
---


import pygame  
from pygame.locals import *  

pygame.init()

screen_width = 300
screen_height = 300
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Tic Tac Toe ")

mark_list = []
line_width = 6
 
def draw_grird():
    bg = (255, 255, 200)
    grid = (50, 50, 50)
    screen.fill(bg)
    for line in range(1, 3):
        pygame.draw.line(screen, grid, (0, line * 100), (screen_width, line * 100), line_width)
        pygame.draw.line(screen, grid, (line * 100, 0), (line * 100, screen_height), line_width)

for x in range(3):
    row = [0] * 3
    mark_list.append(row)

run = True
while run:
    draw_grird()
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
    pygame.display.update()

pygame.quit()
