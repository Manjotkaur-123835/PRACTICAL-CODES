
# CSA CPU SIM PRACTICALS

**Subject:** Computer System Architecture (CSA)  
**Software:** CPU Sim 3.6.9 or higher  
**Language:** Assembly Language

## LIST OF PRACTICALS

1. Design a Basic Computer Machine Architecture.
2. Create a Fetch Routine of the Instruction Cycle.
3. Addition of Two User-Entered Numbers.
4. Subtraction of Two User-Entered Numbers.
5. Logical Operations: AND, OR, NOT, XOR, NOR and NAND.
6. Memory-Reference Instructions: ADD, LDA, STA, BUN and ISZ.
7. Register-Reference Instructions: CLA, CMA, CME and HLT.
8. Register-Reference Instructions: INC, SPA, SNA and SZE.

---

# PRACTICAL 1: DESIGN A BASIC COMPUTER MACHINE ARCHITECTURE

### Aim
To design a basic computer architecture using CPU Sim.

### Architecture Specifications

| Component | Size |
|---|---|
| IR | 16 bits |
| DR | 16 bits |
| AC | 16 bits |
| AR | 12 bits |
| PC | 12 bits |
| I | 1 bit |
| E | 1 bit |
| Memory | 4096 words |
| Word Size | 16 bits |

### Procedure

1. Open CPU Sim.
2. Select File → New Machine.
3. Open Registers configuration.
4. Create IR, DR, AC, AR, PC, I and E.
5. Set their respective bit sizes.
6. Create RAM with 4096 words and 16-bit word size.
7. Configure instruction format.
8. Create a 4-bit opcode and 12-bit address field.
9. Define machine instructions.
10. Configure microinstructions and fetch sequence.
11. Save the machine as BasicComputer.cpu.

### Result
Basic Computer Architecture was designed successfully.

---

# PRACTICAL 2: CREATE A FETCH ROUTINE OF THE INSTRUCTION CYCLE

### Aim
To implement the fetch routine of the instruction cycle.

### Procedure

1. Open the Basic Computer machine.
2. Open Microinstructions configuration.
3. Create the fetch sequence.
4. Transfer PC to AR.
5. Read the instruction from memory into IR.
6. Increment PC.
7. Decode the instruction.
8. Save the machine.

### Fetch Routine

```text
T0: AR ← PC
T1: IR ← M[AR], PC ← PC + 1
T2: Decode IR
T3: AR ← IR(0–11)
```

### Explanation

- PC contains the address of the next instruction.
- AR receives the address from PC.
- IR receives the instruction from memory.
- PC increments to point to the next instruction.
- The instruction is decoded.

### Result
Fetch routine was created successfully.

---

# PRACTICAL 3: ADDITION OF TWO USER-ENTERED NUMBERS

### Aim
To write an assembly language program to add two numbers entered by the user.

### Program: P03_ADD.a

```asm
        INP
        STA A
        INP
        ADD A
        STA SUM
        OUT
        HLT

A:      .data 1 0
SUM:    .data 1 0
```

### Procedure

1. Open BasicComputer.cpu.
2. Open a new assembly file.
3. Enter the above program.
4. Assemble and load.
5. Run the program.
6. Enter two numbers.
7. Observe the output.

### Sample Input

```text
First Number: 25
Second Number: 17
```

### Output

```text
42
```

### Explanation

- INP accepts input.
- STA stores the first number.
- ADD adds the stored number to AC.
- OUT displays the result.
- HLT stops execution.

### Result
Addition of two user-entered numbers was performed successfully.

---

# PRACTICAL 4: SUBTRACTION OF TWO USER-ENTERED NUMBERS

### Aim
To write an assembly language program to subtract two numbers entered by the user.

### Program: P04_SUBTRACT.a

```asm
        INP
        STA A
        INP
        CMA
        INC
        ADD A
        STA DIFF
        OUT
        HLT

A:      .data 1 0
DIFF:   .data 1 0
```

### Procedure

1. Open BasicComputer.cpu.
2. Create a new assembly file.
3. Enter the above program.
4. Assemble and load.
5. Run the program.
6. Enter two numbers.
7. Observe the output.

### Sample Input

```text
First Number: 18
Second Number: 50
```

### Output

```text
-32
```

### Explanation

Subtraction is performed using 2's complement.

Formula:

A - B = A + (~B) + 1

- CMA complements AC.
- INC increments AC.
- ADD adds the first number.
- OUT displays the result.

### Result
Subtraction of two user-entered numbers was performed successfully.

---

# PRACTICAL 5: LOGICAL OPERATIONS – AND, OR, NOT, XOR, NOR AND NAND

### Aim
To perform logical operations on two user-entered numbers.

### Program: P05_LOGICAL.a

```asm
        INP
        STA A
        INP
        STA B

        LDA A
        AND B
        STA ANDR
        OUT

        LDA A
        CMA
        STA NOTA
        OUT

        LDA B
        CMA
        STA NOTB
        OUT

        LDA NOTA
        AND NOTB
        CMA
        STA ORR
        OUT

        LDA ANDR
        CMA
        STA NANDR
        OUT

        LDA ORR
        CMA
        STA NORR
        OUT

        LDA ORR
        AND NANDR
        STA XORR
        OUT

        HLT

A:      .data 1 0
B:      .data 1 0
ANDR:   .data 1 0
NOTA:   .data 1 0
NOTB:   .data 1 0
ORR:    .data 1 0
NANDR:  .data 1 0
NORR:   .data 1 0
XORR:   .data 1 0
```

### Procedure

1. Open BasicComputer.cpu.
2. Create a new assembly file.
3. Enter the program.
4. Assemble and load.
5. Run the program.
6. Enter two numbers.
7. Observe the results.

### Logical Operation Formulas

| Operation | Formula |
|---|---|
| AND | A AND B |
| OR | A OR B |
| NOT | Complement of A |
| XOR | A XOR B |
| NOR | NOT (A OR B) |
| NAND | NOT (A AND B) |

### Result
Logical operations were implemented using assembly instructions.

---

# PRACTICAL 6: MEMORY-REFERENCE INSTRUCTIONS

### Aim
To simulate ADD, LDA, STA, BUN and ISZ instructions.

### Program: P06_MEMORY_REFERENCE.a

```asm
LOOP:   LDA PROD
        ADD X
        STA PROD
        ISZ CTR
        BUN LOOP
        LDA PROD
        HLT

X:      .data 1 5
CTR:    .data 1 -3
PROD:   .data 1 0
```

### Procedure

1. Open BasicComputer.cpu.
2. Create a new assembly file.
3. Enter the program.
4. Assemble and load.
5. Run the program.
6. Observe AC and memory values.

### Explanation

- LDA loads memory contents into AC.
- ADD adds memory contents to AC.
- STA stores AC in memory.
- ISZ increments memory and skips the next instruction if the result is zero.
- BUN performs an unconditional branch.

### Sample Calculation

```text
5 + 5 + 5 = 15
```

### Expected Result

```text
AC = 15
PROD = 15
```

### Result
Memory-reference instructions were simulated successfully.

---

# PRACTICAL 7: REGISTER-REFERENCE INSTRUCTIONS – CLA, CMA, CME AND HLT

### Aim
To simulate CLA, CMA, CME and HLT instructions and observe register contents.

### Program: P07_REGISTER_REFERENCE.a

```asm
        LDA NUM
        CLA
        CMA
        CME
        HLT

NUM:    .data 1 25
```

### Procedure

1. Open BasicComputer.cpu.
2. Create a new assembly file.
3. Enter the program.
4. Assemble and load.
5. Run the program.
6. Observe register values.

### Explanation

| Instruction | Function |
|---|---|
| CLA | Clears AC |
| CMA | Complements AC |
| CME | Complements E |
| HLT | Halts execution |

### Result
Register-reference instructions were simulated successfully.

---

# PRACTICAL 8: REGISTER-REFERENCE INSTRUCTIONS – INC, SPA, SNA AND SZE

### Aim
To simulate INC, SPA, SNA and SZE instructions and observe register contents.

### Program: P08_SKIP_INSTRUCTIONS.a

```asm
        LDA NUM
        INC
        SNA
        HLT
        INC
        SPA
        HLT
        SZE
        HLT
        INC
        HLT

NUM:    .data 1 -2
```

### Procedure

1. Open BasicComputer.cpu.
2. Create a new assembly file.
3. Enter the program.
4. Assemble and load.
5. Run the program.
6. Observe register values.

### Explanation

| Instruction | Function |
|---|---|
| INC | Increments AC by one |
| SPA | Skips next instruction if AC is positive or zero |
| SNA | Skips next instruction if AC is negative |
| SZE | Sk
ChatGPT is AI and can make mistakes.


Chat with ChatGPT
