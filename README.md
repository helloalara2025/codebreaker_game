# codebreaker_game
Python implementation of the Mastermind game with an interactive UI and click/event driven play.

## How It Plays

The computer generates a secret 4-color code from 6 possible colors. You have 10 turns to guess it. After each guess, hint pegs show how close you were — black for correct color and position, red for correct color but wrong position.

## What I Focused On

- **Modular design** — each file has a single responsibility, making it easy to extend or swap components
- **Event-driven architecture** — all gameplay runs through a single `mouse_click()` handler that routes to the appropriate game logic
- **State management** — a central `game_state` dictionary tracks all mutable game data, avoiding global variables
- **Defensive input handling** — validates guesses before evaluation, handles edge cases like incomplete or duplicate selections

## Architecture

The project uses a modular design with clear separation of concerns:

```
mastermind_game.py      → Entry point, initializes game loop
game_logic.py           → Core game state, turn management, guess evaluation
game_ui_components.py   → Turtle-based UI layout, marble rendering, buttons
leaderboard.py          → Persistent score tracking (file I/O)
secret_code.py          → SecretCode class — random code generation
player_guess.py         → Guess class — input validation
row.py                  → Row class — manages guess/hint marble state per turn
Marble.py               → Marble class — individual game piece with position/color state
Point.py                → Point class — x/y coordinate positioning
```

All user interaction is event-driven through `screen.onclick()`, with a central `game_state` dictionary that tracks the current turn, guesses, and UI components throughout the session.

## Tech Stack

**Language:** Python 3  
**GUI:** Turtle graphics  
**Patterns:** OOP, event-driven programming, state management via dictionary  
**Testing:** unittest

## Run It

```bash
git clone https://github.com/helloalara2025/codebreaker-game.git
cd codebreaker-game
python mastermind_game.py
```

## Run Tests

```bash
python -m unittest test_mastermind_game.py
```

