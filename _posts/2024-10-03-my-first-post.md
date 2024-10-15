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
