# Lesson 2: Control Flow

Now that we have variables, let's make our programs smarter. We need to be able to make decisions and repeat actions.

## 1. Loops (`FOR ... NEXT`)

Loops allow you to repeat a block of code a specific number of times.

```basic
10 FOR I = 1 TO 10
20 PRINT I; "COMMODORE"
30 NEXT I
```

You can also use `STEP` to count by a different amount (even backwards!):

```basic
10 FOR I = 10 TO 1 STEP -1
20 PRINT I
30 NEXT I
40 PRINT "BLAST OFF!"
```

## 2. Logic (`IF ... THEN`)

This is how your program makes decisions.

```basic
10 INPUT "ENTER A NUMBER"; A
20 IF A > 10 THEN PRINT "THAT IS A BIG NUMBER"
30 IF A <= 10 THEN PRINT "THAT IS A SMALL NUMBER"
```

**Note:** In standard C64 BASIC v2, there is no `ELSE`. You have to use multiple `IF` statements or `GOTO` to handle alternatives.

## 3. Jumping Around

### `GOTO`
Unconditionally jumps to a line number. Use sparingly, or your code becomes "spaghetti"!

```basic
10 PRINT "INFINITE LOOP"
20 GOTO 10
```

### `GOSUB` and `RETURN`
This is how you create subroutines (reusable blocks of code).

```basic
10 PRINT "MAIN PROGRAM"
20 GOSUB 100
30 PRINT "BACK IN MAIN"
40 END

100 PRINT "  I AM A SUBROUTINE"
110 RETURN
```

## 4. The Challenge: Guess the Number

Write a game where the computer picks a number, and you have to guess it.

1.  **Generate a random number:**
    `R = INT(RND(1)*100) + 1` (Generates a number between 1 and 100).
2.  **Loop:** Ask the user for a guess.
3.  **Check:**
    - If the guess is too low, print "TOO LOW".
    - If the guess is too high, print "TOO HIGH".
    - If the guess is correct, print "YOU GOT IT!" and end the game.
4.  **Count:** Keep track of how many guesses it took.

**Tip:** You'll need a loop that keeps going until the guess is correct. You can use `GOTO` to jump back to the input line if the guess is wrong.
