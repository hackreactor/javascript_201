# Part I: Booleans, Comparisons & Conditionals (Solutions)

### Basic Requirements

#### Comparison Operators

1. Type the two boolean values -- `true` and `false` -- into your console.

2. Use the console to accomplish the following:

    + Write an expression using `>` that will evaluate to `false`
    + Write an expression using `>` that will evaluate to `true`
    + Write an expression using `<` that will evaluate to `false`
    + Write an expression using `<` that will evaluate to `true`
    + Write an expression using two numbers and `===` that will evaluate to `true`
    + Write an expression using two numbers and `===` that will evaluate to `false`
    + Write an expression using two strings and `===` that will evaluate to `true`
    + Write an expression using two strings and `===` that will evaluate to `false`


3. Fill in the `???` with the following operators or values to make the statements
   output the expected Boolean value.

   ```js
   12 ??? 78
   // => true

   24 ??? 16
   // => false

   45 !== ???
   // => true

   "45" ??? 45
   // => false

   "6" ??? "six"
   // => true
   ```

   **POTENTIAL ANSWERS**:
   ```js
   12 < 78
   // => true

   24 > 16
   // => false

   45 !== 46
   // => true

   "45" === 45
   // => false

   "6" !== "six"
   // => true
   ```

4. Write a function `oldEnoughToDrink` that takes an `age` as an argument and
   returns `true` if the person with that age is old enough to drink.

   **ANSWER:**
   ```js
   function oldEnoughToDrink(age) {
     if (age >= 21) {
       return true;
     }
     return false;
   }
   ```

5. There's an easy way to figure out how long a string is by adding `.length` to
   the end of it. Try this out in the console:

  ```js
  "hello".length;
  "".length;
  "John Doe".length;
  ```

  Write a function `sameLength` that accepts two strings as arguments, and
  returns `true` if those strings have the same length, and `false` otherwise.

  **ANSWER:**
  ```js
  function sameLength(string1, string2) {
    if (string1.length === string2.length) {
      return true;
    }
    return false;
  }
  ```

6. Write a function `passwordLongEnough` that accepts a "password" as a
   parameter and returns `true` if that password is *long enough* -- you get to
   decide what constitutes *long enough*.

   **ANSWER:**
   ```js
   function passwordLongEnough(password) {
     if (password.length >= 8) {
       return true;
     }
     return false;
   }
   ```

#### Conditionals: `if`

1. Write a function `bouncer` that accepts a person's name and age as arguments,
   and returns either "Go home, NAME.", or "Welcome, NAME!" (where NAME is the
   parameter that represents the person's name) depending on whether or not the
   person is old enough to drink.

   **ANSWER:**
   ```js
   function bouncer(name, age) {
     if (age >= 21) {
       return 'Welcome, ' + name + '!';
     }
     return 'Go home, ' + name + '.';
   }
   ```

2. Write a function `max` that takes two numbers as arguments, and returns the
   larger one.

   **ANSWER:**
   ```js
   function max(num1, num2) {
     if (num1 > num2) {
       return num1;
     }
     return num2;
   }
   ```

3. Write a function `min` that takes two numbers as arguments, and returns the
   smaller one.

   **ANSWER:**
   ```js
   function min(num1, num2) {
     if (num1 < num2) {
       return num1;
     }
     return num2;
   }
   ```

4. Write functions `larger` and `smaller` that each accept two strings as
   arguments, and return the *larger* and *smaller* strings, respectively.

   **ANSWER:**
   ```js
   function larger(string1, string2) {
     if (string1.length > string2.length) {
       return string1;
     }
     return string2;
   }

   function smaller(string1, string2) {
     if (string1.length < string2.length) {
       return string1;
     }
     return string2;
   }

### More Practice

1. Fill in the `???` with the following operators or values to make the statements
   output the expected Boolean value.

   ```js
   106 ??? 12
   // => false

   "wiz" ??? "wiz"
   // => true

   7 * 7  ??? 49
   // => true

   12 ??? (24 / 2)
   // => false

   (20 % 2) <= ???
   // => true

   (9 / 3) + (5 * 5) === ???
   // => true
   ```

   **POTENTIAL ANSWERS**:
   ```js
   106 <= 12
   // => false

   "wiz" === "wiz"
   // => true

   7 * 7  === 49
   // => true

   12 !== (24 / 2)
   // => false

   (20 % 2) <= 10
   // => true

   (9 / 3) + (5 * 5) === 28
   // => true
   ```

2. Write the following functions that each accept a single number as an
   argument:

    + `even`: returns `true` if its argument is even, and `false` otherwise.

     **ANSWER:**
    ```js
    function even(num) {
      // The number is even if it can be divided by 2 with no remainder
      if (num % 2 === 0) {
        return true;
      }
      return false;
    }
    ```

    + `odd`: the opposite of the above.

     **ANSWER:**
    ```js
    function odd(num) {
      // The number is odd if it cannot be divided by 2 with no remainder
      if (num % 2 !== 0) {
        return true;
      }
      return false;
    }
    ```
    + `positive`: returns `true` if its argument is positive, and `false` otherwise.

     **ANSWER:**
    ```js
    function positive(num) {
      if (num >= 0) {
        return true;
      }
      return false;
    }
    ```

    + `negative`: the opposite of the above.

     **ANSWER:**
    ```js
    function negative(num) {
      if (num < 0) {
        return true;
      }
      return false;
    }
    ```

3. A couple of other useful built-in mathematical functions are `Math.random`,
   `Math.floor` and `Math.ceil`. Look these functions up on
   [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
   to learn how they work, and use them to implement the following functions:

   + `randInt`: Should accept a single numeric argument (`n`), and return a
     number from `0` to `n`.

     **ANSWER:**
     ```js
     function randInt(n) {
       return Math.floor(Math.random() * (n + 1));
     }
     ```

   + `guessMyNumber`: Should accept a single numeric argument and compare it to
     a random number between `0` and `5`. It should return one of the following
     strings:

     + "You guessed my number!" if the argument matches the random number.
     + "Nope! That wasn't it!" if the argument did not match the random number.

     **ANSWER:**
     ```js
     function guessMyNumber(guess) {
        var randomNum = Math.floor(Math.random() * 6);
        if (guess === randomNum) {
          return "You guessed my number!";
        }
        return "Nope! That wasn't it!";
     }
     ```
