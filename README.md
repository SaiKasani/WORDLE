#WORDLE
A recreation of the well known New York Times Game
=====================================================
This project uses a fixed code word of "codes" when playing the Wordle game, however, the word can be replaced with a different word or library if words if desired.
=====================================================

    def input_guess(secret_word_len: int) -> str:
        """Determines if the guess is the same amount of characters as the secret word"""
        guess = input(f"Enter a {secret_word_len} character word: ")

        while len(guess) != secret_word_len):  # loops every time guess is not the same number of characters as the secret word
        guess = input(f"That wasn't {secret_word_len} chars! Try again:")

        return guess


    def contains_char(secret_word: str, char_guess: str) -> bool:
        """Determines if the inputted word contains the inputted character"""
        assert len(char_guess) == 1  # makes sure second parameter is 1 character

        count = 0
        instances = 0

        while count < len(secret_word):  # counts how many times the character shows up in the secret word, if at all
            if char_guess == secret_word[count]:
                instances += 1
                count += 1
            else:
                count += 1

        if (instances != 0):  # returns True or False based on if the character showed up in the string
            return True
        else:
            return False


    def emojified(user_guess: str, secret_word: str) -> str:
        """Determines the accuracy of the user's guess in relation to the secret word"""
        assert len(user_guess) == len(secret_word)  # makes sure the two words are of the same length

        WHITE_BOX: str = "\U00002B1C"
        GREEN_BOX: str = "\U0001F7E9"
        YELLOW_BOX: str = "\U0001F7E8"

        count = 0

        output = ""  # string to add emojis to in the while loop when outputting the result of the function

        while count < len(secret_word):  # determines if each index should get a green, yellow, or white box
            if user_guess[count] == secret_word[count]:
                count += 1
                output = output + GREEN_BOX
            else:
                if contains_char(secret_word=secret_word, char_guess=user_guess[count]):
                    count += 1
                    output = output + YELLOW_BOX
                else:
                    count += 1
                    output = output + WHITE_BOX

        return output  # returns the string of emojis


    def main(secret: str) -> None:
        """Entrypoint of the main game and the game loop"""
        turn = 1

        while turn <= 6:  # loops the user for 6 rounds
            print(f"=== Turn {turn}/6 ===")
            guess = input_guess(secret_word_len=len(secret))
            print(emojified(user_guess=guess, secret_word=secret))

            if guess == secret:  # determines if you correctly guessed the string
                print(f"You won in {turn}/6 turns!")
                exit()
            else:
                turn += 1

            if turn > 6:
                print("X/6 - Sorry, try again tomorrow!")  # you lost if you get this line


    if __name__ == "__main__":  # runs the function automatically
         main(secret="codes")

