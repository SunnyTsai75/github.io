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
game_over = False
winner = 0
chech_list = []

# define color
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 255)

# define font
font = pygame.font.SysFont(None, 40)

# define again rect
again_rect = Rect(screen_width // 2 -90, screen_height//2, 180, 60)


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
                pygame.draw.line(screen, red, (y_pos * 100 + 15, x_pos * 100 + 15), (y_pos * 100 + 85, x_pos * 100 + 85), line_width)
                pygame.draw.line(screen, red, (y_pos * 100 + 85, x_pos * 100 + 15), (y_pos * 100 + 15, x_pos * 100 + 85), line_width)
            if(y == -1):
                pygame.draw.circle(screen, green, (y_pos * 100 + 50, x_pos * 100 + 50), 38, line_width)
            y_pos+=1
        x_pos+=1

def check_winner():
    global winner
    global game_over

    y_pos = 0
    for x in mark_list:
        # count rows
        if(sum(x) == 3):
            winner = 1
            game_over = True
            print(winner)
        elif(sum(x) == -3):
            winner = 2
            game_over = True
            print(winner)
        # count columns
        if(mark_list[0][y_pos] + mark_list[1][y_pos] + mark_list[2][y_pos] == 3):
            winner = 1
            game_over = True
            print(winner)
        if(mark_list[0][y_pos] + mark_list[1][y_pos] + mark_list[2][y_pos] == -3):
            winner = 2
            game_over = True
            print(winner)
        y_pos += 1
    # Detect cross lines
    if(mark_list[0][0] + mark_list[1][1] + mark_list[2][2] == 3) or (mark_list[0][2] + mark_list[1][1] + mark_list[2][0] == 3):
        winner = 1
        game_over = True
        print(winner)
    if(mark_list[0][0] + mark_list[1][1] + mark_list[2][2] == -3) or (mark_list[0][2] + mark_list[1][1] + mark_list[2][0] == -3):
        winner = 2
        game_over = True
        print(winner)
    if(winner == 0) and len(chech_list) == 9 :
        game_over = True

def draw_winner(winner):
    win_txt = "Player %s Wins!" %(str(winner))
    win_img = font.render(win_txt, True, blue)
    # pygame.draw.rect(surface, color, rect, width, border_radius)
    pygame.draw.rect(screen, green, (screen_width // 2 - 110, screen_height//2 - 67.5, 220, 60))
    # surface.blit(source, dest, area, special_flags)
    screen.blit(win_img, (screen_width // 2 - 100, screen_height//2 - 50))

    again_txt = "Play Again?"
    again_img = font.render(again_txt, True, blue)
    pygame.draw.rect(screen, green, again_rect)
    screen.blit(again_img, (screen_width // 2  - 80, screen_height//2 + 20))

def reset_list():
    for x in range(3):
        row = [0] * 3
        mark_list.append(row)
        print(mark_list)


reset_list()

#main loop
run = True
while run:
    # add event handlers
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        if(game_over == False):
            if event.type == pygame.MOUSEBUTTONDOWN and clicked == False:
                clicked = True
            if event.type == pygame.MOUSEBUTTONUP and clicked == True:
                clicked = False
                pos = pygame.mouse.get_pos()
                mouse_x = pos[0]//100
                mouse_y = pos[1]//100
                # if array is empty, can put on player mark, and change player.
                # The video explains why the mark is placed upside down.
                if mark_list[mouse_y][mouse_x] == 0:
                    mark_list[mouse_y][mouse_x] = player
                    chech_list.append(player)
                    player = player * -1
                    check_winner()

    draw_grird()     # Draw the game grid
    draw_markers()    # Draw the markers (X or O)
    if(game_over == True):
        draw_winner(winner)
        if event.type == pygame.MOUSEBUTTONDOWN and clicked == False:
            clicked = True
        if event.type == pygame.MOUSEBUTTONUP and clicked == True:
            clicked = False
            pos = pygame.mouse.get_pos()
            # when again button clicked restart the game.
            if(again_rect.collidepoint(pos)):
                mark_list = []
                player = 1
                game_over = False
                winner = 0
                chech_list = []
                reset_list()


    pygame.display.update()

pygame.quit()
