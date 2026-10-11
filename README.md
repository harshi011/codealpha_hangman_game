# codealpha_hangman_game

import random

word_bank = ["python", "network", "keyboard", "program", "computer"]
secret_word = random.choice(word_bank)
guessed = set()
wrong_count = 0
limit = 6

while wrong_count < limit:
    word = ""
    for ch in secret_word:
        if ch in guessed:
            word += ch + " "
        else:
            word += "_ "

    print("\nWord:", word.strip())
    print("Attempts left:", limit - wrong_count)

    letter = input("Enter a letter: ").lower().strip()

    if len(letter) != 1 or not letter.isalpha():
        continue

    if letter in guessed:
        continue

    guessed.add(letter)

    if letter in secret_word:
        print("\nCorrect guess!")

        if all(ch in guessed for ch in secret_word):
            print("Congratulations! You WON!")
            print("The correct word was:", secret_word)
            break
    else:
        wrong_count += 1
        print("Wrong guess!")

else:
    print("\nGAME OVER!")
    print("The correct word was:", secret_word)

print("\nPossible words were:", ", ".join(word_bank))
print("Thanks for playing!")

