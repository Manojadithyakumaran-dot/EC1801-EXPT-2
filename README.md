# EXPT 2 - Verification of Logic Gates
### SIMULATION AND VERIFICATION OF AND, OR, AND NOT GATES
## Aim
To design, implement, and verify the functionality of basic AND, OR, and NOT logic gates using Verilog HDL, and verify the functionality using Synopsys VCS and DVE.
# Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
# Boolean Function
The basic logic gates realize the following Boolean functions:

•	AND: Y_AND = A . B
•	OR: Y_OR = A + B
•	NOT: Y_NOT = A'

# Theory / Synopsis
Logic gates are the basic building blocks of digital systems. NAND and NOR are universal gates. XOR produces 1 when its inputs differ, while XNOR produces 1 when its inputs are equal.
# Files to be Created
File name	Purpose
logic_gates.v	Logic-gate RTL
logic_gates_tb.v	All input combinations and VCD generation
 # Verilog  Program
 module basic_gates (
    input  wire a,
    input  wire b,
    output wire y_and,
    output wire y_or,
    output wire y_not
);

    assign y_and = a & b;   // AND gate
    assign y_or  = a | b;   // OR gate
    assign y_not = ~a;      // NOT gate (inverter)

endmodule
# **Test Bench Program**
module basic_gates (
    input  wire a,
    input  wire b,
    output wire y_and,
    output wire y_or,
    output wire y_not
);

    assign y_and = a & b;   // AND gate
    assign y_or  = a | b;   // OR gate
    assign y_not = ~a;      // NOT gate (inverter)

endmodule
# **Truth Table** 
<img width="940" height="318" alt="image" src="https://github.com/user-attachments/assets/8a343bdb-ffb4-4aac-8b88-cf59eca374a8" />

# Simulation Procedure
STEP 1 – Open Terminal
Open a terminal in the experiment folder.
bash

STEP 2 – Load Synopsys Environment
source /synopsys/start.sh

STEP 3 – Compile Using VCS
vcs logic_gates.v logic_gates_tb.v -full64
If compilation is successful, VCS generates the simulation executable:
simv

STEP 4 – Run Simulation
./simv
The terminal displays the input combinations and corresponding output F.
A VCD waveform file is also generated:
exp1_boolean_min.vcd

STEP 5 – Open DVE
dve -full64
Other option
dve -full64 &
A DVE environment will open.

DVE Waveform Verification
In DVE:
Open the testbench hierarchy.
Locate the signals: 
a
b
y_and
y_or
y_not
Add the signals to the waveform window.
Run/inspect the waveform.
Verify that y_and = 1 only when a=1 AND b=1 — the single combination where both inputs are high.
Verify that y_or = 1 whenever a=1 OR b=1 (any input high forces the output high).
Verify that y_not is always the exact complement of a, regardless of b.
The waveform should agree with the truth table.
# Expected Result
The basic logic gates — AND, OR, and NOT — were realized using Verilog HDL:
Y_AND = A.B
Y_OR = A+B
Y_NOT = A'
The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis, matching the expected truth table.
Output
# OUTPUT
<img width="1912" height="1025" alt="Screenshot 2026-10-14 124446" src="https://github.com/user-attachments/assets/2ee97cdc-b76f-49b5-b51a-5c85d280390b" />

# Viva-Voce Questions

•	What is a logic gate?

•	What are the basic logic gates in digital electronics?

•	What is the Boolean expression for an AND gate? An OR gate? A NOT gate?

•	Why is the NOT gate also called an inverter?

•	What is a universal gate, and how can NAND/NOR realize AND, OR, and NOT?

•	What is the purpose of a Verilog testbench?

•	Why is a VCD file generated?

•	What is the purpose of ./simv?
•	What is the purpose of DVE?
•	What is the difference between simulation and synthesis?
•	What is the difference between $dumpfile and $dumpvars?

