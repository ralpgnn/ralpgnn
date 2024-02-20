import pygame
from pygame.locals import *
import sys

# Initialize Pygame
pygame.init()

# Set up screen
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Simple FPS Game")

# Set up colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Set up player
player_pos = [screen_width/2, screen_height/2]
player_speed = 5

# Main game loop
while True:
    # Handle events
    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            sys.exit()

    # Get keyboard input
    keys = pygame.key.get_pressed()
    if keys[K_w]:
        player_pos[1] -= player_speed
    if keys[K_s]:
        player_pos[1] += player_speed
    if keys[K_a]:
        player_pos[0] -= player_speed
    if keys[K_d]:
        player_pos[0] += player_speed

    # Draw everything
    screen.fill(BLACK)
    pygame.draw.circle(screen, WHITE, (int(player_pos[0]), int(player_pos[1])), 10)
    
    # Update display
    pygame.display.flip()
