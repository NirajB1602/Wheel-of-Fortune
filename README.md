# Wheel of Fortune Project

## Project Overview

This project is about creating a simplified version of the game Wheel of Fortune. In our game, there will be human players and computer players, each having money and a set of prizes. The goal is to guess a phrase within a specific category.

When it's a player's turn, they spin a wheel to determine a prize amount, and they can take one of the following actions:

- Guess a letter: Players can guess any letter that hasn't been guessed yet, and they earn money for each appearance of that letter in the phrase. Vowels cost $250 to guess, and they can't be guessed if the player doesn't have enough money. Other letters are free to guess.

- Guess the complete phrase: If a player believes they know the answer, they can guess the entire phrase. If they're correct, they win the game.

- Pass the turn: If a player doesn't want to make a move, they can pass their turn.

There are also special wheel outcomes:

- "Lose a turn": The player loses their turn.

- "Bankrupt": The player loses their turn and all their money but keeps their prizes.

The game continues until the entire phrase is revealed or one player guesses the complete phrase.

For this project, we'll use various functions and methods, such as time.sleep(), random.randint(), random.choice(), and string methods like .upper() and .count(). These functions will help in implementing different aspects of the game, including player actions, wheel outcomes, and difficulty levels for computer players.

We will also create three classes:

1. **WOFPlayer**: Represents a player and contains methods to add money, go bankrupt, add prizes, and display player information. We’re going to start by defining a class to represent a Wheel of Fortune player, called WOFPlayer. Every instance of WOFPlayer has three instance variables:
   - .name: The name of the player (should be passed into the constructor)

   - .prizeMoney: The amount of prize money for this player (an integer, initialized to 0)

   - .prizes: The prizes this player has won so far (a list, initialized to [])
     
    <pre>
    Of these instance variables, only name should be passed into the constructor.</pre> It should also have the following methods (note: we will exclude self in our descriptions).
    - .addMoney(amt): Add amt to self.prizeMoney

    - .goBankrupt(): Set self.prizeMoney to 0

    - .addPrize(prize): Append prize to self.prizes

    - .__str__(): Returns the player’s name and prize money in the following format:
      - Steve ($1800) (for a player with instance variables .name == 'Steve' and prizeMoney == 1800)

2. **WOFHumanPlayer**: Represents a human player, with a method to get their move. The player can guess letters, the complete phrase, or choose to pass their turn. Next, we’re going to define a class named WOFHumanPlayer, which should inherit from WOFPlayer (part A). This class is going to represent a human player. In addition to having all of the instance variables and methods that WOFPlayer has, WOFHumanPlayer should have an additional method:
    - .getMove(category, obscuredPhrase, guessed): Should ask the user to enter a move (using input()) and return whatever string they entered.
      
<pre>
  The user can then enter:

    - 'exit' to exit the game

    - 'pass' to skip their turn

    -  a single character to guess that letter

    -  a complete phrase (a multi-character phrase other than 'exit' or 'pass') to guess that phrase.</pre>


3. **WOFComputerPlayer**: Represents a computer player with a difficulty level. Finally, we’re going to define a class named WOFComputerPlayer, which should inherit from WOFPlayer (part A). This class is going to represent a computer player. Every computer player will have a difficulty instance variable. Players with a higher difficulty generally play “better”. There are many ways to implement this. We’ll do the following:

   - If there aren’t any possible letters to choose (for example: if the last character is a vowel but this player doesn’t have enough to guess a vowel), we’ll 'pass'

   - Otherwise, semi-randomly decide whether to make a “good” move or a “bad” move on a given turn (a higher difficulty should make it more likely for the player to make a “good” move)

            To make a “bad” move, we’ll randomly decide on a possible letter.

            To make a “good” move, we’ll choose a letter according to their overall frequency in the English language.


    In addition to having all of the instance variables and methods that WOFPlayer has, WOFComputerPlayer should have:

    - Class variable
    
      - .SORTED_FREQUENCIES: Should be set to 'ZQXJKVBPYGFWMUCLDRHSNIOATE', which is a list of English characters sorted from least frequent ('Z') to most frequent ('E'). We’ll use this when trying to make a “good” move.

    - Additional Instance variable

      - .difficulty: The level of difficulty for this computer (should be passed as the second argument into the constructor after .name)

    - Methods

      - .smartCoinFlip(): This method will help us decide semi-randomly whether to make a “good” or “bad” move. A higher difficulty should make us more likely to make a “good” move. Implement this by choosing a random number between 1 and 10 using random.randint(1, 10) (see above) and returning False if that random number is greater than self.difficulty. If the random number is less than or equal to self.difficulty, return True.

      - .getPossibleLetters(guessed): This method should return a list of letters that can be guessed.

          -  These should be characters that are in LETTERS ('ABCDEFGHIJKLMNOPQRSTUVWXYZ') but not in the guessed parameter.

          -  Additionally, if this player doesn’t have enough prize money to guess a vowel (variable VOWEL_COST set to 250), then vowels (variable VOWELS set to 'AEIOU') should not be included

      - .getMove(category, obscuredPhrase, guessed): Should return a valid move.

          -  Use the .getPossibleLetters(guessed) method described above.

          -  If there aren’t any letters that can be guessed (this can happen if the only letters left to guess are vowels and the player doesn’t have enough for vowels), return 'pass'

          -  Use the .smartCoinFlip() method to decide whether to make a “good” or a “bad” move

                  -  If making a “good” move (.smartCoinFlip() returns True), then return the most frequent (highest index in .SORTED_FREQUENCIES) possible character

                  -  If making a “bad” move (.smartCoinFlip() returns False), then return a random character from the set of possible characters (use random.choice())
             
Overall, the project focuses on creating a fun and interactive game based on the rules of "Wheel of Fortune."

## Project Description

The project encompasses several key components:

1. **Game Mechanics**: The project replicates the core game mechanics of "Wheel of Fortune." Players can spin the wheel to earn prizes, guess letters, and solve word puzzles.

2. **Word Puzzles**: The game includes a collection of word puzzles in various categories, such as "Movie Titles," "Famous Phrases," and "Places." These puzzles are randomly selected for each game session.

3. **Player Interactions**: Players can interact with the game by choosing letters, spinning the wheel, and solving puzzles. They can also choose to "buy a vowel" or "solve the puzzle" when they believe they know the answer.

4. **Scoring and Prizes**: The project keeps track of players' scores, including the amount they've earned and their total winnings. Prizes may include virtual currency, which can be used to buy in-game items.

5. **User Interface**: The game features a user-friendly interface that replicates the look and feel of the original "Wheel of Fortune" game show. It includes the spinning wheel, a puzzle board, and options for letter selection and puzzle solving.

6. **Multiplayer Mode**: For an enhanced gaming experience, the project may include a multiplayer mode, allowing players to challenge friends or other online players in solving puzzles.

7. **Documentation**: The project documentation, including the README.md file, provides details about the project, its components, and how to play the game.

## Contributors

- [Niraj Bansal](https://github.com/NirajB1602)

Feel free to fork, contribute, and share this project with others who enjoy the thrill of the "Wheel of Fortune" game.
