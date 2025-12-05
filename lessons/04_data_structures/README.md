# Lesson 4: Data Structures

Writing `PRINT` statements for every single line of text gets tedious. Let's learn how to store data efficiently.

## 1. Arrays (`DIM`)

Arrays allow you to store a list of values under one variable name.

```basic
10 DIM A(5) : REM CREATES A LIST OF 6 ITEMS (0 TO 5)
20 A(0) = 10
30 A(1) = 20
40 PRINT A(0) + A(1)
```

- **Default size:** If you don't use `DIM`, arrays default to size 10 (indices 0-10).
- **String Arrays:** `DIM N$(20)` stores 21 strings.

## 2. `READ`, `DATA`, and `RESTORE`

This is the most common way to store game data (level maps, quiz questions, sprite data) in BASIC.

- `DATA`: Stores a list of values. The computer ignores these lines until asked to read them.
- `READ`: Reads the next value from the `DATA` lines into a variable.
- `RESTORE`: Resets the "read pointer" back to the beginning.

**Example:**
```basic
10 READ A, B$
20 PRINT "NUMBER IS"; A
30 PRINT "TEXT IS "; B$
40 END
100 DATA 42, "THE ANSWER"
```

**Looping through Data:**
```basic
10 FOR I = 1 TO 3
20 READ N$
30 PRINT "FRIEND #"; I; ": "; N$
40 NEXT I
100 DATA "FRODO", "SAM", "GANDALF"
```

## 3. The Challenge: Data-Driven Quiz

Rewrite your Quiz Master program to use `READ` and `DATA`.

1.  **Store Questions in DATA:**
    Format: Question, Option A, Option B, Option C, Correct Answer Key
    ```basic
    1000 DATA "WHO MADE THE C64?", "ATARI", "COMMODORE", "APPLE", "B"
    1010 DATA "HOW MUCH RAM?", "64 KB", "32 KB", "128 KB", "A"
    1020 DATA "END", "", "", "", ""
    ```
2.  **Main Loop:**
    - Read the Question.
    - If Question is "END", stop the game.
    - Read the 3 Options and the Correct Answer.
    - Print the Question and Options.
    - Get User Input.
    - Compare Input to Correct Answer.
    - Loop back to read the next question.

**Why is this better?**
You can now add 50 questions just by adding `DATA` lines, without changing your code logic at all!
