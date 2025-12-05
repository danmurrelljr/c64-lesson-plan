# Lesson 5: Screen Manipulation (PEEK & POKE)

This is where the C64 shines. We are going to bypass the slow `PRINT` command and write directly to the computer's memory!

## 1. The Memory Map

The C64 has 64KB of memory. Each byte has an address from 0 to 65535.

- **`PEEK(Address)`**: Reads the value (0-255) at that address.
- **`POKE Address, Value`**: Writes a value (0-255) to that address.

## 2. Screen Memory ($0400 or 1024)

The screen is a grid of 40 columns x 25 rows.
- Top-Left corner: Address **1024**
- Bottom-Right corner: Address **2023**

Try this:
```basic
POKE 1024, 1   : REM PUTS AN 'A' AT TOP LEFT
POKE 1025, 2   : REM PUTS A 'B' NEXT TO IT
```

**Formula for X, Y coordinates:**
`Address = 1024 + Y * 40 + X`
(Where X is 0-39 and Y is 0-24)

## 3. Color Memory ($D800 or 55296)

Each character on the screen has a corresponding color byte.
- Top-Left Color: Address **55296**

Colors are numbered 0-15 (0=Black, 1=White, 2=Red, etc.).

```basic
POKE 1024, 81  : REM A BALL
POKE 55296, 2  : REM MAKE IT RED
```

## 4. The Challenge: Screen Painter

Write a program that fills the screen with a pattern.

1.  **Clear the Screen:** `PRINT CHR$(147)`
2.  **Loop through every position:**
    - Use a `FOR` loop from 1024 to 2023.
3.  **Draw something:**
    - `POKE` a random character code (0-255) into each position.
    - `POKE` a random color (0-15) into the corresponding color memory address.
    - *Hint: Color Address = Screen Address + 54272*

**Bonus:** Make it an infinite loop so the screen constantly changes like "The Matrix"!
