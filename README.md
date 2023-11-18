# Number-Guessing-game__CodSoft_Project-1-
Number Guessing game


CODE IN C++--

#include <bits/stdc++.h>
//#include <cstdlib>
//#include <ctime>

using namespace std;

int getFeedback(int guess, int secretNumber) {
    if (guess == secretNumber) {
        cout << "Congratulations! You guessed the correct number " << secretNumber << ".\n";
        return 0;
    } else if (guess < secretNumber) {
        cout << "Too low! Try again.\n";
        return -1;
    } else {
        cout << "Too high! Try again.\n";
        return 1;
    }
}

void playGame(int rangeStart, int rangeEnd, const string& userName) {
    srand(static_cast<unsigned int>(time(0)));
    int secretNumber = rand() % (rangeEnd - rangeStart + 1) + rangeStart;

    cout << "Welcome, " << userName << ", to the Number Guessing Game!\n";
    cout << "I have selected a random number between " << rangeStart << " and " << rangeEnd << ". Try to guess it.\n";

    int attempts = 0;
    int guess;

    do {
        cout << "Enter your guess: ";
        cin >> guess;
        attempts++;

        int feedback = getFeedback(guess, secretNumber);

        if (feedback == 0) {
            cout << "You guessed the correct number in " << attempts << " attempts.\n";
            return;
        }

        // Check if the user wants to give up after 5 attempts
        if (attempts == 5) {
            int giveUpChoice;
            cout << "You've reached 5 attempts. Do you want to give up and know the number? (Enter 1 to give up, Enter 2 to continue): ";
            cin >> giveUpChoice;

            if (giveUpChoice == 1) {
                cout << "The correct number was " << secretNumber << ". Better luck next time, " << userName << "!\n";
                return;
            } else if (giveUpChoice == 2) {
                cout << "Great! Let's continue the game, " << userName << ".\n";
            } else {
                cout << "Invalid choice. Continuing the game.\n";
            }
        }

    } while (true);
}

int main() {
    string userName;
    cout << "Enter your name: ";
    getline(cin, userName);

    int rangeStart, rangeEnd;
    cout << "Enter the range for the number (e.g., 1 100): ";
    cin >> rangeStart >> rangeEnd;

    playGame(rangeStart, rangeEnd, userName);

    return 0;
}
