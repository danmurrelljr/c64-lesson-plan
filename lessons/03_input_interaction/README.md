# Lesson 3: Input & Interaction

So far we've used `INPUT` to get numbers from the user. But for games, we often need something faster and more immediate.

## 1. `INPUT` Revisited

`INPUT` is great for asking questions where the user types an answer and hits RETURN.

```basic
10 INPUT "WHAT IS YOUR NAME"; N$
20 PRINT "HELLO, "; N$
```

You can ask for multiple variables at once:
```basic
10 INPUT "ENTER X,Y COORDINATES"; X, Y
```

## 2. `GET`: The Real-Time Input

`GET` reads a single keypress from the keyboard buffer. It does **not** wait for the user to press a key, and it does **not** wait for RETURN.

If no key is pressed, the variable is empty.

**The Standard "Wait for Key" Loop:**
```basic
10 GET K$
20 IF K$ = "" THEN GOTO 10
30 PRINT "YOU PRESSED: "; K$
```

This is essential for controlling games (like Snake!).

## 3. Handling Input

Since `GET` returns a string, you often need to check what it is.

```basic
10 GET A$
20 IF A$ = "" THEN GOTO 10
30 IF A$ = "A" THEN PRINT "LEFT"
40 IF A$ = "D" THEN PRINT "RIGHT"
50 GOTO 10
```

## 4. The Challenge: The Quiz Master

Create a multiple-choice quiz program.

1.  **Ask a Question:** Print a question and 3 options (A, B, C).
2.  **Wait for Input:** Use `GET` to wait for the user to press A, B, or C.
3.  **Check Answer:**
    - If they press the correct key, print "CORRECT!" and add to their score.
    - If they press the wrong key, print "WRONG!".
    - Ignore other keys.
4.  **Repeat:** Do this for at least 3 questions.
5.  **Final Score:** Print the total score at the end.

**Tip:** You can use `GOSUB` to handle the "Wait for Input" part if you want to be fancy!
