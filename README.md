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
```
module logic_gates(
    input  wire a, b,
    output wire y_and,y_or,y_not
);
    assign y_and = a & b;
    assign y_or = a | b;
    assign y_not = ~a;
endmodule
```
# **Test Bench Program**
```
module tb;
reg a_tb, b_tb;
wire y_and,y_or,y_not;
logic_gates uut (.a(a_tb), .b(b_tb), .y_and(y_and), .y_or(y_or), .y_not(y_not));



initial begin
        // ---- VCD dump setup ----
        $dumpfile("logic_gates.vcd");   // name of the VCD file to be generated
        $dumpvars(0, tb);   // dump all signals in this testbench hierarchy

	$monitor("a_tb=%b b_tb=%b y_and=%b y_or=%b y_not=%b", 
	a_tb,b_tb,y_and,y_or,y_not);
	a_tb=0; b_tb=0; #10;
	a_tb =0; b_tb=1; #10;
	a_tb =1; b_tb=0; #10;
	a_tb =1; b_tb=1; #10;
	$finish;
	end
endmodule
```


# TRUTH TABLE
 
<img width="737" height="230" alt="2b5b0868-8bf5-402d-a848-26c940779c97" src="https://github.com/user-attachments/assets/0cd31460-9f7d-4904-827e-ca95535d0fbd" />


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

<img width="1600" height="489" alt="bf274c85-ef1c-4817-8847-0acff76fb9ca" src="https://github.com/user-attachments/assets/9fce6b55-6867-4f83-9d4d-a2304316fc70" />

 
# RESULT 
The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis.

Result Thus, the LOGIC GATES was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

