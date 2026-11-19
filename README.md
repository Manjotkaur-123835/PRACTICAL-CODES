# CPU Sim Practicals

## Practical 1: Create Machine Architecture

**Steps:**
1. Open CPU Sim.
2. Click File → Open Machine.
3. Select `Wombat1.cpu`.
4. Check the registers and RAM.
5. Save the machine.

## Practical 2: Open and Run Assembly Program

**Steps:**
1. Click File → Open Text.
2. Select `W1-0.a`.
3. Click Execute → Assemble & Load.
4. Click Execute → Run.
5. Enter the input when prompted.
6. Check the output in the console.

## Practical 3: Addition

**Code:**
```asm
        read
        store num1
        read
        add num1
        write
        stop

num1:   .data 2 0
```

**Input:** 5, 3

**Output:** 8

## Practical 4: Subtraction

**Code:**
```asm
        read
        store num1
        read
        store num2
        load num1
        subtract num2
        write
        stop

num1:   .data 2 0
num2:   .data 2 0
```

**Input:** 10, 4

**Output:** 6

## Practical 10: Sum Until Negative Number

**Code:**
```asm
Start:  read
        jmpn Done
        add sum
        store sum
        jump Start

Done:   load sum
        write
        stop

sum:    .data 2 0
```

**Input:** 10, 3, 7, -3

**Output:** 20

## Practical 11: Sum Until Zero

**Code:**
```asm
Start:  read
        jmpz Done
        add sum
        store sum
        jump Start

Done:   load sum
        write
        stop

sum:    .data 2 0
```

**Input:** 5, 10, 15, 0

**Output:** 30
