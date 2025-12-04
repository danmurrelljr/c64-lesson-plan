# Lesson 1: The Basics & Variables

Welcome back to the Commodore 64! This lesson is a refresher on the environment and how to handle data.

## 1. The Environment

When you see the `READY.` prompt, you are in **Direct Mode** (or Immediate Mode). You can type commands and they execute immediately.

Try this:
```basic
PRINT "HELLO WORLD"
```

To write a program, we use **Line Numbers**. This tells the computer to store the command instead of running it immediately.

```basic
10 PRINT "HELLO WORLD"
20 GOTO 10
```

- `RUN`: Executes the program in memory.
- `LIST`: Shows the program code.
- `NEW`: Clears the memory for a new program.
- `SAVE "NAME",8`: Saves to disk (device 8).
- `LOAD "NAME",8`: Loads from disk.

## 2. Variables

C64 BASIC has three main types of variables:

1.  **Float** (Real numbers): The default.
    ```basic
    A = 3.14
    ```
2.  **Integer** (Whole numbers): Suffix with `%`. slightly faster, uses less memory, but range is limited (-32768 to +32767).
    ```basic
    A% = 10
    ```
3.  **String** (Text): Suffix with `$`. Max 255 characters.
    ```basic
    A$ = "COMMODORE"
    ```

## 3. The Challenge: Simple Calculator

Write a program that:
1.  Defines two variables, `A` and `B`, with values of your choice (e.g., 10 and 5).
2.  Calculates their Sum, Difference, Product, and Quotient.
3.  Prints the results nicely to the screen.

**Example Output:**
```text
NUMBERS ARE 10 AND 5
SUM: 15
DIFF: 5
PROD: 50
QUOT: 2
```

**Bonus:** Use `INPUT` to ask the user for the numbers instead of hardcoding them!
```basic
INPUT "ENTER FIRST NUMBER"; A
```

## 4. How to Run
1.  Type your code.
2.  Type `RUN`.
3.  Debug if necessary!
