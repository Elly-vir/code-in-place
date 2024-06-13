# code-in-place
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the display
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Dungeon Adventure")

# Colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Player attributes
player_size = 40
player_x = 50
player_y = HEIGHT // 2 - player_size // 2
player_speed = 5

# Main game loop
running = True
while running:
    # Event handling
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Player movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed
    
    # Boundary checking
    if player_x < 0:
        player_x = 0
    if player_x > WIDTH - player_size:
        player_x = WIDTH - player_size
    if player_y < 0:
        player_y = 0
    if player_y > HEIGHT - player_size:
        player_y = HEIGHT - player_size

    # Clear the screen
    screen.fill(BLACK)
    
    # Draw player
    pygame.draw.rect(screen, WHITE, (player_x, player_y, player_size, player_size))

    # Update the display
    pygame.display.update()

# Quit Pygame
pygame.quit()
sys.exit()
