# Part III: Variables (Solutions)

### Basic Requirements

1. Fix each of the following variable declarations in a console -- some are
   syntactically invalid, some are disobey style guidelines, and some are just
   weird.

   ```js
   var "animal" = "monkey";
   var "monkey" = animal;
   var x= 15;
   var y =10;
   var var = "huh?";
   var true = false;
   var isTenEven = 10 % 2 = 0;
   ```

   **FIXED:**
   ```js
   var animal = "monkey";
   var monkey = animal;
   var x = 15;
   var y = 10;
   var variable = "huh?";
   var truth = false;
   var isTenEven = 10 % 2 === 0;
   ```

2. Perform the following in the console:

   + Create a variable `firstName` and assign your first name to it.
   + Create another variable, `lastName`, and assign your last name to it.
   + Have a middle name? If so, repeat the process.
   + Now, create a variable `fullName` and assign your full name to it by using
     the above variables.

    **ANSWER:**
   ```js
   var firstName = 'Michael';
   var lastName = 'Jordan';
   var middleName = 'Jeffrey';
   var fullName = firstName + ' ' + middleName + ' ' + lastName;
   ```

3. For each of the following code blocks, **use a whiteboard (or a piece of paper)** to reason about
   what the value of `x` is supposed to be on the last line. Once you have
   arrived at a conclusion that you are comfortable with, enter the lines into a
   console and check your answer. Was your hypothesis correct? If not, ensure
   that you understand why (talk with a classmate, or ask for help).

   ```js
   var x = 5;
   x + 10;
   x; // => ???
   ```

   **ANSWER:**
   ```js
   x; // => 5
   ```

   ```js
   var x = 17;
   x = (x + 1) / 2;
   x * 4;
   x; // => ???
   ```

   **ANSWER:**
   ```js
   x; // => 9
   ```

   ```js
   var x = 5;
   var y = 20;
   x = y;
   y = y + 7;
   x; // => ???
   ```

   **ANSWER:**
   ```js
   x; // => 20
   ```

   ```js
   var x = 10;
   var y = 5;
   x = (x * 4) - 3;
   x + 17;
   x = x + y;
   x; // => ???
   ```

   **ANSWER:**
   ```js
   x; // => 42
   ```

4. Write a function called `counter` that, when invoked, always returns a number
   that is *one more* than the previous invocation. For instance:

   ```js
   var count = 0;

   function counter() {
     count = count + 1;
     return count;
   }
   counter(); // => 1
   counter(); // => 2
   counter(); // => 3
   // etc.
   ```

   **HINT:** You'll need a variable for this. *Where* should the variable be
   declared?

   **ANSWER:** Declaring the variable outside of the function (in global scope) allows the program to properly track how many times the counter() function has been called. The value of the count variable is persistent.

### More Practice

**All of the following exercises involve augmenting the `guessMyNumber` function.**

1. In a previous module you wrote a function called `guessMyNumber` that
   simulated a guessing game: the idea is that the function picks a random
   number between `0` and `5`, and you invoke the function with your guess -- if
   you and the function are thinking of the same number, you win! Otherwise, the
   function informs you that your guess was incorrect. A version of this game
   might look like this (the `randInt` function is included for convenience):

   ```js
   function guessMyNumber(n) {
     if (n > 5) {
       return "Out of bounds! Please try a number between 0 and 5.";
     } else if (n === randInt(5)) {
       return "You guessed my number!";
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

   Read and test both of the functions in your console and
   affirm that you understand how they work; then, answer the following
   questions:

   + At present, the guess should be between `0` and `5`. We can think of `5` as
     the *upper bound* of the guess. How many times is the *upper bound*
     repeated? What if we wanted to change the upper bound to `6`? How many
     changes would be required?

     **ANSWER:** Changes would be needed each time the number 5 is used. For the function above, that would be 3 changes in total.

   + Create a variable called `upperBound` to hold the upper bound, and then
     reference **it** instead of the number `5`. If you were asked to change the
     upper bound to some other number (*e.g.* `7`), you should only have to make
     *one* change.

      **ANSWER:**
     ```js
     function guessMyNumber(n) {
       var upperBound = 5;

       if (n > upperBound) {
         return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
       } else if (n === randInt(upperBound)) {
         return "You guessed my number!";
       }
       return "Nope! That wasn't it!";
     }

     function randInt(n) {
       return Math.floor(Math.random() * (n + 1))
     }
     ```

   + Modify `guessMyNumber` so that if the guess is incorrect, `guessMyNumber`
     includes the correct guess in its output, *e.g.* `"Nope! The correct number
     was: X"` (where `X` would have been the correct number).

      **ANSWER:**
     ```js
     function guessMyNumber(n) {
       var upperBound = 5;
       var randomNum = randInt(upperBound);

       if (n > upperBound) {
         return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
       } else if (n === randomNum)) {
         return "You guessed my number!";
       }
       return "Nope! That wasn't it! The correct answer was: " + randomNum;
     }

     function randInt(n) {
       return Math.floor(Math.random() * (n + 1))
     }
     ```

2. At present, the guessing game picks a new random number every time it is
   "played" (invoked). Now that you know how to make information *persistent*
   between function invocations, change the guessing game so that it picks a
   random number **once** and allows you to guess until you get the correct
   answer.

  **ANSWER:**
   ```js
   var upperBound = 5;
   var randomNum = randInt(upperBound);

   function guessMyNumber(n) {
     if (n > upperBound) {
       return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
     } else if (n === randomNum) {
       return "You guessed my number!";
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

3. It would be really cool if, after the answer was guessed, the message
   included the number of guesses it had taken to find the answer; for example,
   "You guessed my number in 3 guesses."

   + **Tangent Problem:** What happens if you get the number right on the
     first try? Does it say, "You guessed my number in 1 guesses."? If so,
     perhaps the wording should be different? Some better ideas are:

     + "You guessed my number in 1 guess."
     + "Congratulations! You guessed my number on the first try!"

    **ANSWER:**
     ```js
     var upperBound = 5;
     var randomNum = randInt(upperBound);
     var guessCount = 0;

     function guessMyNumber(n) {
       guessCount = guessCount + 1;

       if (n > upperBound) {
         return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
       } else if (n === randomNum && guessCount === 1) {
         return "Congratulations! You guessed my number on the first try!";
       } else if (n === randomNum) {
         return "You guessed my number! It took you " + guessCount + ' guesses.';
       }
       return "Nope! That wasn't it!";
     }

     function randInt(n) {
       return Math.floor(Math.random() * (n + 1))
     }
     ```

4. Implement a way to **limit** the number of guesses that can be made so that a
   player loses after exceeding the limit.

   **ANSWER:**
   ```js
   var upperBound = 5;
   var randomNum = randInt(upperBound);
   var guessCount = 0;
   var guessLimit = 4;

   function guessMyNumber(n) {
     guessCount = guessCount + 1;

     if (guessCount > guessLimit) {
       randomNum = randInt(upperBound);
       return "You have exceeded the maximum number of guesses. You lose!";
     } else if (n > upperBound) {
       return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
     } else if (n === randomNum && guessCount === 1) {
       randomNum = randInt(upperBound);
       return "Congratulations! You guessed my number on the first try!";
     } else if (n === randomNum) {
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guessCount + ' guesses.';
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

5. Keep track of a **high score** (the lowest number of guesses) between games,
   and, when the correct number has been guessed in a record number of times,
   include in the message something that indicates that a new high score has
   been set.

   **ANSWER:**
   ```js
   var upperBound = 5;
   var randomNum = randInt(upperBound);
   var guessCount = 0;
   var guessLimit = 4;
   var highScore = guessLimit + 1;

   function guessMyNumber(n) {
     guessCount = guessCount + 1;

     if (guessCount > guessLimit) {
       guessCount = 0;
       randomNum = randInt(upperBound);
       return "You have exceeded the maximum number of guesses. You lose!";
     } else if (n > upperBound) {
       return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
     } else if (n === randomNum && guessCount === 1 && guessCount < highScore) {
       highScore = guessCount;
       guessCount = 0;
       randomNum = randInt(upperBound);
       return "Congratulations! You guessed my number on the first try! And you set a new high score!";
     } else if (n === randomNum && guessCount < highScore) {
       var guesses = guessCount;
       highScore = guessCount;
       guessCount = 0;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses, which is a new high score!';
     } else if (n === randomNum) {
       var guesses = guessCount;
       guessCount = 0;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses.';
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

6. Whenever a player wins, **increase the difficulty** by increasing the
   `upperBound`; whenever a player loses, **decrease the difficulty** by
   decreasing the `upperBound`.

   **ANSWER:**
   ```js
   var upperBound = 5;
   var randomNum = randInt(upperBound);
   var guessCount = 0;
   var guessLimit = 4;
   var highScore = guessLimit + 1;

   function guessMyNumber(n) {
     guessCount = guessCount + 1;

     if (guessCount > guessLimit) {
       guessCount = 0;
       upperBound = upperBound - 1;
       randomNum = randInt(upperBound);
       return "You have exceeded the maximum number of guesses. You lose!";
     } else if (n > upperBound) {
       return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
     } else if (n === randomNum && guessCount === 1 && guessCount < highScore) {
       highScore = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "Congratulations! You guessed my number on the first try! And you set a new high score!";
     } else if (n === randomNum && guessCount < highScore) {
       var guesses = guessCount;
       highScore = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses, which is a new high score!';
     } else if (n === randomNum) {
       var guesses = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses.';
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

7. Implement a **high/low hinting system** to tell the the user that the guess
   is either too high or too low. You may want to increase the `upperBound` on
   the guess.

   **ANSWER:**
   ```js
   var upperBound = 5;
   var randomNum = randInt(upperBound);
   var guessCount = 0;
   var guessLimit = 4;
   var highScore = guessLimit + 1;

   function guessMyNumber(n) {
     var hint = '';
     guessCount = guessCount + 1;

     if (n < randomNum) {
       hint = 'Your guess was too low.';
     } else if (n > randomNum) {
       hint = 'Your guess was too high.';
     }

     if (guessCount > guessLimit) {
       guessCount = 0;
       upperBound = upperBound - 1;
       randomNum = randInt(upperBound);
       return "You have exceeded the maximum number of guesses. You lose!";
     } else if (n > upperBound) {
       return "Out of bounds! Please try a number between 0 and " + upperBound + ".";
     } else if (n === randomNum && guessCount === 1 && guessCount < highScore) {
       highScore = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "Congratulations! You guessed my number on the first try! And you set a new high score!";
     } else if (n === randomNum && guessCount < highScore) {
       var guesses = guessCount;
       highScore = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses, which is a new high score!';
     } else if (n === randomNum) {
       var guesses = guessCount;
       guessCount = 0;
       upperBound = upperBound + 1;
       randomNum = randInt(upperBound);
       return "You guessed my number! It took you " + guesses + ' guesses.';
     }
     return "Nope! That wasn't it! " + hint;
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```
