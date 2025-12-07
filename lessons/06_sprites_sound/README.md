# Lesson 6: Sprites & Sound

This is the advanced class! Sprites (Movable Object Blocks) and the SID chip are what made the C64 legendary.

## 1. Sprites (The Basics)

Sprites are 24x21 pixel graphics that float *over* the screen.

**Key Memory Addresses (VIC-II Chip):**
- **Enable Sprites:** `53269` (Bitmask: 1=Sprite0, 2=Sprite1, etc.)
- **X Coordinate:** `53248` (Sprite 0)
- **Y Coordinate:** `53249` (Sprite 0)
- **Color:** `53287` (Sprite 0)
- **Sprite Pointer:** `2040` (Screen RAM + 1016). This tells the C64 *where* in memory to find the sprite's picture.

**Example: Turning on a Block**
```basic
10 POKE 2040, 13      : REM POINT SPRITE 0 TO BLOCK 13 (ADDR 832)
20 FOR I = 832 TO 894 : POKE I, 255 : NEXT : REM FILL BLOCK WITH SOLID PIXELS
30 POKE 53248, 100    : REM SET X
40 POKE 53249, 100    : REM SET Y
50 POKE 53269, 1      : REM ENABLE SPRITE 0
```

## 2. Sound (The SID Chip)

The SID chip is complex, but making a noise is easy.

**Key Memory Addresses (SID Chip):**
- **Volume:** `54296` (Set to 15 for max)
- **Voice 1 Freq:** `54272` (Low byte) & `54273` (High byte)
- **Voice 1 Control:** `54276` (17 = Triangle Wave + Gate On, 16 = Gate Off)
- **Envelope:** `54277` (Attack/Decay), `54278` (Sustain/Release)

**Example: A Simple Beep**
```basic
10 POKE 54296, 15    : REM MAX VOLUME
20 POKE 54277, 0     : REM ATTACK/DECAY
30 POKE 54278, 240   : REM SUSTAIN/RELEASE
40 POKE 54272, 0     : REM FREQ LOW
50 POKE 54273, 20    : REM FREQ HIGH
60 POKE 54276, 17    : REM START SOUND (TRIANGLE)
70 FOR I=1 TO 500: NEXT : REM WAIT
80 POKE 54276, 16    : REM STOP SOUND
```

## 3. The Challenge: Sprite Mover

Write a program that:
1.  Creates a simple sprite (a solid block is fine).
2.  Enables it.
3.  Uses `GET` to read keys (e.g., W, A, S, D or I, J, K, L).
4.  Updates the Sprite's X and Y coordinates based on the key press.

**Bonus:** Make a sound every time it moves!
