---
title: "Connect 4"
date: "2023-03-10"
author: "Gabriel"
cover: ""
description: "My attempt at making Connect 4 in python"
hideComments: true
---

When making Connect 4; I used what I learned from Tic Tac Toe to check for the win, although the math was a little confusing because of the way I set the board up at the start, and I was too far in to switch it. (You can see it in the diagnol check wins) It was a fun challenge to figure out how each piece is dropped in, and test outcomes till I was confident it all worked.

```python
import os
clear = lambda: os.system('clear')
clear()

# Make the board using [x][y]
row6 = ["  ","  ","  ","  ","  ","  ","  "]
row5 = ["  ","  ","  ","  ","  ","  ","  "]
row4 = ["  ","  ","  ","  ","  ","  ","  "]
row3 = ["  ","  ","  ","  ","  ","  ","  "]
row2 = ["  ","  ","  ","  ","  ","  ","  "]
row1 = ["  ","  ","  ","  ","  ","  ","  "]
row = ["0",row1,row2,row3,row4,row5,row6]

# Function to print the connect four board
def c4_board():
    print("            Connect Four         ")
    print("- 1  - 2  - 3  - 4  - 5  - 6  - 7  -",)   
    print("+----+----+----+----+----+----+----+")
    print("|",row[6][0],"|",row[6][1],"|",row[6][2],"|",row[6][3],"|",row[6][4],"|",row[6][5],"|",row[6][6],"|")
    print("+----+----+----+----+----+----+----+")
    print("|",row[5][0],"|",row[5][1],"|",row[5][2],"|",row[5][3],"|",row[5][4],"|",row[5][5],"|",row[5][6],"|")
    print("+----+----+----+----+----+----+----+")
    print("|",row[4][0],"|",row[4][1],"|",row[4][2],"|",row[4][3],"|",row[4][4],"|",row[4][5],"|",row[4][6],"|")
    print("+----+----+----+----+----+----+----+")
    print("|",row[3][0],"|",row[3][1],"|",row[3][2],"|",row[3][3],"|",row[3][4],"|",row[3][5],"|",row[3][6],"|")
    print("+----+----+----+----+----+----+----+")
    print("|",row[2][0],"|",row[2][1],"|",row[2][2],"|",row[2][3],"|",row[2][4],"|",row[2][5],"|",row[2][6],"|")
    print("+----+----+----+----+----+----+----+")
    print("|",row[1][0],"|",row[1][1],"|",row[1][2],"|",row[1][3],"|",row[1][4],"|",row[1][5],"|",row[1][6],"|")
    print("+----+----+----+----+----+----+----+")
    
# Function to check for a win
def check_win(player):
    global win
    
    # Check Horizontal
    for j in range(1,6):
        for i in range(1,5):
            if row[j][i-1] == player and row[j][i+0] == player and row[j][i+1] == player and row[j][i+2] == player:
                clear()
                print(player,"wins!")
                win = 1
                
    # Check Vertical
    for j in range(7):
        for i in range(1,4):
            if row[i][j] == player and row[i+1][j] == player and row[i+2][j] == player and row[i+3][j] == player:
                clear()
                print(player,"wins!")
                win = 1
                
    # Check diagnal up
    for j in range(3):
        for i in range(4):
            if row[j+1][i+0] == player and row[j+2][i+1] == player and row[j+3][i+2] == player and row[j+4][i+3] == player:
                clear()
                print(player,"wins!")
                win = 1
                
    # Check diagnal down
    for j in range(3):
        for i in range(4):
            if row[j+4][i+0] == player and row[j+3][i+1] == player and row[j+2][i+2] == player and row[j+1][i+3] == player:
                clear()
                win = 1
                
#Function to go through each player's turn
def player_turn(player):
    turn = 0
    while turn == 0:
        turn = 1
        # Player's Input
        c4_board()
        print("It is "+player+"'s turn")
        move = input("Where would you like to play?: ")
        clear()
        # CHeck if valid move
        if move == "1" or move == "2" or move == "3" or move == "4" or move == "5" or move == "6" or move == "7":
            move = int(move)
            
            # Put players piece where they moved
            move -= 1
            for i in range(7):
                if move == i:
                    print("")
                    if row[1][i] == "  ":
                        row[1][i] = player
                    elif row[2][i] == "  ":
                        row[2][i] = player
                    elif row[3][i] == "  ":
                        row[3][i] = player 
                    elif row[4][i] == "  ":
                        row[4][i] = player
                    elif row[5][i] == "  ":
                        row[5][i] = player
                    elif row[6][i] == "  ":
                        row[6][i] = player
                    else:
                        clear()
                        print("Invalid move, Try again.")
                        turn = 0
        else:
            print("Invalid move, Try again.")
            turn = 0
    check_win(player)
    
print("")
# Game play steps
win = 0
while win == 0:
    player_turn("🔴 ")
    if win == 1:
        break
    player_turn("🔵 ")
    if win == 1:
        break
c4_board()
```
