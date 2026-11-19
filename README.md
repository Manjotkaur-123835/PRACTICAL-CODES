Step 2: Create instruction format
We need two fields:

Field

Bits

Opcode

4

Address

12

Total

16

Step 3: Create the instructions
Open the Instructions section in CPU Sim.

Start by creating these memory-reference instructions:

Name

Opcode

AND

0xxx

ADD

1xxx

LDA

2xxx

STA

3xxx

BUN

4xxx

ISZ

6xxx

Then we'll add register-reference and input/output instructions.

Your next task
Tell me what you see on your CPU Sim screen now.

Instruction

Instruction Set

Microinstructions

Fetch Sequence

Or send me a screenshot of your CPU Sim window.

I'll guide you button by button, including what values to enter. Don't worry about memorizing anything yet.



I DONT HAVE ENOUGH TIME TO PERFORM IT SO JUST GIVE ME STEPS AND THEN THE CODE WITH THE PRACTICAL HEADING

Understood. No more questions or interactive practice. I'll give you all 8 practicals in record format, with the practical heading, aim, procedure, code, and expected output wherever applicable.

You can copy these into your practical notebook and use the instructions for tomorrow's lab examination.

CSA Practical File – CPU Sim 3.6.9
Practical 1: Design a machine based on the given architecture
Aim: To design a basic computer architecture using CPU Sim.

Software required: CPU Sim 3.6.9 or higher.

Architecture specifications:

Component

Size

IR

16 bits

DR

16 bits

AC

16 bits

AR

12 bits

PC

12 bits

I

1 bit

E

1 bit

Memory

4096 words

Memory word size

16 bits

Procedure:

Open CPU Sim.

Select File → New Machine.

Open the Registers configuration.

Create IR, DR, AC, AR, PC, I and E with the specified bit sizes.

Create memory RAM with 4096 words and 16 bits per word.

Open the instruction format configuration.

Create an opcode field of 4 bits and an address field of 12 bits.

Define the required machine instructions.

Configure the microinstructions and fetch sequence.

Save the machine as BasicComputer.cpu.

Instruction codes:

Instruction

Hexadecimal

AND

0xxx

ADD

1xxx

LDA

2xxx

STA

3xxx

BUN

4xxx

BSA

5xxx

ISZ

6xxx

AND indirect

8xxx

ADD indirect

9xxx

LDA indirect

Axxx

STA indirect

Bxxx

BUN indirect

Cxxx

BSA indirect

Dxxx

ISZ indirect

Exxx

CLA

7800

CLE

7400

CMA

7200

CME

7100

CIR

7080

CIL

7040

INC

7020

SPA

7010

SNA

7008

SZA

7004

SZE

7002

HLT

7001

INP

F800

OUT

F400

Result: The basic computer architecture was designed using CPU Sim.

Practical 2: Create a Fetch Routine of the Instruction Cycle
Aim: To implement the fetch routine of the instruction cycle.

Procedure:

Open the previously created Basic Computer machine.

Open the microinstructions configuration.

Create the fetch sequence.

Transfer PC to AR.

Read the memory location addressed by AR into IR.

Increment PC.

Decode the instruction.

Save the machine.

Fetch sequence:


text
T0: AR ← PC
T1: IR ← M[AR], PC ← PC + 1
T2: Decode IR
T3: AR ← IR(0–11)
Explanation:

PC contains the address of the next instruction.

AR receives the address from PC.

IR receives the instruction from memory.

PC increments to point to the next instruction.

The opcode is decoded for execution.

Result: The fetch routine of the instruction cycle was created.

Practical 3: Write an assembly program to simulate ADD operation on two user-entered numbers
Aim: To write an assembly language program to add two numbers entered by the user.

Procedure:

Open BasicComputer.cpu.

Select File → Open Text.

Open or create P03_ADD.a.

Enter the assembly program.

Press Ctrl + 2 to assemble and load.

Press Ctrl + R to execute.

Enter two numbers.

Observe the sum in the output console.

Program: P03_ADD.a


asm
        INP
        STA A
        INP
        ADD A
        STA SUM
        OUT
        HLT

A:      .data 1 0
SUM:    .data 1 0
Sample input:

First number: 25

Second number: 17

Output:


text
42
Explanation:

INP accepts a number.

STA stores the first number in memory.

ADD adds the stored number to AC.

OUT displays the result.

HLT stops the program.

Result: The addition of two user-entered numbers was performed successfully. 

GitHub
+1

Practical 4: Write an assembly program to simulate SUBTRACT operation on two user-entered numbers
Aim: To subtract two numbers entered by the user.

Procedure:

Open the Basic Computer machine.

Open practical04.a.

Assemble and load using Ctrl + 2.

Run using Ctrl + R.

Enter two numbers.

Observe the subtraction result.

Program: practical04.a

Use the repository's original program: Open subtraction code .

Logic:

The Basic Computer does not have a direct SUB instruction. Therefore, subtraction is performed using 2's complement.

A
−
B
=
A
+
B
‾
+
1
A−B=A+ 
B
 +1
CMA complements the second number.

INC adds one.

ADD adds the first number.

Sample input:


text
A = 18
B = 50
Output:


text
-32
Result: Subtraction of two user-entered numbers was performed successfully. 

GitHub
+1

Practical 5: Write an assembly program to simulate logical operations on two user-entered numbers
Aim: To perform AND, OR, NOT, XOR, NOR and NAND operations.

Procedure:

Open the Basic Computer machine.

Open PR05.a.

Assemble and load the program.

Run the program.

Enter two numbers.

Observe all logical operation results.

Program: PR05.a

For the complete tested assembly source, use:

Open logical operations assembly program 
The important logic is:

Operation

Formula

AND

A
⋅
B
A⋅B

OR

A
+
B
A+B

NOT

A
‾
A
 

XOR

A
B
‾
+
A
‾
B
A 
B
 + 
A
 B

NOR

A
+
B
‾
A+B
​
 

NAND

A
⋅
B
‾
A⋅B
 

Sample input:


text
A = 12
B = 10
Expected output:

Operation

Output

AND

8

OR

14

NOT A

-13

NOT B

-11

XOR

6

NOR

-15

NAND

-9

Result: All six logical operations were performed successfully using the Basic Computer instructions. 

GitHub
+1

Practical 6: Write an assembly program for memory-reference instructions
Aim: To simulate ADD, LDA, STA, BUN and ISZ instructions.

Procedure:

Open BasicComputer.cpu.

Create a new assembly file named PR06.a.

Write the program.

Assemble and load using Ctrl + 2.

Run using Ctrl + R.

Observe the final value in AC.

Program: PR06.a


asm
LOOP: LDA PROD
      ADD X
      STA PROD
      ISZ CTR
      BUN LOOP
      LDA PROD
      HLT

X:    .data 1 5
CTR:  .data 1 -3
PROD: .data 1 0
Explanation:

LDA loads data into AC.

ADD adds the contents of memory to AC.

STA stores AC in memory.

ISZ increments CTR and skips the next instruction when CTR becomes zero.

BUN jumps to LOOP.

Sample calculation:

5
+
5
+
5
=
15
5+5+5=15
Expected output:


text
AC = 15
PROD = 15
Result: Memory-reference instructions were successfully simulated. 

GitHub
+1

Practical 7: Write an assembly program to simulate CLA, CMA, CME and HLT instructions
Aim: To simulate register-reference instructions and determine the contents of AC, E, PC, AR and IR in decimal.

Procedure:

Open the Basic Computer machine.

Open a new assembly file PR07.a.

Write the program.

Assemble and load.

Execute the program.

Observe the registers after execution stops.

Program: PR07.a


asm
      LDA NUM
      CLA
      CMA
      CME
      HLT

NUM:  .data 1 25
Explanation:

Instruction

Function

LDA

Loads NUM into AC

CLA

Clears AC

CMA

Complements AC

CME

Complements E

HLT

Stops execution

Expected register values:

Register

Decimal value

AC

65535

E

1

PC

5

AR

1

IR

28673

Note: AC = 65535 represents -1 in 16-bit two's complement.

Result: Register-reference instructions CLA, CMA, CME and HLT were successfully simulated. 

GitHub
+1

Practical 8: Write an assembly program to simulate INC, SPA, SNA and SZE instructions
Aim: To simulate INC, SPA, SNA and SZE instructions and determine register contents after execution.

Procedure:

Open the Basic Computer machine.

Create a file named PR08.a.

Enter the assembly program.

Assemble and load.

Run the program.

Observe the register values.

Program: PR08.a


asm
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

NUM:  .data 1 -2
Explanation:

Instruction

Function

INC

Increments AC by one

SPA

Skips next instruction if AC is positive or zero

SNA

Skips next instruction if AC is negative

SZE

Skips next instruction if E is zero

Expected register values:

Register

Decimal value

AC

1

E

0

PC

11

AR

1

IR

28673

Result: Register-reference skip instructions were successfully simulated. 

GitHub
+1

Important correction for Practical 5
The reference repository's practical05.a has duplicate labels and incorrect variable references. Use this corrected version instead.

File: PR05.a


asm
        INP
        STA A
        INP
        STA B

; AND
        LDA A
        AND B
        STA ANDR
        OUT

; NOT A
        LDA A
        CMA
        STA NOTA
        OUT

; NOT B
        LDA B
        CMA
        STA NOTB
        OUT

; OR
        LDA NOTA
        AND NOTB
        CMA
        STA ORR
        OUT

; NAND
        LDA ANDR
        CMA
        STA NANDR
        OUT

; NOR
        LDA ORR
        CMA
        STA NORR
        OUT

; XOR
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
If your assembler rejects semicolon comments, remove the comment lines.

11. Final GitHub repository setup
Use these exact files:

CSA-CPU-SIM-Practicals

Recommended repository structure


text
CSA-CPU-SIM-Practicals/
│
├── README.md
├── BasicComputer.cpu
│
└── Practicals/
    ├── P03_ADD.a
    ├── practical04.a
    ├── PR05.a
    ├── PR06.a
    ├── PR07.a
    └── PR08.a
Reference machine and programs

Download reference repository ZIP 
How to run any assembly program tomorrow
Open CPU Sim.

File → Open Machine → BasicComputer.cpu.

File → Open Text → select your .a program.

Press Ctrl + 2 (Assemble and Load).

Press Ctrl + R (Run).

Enter input if requested.

Check output and registers.

Compatibility note: The reference machine repository documents CPU Sim 4.0.11, whereas your syllabus permits 3.6.9 or higher. Check that the machine file loads correctly in your lab version before relying on it. 

GitHub
+1

12. Last-minute viva revision
Learn these seven concepts especially well:

AC – Accumulator.

PC – Program Counter.

IR – Instruction Register.

AR – Address Register.

Fetch cycle – Fetch, decode and execute.

CMA – One's complement of AC.

ISZ – Increment memory and skip if zero.

One final thing: The practical questions visible in your screenshots end at Practical 8. I have kept this record focused on those eight rather than adding unrelated experiments.

For tomorrow, prioritize understanding how INP, OUT, LDA, STA, ADD, CMA, INC, BUN and ISZ work. These instructions form the foundation of most of your programs.



I WANT TO ADD README .MD SO GIVE ME ALL CODES IN ONE GO WITH THEIR HEADING I WILL DIRECTLY COPY PASTE THEM



.

Copy everything below directly into your GitHub repository's README.md file.

I've arranged it with all 8 practical headings, aims, procedures, assembly codes, sample outputs and results.

Repository name: CSA-CPU-SIM-Practicals

Writing


Computer System Architecture (CSA) – CPU Sim Practicals
Software: CPU Sim 3.6.9 or higher
Subject: Computer System Architecture
Language: Assembly Language

List of Practicals
Design a Basic Computer Machine Architecture.
Create the Fetch Routine of the Instruction Cycle.
Write an Assembly Program to Add Two User-Entered Numbers.
Write an Assembly Program to Subtract Two User-Entered Numbers.
Perform Logical Operations: AND, OR, NOT, XOR, NOR and NAND.
Simulate Memory-Reference Instructions: ADD, LDA, STA, BUN and ISZ.
Simulate Register-Reference Instructions: CLA, CMA, CME and HLT.
Simulate Register-Reference Instructions: INC, SPA, SNA and SZE.
Practical 1: Design a Basic Computer Machine Architecture
Aim
To design a basic computer architecture using CPU Sim.

Architecture Specifications

Register/Component	Size
IR	16 bits
DR	16 bits
AC	16 bits
AR	12 bits
PC	12 bits
I	1 bit
E	1 bit
Memory	4096 words
Memory Word Size	16 bits
Procedure
Open CPU Sim.
Select File → New Machine.
Open the Registers configuration.
Create IR, DR, AC, AR, PC, I and E with their specified sizes.
Create RAM with 4096 words and 16-bit word size.
Configure the instruction format.
Create a 4-bit opcode field and a 12-bit address field.
Define the required machine instructions.
Configure the microinstructions and fetch sequence.
Save the machine as BasicComputer.cpu.
Result
The basic computer architecture was designed using CPU Sim.

Practical 2: Create a Fetch Routine of the Instruction Cycle
Aim
To implement the fetch routine of the instruction cycle.

Procedure
Open the previously created Basic Computer machine.
Open the microinstructions configuration.
Create the fetch sequence.
Transfer PC to AR.
Read the instruction from memory into IR.
Increment PC.
Decode the instruction.
Save the machine.
Fetch Routine

text
T0: AR ← PC
T1: IR ← M[AR], PC ← PC + 1
T2: Decode IR
T3: AR ← IR(0–11)
Explanation
PC contains the address of the next instruction.
AR receives the address from PC.
IR receives the instruction from memory.
PC increments to point to the next instruction.
The opcode is decoded for execution.
Result
The fetch routine of the instruction cycle was created.

Practical 3: Addition of Two User-Entered Numbers
Aim
To write an assembly language program to add two numbers entered by the user.

Program: P03_ADD.a

asm
        INP
        STA A
        INP
        ADD A
        STA SUM
        OUT
        HLT

A:      .data 1 0
SUM:    .data 1 0
Procedure
Open the Basic Computer machine.
Open a new assembly file.
Enter the above program.
Assemble and load the program.
Run the program.
Enter two numbers.
Observe the result.
Sample Input

text
First Number: 25
Second Number: 17
Output

text
42
Explanation
INP accepts input from the user.
STA stores the first number in memory.
ADD adds the stored number to AC.
OUT displays the result.
HLT stops execution.
Result
Addition of two user-entered numbers was performed.

Practical 4: Subtraction of Two User-Entered Numbers
Aim
To write an assembly language program to subtract two numbers entered by the user.

Program: P04_SUBTRACT.a

asm
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
Procedure
Open the Basic Computer machine.
Create a new assembly file.
Enter the above program.
Assemble and load the program.
Run the program.
Enter two numbers.
Observe the subtraction result.
Sample Input

text
First Number: 18
Second Number: 50
Output

text
-32
Explanation
Subtraction is performed using 2's complement.

Formula:


text
A - B = A + (~B) + 1
CMA complements AC.
INC increments AC by one.
ADD adds the first number.
OUT displays the result.
Result
Subtraction of two user-entered numbers was performed.

Practical 5: Logical Operations – AND, OR, NOT, XOR, NOR and NAND
Aim
To perform logical operations on two user-entered numbers.

Program: P05_LOGICAL.a

asm
        INP
        STA A
        INP
        STA B

; AND
        LDA A
        AND B
        STA ANDR
        OUT

; NOT A
        LDA A
        CMA
        STA NOTA
        OUT

; NOT B
        LDA B
        CMA
        STA NOTB
        OUT

; OR
        LDA NOTA
        AND NOTB
        CMA
        STA ORR
        OUT

; NAND
        LDA ANDR
        CMA
        STA NANDR
        OUT

; NOR
        LDA ORR
        CMA
        STA NORR
        OUT

; XOR
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
Procedure
Open the Basic Computer machine.
Create a new assembly file.
Enter the above program.
Assemble and load.
Run the program.
Enter two numbers.
Observe the logical operation results.
Logical Operation Formulas

Operation	Formula
AND	A AND B
OR	A OR B
NOT	Complement of A
XOR	A XOR B
NOR	NOT (A OR B)
NAND	NOT (A AND B)
Result
Logical operations were implemented using assembly instructions.

Practical 6: Memory-Reference Instructions
Aim
To simulate ADD, LDA, STA, BUN and ISZ instructions.

Program: P06_MEMORY_REFERENCE.a

asm
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
Procedure
Open the Basic Computer machine.
Create a new assembly file.
Enter the program.
Assemble and load.
Run the program.
Observe the final result in AC.
Explanation
LDA loads memory contents into AC.
ADD adds memory contents to AC.
STA stores AC in memory.
ISZ increments memory and skips the next instruction if the result becomes zero.
BUN performs an unconditional branch.
Sample Calculation

text
5 + 5 + 5 = 15
Expected Result

text
AC = 15
PROD = 15
Result
Memory-reference instructions were simulated successfully.

Practical 7: Register-Reference Instructions – CLA, CMA, CME and HLT
Aim
To simulate CLA, CMA, CME and HLT instructions and observe register contents.

Program: P07_REGISTER_REFERENCE.a

asm
        LDA NUM
        CLA
        CMA
        CME
        HLT

NUM:    .data 1 25
Procedure
Open the Basic Computer machine.
Create a new assembly file.
Enter the program.
Assemble and load.
Run the program.
Observe the register values.
Explanation

Instruction	Function
CLA	Clears AC
CMA	Complements AC
CME	Complements E
HLT	Halts execution
Result
Register-reference instructions CLA, CMA, CME and HLT were simulated.

Practical 8: Register-Reference Instructions – INC, SPA, SNA and SZE
Aim
To simulate INC, SPA, SNA and SZE instructions and observe register contents.

Program: P08_SKIP_INSTRUCTIONS.a

asm
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
Procedure
Open the Basic Computer machine.
Create a new assembly file.
Enter the program.
Assemble and load.
Run the program.
Observe the register values.
Explanation

Instruction	Function
INC	Increments AC by one
SPA	Skips next instruction if AC is positive or zero
SNA	Skips next instruction if AC is negative
SZE	Skips next instruction if E is zero
Result
Register-reference skip instructions were simulated successfully.

How to Run Programs in CPU Sim
Open CPU Sim.
Select File → Open Machine.
Open BasicComputer.cpu.
Select File → Open Text.
Choose the required .a file.
Assemble and load the program using the appropriate menu command.
Run the program.
Enter input values if requested.
Observe the output and registers.
Note: Keyboard shortcuts may differ between CPU Sim versions. Use the equivalent menu commands if necessary.

Important CPU Sim Instructions

Instruction	Meaning
INP	Input
OUT	Output
LDA	Load Accumulator
STA	Store Accumulator
ADD	Addition
AND	Logical AND
CMA	Complement Accumulator
CLA	Clear Accumulator
INC	Increment Accumulator
BUN	Branch Unconditionally
ISZ	Increment and Skip if Zero
HLT	Halt
Important Viva Questions
1. What is CPU Sim?
CPU Sim is a simulator used to design and simulate computer architectures.

2. What is AC?
AC stands for Accumulator. It stores intermediate arithmetic and logical results.

3. What is PC?
PC stands for Program Counter. It stores the address of the next instruction.

4. What is IR?
IR stands for Instruction Register. It stores the currently fetched instruction.

5. What is AR?
AR stands for Address Register. It stores the memory address.

6. What is DR?
DR stands for Data Register. It stores data read from memory.

7. What is the fetch cycle?
It is the process of retrieving an instruction from memory.

8. What is CMA?
CMA complements every bit of AC.

9. What is CLA?
CLA clears the Accumulator.

10. What is INC?
INC increments the Accumulator by one.

11. What is BUN?
BUN performs an unconditional branch.

12. What is ISZ?
ISZ increments a memory word and skips the next instruction if the result is zero.

13. What is HLT?
HLT stops program execution.

14. What is RAM?
RAM stands for Random Access Memory. It stores data and instructions.

15. What is an opcode?
An opcode specifies the operation to be performed by the CPU.

Repository Structure

text
CSA-CPU-SIM-Practicals/
│
├── README.md
├── BasicComputer.cpu
│
└── Practicals/
    ├── P03_ADD.a
    ├── P04_SUBTRACT.a
    ├── P05_LOGICAL.a
    ├── P06_MEMORY_REFERENCE.a
    ├── P07_REGISTER_REFERENCE.a
    └── P08_SKIP_INSTRUCTIONS.a
References
CPU Sim: https://www.cs.colby.edu/djskrien/CPUSim/
Reference practical repository: https://github.com/Riya44244/CPU-SIMPRACTICALS
End of CSA CPU Sim Practical File

One important note before you publish: The assembly programs above are formatted for your practical file, but you should test them against your actual BasicComputer.cpu machine. In particular, the subtraction and logical-operation programs depend on how your machine implements input, output and complement instructions. The README is documentation, not proof that every program assembles successfully.


Log in for personalized, step-by-step guidance.


Log in

Sign up for free
Create a new account to keep this chat.

ChatGPT is AI and can make mistakes.


Chat
