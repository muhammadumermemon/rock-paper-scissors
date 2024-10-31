# Rock, Paper, Scissors Game

This repository contains a simple command-line Rock, Paper, Scissors game written in Python. The game allows a user to play against the computer.

## Requirements

- Python 3.x

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

## Usage

1. **Run the game:**

    Execute the script using Python:

    ```bash
    python script.py
    ```

2. **Gameplay:**

    - The game will prompt you to enter your choice (rock, paper, or scissors).
    - The computer will randomly select its choice.
    - The result of the game (win, lose, or tie) will be displayed.

## Example

Here's an example of how the game works:

```python
import random

def get_user_choice():
    user_choice = input("Enter your choice (rock, paper, scissors): ").lower()
    while user_choice not in ['rock', 'paper', 'scissors']:
        user_choice = input("Invalid choice. Please enter rock, paper, or scissors: ").lower()
    return user_choice

def get_computer_choice():
    choices = ['rock', 'paper', 'scissors']
    return random.choice(choices)

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == 'rock' and computer_choice == 'scissors') or \
         (user_choice == 'paper' and computer_choice == 'rock') or \
         (user_choice == 'scissors' and computer_choice == 'paper'):
        return "You win!"
    else:
        return "You lose!"

def play_game():
    user_choice = get_user_choice()
    computer_choice = get_computer_choice()
    print(f"\nYou chose: {user_choice}")
    print(f"Computer chose: {computer_choice}")
    result = determine_winner(user_choice, computer_choice)
    print(result)

if __name__ == "__main__":
    play_game()
