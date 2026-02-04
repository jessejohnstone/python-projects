## the first project is to toss a die/dice
this the code bellow 
##import random
def roll_die():
    return random.randint(1, 6)
def main():
    while True:
        choice = input("Roll the die? (y/n): ").lower()
        if choice == 'y':
            result = roll_die()
            print(f'You rolled a {result}!')
        elif choice == 'n':
            print("Thanks for playing!")
            break
        else:
            print("Invalid input. Please enter 'y' or 'n'.")
if __name__ == "__main__":
    main()
## THIS THE END OF THE CODE FOR PROJECT ONE

SAME GAME BUT AN IMPROVEMENT OF THE FIRST
For the second phase, let's add a guessing element to the game. In this, the player will guess the number they think the die will land on, and if they're correct, they'll earn points. We can also keep track of the score and let the player play multiple rounds
 THIS THE CODE BELOW
  
   
   import random
def roll_die():
    return random.randint(1, 6)

def main():
    score = 0
    while True:
        guess_input = input("Guess the number (1-6): ")
        if not guess_input.isdigit() or not (1 <= int(guess_input) <= 6):
            print("Please enter a number between 1 and 6.")
            continue

        guess = int(guess_input)
        result = roll_die()
        print(f'The die landed on {result}.')

        if guess == result:
            print("Correct! You earn 1 point.")
            score += 1
        else:
            print("Wrong guess. No points earned.")

        print(f'Current score: {score}')
continue_choice = input("Do you want to play another round? (y/n): ").lower()
        if continue_choice != 'y':
            print(f"Final score: {score}. Thanks for playing!")
break

if __name__ == "__main__":
    main()


END OF THE FIST PROJECT WITH AN IMPROVEMRNT OF IT




.
