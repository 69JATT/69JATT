import pygame
import random

# Initialize Pygame
pygame.init()

# Set screen dimensions
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600

# Set colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
RED = (255, 0, 0)
GREEN = (0, 255, 0)
BLUE = (0, 0, 255)

# Set block dimensions and gap between blocks
BLOCK_SIZE = 50
GAP = 10

# Set grid dimensions
GRID_WIDTH = 8
GRID_HEIGHT = 8

# Set game speed
FPS = 30

# Set up the screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Candy Crush")

clock = pygame.time.Clock()

# Function to create the initial grid of candies
def create_grid():
    grid = []
    for i in range(GRID_WIDTH):
        column = []
        for j in range(GRID_HEIGHT):
            candy = random.choice([RED, GREEN, BLUE])
            column.append(candy)
        grid.append(column)
    return grid

# Function to draw the grid
def draw_grid(grid):
    for i in range(GRID_WIDTH):
        for j in range(GRID_HEIGHT):
            pygame.draw.rect(screen, grid[i][j], (i * (BLOCK_SIZE + GAP), j * (BLOCK_SIZE + GAP), BLOCK_SIZE, BLOCK_SIZE))

# Main game loop
def main():
    grid = create_grid()

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

        screen.fill(WHITE)
        draw_grid(grid)

        pygame.display.flip()
        clock.tick(FPS)

    pygame.quit()

if __name__ == "__main__":
    main()


