import pygame
import math
import random

# Initialize Pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Rotating Triangle with Bouncing Ball")

# Colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
COLORS = [
    (255, 0, 0), (0, 255, 0), (0, 0, 255),
    (255, 255, 0), (0, 255, 255), (255, 0, 255)
]

# Triangle properties
TRIANGLE_SIZE = 200
TRIANGLE_POS = (WIDTH // 2, HEIGHT // 2)
angle = 0.0 # Use float for angle
rotation_speed = 0.02  # Triangle rotation speed

# Ball properties
BALL_RADIUS = 15
ball_pos = [float(WIDTH // 2), float(HEIGHT // 2)]
ball_speed = [3.0, 3.0] # Use floats for ball speed
ball_color = random.choice(COLORS)

clock = pygame.time.Clock()

# Function definitions skipped for brevity, assuming included above

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                ball_speed[1] -= 0.5
            elif event.key == pygame.K_DOWN:
                ball_speed[1] += 0.5
            elif event.key == pygame.K_LEFT:
                ball_speed[0] -= 0.5
            elif event.key == pygame.K_RIGHT:
                ball_speed[0] += 0.5

    screen.fill(BLACK)

    angle += rotation_speed
    vertices = get_triangle_vertices(TRIANGLE_POS, TRIANGLE_SIZE, angle)
    pygame.draw.polygon(screen, WHITE, vertices, 2)

    ball_pos[0] += ball_speed[0]
    ball_pos[1] += ball_speed[1]

    collided, new_speed = check_collision_with_triangle(ball_pos, BALL_RADIUS, vertices, ball_speed)
    if collided:
        ball_speed = new_speed
        ball_color = random.choice(COLORS)

    pygame.draw.circle(screen, ball_color, (int(ball_pos[0]), int(ball_pos[1])), BALL_RADIUS)

    pygame.display.flip()
    clock.tick(60)

pygame.quit()
