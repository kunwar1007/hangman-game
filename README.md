# hangman-game
import random

# List of words for the game
word_list = ['python', 'hangman', 'challenge', 'programming', 'developer', 'keyboard']

# Choose a random word from the list
word = random.choice(word_list)
guessed_letters = []
attempts = 6  # Number of incorrect guesses allowed

# Create a display of underscores for the word
display = ['_' for _ in word]

print("Welcome to Hangman!")

# Game loop
while attempts > 0 and '_' in display:
    print("\nWord:", ' '.join(display))
    print(f"Guessed letters: {', '.join(guessed_letters)}")
    print(f"Attempts remaining: {attempts}")

    guess = input("Guess a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("Please enter a single alphabetic character.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in word:
        for idx, letter in enumerate(word):
            if letter == guess:
                display[idx] = guess
        print("Good guess!")
    else:
        attempts -= 1
        print("Wrong guess!")

# Result
if '_' not in display:
    print(f"\n🎉 Congratulations! You guessed the word: {word}")
else:
    print(f"\n😢 Game Over! The word was: {word}")
