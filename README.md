# COMPUTER SYSTEM ARCHITECTURE (DSC-2)
## CPU SIM – PRACTICAL FILE

**Course:** B.Sc. (Hons.) Computer Science  
**Subject:** Computer System Architecture  
**Software:** CPU Sim 3.6.9 or higher  
**Architecture:** Mano Basic Computer

---

# SOFTWARE REQUIREMENTS

1. CPU Sim 3.6.9 or higher.
2. Java installed on the computer.
3. Mano Basic Computer machine configuration.
4. Text editor for writing assembly programs.

# PRACTICAL 1: DESIGN A MACHINE BASED ON GIVEN ARCHITECTURE

### Aim
To create a machine in CPU Sim using the given Mano Basic Computer architecture.

### Architecture Details

| Register | Size |
|---|---:|
| IR | 16 bits |
| DR | 16 bits |
| AC | 16 bits |
| AR | 16 bits |
| PC | 12 bits |
| I | 1 bit |
| E | 1 bit |

**Memory:**
- Memory size: 4096 words
- Word size: 16 bits

### Procedure

1. Open CPU Sim.
2. Create a new machine.
3. Open the machine configuration settings.
4. Create the following registers:
   - IR – 16 bits
   - DR – 16 bits
   - AC – 16 bits
   - AR – 16 bits
   - PC – 12 bits
   - I – 1 bit
   - E – 1 bit
5. Create memory with 4096 words.
6. Set each memory word to 16 bits.
7. Create the instruction format.
8. Divide the instruction into:
   - Opcode: 3 bits
   - Address: 12 bits
   - Indirect bit: 1 bit
9. Define the memory-reference instructions.
10. Define the register-reference instructions.
11. Define the input-output instructions.
12. Save the machine configuration.

### Instruction Set

**Memory Reference Instructions**

| Instruction | Hexadecimal |
|---|---|
| AND | 0XXX |
| ADD | 1XXX |
| LDA | 2XXX |
| STA | 3XXX |
| BUN | 4XXX |
| BSA | 5XXX |
| ISZ | 6XXX |

**Indirect Instructions**

| Instruction | Hexadecimal |
|---|---|
| AND_I | 8XXX |
| ADD_I | 9XXX |
| LDA_I | AXXX |
| STA_I | BXXX |
| BUN_I | CXXX |
| BSA_I | DXXX |
| ISZ_I | EXXX |

**Register Reference Instructions**

| Instruction | Hexadecimal |
|---|---|
| CLA | 7800 |
| CLE | 7400 |
| CMA | 7200 |
| CME | 7100 |
| CIR | 7080 |
| CIL | 7040 |
| INC | 7020 |
| SPA | 7010 |
| SNA | 7008 |
| SZA | 7004 |
| SZE | 7002 |
| HLT | 7001 |

**Input-Output Instructions**

| Instruction | Hexadecimal |
|---|---|
| INP | F800 |
| OUT | F400 |

### Result
The Mano Basic Computer architecture was successfully designed in CPU Sim.

---

# PRACTICAL 2: CREATE A FETCH ROUTINE

### Aim
To create and execute the fetch routine of the instruction cycle.

### Procedure

1. Open the Mano machine in CPU Sim.
2. Open the microinstruction editor.
3. Create the fetch microinstructions.
4. Define the register transfers.
5. Save the microinstructions.
6. Execute the machine step by step.
7. Observe the changes in PC, AR, IR and memory.

### Fetch Cycle

**Step 1: Transfer PC to AR**

```text
AR ← PC
```

**Step 2: Read memory and increment PC**

```text
IR ← M[AR]
PC ← PC + 1
```

**Step 3: Decode instruction**

```text
Decode IR(12–14)
AR ← IR(0–11)
I ← IR(15)
```

### Explanation

- PC contains the address of the next instruction.
- AR stores the memory address.
- IR stores the fetched instruction.
- The control unit decodes the opcode.
- The machine proceeds to the execute cycle.

### Result
The fetch routine of the instruction cycle was implemented successfully.

---

# PRACTICAL 3: ADD TWO USER-ENTERED NUMBERS

### Aim
To write an assembly language program to add two numbers entered by the user.

### Procedure

1. Open CPU Sim.
2. Open the Mano machine.
3. Open the assembly program editor.
4. Create a new program.
5. Enter the following code.
6. Assemble and load the program.
7. Execute the program.
8. Enter two numbers.
9. Observe the sum in the output.

### Program

```asm
        INP
        STA NUM1

        INP
        ADD NUM1

        OUT
        HLT

NUM1,   HEX 0000
```

### Explanation

| Instruction | Function |
|---|---|
| INP | Takes input from user |
| STA NUM1 | Stores first number |
| INP | Takes second input |
| ADD NUM1 | Adds first number to AC |
| OUT | Displays result |
| HLT | Stops execution |

### Sample Input

```text
First number: 5
Second number: 3
```

### Expected Output

```text
8
```

### Result
The addition of two user-entered numbers was performed successfully.

---

# PRACTICAL 4: SUBTRACT TWO USER-ENTERED NUMBERS

### Aim
To write an assembly language program to subtract two numbers.

### Procedure

1. Open the assembly editor.
2. Create a new program.
3. Enter the following code.
4. Assemble and load it.
5. Run the program.
6. Enter two numbers.
7. Observe the result.

### Program

```asm
        INP
        STA NUM1

        INP
        STA NUM2

        LDA NUM2
        CMA
        INC
        ADD NUM1

        OUT
        HLT

NUM1,   HEX 0000
NUM2,   HEX 0000
```

### Explanation

| Instruction | Function |
|---|---|
| INP | Takes first input |
| STA NUM1 | Stores first number |
| INP | Takes second input |
| STA NUM2 | Stores second number |
| LDA NUM2 | Loads second number |
| CMA | Complements AC |
| INC | Adds 1 to AC |
| ADD NUM1 | Adds first number |
| OUT | Displays result |
| HLT | Stops program |

**Concept:** Subtraction is performed using 2's complement.

Formula:

```text
A - B = A + (2's complement of B)
```

### Sample Input

```text
10
4
```

### Expected Output

```text
6
```

### Result
The subtraction operation was performed successfully.

---

# PRACTICAL 5: PERFORM LOGICAL OPERATIONS

### Aim
To perform AND, OR, NOT, XOR, NOR and NAND operations on two user-entered numbers.

### Procedure

1. Open CPU Sim.
2. Create a new assembly program.
3. Enter the required logical operation.
4. Assemble and load the program.
5. Enter the two input values.
6. Execute the program.
7. Observe the output.

### 1. AND Operation

**Code:**

```asm
        INP
        STA NUM1
        INP
        AND NUM1
        OUT
        HLT

NUM1,   HEX 0000
```

**Explanation:** AND gives 1 only when both corresponding bits are 1.

**Example:**

```text
A = 6  (0110)
B = 3  (0011)

A AND B = 0010
Output = 2
```

### 2. OR Operation

Mano Basic Computer does not have a direct OR instruction. Use De Morgan's theorem.

**Logic:**

```text
A OR B = NOT(NOT A AND NOT B)
```

**Code logic:**

1. Complement A.
2. Store the result.
3. Complement B.
4. AND it with the complemented A.
5. Complement the result.
6. Display output.

### 3. NOT Operation

**Code:**

```asm
        INP
        CMA
        OUT
        HLT
```

**Explanation:** CMA complements every bit of AC.

### 4. XOR Operation

**Logic:**

```text
A XOR B = (A AND NOT B)
          OR (NOT A AND B)
```

**Procedure:**

1. Read both inputs.
2. Complement B.
3. AND it with A.
4. Store the first result.
5. Complement A.
6. AND it with B.
7. Combine both terms using OR logic.
8. Display the result.

### 5. NOR Operation

**Logic:**

```text
NOR = NOT(A OR B)
```

**Procedure:**

1. Read A and B.
2. Perform OR using De Morgan's theorem.
3. Complement the result.
4. Display output.

### 6. NAND Operation

**Logic:**

```text
NAND = NOT(A AND B)
```

**Procedure:**

1. Read A and B.
2. Perform AND.
3. Complement the result using CMA.
4. Display output.

### Result
The six logical operations were studied and implemented using the available Mano instructions and Boolean identities.

---

# PRACTICAL 6: MEMORY REFERENCE INSTRUCTIONS

### Aim
To simulate memory-reference instructions ADD, LDA, STA, BUN and ISZ.

### Instructions

**1. ADD**

Adds the contents of a memory location to AC.

```asm
        LDA NUM1
        ADD NUM2
        OUT
        HLT

NUM1,   HEX 0005
NUM2,   HEX 0003
```

Output:

```text
8
```

**2. LDA**

Loads the contents of memory into AC.

```asm
        LDA NUM1
        OUT
        HLT

NUM1,   HEX 0005
```

Output: 5

**3. STA**

Stores the contents of AC into memory.

```asm
        LDA NUM1
        STA NUM2
        HLT

NUM1,   HEX 0005
NUM2,   HEX 0000
```

Expected result: NUM2 contains 0005.

**4. BUN**

Unconditionally transfers program control to another address.

```asm
        BUN NEXT

        HLT

NEXT,   LDA NUM1
        OUT
        HLT

NUM1,   HEX 0005
```

Output: 5

**5. ISZ**

Increments the memory value and skips the next instruction if the result becomes zero.

```asm
        LDA NUM1
        STA COUNT

        ISZ COUNT
        BUN NEXT

        HLT

NEXT,   LDA COUNT
        OUT
        HLT

NUM1,   HEX FFFF
COUNT,  HEX 0000
```

Expected output: 0

### Result
Memory-reference instructions were studied and simulated successfully.

---

# PRACTICAL 7: REGISTER REFERENCE INSTRUCTIONS (PART 1)

### Aim
To simulate CLA, CMA, CME and HLT instructions.

### 1. CLA – Clear Accumulator

```asm
        LDA NUM
        CLA
        OUT
        HLT

NUM,    HEX 0005
```

Output: 0

**Function:** Clears AC.

### 2. CMA – Complement Accumulator

```asm
        LDA NUM
        CMA
        OUT
        HLT

NUM,    HEX 0005
```

**Function:** Complements all bits of AC.

### 3. CME – Complement E

```asm
        CME
        HLT
```

**Function:** Complements the E flip-flop.

### 4. HLT – Halt

```asm
        HLT
```

**Function:** Stops program execution.

### Result
CLA, CMA, CME and HLT were successfully studied.

---

# PRACTICAL 8: REGISTER REFERENCE INSTRUCTIONS (PART 2)

### Aim
To simulate INC, SPA, SNA and SZE instructions.

### 1. INC – Increment AC

```asm
        LDA NUM
        INC
        OUT
        HLT

NUM,    HEX 0005
```

Output: 6

### 2. SPA – Skip if AC is Positive

```asm
        LDA NUM
        SPA
        LDA ZERO
        OUT
        HLT

NUM,    HEX 0005
ZERO,   HEX 0000
```

Function: Skips the next instruction if AC is non-negative.

### 3. SNA – Skip if AC is Negative

```asm
        LDA NUM
        SNA
        LDA ZERO
        OUT
        HLT

NUM,    HEX FFFF
ZERO,   HEX 0000
```

Function: Skips the next instruction if AC is negative.

### 4. SZE – Skip if E is Zero

```asm
        CLE
        SZE
        LDA NUM
        HLT

NUM,    HEX 0005
```

Function: Skips the next instruction if E = 0.

### Result
INC, SPA, SNA and SZE instructions were simulated successfully.

---

# PRACTICAL 9: CIR AND CIL INSTRUCTIONS

### Aim
To simulate circular right and circular left shift operations.

### 1. CIR – Circulate Right

```asm
        LDA NUM
        CIR
        OUT
        HLT

NUM,    HEX 0008
```

Function:
- Rotates AC one bit to the right.
- The least significant bit moves to E.
- E moves into the most significant bit.

### 2. CIL – Circulate Left

```asm
        LDA NUM
        CIL
        OUT
        HLT

NUM,    HEX 0008
```

Function:
- Rotates AC one bit to the left.
- The most significant bit moves to E.
- E moves into the least significant bit.

### Result
CIR and CIL instructions were studied and executed successfully.

---

# PRACTICAL 10: ADD NUMBERS UNTIL A NEGATIVE NUMBER IS ENTERED

### Aim
To write an assembly program that adds integers until a negative non-zero number is entered.

### Procedure

1. Open the assembly editor.
2. Create a new program.
3. Enter the following code.
4. Assemble and load.
5. Run the program.
6. Enter positive or zero values.
7. Enter a negative number to stop.
8. Observe the final sum.

### Program Logic

```text
Initialize SUM = 0

Read a number

If number is negative:
    Display SUM
    Stop

Otherwise:
    Add number to SUM
    Repeat
```

### Assembly Code

```asm
START,  INP
        SNA
        BUN ADDNUM
        BUN DONE

ADDNUM, ADD SUM
        STA SUM
        BUN START

DONE,   LDA SUM
        OUT
        HLT

SUM,    HEX 0000
```

### Sample Input

```text
10
5
3
-2
```

### Expected Output

```text
18
```

### Explanation

- INP reads a number.
- SNA checks whether AC is negative.
- BUN ADDNUM runs when the number is non-negative.
- A negative input transfers control to DONE.
- ADD SUM adds the input to the accumulated sum.
- OUT displays the final sum.

### Result
The program successfully adds numbers until a negative non-zero value is entered.

---

# PRACTICAL 11: ADD NUMBERS UNTIL ZERO IS ENTERED

### Aim
To write an assembly program that reads integers and adds them until zero is entered.

### Procedure

1. Open CPU Sim.
2. Open the assembly editor.
3. Enter the following program.
4. Assemble and load it.
5. Execute the program.
6. Enter multiple numbers.
7. Enter zero to stop.
8. Observe the sum.

### Program Logic

```text
Initialize SUM = 0

Read a number

If number is zero:
    Display SUM
    Stop

Otherwise:
    Add number to SUM
    Repeat
```

### Assembly Code

```asm
START,  INP
        SZA
        BUN ADDNUM
        BUN DONE

ADDNUM, ADD SUM
        STA SUM
        BUN START

DONE,   LDA SUM
        OUT
        HLT

SUM,    HEX 0000
```

### Sample Input

```text
5
10
15
0
```

### Expected Output

```text
30
```

### Explanation

- INP reads a number.
- SZA checks whether AC is zero.
- If zero, the program jumps to DONE.
- Otherwise, the number is added to SUM.
- The process repeats until zero is entered.
- OUT displays the final sum.

### Result
The program successfully calculates the sum until zero is entered.

---

# HOW TO RUN A PROGRAM IN CPU SIM

Follow these steps for every assembly practical:

1. Open CPU Sim.
2. Load the Mano Basic Computer machine.
3. Open the assembly language editor.
4. Create a new program.
5. Type or paste the assembly code.
6. Save the program with a `.a` extension if supported by your version.
7. Select Assemble.
8. Select Load.
9. Check for assembly errors.
10. Select Run or Single Step.
11. Enter the required input.
12. Observe the output.
13. Take a screenshot of the code and output.

**Important:** CPU Sim requires the assembly language mnemonics and instruction definitions to match the machine configuration. If your assembler uses different syntax for labels, constants, input/output or program loading, adapt the syntax accordingly.

---

# GITHUB REPOSITORY STRUCTURE

Create the following folders:

```text
CPU-Sim-Practicals/
│
├── README.md
│
├── Practical-01-Machine-Architecture/
│   ├── architecture.png
│   └── machine.cpu
│
├── Practical-02-Fetch-Routine/
│   └── fetch.png
│
├── Practical-03-Addition/
│   ├── addition.a
│   └── output.png
│
├── Practical-04-Subtraction/
│   ├── subtraction.a
│   └── output.png
│
├── Practical-05-Logical-Operations/
│   ├── and.a
│   ├── or.a
│   ├── not.a
│   ├── xor.a
│   ├── nor.a
│   └── nand.a
│
├── Practical-06-Memory-Reference/
│   └── memory-reference.a
│
├── Practical-07-Register-Reference/
│   └── register-reference-1.a
│
├── Practical-08-Register-Reference/
│   └── register-reference-2.a
│
├── Practical-09-CIR-CIL/
│   └── cir-cil.a
│
├── Practical-10-Sum-Negative/
│   └── sum-negative.a
│
└── Practical-11-Sum-Zero/
    └── sum-zero.a
```

# CONCLUSION

All eleven practicals of Computer System Architecture were studied using CPU Sim and the Mano Basic Computer instruction set. The practicals cover machine architecture, instruction cycles, arithmetic operations, logical operations, memory-reference instructions and register-reference instructions.
