---
layout: post
title: Coding a TicTacToe game in Python
date: 2022-11-26 10:00:09 +0200
categories: programming
image: post_7.jpg
caption: <a href="https://www.freepik.com/free-vector/decision-fatigue-concept-illustration_24488359.htm#query=tired&position=9&from_view=search&track=sph">Image by storyset</a>
---
Last week, I was wondering what kind of post I will write for today.

Fortunally, I have worked on a challenge offer by the Python Institute on which you can find more informations [here](https://pythoninstitute.org/).

Challenge occurs at the end of the first part of the Python fundamentals.
It consists in creating a tic-tac-toe game which you can run from the command line.

## 1. Drawing the board

First, the initial **board** variable corresponds to :

```py
board = [[1,2,3],[4,"X",6],[7,8,9]]
```

Then, I struggle trying to not to write an awfull syntax for drawing the board.

```py
def display_board(board) -> str:
    tabl = "|"+"\t|"*3
    hyphl = ("+"+"-"*7)*3+"+"
    layer1 = [board[0][_] for _ in range(3)]
    layer2 = [board[1][_] for _ in range(3)]
    layer3 = [board[2][_] for _ in range(3)]
    val = lambda x: "|".ljust(4) + f"{x}".ljust(4)
    row1 = [hyphl, tabl, val(layer1[0]) + val(layer1[1]) + val(layer1[2])+"|", tabl, hyphl]
    row2 = [tabl, val(layer2[0]) + val(layer2[1]) + val(layer2[2]) + "|", tabl, hyphl]
    row3 = [tabl, val(layer3[0]) + val(layer3[1]) + val(layer3[2]) + "|", tabl ,hyphl]
    board = [row1,row2,row3]
    for _ in range(3):
        print("\n".join(board[_]))
```

## 2. Scanning the board

Firstly, I was not doing the job in the right way.

Although this snippet was a draft, It helps to understand how I solve the problem about linking the letters to their coordinates.

The following snippet outputs a dictionary where I have generated the value with itertools built-in library.

```py
from itertools import permutations,combinations_with_replacement

def dictionary_fields() -> dict:
    key = [str(_) for _ in range(1,10)]
    key[4] = "X"
    value1 = set(permutations([str(_) for _ in range(3)],2))
    value2 = set(combinations_with_replacement([str(_) for _ in range(3)],2))
    value = sorted(list(value1 | value2))
    d = dict(zip(key,value))
    return d
```

Output expected:

```sh
{'1': ('0', '0'), '2': ('0', '1'), '3': ('0', '2'), '4': ('1', '0'), 'X': ('1', '1'), '6': ('1', '2'), '7': ('2', '0'), '8': ('2', '1'), '9': ('2', '2')}
```

I kept the idea of using a dictionary.

```py
def make_list_of_free_fields(board) -> list:
    brwrow1,brwrow2,brwrow3 = [], [], []
    for _ in board[0]:
        # keep just the integer items and replace the string by a None value
        if isinstance(_, int):
            brwrow1.append((0, board[0].index(_)))
        else:
            brwrow1.append(None)
    for _ in board[1]:
        if isinstance(_,int):
            brwrow2.append((1, board[1].index(_)))
        else:
            brwrow2.append(None)
    for _ in board[2]:
        if isinstance(_,int):
            brwrow3.append((2, board[2].index(_)))
        else:
            brwrow3.append(None)
    return [brwrow1,brwrow2,brwrow3]
```

Output expected:

```sh
[[(0, 0), (0, 1), (0, 2)], [(1, 0), None, (1, 2)], [(2, 0), (2, 1), (2, 2)]]
```

## 3. The moves

The game start with the board full with digit from 1 to 9.
The fifth box is marked with a cross.
So the first turn is for yours.

### 3.1 User moves

```py
def enter_move(board) -> list:
    user_input = input("Enter a number or enter 'q' to quit : ")
    freeflds = make_list_of_free_fields(board)
    digits_key = [str(_) for _ in range(1,10)]
    if str(user_input) in digits_key:
        d = dict(zip(digits_key, freeflds[0] + freeflds[1] + freeflds[2]))
        # checking for None value
        if bool(d[str(user_input)]):
            crd = d[str(user_input)]
            # update the board with the correct sign
            board[int(crd[0])][int(crd[1])] = "O"
            del d[str(user_input)]
            display_board(board)
            return board
        else:
            print("Enter a correct number")
            return enter_move(board)
    elif str(user_input).lower() == 'q':
        exit()
    else:
        print("Enter a correct number")
        return enter_move(board)
```

### 3.2 Computer moves

We are going to use the built-in random module.

Make the import as usual.

```py
from random import randint
```

I use the same logic as in the user move function, changing the update with a while loop.

```py
def draw_move(board) -> list:
    freeflds = make_list_of_free_fields(board)
    digits_key = [str(_) for _ in range(1,10)]
    start_bot = True
    while start_bot:
        bot_input = randint(1,9)
        d = dict(zip(digits_key,freeflds[0] + freeflds[1] + freeflds[2]))
        if bool(d[str(bot_input)]):
            crd = d[str(bot_input)]
            board[int(crd[0])][int(crd[1])] = "X"
            del d[str(bot_input)]
            display_board(board)
            start_bot = False
            return board
        else:
            start_bot = True
```

## 4. Win or loose

I use some string manipulations to get the result.

```py
def victory_for(board, sign=["XXX","OOO"]) -> str:
    row1 = ["".join(str(_)) for _ in board[0]]
    row2 = ["".join(str(_)) for _ in board[1]]
    row3 = ["".join(str(_)) for _ in board[2]]
    row1 = "".join(row1)
    row2 = "".join(row2)
    row3 = "".join(row3)
    result = row1 + row2 + row3
    rows_check = lambda x: [x[0:3], x[3:6], x[6:]]
    cols_check = lambda x: [x[0]+ x[3] + x[6], x[1] + x[4] + x[7], x[2] + x[5] + x[8]]
    diags_check = lambda x: [x[0] + x[4] + x[-1], x[2] + x[4] + x[6]]
    result1 = rows_check(result)
    result2 = cols_check(result)
    result3 = diags_check(result)
    bot,user = sign[0], sign[1]
    if user in result1 or user in result2 or user in result3:
        print("User Win")
        exit()
    if bot in result1 or bot in result2 or bot in result3:
        print("Bot Win")
        exit()
```

## 5. Makes all work

Finally, I define the last main function.

```py
def main(board):
    display_board(board)
    STARTGAME = True
    while STARTGAME:
        enter_move(board)
        draw_move(board)
        victory_for(board)
```

## 6. Conclusion

You can find all the code on my GitHub [CMagnac](https://github.com/CMagnac/TicTacToe).

Enjoy 🤙
