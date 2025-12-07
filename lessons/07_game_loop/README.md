# Lesson 7: Game Loops & Timing

Welcome to the "Architecture" class. Up until now, our programs have mostly been linear (Start -> Do Thing -> End) or simple loops.

Real games follow a specific pattern called the **Game Loop**.

## 1. The Game Loop Structure

Every frame (usually 60 times a second), a game does three things:
1.  **Input:** Check keys/joysticks.
2.  **Update:** Move characters, check collisions, update timers.
3.  **Draw:** Update the screen.

```basic
10 REM *** INITIAL SETUP ***
20 X = 10 : Y = 10

100 REM *** INPUT ***
110 GET K$

200 REM *** UPDATE ***
210 IF K$="A" THEN X = X - 1
220 REM (Add boundaries, physics, etc here)

300 REM *** DRAW ***
310 PRINT CHR$(19); : REM HOME CURSOR (Don't clear screen, just move to top)
320 POKE 1024 + X + (Y*40), 81 : REM DRAW BALL

400 GOTO 100 : REM LOOP FOREVER
```

## 2. Timing with `TI` (The Jiffy Clock)

The variable `TI` counts up by 1 every 1/60th of a second. We can use this for delays or timers without freezing the computer!

**The Old Way (Freezes Computer):**
`FOR I = 1 TO 500 : NEXT`

**The New Way (Non-Blocking):**
```basic
10 NOW = TI
20 TARGET = NOW + 60 : REM 1 SECOND LATER
30 IF TI < TARGET THEN GOTO 30
```
*Wait... that's still blocking!*

**The "Game Loop" Way:**
```basic
10 TARGET = TI + 300 : REM 5 SECONDS
100 REM ... GAME LOOP ...
200 IF TI > TARGET THEN GOSUB 1000 : REM TIME IS UP!
300 GOTO 100
```
This lets the player move and shoot *while* the timer is ticking down!

## 3. `TI$` (The Real-Time Clock)

`TI$` is a string "HHMMSS".
- Reset it: `TI$ = "000000"`
- Read it: `PRINT TI$`

## 4. The Challenge: Reflex Tester

Write a game that tests your reaction time.

1.  Print "GET READY..."
2.  Wait for a **random** amount of time (2-5 seconds).
    - *Hint: Use `TI` + `RND` to pick a target time.*
3.  Print "GO!!!"
4.  Start counting time (Save the current `TI` in a variable called `START`).
5.  Wait for the user to press ANY key.
6.  When they press a key, get the current `TI` (`END`).
7.  Calculate the difference (`DIFF = END - START`).
8.  Print "YOUR REACTION TIME: " + `DIFF` + " JIFFIES".

**Score Guide:**
- < 15: Superhuman
- 15-30: Gamer
- 30-60: Average
- > 60: ...Are you awake?
