# Guess-the-word-game-
My c program project
#include <stdio.h>
#include <string.h>

int main() {
    char word[] = "computer";      // Word to guess
    char guess[20];
    int chances = 7;
    int correct = 0;
    int length = strlen(word);

    // Initialize guess array with underscores
    for (int i = 0; i < length; i++) {
        guess[i] = '_';
    }
    guess[length] = '\0';

    printf("🎮 Welcome to Guess the Word Game!\n");
    printf("Hint: It is related to CSE\n");

    while (chances > 0 && correct < length) {
        char letter;
        int found = 0;

        printf("\nWord: %s", guess);
        printf("\nEnter a letter: ");
        scanf(" %c", &letter);

        for (int i = 0; i < length; i++) {
            if (word[i] == letter && guess[i] == '_') {
                guess[i] = letter;
                found = 1;
                correct++;
            }
        }

        if (!found) {
            chances--;
            printf("Wrong guess! Chances left: %d\n", chances);
        } else {
            printf("Good guess!\n");
        }
    }

    if (correct == length) {
        printf("\n🎉 Congratulations! You guessed the word: %s\n", word);
    } else {
        printf("\n😢 Game Over! The word was: %s\n", word);
    }

    return 0;
}
