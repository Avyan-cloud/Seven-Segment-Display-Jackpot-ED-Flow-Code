# Seven-Segment-Display-Jackpot-ED-Flow-Code
from machine import Pin
from time import sleep
import random

A = Pin(1, Pin.OUT)
B = Pin(2, Pin.OUT)
C = Pin(3, Pin.OUT)
D = Pin(4, Pin.OUT)
E = Pin(5, Pin.OUT)
F = Pin(6, Pin.OUT)
G = Pin(7, Pin.OUT)

buttonA = Pin(8, Pin.IN)
buttonB = Pin(9, Pin.IN)

while True:
    print('Welcome to the Seven Segment Display Jackpot ED!')
    sleep(0.1)
    print('Press the button to begin...\n')
    chances = 3
    total_score = 0
    print('Game Started! You have 3 chances.\n')
    print('Press button A to continue and B to end the game')
    while chances > 0:
      number = random.randint(0, 9)
      if buttonA.value() == 1:
        # Reset all segments
        A.value(0)
        B.value(0)
        C.value(0)
        D.value(0)
        E.value(0)
        F.value(0)
        G.value(0)
    
        # -------------------------------
        # Segment Control
        # -------------------------------
        if number == 0 or number == 2 or number == 3 or number == 5 or number == 6 or number == 7 or number == 8 or number == 9:
            A.value(1)
      
        if number == 0 or number == 1 or number == 2 or number == 3 or number == 4 or number == 7 or number == 8 or number == 9:
            B.value(1)  
      
        if number == 0 or number == 1 or number == 3 or number == 4 or number == 5 or number == 6 or number == 7 or number == 8 or number == 9:
            C.value(1)
      
        if number == 0 or number == 2 or number == 3 or number == 5 or number == 6 or number == 8 or number == 9:
            D.value(1)
      
        if number == 0 or number == 2 or number == 6 or number == 8:
            E.value(1)
      
        if number == 0 or number == 4 or number == 5 or number == 6 or number == 8 or number == 9:
            F.value(1)
      
        if number == 2 or number == 3 or number == 4 or number == 5 or number == 6 or number == 8 or number == 9:
            G.value(1)
    
        # Pause before next round
        sleep(1)
    
        total_score = total_score + number
        chances -= 1
        remaining_chances = chances
        chance_count = 4 - remaining_chances
 

        print('Chances', chance_count, ': You got', number, 'remaining chances:', remaining_chances)
        print('You got', number)
        sleep(1)
  
      if chances < 0:
        print('All chances used!')
        print('Total Score:', total_score)
        break
  
    if total_score <= 5:
        print("Bronze Reward: You got 150 coins.")
    elif total_score <= 10:
        print("Silver Reward: You got 300 coins.")
    elif total_score <= 15:
        print("Gold Reward: You got 500 coins.")
    elif total_score <= 20:
        print("Platinum Reward: You got 750 coins.")
    elif total_score <= 27:
        print("Diamond Reward: You got 1000 coins.")
    else:
        print("Wood Reward: You got 100 coins.")

    # -------------------------------
    # Play Again?
    # -------------------------------
    print("Would you like to play again? (y = buttonA, n = buttonB \n")
    if buttonB.value() == 1:
        print('Thank you for playing this awesome game! Goodbye!')
        break
    else:
      sleep(1)
      print('Restarting the game...\n')
      
      A.value(0)
      B.value(0)
      C.value(0)
      D.value(0)
      E.value(0)
      F.value(0)
      G.value(0)
      
      sleep(1)
