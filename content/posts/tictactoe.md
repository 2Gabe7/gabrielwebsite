---
title: "Tic Tac Toe"
date: "2023-03-08"
author: "Gabriel"
cover: ""
description: "My attempt at making Tic Tac Toe using python"
hideComments: true
---

When making this I had just started learning python in school in a class call computer programming. Although it's a little clunky, I think I did pretty good for one of my first attempts at a game.

```python
import os
clear = lambda: os.system('clear')
clear()
 
# The tic tac toe board
board = [" ", " ", " ", " ", " ", " ", " ", " ", " "]
# Printing the ttt board
def ttt_board():
    print(board[0],"|",board[1],"|",board[2])
    print("--+---+--")
    print(board[3],"|",board[4],"|",board[5])
    print("--+---+--")
    print(board[6],"|",board[7],"|",board[8])

# Check for win function
def win(player):
    for i in range(3):
        # Check horizontils
        if board[i] == player and board[i+1] == player and board[i+2] == player: 
            return True
        # Check Verticals
        elif board[i] == player and board[i+3] == player and board[i+6] == player:
                return True
        # Check diagnals
        elif board[0] == player and board[4] == player and board[8] == player or  board[2] == player and board[4] == player and board[6] == player:
            return True
# Entire Game
print("")
game = 0
for j in range(9):
    player1 = 0
    while player1 == 0:
        # Player 1 move
        ttt_board()
        move = int(input("Where will X play?: ")) - 1
        if move != 0 or 1 or 2 or 3 or 4 or 5 or 6 or 7 or 8:
            clear()
            print("Invalid move, try again")
        move = int(move)          
        for i in range(9):
            if board[i] == " ":
                if move == i:
                    board[i] = "X"
                    player1 = 1
                    clear()
                    print("")
    # Check for win
    if win("X") == True:
        break
    # Player 2 move
    player2 = 0
    while player2 == 0:
        # Player 2 move
        ttt_board()
        move = int(input("Where will O play?: ")) - 1
        if move != 0 or 1 or 2 or 3 or 4 or 5 or 6 or 7 or 8:
            clear()
            print("Invalid move, try again")
        for i in range(9):
            if board[i] == " ":
                if move == i:
                    board[i] = "O"
                    player2 = 1
                    clear()
                    print("")
    # Check for win
    if win("O") == True:
        break

# Winning Sequence
clear()
if win("X") == True:
    print("Player X Wins!")
elif win("O") == True:
    print("Player O Wins!")
else:
    print("Tie")
ttt_board()

```
