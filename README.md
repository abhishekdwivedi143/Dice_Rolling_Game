# Dice_Rolling_Game

import random


# Function 1: roll the die n times
def roll_dice(n):
    rolls = []
    for i in range(n):
        rolls.append(random.randint(1, 6))
    return rolls


# Function 2: show frequency, total, average and most frequent
def show_result(rolls):
    # count[1] to count[6] store how many times each face came
    count = [0, 0, 0, 0, 0, 0, 0]
    for r in rolls:
        count[r] = count[r] + 1

    print("Frequency: 1:" + str(count[1]) + " | 2:" + str(count[2]) + " | 3:" + str(count[3]) +
          " | 4:" + str(count[4]) + " | 5:" + str(count[5]) + " | 6:" + str(count[6]))

    total = sum(rolls)
    average = total / len(rolls)
    print("Total:", total, "| Average:", f"{average:.2f}")

    # find the face(s) which came the most
    highest = max(count)
    winners = ""
    for face in range(1, 7):
        if count[face] == highest:
            if winners == "":
                winners = str(face)
            else:
                winners = winners + " and " + str(face)

    if highest == 1:
        times = "1 time"
    else:
        times = str(highest) + " times"

    if " and " in winners:
        times = times + " each"

    print("Most frequent: " + winners + " (" + times + ")")


# ---------------- Main program ----------------
play = "y"
while play == "y":

    n = input("Number of rolls: ")
    while not (n.isdigit() and 1 <= int(n) <= 1000):
        print("Invalid input. Enter a whole number from 1 to 1000.")
        n = input("Number of rolls: ")
    n = int(n)

    # type fixed rolls like 3, 6, 3, 1, 5 (for testing) or press Enter for random
    text = input("Rolls (press Enter for random): ")
    if text == "":
        rolls = roll_dice(n)
    else:
        rolls = []
        for x in text.replace(",", " ").split():
            rolls.append(int(x))

    show_result(rolls)

    play = input("Play again? (y/n): ")

print("Thanks for playing!")[code.py](https://github.com/user-attachments/files/34868897/code.py)


