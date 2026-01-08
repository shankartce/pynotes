---
title: Cricket Match
date: 2026-01-08
author: Your Name
cell_count: 2
score: 0
---

```python
# pylint: disable=missing-function-docstring, pointless-string-statement, missing-class-docstring

#Gonna try this using the game of chess

"""
@author: Shankar P

"""

import random
import time

canadian_player_names = [
    "Akhil Kumar",
    "Jaskaran Singh",
    "Shreyas Movva",
    "Saad Bin Zafar"
]

australian_player_names = [
    "Tim David",
    "Cummins",
    "Green"
]

team_a_name = "Canada"
team_b_name = "Australia"

# Cricket Constants
SLEEP_GAP_SECONDS = 0.7
OVERS_PER_INNINGS = 2

def get_random_player_name():

    return random.choice(canadian_player_names)

def print_line_gap():

    print(f"")

def get_random_run():
    # TODO: improve the weights so we can get wicket as well.
    # However, getting a wicket should be 1/25 balls.
    return random.randint(0, 6)

def play_single_ball(
    c_player_name,
    c_ball_index
):

    current_run = get_random_run()
    print(f"[{c_ball_index}]: {c_player_name} scored: {current_run}")

    return current_run

def play_single_over(team_name, over_index):

    current_player = get_random_player_name()

    score_this_over = 0
    for i in range(6):
        current_over_and_ball = f"{over_index}.{ (i+1)}"
        c_run = play_single_ball(current_player, current_over_and_ball)

        score_this_over += c_run
        time.sleep(SLEEP_GAP_SECONDS)

    print_line_gap()
    print(f"{team_name} Scored: {score_this_over} / 0 in {over_index+1} overs")

    return score_this_over
    

def play_single_innings(team_name):

    print(f"{team_name} is batting now!")
    print_line_gap()

    innings_score = 0
    for i in range(OVERS_PER_INNINGS):
        score_per_over = play_single_over(team_name, i)
        print('-' * 30)

        innings_score += score_per_over

    print(f"{team_name} Final Score: {innings_score}")

    return innings_score

def play_single_match():

    team_a_final_score = play_single_innings(team_a_name)
    print_line_gap()
    print_line_gap()
    team_b_final_score = play_single_innings(team_b_name)

    if(team_b_final_score > team_a_final_score):
        print(f"{team_b_name} wins")
    elif(team_b_final_score == team_a_final_score):
        print(f"It's a tie between {team_a_name} and {team_b_name}")
    else:
        print(f"{team_a_name} wins")

def startpy():
    # print("Tact101")

    # play_single_ball()

    # play_single_over()

    play_single_match()

if __name__ == "__main__":
    startpy()

# startpy()

```

    Canada is batting now!
    
    [0.1]: Saad Bin Zafar scored: 6
    [0.2]: Saad Bin Zafar scored: 2
    [0.3]: Saad Bin Zafar scored: 0
    [0.4]: Saad Bin Zafar scored: 6
    [0.5]: Saad Bin Zafar scored: 6
    [0.6]: Saad Bin Zafar scored: 6
    
    Canada Scored: 26 / 0 in 1 overs
    ------------------------------
    [1.1]: Akhil Kumar scored: 3
    [1.2]: Akhil Kumar scored: 4
    [1.3]: Akhil Kumar scored: 4
    [1.4]: Akhil Kumar scored: 6
    [1.5]: Akhil Kumar scored: 5
    [1.6]: Akhil Kumar scored: 3
    
    Canada Scored: 25 / 0 in 2 overs
    ------------------------------
    Canada Final Score: 51
    
    
    Australia is batting now!
    
    [0.1]: Shreyas Movva scored: 6
    [0.2]: Shreyas Movva scored: 2
    [0.3]: Shreyas Movva scored: 3
    [0.4]: Shreyas Movva scored: 4
    [0.5]: Shreyas Movva scored: 2
    [0.6]: Shreyas Movva scored: 3
    
    Australia Scored: 20 / 0 in 1 overs
    ------------------------------
    [1.1]: Saad Bin Zafar scored: 2
    [1.2]: Saad Bin Zafar scored: 1
    [1.3]: Saad Bin Zafar scored: 2
    [1.4]: Saad Bin Zafar scored: 2
    [1.5]: Saad Bin Zafar scored: 1
    [1.6]: Saad Bin Zafar scored: 5
    
    Australia Scored: 13 / 0 in 2 overs
    ------------------------------
    Australia Final Score: 33
    Canada wins
    


```python

```


---
**Score: 0**