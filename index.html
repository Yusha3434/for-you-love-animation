import math
import random
import pygame

# =========================================================
# SETTINGS
# =========================================================

WIDTH, HEIGHT = 1080, 1920
BACKGROUND_COLOR = (10, 5, 8)
FPS = 60

SCALE = 24
Y_OFFSET = 60

WORDS = ["i love you", "I LOVE YOU", "love you"]
CENTER_TEXT = "I Love you"

COLORS = [
    (255, 70, 35),
    (255, 130, 45),
    (255, 45, 45),
    (255, 190, 90),
    (255, 95, 60)
]


# =========================================================
# PARTICLE CLASS
# =========================================================

class Particle:
    __slots__ = (
        'x', 'y', 'order', 'kind', 'word',
        'color', 'alpha', 'flicker',
        'font', 'delay', 'size_mult'
    )

    def __init__(self, x, y, order, kind):
        self.x = x
        self.y = y
        self.order = order
        self.kind = kind
        self.word = random.choice(WORDS)
        self.color = random.choice(COLORS)
        self.alpha = 0
        self.flicker = random.uniform(0, math.pi * 2)
        self.font = None
        self.delay = 0
        self.size_mult = random.uniform(0.85, 1.15)


# =========================================================
# HEART MATH
# =========================================================

def heart_xy(t):
    x = 16 * (math.sin(t) ** 3)

    y = (
        13 * math.cos(t)
        - 5 * math.cos(2 * t)
        - 2 * math.cos(3 * t)
        - math.cos(4 * t)
    )

    return x, -y


def to_screen(x, y):
    return (
        x * SCALE + WIDTH / 2,
        y * SCALE + HEIGHT / 2 + Y_OFFSET
    )


# =========================================================
# BUILD HEART PARTICLES
# =========================================================

def build_outline_particles(n_outline, min_gap=34):

    particles = []
    placed = []

    for i in range(n_outline):

        t = (i / n_outline) * 2 * math.pi

        bx, by = heart_xy(t)

        sx, sy = to_screen(bx, by)

        if any(
            math.hypot(sx - px, sy - py) < min_gap
            for (px, py) in placed
        ):
            continue

        placed.append((sx, sy))

        particles.append(
            Particle(
                sx,
                sy,
                i,
                "outline"
            )
        )

    return particles


def build_fill_particles(n_fill, min_gap=46):

    particles = []
    placed = []

    attempts = 0
    max_attempts = n_fill * 80

    while len(particles) < n_fill and attempts < max_attempts:

        attempts += 1

        t = random.uniform(0, 2 * math.pi)

        r = random.uniform(0.0, 0.86)

        bx, by = heart_xy(t)

        px, py = bx * r, by * r

        sx, sy = to_screen(px, py)

        if any(
            math.hypot(sx - qx, sy - qy) < min_gap
            for (qx, qy) in placed
        ):
            continue

        placed.append((sx, sy))

        particles.append(
            Particle(
                sx,
                sy,
                random.randint(0, 320),
                "fill"
            )
        )

    return particles


# =========================================================
# GLOW TEXT
# =========================================================

def draw_glow_text(
    glow_layer,
    screen_layer,
    font,
    word,
    color,
    x,
    y,
    alpha,
    size_mult=1.0
):

    if alpha <= 0:
        return

    if size_mult != 1.0:

        scaled_font = pygame.font.Font(
            None,
            int(font.get_height() * size_mult)
        )

        txt = scaled_font.render(
            word,
            True,
            color
        )

    else:

        txt = font.render(
            word,
            True,
            color
        )

    txt.set_alpha(alpha)

    txt_rect = txt.get_rect(
        center=(x, y)
    )

    # Big glow
    if alpha > 10:

        glow_big = pygame.transform.smoothscale(
            txt,
            (
                int(txt.get_width() * 2.4),
                int(txt.get_height() * 2.4)
            )
        )

        glow_big.set_alpha(
            max(0, alpha // 7)
        )

        glow_rect = glow_big.get_rect(
            center=(x, y)
        )

        glow_layer.blit(
            glow_big,
            glow_rect
        )

        # Small glow
        glow_small = pygame.transform.smoothscale(
            txt,
            (
                int(txt.get_width() * 1.6),
                int(txt.get_height() * 1.6)
            )
        )

        glow_small.set_alpha(
            max(0, alpha // 3)
        )

        glow_rect = glow_small.get_rect(
            center=(x, y)
        )

        glow_layer.blit(
            glow_small,
            glow_rect
        )

    screen_layer.blit(
        txt,
        txt_rect
    )


# =========================================================
# DRAW HEART SHAPE
# =========================================================

def draw_small_heart(surface, x, y, size, alpha):

    heart_surface = pygame.Surface(
        (size * 2, size * 2),
        pygame.SRCALPHA
    )

    color = (
        255,
        90,
        150,
        alpha
    )

    pygame.draw.circle(
        heart_surface,
        color,
        (int(size * 0.65), int(size * 0.65)),
        int(size * 0.45)
    )

    pygame.draw.circle(
        heart_surface,
        color,
        (int(size * 1.35), int(size * 0.65)),
        int(size * 0.45)
    )

    pygame.draw.polygon(
        heart_surface,
        color,
        [
            (int(size * 0.22), int(size * 0.78)),
            (int(size * 1.78), int(size * 0.78)),
            (int(size), int(size * 1.75))
        ]
    )

    rect = heart_surface.get_rect(
        center=(int(x), int(y))
    )

    surface.blit(
        heart_surface,
        rect
    )


# =========================================================
# INTRO FLOATING HEARTS
# =========================================================

class FloatingHeart:

    def __init__(self):

        self.x = random.randint(
            40,
            WIDTH - 40
        )

        self.y = random.randint(
            0,
            HEIGHT
        )

        self.speed = random.uniform(
            0.4,
            1.2
        )

        self.size = random.randint(
            7,
            20
        )

        self.alpha = random.randint(
            50,
            150
        )

        self.wave = random.uniform(
            0,
            math.pi * 2
        )

    def update(self):

        self.y -= self.speed

        self.x += math.sin(
            pygame.time.get_ticks() * 0.001
            + self.wave
        ) * 0.3

        if self.y < -40:

            self.y = HEIGHT + 40

            self.x = random.randint(
                40,
                WIDTH - 40
            )

    def draw(self, surface):

        pulse = 1 + (
            0.15 *
            math.sin(
                pygame.time.get_ticks() * 0.004
                + self.wave
            )
        )

        size = int(
            self.size * pulse
        )

        draw_small_heart(
            surface,
            self.x,
            self.y,
            size,
            self.alpha
        )


# =========================================================
# INTRO SCREEN
# =========================================================

def intro_screen(screen, clock):

    # Romance fonts
    title_font = pygame.font.SysFont(
        "georgia",
        105,
        bold=True,
        italic=True
    )

    subtitle_font = pygame.font.SysFont(
        "georgia",
        32,
        italic=True
    )

    button_font = pygame.font.SysFont(
        "georgia",
        42,
        bold=True,
        italic=True
    )

    small_font = pygame.font.SysFont(
        "arial",
        24
    )

    # Floating hearts
    hearts = [
        FloatingHeart()
        for _ in range(35)
    ]

    # Button
    button_width = 300
    button_height = 95

    button_rect = pygame.Rect(
        WIDTH // 2 - button_width // 2,
        HEIGHT // 2 + 250,
        button_width,
        button_height
    )

    start_time = pygame.time.get_ticks()

    running = True

    while running:

        mouse_pos = pygame.mouse.get_pos()

        for event in pygame.event.get():

            if event.type == pygame.QUIT:

                return False

            if event.type == pygame.KEYDOWN:

                if event.key == pygame.K_ESCAPE:

                    return False

            if event.type == pygame.MOUSEBUTTONDOWN:

                if event.button == 1:

                    if button_rect.collidepoint(
                        event.pos
                    ):

                        return True

        # Background
        screen.fill(
            (12, 5, 10)
        )

        # Time animation
        elapsed = (
            pygame.time.get_ticks()
            - start_time
        )

        # Floating hearts
        for heart in hearts:

            heart.update()

            heart.draw(screen)

        # -------------------------------------------------
        # TITLE
        # -------------------------------------------------

        title_y = (
            HEIGHT // 2
            - 180
            + math.sin(
                elapsed * 0.002
            ) * 8
        )

        title_surface = title_font.render(
            "For You",
            True,
            (255, 235, 242)
        )

        title_rect = title_surface.get_rect(
            center=(
                WIDTH // 2,
                int(title_y)
            )
        )

        # Title glow
        glow_title = pygame.transform.smoothscale(
            title_surface,
            (
                int(title_surface.get_width() * 1.25),
                int(title_surface.get_height() * 1.25)
            )
        )

        glow_title.set_alpha(40)

        glow_rect = glow_title.get_rect(
            center=title_rect.center
        )

        screen.blit(
            glow_title,
            glow_rect
        )

        screen.blit(
            title_surface,
            title_rect
        )

        # -------------------------------------------------
        # HEART UNDER TITLE
        # -------------------------------------------------

        heart_pulse = (
            1
            + 0.12 * math.sin(
                elapsed * 0.006
            )
        )

        draw_small_heart(
            screen,
            WIDTH // 2,
            int(title_y + 115),
            int(25 * heart_pulse),
            230
        )

        # -------------------------------------------------
        # SUBTITLE
        # -------------------------------------------------

        subtitle = subtitle_font.render(
            "A little something made with love",
            True,
            (230, 190, 205)
        )

        subtitle_rect = subtitle.get_rect(
            center=(
                WIDTH // 2,
                int(title_y + 180)
            )
        )

        screen.blit(
            subtitle,
            subtitle_rect
        )

        # -------------------------------------------------
        # OPEN BUTTON
        # -------------------------------------------------

        hovering = button_rect.collidepoint(
            mouse_pos
        )

        pulse = (
            1
            + 0.025 * math.sin(
                elapsed * 0.005
            )
        )

        current_width = int(
            button_width * pulse
        )

        current_height = int(
            button_height * pulse
        )

        current_rect = pygame.Rect(
            WIDTH // 2 - current_width // 2,
            button_rect.centery - current_height // 2,
            current_width,
            current_height
        )

        if hovering:

            button_color = (
                255,
                80,
                135
            )

            border_color = (
                255,
                210,
                225
            )

        else:

            button_color = (
                190,
                45,
                95
            )

            border_color = (
                255,
                120,
                165
            )

        # Button glow
        glow_rect = current_rect.inflate(
            30,
            30
        )

        glow_surface = pygame.Surface(
            (
                glow_rect.width,
                glow_rect.height
            ),
            pygame.SRCALPHA
        )

        pygame.draw.rounded_rect(
            glow_surface,
            (
                255,
                60,
                130,
                35
            ),
            glow_surface.get_rect(),
            30
        )

        screen.blit(
            glow_surface,
            glow_rect
        )

        # Button
        pygame.draw.rect(
            screen,
            button_color,
            current_rect,
            border_radius=25
        )

        pygame.draw.rect(
            screen,
            border_color,
            current_rect,
            width=3,
            border_radius=25
        )

        # Button text
        button_text = button_font.render(
            "OPEN",
            True,
            (255, 245, 250)
        )

        button_text_rect = button_text.get_rect(
            center=current_rect.center
        )

        screen.blit(
            button_text,
            button_text_rect
        )

        # Small instruction
        instruction = small_font.render(
            "Tap OPEN to reveal your message",
            True,
            (170, 130, 145)
        )

        instruction_rect = instruction.get_rect(
            center=(
                WIDTH // 2,
                current_rect.bottom + 60
            )
        )

        screen.blit(
            instruction,
            instruction_rect
        )

        pygame.display.flip()

        clock.tick(FPS)


# =========================================================
# LOVE HEART ANIMATION
# =========================================================

def love_animation(screen, clock):

    font_outline = pygame.font.SysFont(
        "arial",
        20,
        bold=True
    )

    font_fill = pygame.font.SysFont(
        "arial",
        17,
        bold=True
    )

    font_center = pygame.font.SysFont(
        "georgia",
        54,
        bold=True,
        italic=True
    )

    background = pygame.Surface(
        (WIDTH, HEIGHT)
    )

    background.fill(
        BACKGROUND_COLOR
    )

    outline = build_outline_particles(
        n_outline=160
    )

    fill = build_fill_particles(
        n_fill=130
    )

    outline_span = (
        max(
            p.order
            for p in outline
        )
        if outline
        else 0
    )

    frames_per_step = 1.6

    fill_start_frame = (
        int(
            outline_span
            * frames_per_step
        )
        + 30
    )

    for p in fill:

        p.delay = (
            fill_start_frame
            + p.order
        )

    for p in outline:

        p.delay = int(
            p.order
            * frames_per_step
        )

    particles = outline + fill

    for p in particles:

        p.font = (
            font_outline
            if p.kind == "outline"
            else font_fill
        )

    frame = 0

    glow_layer = pygame.Surface(
        (WIDTH, HEIGHT),
        pygame.SRCALPHA
    )

    text_layer = pygame.Surface(
        (WIDTH, HEIGHT),
        pygame.SRCALPHA
    )

    running = True

    while running:

        for event in pygame.event.get():

            if event.type == pygame.QUIT:

                return False

            if event.type == pygame.KEYDOWN:

                if event.key == pygame.K_ESCAPE:

                    return False

        screen.blit(
            background,
            (0, 0)
        )

        glow_layer.fill(
            (0, 0, 0, 0)
        )

        text_layer.fill(
            (0, 0, 0, 0)
        )

        frame += 1

        # -------------------------------------------------
        # HEART PARTICLES
        # -------------------------------------------------

        for p in particles:

            if (
                frame > p.delay
                and p.alpha < 255
            ):

                p.alpha = min(
                    255,
                    p.alpha
                    + 14
                    + random.randint(0, 4)
                )

            if p.alpha >= 255:

                flick = (
                    0.75
                    + 0.25
                    * math.sin(
                        frame * 0.04
                        + p.flicker
                    )
                )

            else:

                flick = 1.0

            alpha = int(
                p.alpha * flick
            )

            if alpha <= 0:

                continue

            draw_glow_text(
                glow_layer,
                text_layer,
                p.font,
                p.word,
                p.color,
                p.x,
                p.y,
                alpha,
                p.size_mult
            )

        screen.blit(
            glow_layer,
            (0, 0)
        )

        screen.blit(
            text_layer,
            (0, 0)
        )

        # -------------------------------------------------
        # CENTER MESSAGE
        # -------------------------------------------------

        center_start = (
            fill_start_frame
            + 200
        )

        if frame > center_start:

            progress = min(
                1.0,
                (
                    frame
                    - center_start
                ) / 60
            )

            center_alpha = int(
                255
                * (
                    1
                    - math.exp(
                        -progress * 8
                    )
                )
            )

            pulse = (
                1.0
                + 0.025
                * math.sin(
                    frame * 0.05
                )
            )

            center_surf = font_center.render(
                CENTER_TEXT,
                True,
                (255, 250, 245)
            )

            new_width = int(
                center_surf.get_width()
                * pulse
            )

            new_height = int(
                center_surf.get_height()
                * pulse
            )

            if (
                new_width > 0
                and new_height > 0
            ):

                center_surf = (
                    pygame.transform.smoothscale(
                        center_surf,
                        (
                            new_width,
                            new_height
                        )
                    )
                )

            center_surf.set_alpha(
                center_alpha
            )

            if center_alpha > 10:

                glow_center = (
                    pygame.transform.smoothscale(
                        center_surf,
                        (
                            int(
                                center_surf.get_width()
                                * 1.4
                            ),
                            int(
                                center_surf.get_height()
                                * 1.4
                            )
                        )
                    )
                )

                glow_center.set_alpha(
                    center_alpha // 5
                )

                glow_rect = (
                    glow_center.get_rect(
                        center=(
                            WIDTH / 2,
                            HEIGHT / 2
                        )
                    )
                )

                screen.blit(
                    glow_center,
                    glow_rect
                )

            text_rect = (
                center_surf.get_rect(
                    center=(
                        WIDTH / 2,
                        HEIGHT / 2
                    )
                )
            )

            screen.blit(
                center_surf,
                text_rect
            )

        pygame.display.flip()

        clock.tick(FPS)

    return False


# =========================================================
# MAIN
# =========================================================

def main():

    pygame.init()

    screen = pygame.display.set_mode(
        (WIDTH, HEIGHT)
    )

    pygame.display.set_caption(
        "For You ❤️"
    )

    clock = pygame.time.Clock()

    # First show Intro Screen
    opened = intro_screen(
        screen,
        clock
    )

    # If OPEN is clicked
    if opened:

        love_animation(
            screen,
            clock
        )

    pygame.quit()


# =========================================================
# RUN
# =========================================================

if __name__ == "__main__":

    try:

        main()

    except Exception as e:

        print(
            "OCURRIO UN ERROR:",
            e
        )

        import traceback

        traceback.print_exc()
