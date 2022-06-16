# Hangman

A hangman game programmed with python.

## Milestone 1

Allows the user to input a letter, checks if the letter is valid and if it isn't it asks for a letter again. Keeps repeating until a valid input is given. here a valid input is a single character which is a letter.

```python
valid = False
while valid == False:
    letter = input("Guess a letter in the word:")
    if letter.isalpha() and len(letter) == 1:
        valid = True
    else:
        print("Please, enter just one character")
```

## Milestone 2

Sets up initialiser function.

```python
self.word = random.choice(word_list)
self.word_guessed = ['_' for i in self.word]
self.num_letters = len(set([char for char in self.word]))
self.num_lives = num_lives
self.list_letters = []
print(f"The mystery word has {len(self.word)} characters")
print(self.word_guessed)
```

Also checks if letter has already been tried.

```python
if letter not in self.list_letters:
    valid = True
else:
    print(f"{letter} was already tried")
```

## Milestone 3

Checks if the letter guessed by the user is in the word. If it is, updates the list with missing letters to show the letters that have been guessed correctly. If not, then reduces number of lives. In either case, the list of guessed letters is updated.

```python
if letter.lower() in self.word:
    for i in range(len(self.word)):
        if letter.lower() == self.word[i]:
            self.word_guessed[i] = letter.lower()
    self.num_letters -= 1
    print(f"Nice! {letter} is in the word!")
    print(self.word_guessed)
else:
    self.num_lives -= 1
    print(f"Sorry, {letter} is not in the word.")
    print(f"You have {self.num_lives} lives left.")
self.list_letters.append(letter.lower())
```

## Milestone 4

Completes game logic to create a playable game. Keeps asking the user to guess until lives run out or word has been guessed. When finished, dislays appropriate message.

```python
game = Hangman(word_list, num_lives=5)
while game.num_lives > 0 and game.num_letters > 0:
    game.ask_letter()
if game.num_letters == 0:
    print("Congratulations, you won!")
else:
    print(f"You ran out of lives. The word was {game.word}")   
```
