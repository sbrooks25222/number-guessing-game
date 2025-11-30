import random

def play_game():
    secret_number = random.randint(1, 10)
    guess_count = 0
    max_guesses = 5  # Optional: set a limit

    print("\nLet's play a guessing game!!")
    print("I'm thinking of a number between 1 and 10.")

    while True:
        try:
            guess = int(input("Enter your guess: "))
        except ValueError:
            print("❌ Please enter a valid number!")
            continue

        if guess < 1 or guess > 10:
            print("⚠ Guess must be between 1 and 10!")
            continue

        guess_count += 1

        if guess == secret_number:
            if guess_count == 1:
                print("🎉 Amazing guess! You got it on the first try!")
            else:
                print(f"🎯 Well done! You guessed it in {guess_count} tries!")
            break
        elif guess < secret_number:
            print("📉 Too low! Try again.")
        else:
            print("📈 Too high! Try again.")

        if guess_count >= max_guesses:
            print(f"❌ You've used all {max_guesses} guesses. The number was {secret_number}.")
            break

    print("\nGame over!")

while True:
    play_game()
    play_again = input("🔁 Would you like to play again? (y/n): ").strip().lower()
    if play_again != "y":
        print("👋 Thanks for playing! Goodbye.")
        break