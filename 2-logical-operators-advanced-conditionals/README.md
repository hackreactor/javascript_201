# Part II: Logical Operators & Advanced Conditionals (Solutions)

### Basic Requirements

#### Logical Operators

1. Is the `!` operator a *unary* operator, or *binary* operator?

   **ANSWER:** It is a unary operator, because it has only one operand.

2. Evaluate each of the following expressions first on a whiteboard, and then in
   a console:

   ```js
   !(2 >= 2)      // => false
   !(4 === 4)     // => false
   !(5 !== 5)     // => true
   ```

3. Evaluate each of the following expressions first on a whiteboard, and then in a
   console:

   ```js
   1 > 2 || 2 > 2 || 3 > 2    // => true
   5 < 5 || 75 < 74           // => false
   ```

#### Conditionals: `else if` & `else`

1. This guy named "Joe" keeps blacking out at the bar that your function,
   `bouncer` (from the previous module), is in charge of; thus, management has
   decided to add him to the "blacklist" -- modify the `bouncer` function from
   the previous section so that the person named "Joe" is rejected with an
   appropriate message, regardless of his age.

    **ANSWER:**
   ```js
   function bouncer(name, age) {
     if (name === 'Joe') {
       return 'Go home, ' + name + '. You are banned from the bar.';
     } else if (age >= 21) {
       return 'Welcome, ' + name + '!';
     }
     return 'Go home, ' + name + '.';
   }
   ```

2. Write a function called `scoreToGrade` that accepts a *number* as a parameter
   and returns a *string* representing a letter grade corresponding to that
   score.

   For example, the following grades should be returned given these scores:

   + 'A' >= 90
   + 'B' >= 80
   + 'C' >= 70
   + 'D' >= 60
   + 'F' < 60

   **ANSWER:**
   ```js
   function scoreToGrade(score) {
     if (score >= 90) {
       return 'A';
     } else if (score >= 80) {
       return 'B';
     } else if (score >= 70) {
       return 'C';
     } else if (score >= 60) {
       return 'D';
     } else {
       return 'F';
     }
   }
   scoreToGrade(95); // => 'A'
   scoreToGrade(72); // => 'C'
   ```

3. Modify the `scoreToGrade` function so that it returns `'INVALID SCORE'` if
   the score is greater than `100` or less than `0`.

   **ANSWER:**
   ```js
   function scoreToGrade(score) {
     if (score > 100 || score < 0) {
       return 'INVALID SCORE';
     } else if (score >= 90) {
       return 'A';
     } else if (score >= 80) {
       return 'B';
     } else if (score >= 70) {
       return 'C';
     } else if (score >= 60) {
       return 'D';
     } else {
       return 'F';
     }
   }
   ```

### More Practice

1. Think of at least three activities that you enjoy doing outdoors and the
   range of temperatures and weather patterns (*e.g* sunny, windy, snowy, rainy,
   etc.) that are best for these activities. Write a function `whatToDoOutside`
   that accepts a *temperature* and *condition* as parameters and outputs a
   string of the format: "The weather is ideal for: ACTIVITY" (where ACTIVITY is
   an actual activity). Make sure to include an `else` that indicates what
   should be done if the conditions do not match any activities. If you're short
   on inspiration, here are some ideas:

   + **Snow Sports:** snowboarding, skiing
   + **Water Sports:** surfing, sailing, paddle boarding, swimming
   + **Team Sports:** basketball, baseball, football (American or everywhere
     else), etc.

    **ANSWER:**
   ```js
   function whatToDoOutside(temperature, condition) {
     var activity = '';

     if (temperature >= 80 && condition === 'sunny') {
       activity = 'swimming';
     } else if (temperature >= 80 && condition === 'windy') {
       activity = 'sailing';
     } else if (temperature >= 60 && condition === 'sunny') {
       activity = 'basketball';
     } else if (temperature >= 60 && condition === 'windy') {
       activity = 'hiking';
     } else if (temperature < 60 && condition === 'snowy') {
       activity = 'skiing';
     } else {
       activity = 'building a bonfire';
     }

     return 'The weather is ideal for: ' + activity + '.';
   }
   ```

2. The `guessMyNumber` function from the **Booleans & Conditionals** module
   (**More Practice** section) accepts a guess `n` and checks it against a
   random number from `0` to `5` -- if the guess `n` is greater than `5`, output
   a different message indicating that the guess is out of bounds.

   - **NOTE:** It will be helpful to *first* write a `randInt` function that
     accepts a number `n` and computes a random integer from `0` to `n`; then,
     you can use this function in `guessMyNumber`.

      **ANSWER:**
     ```js
     function randInt(n) {
       return Math.floor(Math.random() * (n + 1));
     }

     function guessMyNumber(n) {
        var randomNum = randInt(5);

        if (n > 5) {
          return "Your guess is out bounds."
        } else if (n === randomNum) {
          return "You guessed my number!";
        }
        return "Nope! That wasn't it!";
     }
     ```

3. Modify the `scoreToGrade` function so that it returns `'A+/A-'` for
   scores of 98-100/90-92 respectively. Apply the same logic for all other
   letter grades.

   **ANSWER:**
   ```js
   function scoreToGrade(score) {
     if (score > 100 || score < 0) {
       return 'INVALID SCORE';
     } else if (score >= 98) {
       return 'A+';
     } else if (score >= 93) {
       return 'A';
     } else if (score >= 90) {
       return 'A-';
     } else if (score >= 88) {
       return 'B+';
     } else if (score >= 83) {
       return 'B';
     } else if (score >= 80) {
       return 'B-';
     } else if (score >= 78) {
       return 'C+';
     } else if (score >= 73) {
       return 'C';
     } else if (score >= 70) {
       return 'C-';
     } else if (score >= 68) {
       return 'D+';
     } else if (score >= 63) {
       return 'D';
     } else if (score >= 60) {
       return 'D-';
     } else {
       return 'F';
     }
   }
   ```

### Advanced

1. The bar that employs our `bouncer` function has decided to do live music on
   Friday and Saturday nights, and will be admitting those that are over 18 to
   the bar on those nights; the catch however, is that all who are 21 or older
   will need to be given a wristband to distinguish them from the minors. Modify
   your `bouncer` function to handle this situation.

   **ANSWER:**
   ```js
   function bouncer(name, age, day) {
     if (name === 'Joe') {
       return 'Go home, ' + name + '. You are banned from the bar.';
     } else if ((day === 'Friday' || day === 'Saturday') && age >= 21) {
       return 'Welcome, ' + name + '! Here is your wristband.'
     } else if ((day === 'Friday' || day === 'Saturday') && age >= 18) {
       return 'Welcome, ' + name + '! You can come in but no drinking.'
     } else if (age >= 21) {
       return 'Welcome, ' + name + '!';
     }
     return 'Go home, ' + name + '.';
   }
   ```

2. You should have noticed a large amount of repetitive code when modifying
   `scoreToGrade` to accommodate `+` or `-` grades. When we do lots of repetitive
   things, that's a clear signal that there's a better way. Write a helper function
   `letterGrade` that accepts two arguments, *letter* and *score*, and works as
   follows:

   **ANSWER:**
   ```js
   function letterGrade(letter, score) {
     if (score % 10 >= 8) {
       return letter + '+';
     } else if (score % 10 >= 3) {
       return letter;
     } else {
       return letter + '-';
     }
   }

   // These are examples of what a *working* function would output.
   letterGrade('A', 95); // => 'A'
   letterGrade('A', 91); // => 'A-'
   letterGrade('B', 88); // => 'B+'
   letterGrade('monkey', 160); // => 'monkey-'
   ```

   Finally, use `letterGrade` to remove the repetition in `scoreToGrade`.

   **ANSWER:**
   ```js
   function scoreToGrade(score) {
     if (score > 100 || score < 0) {
       return 'INVALID SCORE';
     } else if (score === 100) {
       return 'A+';
     } else if (score >= 90) {
       return letterGrade('A', score);
     } else if (score >= 80) {
       return letterGrade('B', score);
     } else if (score >= 70) {
       return letterGrade('C', score);
     } else if (score >= 60) {
       return letterGrade('D', score);
     } else {
       return 'F';
     }
   }
   ```

3. It turns out that we can write logical *and* and logical *or* in terms of each
   other and logical *not* using <a href="https://en.wikipedia.org/wiki/De_Morgan%27s_laws" target="_blank">De Morgan's Laws</a>.

     + Write a function `or` that works like `||`, but only uses `!` and `&&`.

      **ANSWER:**
     ```js
     function or(a, b) {
       return !(!a && !b);
     }

     or(true, false);    // => true
     or(true, true);     // => true
     or(false, false);   // => false
     ```

     + Write a function `and` that works like `&&`, but only uses `!` and `||`.

      **ANSWER:**
     ```js
     function and(a, b) {
       return !(!a || !b);
     }

     and(true, false);   // => false
     and(true, true);    // => true
     and(false, false);  // => false
     ```
