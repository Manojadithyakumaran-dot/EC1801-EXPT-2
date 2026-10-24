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
The basic logic gates — AND, NAND, OR, NOR, XOR and NOT — were realized using Verilog HDL:
Y_AND = A.B
Y_NAND = ~(A.B)
Y_OR = A+B
Y_NOR = ~(A+B)
Y_XOR = A^B
Y_NOT = A'

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
    output wire y_nand,
    output wire y_or,
    output wire y_nor,
    output wire y_xor,
    output wire y_not
);

    assign y_and = a & b;   // AND gate
    assign y_nand = ~(a & b);
    assign y_or  = a | b;   // OR gate
    assign y_nor = ~(a |b);
    assign y_xor = a ^ b;
    assign y_not = ~a;      // NOT gate (inverter)
    
    
endmodule
# **Test Bench Program**
module tb2;

    reg a, b;
    wire y_and, y_nand, y_or, y_nor, y_xor, y_not;

    // Instantiate the design under test (DUT)
    basic_gates uut (
        .a(a),
        .b(b),
        .y_and(y_and),
        .y_nand(y_nand),
        .y_or(y_or),
        .y_nor(y_nor),
        .y_xor(y_xor),
        .y_not(y_not)
    );

    initial begin
        // ---- VCD dump setup ----
        $dumpfile("basic_gates.vcd");   // name of the VCD file to be generated
        $dumpvars(0, tb2);               // dump all signals in this testbench hierarchy

        // ---- Apply all 4 input combinations ----
        $monitor("Time=%0t a=%b b=%b | AND=%b NAND=%b OR=%b NOR=%b XNOR=%b NOT(a)=%b", $time, a, b, y_and, y_nand, y_or, y_nor, y_xor, y_not);

        a = 0; b = 0; #10;
        a = 0; b = 1; #10;
        a = 1; b = 0; #10;
        a = 1; b = 1; #10;

        #10 $finish;
#10;
    end

endmodule

# **Truth Table** 

<img width="727" height="257" alt="image" src="https://github.com/user-attachments/assets/421a0542-8098-42d5-a0aa-cf25278e7b7a" />

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
<img width="920" height="232" alt="EXPT 2-NEW expected result" src="https://github.com/user-attachments/assets/e2778e90-29bf-4eb5-8dec-e348d3c8698d" />

The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis, matching the expected truth table.
Output
# OUTPUT
<img width="1847" height="1020" alt="EXPT-2 NEW" src="https://github.com/user-attachments/assets/157cca89-f93b-466c-afd6-441b9eedbec0" />

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

