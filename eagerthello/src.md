2024-12-21
# Eagerthello
```
O O O O O O O O
O O ■ ■ ■ ■ O O
O ■ ■ O O ■ ■ O
O ■ O O O O O O
O ■ O O ■ ■ ■ O
O ■ ■ O O ■ O O
O O ■ ■ ■ ■ O O
O O O O O O O O
```

I wrote a simple 25loc othello-playing script for an online hackathon-style competition.
For shits, I decided to forego any strategy and leave the bot to greedily pick the most instantly-gratifying disc that'd flank the most discs of the opponent.

You can view the script [here](https://github.com/AashvikTyagi/eagerthello/blob/main/bot.py) along with scripts to test it [against a human](https://github.com/AashvikTyagi/eagerthello/blob/main/test-human.py) and to [play against itself](https://github.com/AashvikTyagi/eagerthello/blob/main/test-bot.py).

Then again, it's only 25loc... here you go:
```python
def move(board_state, player_color: int):
    b, maxf = player_color, 0 # own color, max flanked
    for row in range(8):
        for col in range(8):
            if board_state[row][col]==0:
                dirs = [
                    d for d in ((-1,0), (1,0), (0,-1), (0,1), (-1,-1), (-1,1), (1,-1), (1,1))
                    if row+d[0] in range(8) and col+d[1] in range(8) # exists
                    and board_state [row+d[0]] [col+d[1]] == -b # oppo color
                ] # potentially flankable directions
                flanked = 0
                for d in dirs:
                    rcst, travelled = [row,col], 0
                    while 1: # raycast
                        rcst[0] += d[0]
                        rcst[1] += d[1]
                        try: rcstate = board_state [rcst[0]] [rcst[1]]
                        except IndexError: break # ray hit border
                        if rcstate == -b: travelled += 1
                        else: # ray hit
                            if rcstate == b and travelled: flanked += travelled
                            break
                if flanked>maxf: best, maxf = (row, col), flanked + row in (0, 7) and col in (0,7) # prefer corners
    try: return best
    except UnboundLocalError: pass # forfeit
```

(The competition asked for a python file with a move function they'd automatically call with the current `board_state` in a format they'd specified and that bot's `player_color`.)

Oh, how I love list comprehensions.
