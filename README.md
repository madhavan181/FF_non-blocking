# FF_blocking_non-blocking
# EXPERIMENT 3A: Simulation of All Flip-Flops using Blocking Statement
# AIM
To design and simulate basic flip-flops (SR, D, JK, and T) using blocking statements in Verilog HDL, and verify their functionality through simulation in Vivado 2023.1.

# APPARATUS REQUIRED
Vivado 2023.1
Computer with HDL Simulator
# DESCRIPTION
Flip-flops are the basic memory elements in sequential circuits.
In this experiment, different types of flip-flops (SR, D, JK, T) are modeled using behavioral modeling with blocking assignment (=) inside the always block.
Blocking assignments execute sequentially in the given order, which makes it easier to describe simple synchronous circuits.

# PROCEDURE
Open Vivado 2023.1.
Create a New RTL Project (e.g., FlipFlop_Simulation).
Add Verilog source files for each flip-flop (SR, D, JK, T).
Add a testbench file to verify all flip-flops.
Run Behavioral Simulation.
Observe waveforms of inputs and outputs for each flip-flop.
Verify that outputs match the truth table.
Save results and capture simulation screenshots.
# VERILOG CODE
SR Flip-Flop (Non Blocking)
```

`timescale 1ns / 1ps

module sr_ff(S,R,clk,rst,Q);
input S,R,clk,rst;
output reg Q;
always @(posedge clk)
begin
if (rst==1)
    Q=0;
else    
    begin
        case({S,R})
            2'b00: Q<= Q;
            2'b01: Q<= 1'b0;
            2'b10: Q<= 1'b1;
            2'b11: Q<= 1'bX;
        endcase
     end
end
endmodule

```
SR Flip-Flop Test bench
```

`timescale 1ns / 1ps

module jk_ff(J,K,clk,rst,Q);
input J,K,clk,rst;
output reg Q;
always @(posedge clk)
begin
if (rst==0)
    Q = 0;
else
    begin
        case({J,K})
            2'b00: Q <= Q;
            2'b01: Q <= 1'b0;
            2'b10: Q <= 1'b1;
            2'b01: Q <= ~Q;
        endcase
    end
end
endmodule

```
SIMULATION OUTPUT
------- paste the output here -------

JK Flip-Flop (Non Blocking)
```

`timescale 1ns / 1ps

module jk_ff(J,K,clk,rst,Q);
input J,K,clk,rst;
output reg Q;
always @(posedge clk)
begin
if (rst==0)
    Q = 0;
else
    begin
        case({J,K})
            2'b00: Q <= Q;
            2'b01: Q <= 1'b0;
            2'b10: Q <= 1'b1;
            2'b01: Q <= ~Q;
        endcase
    end
end
endmodule

```
JK Flip-Flop Test bench
```
`timescale 1ns / 1ps

module jk_ff_tb;

reg J, K, clk, rst;
wire Q;

jk_ff uut(J, K, clk, rst, Q);

always #5 clk = ~clk;

initial
begin
    J = 0;
    K = 0;
    clk = 0;
    rst = 1;

    #10 rst = 0;
    #10 J = 0; K = 0;
    #10 J = 0; K = 1;
    #10 J = 1; K = 0;
    #10 J = 1; K = 1;
    #10 $finish;
end

endmodule
```
SIMULATION OUTPUT
------- paste the output here -------

D Flip-Flop (Non Blocking)
```
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
D Flip-Flop Test bench

SIMULATION OUTPUT
------- paste the output here -------

T Flip-Flop (Non Blocking)
```

timescale 1ns / 1ps

module d_ff(D,clk,rst,Q);
input D,clk,rst;
output reg Q;
always @(posedge clk)
begin
if (rst==1)
    Q<=0;
else
    Q<=D;
end
endmodule

```
T Flip-Flop Test bench
```
`timescale 1ns / 1ps

module d_ff_tb;

reg D, rst, clk;
wire Q;

d_ff uut(D, clk, rst, Q);

always #5 clk = ~clk;

initial
begin
    D = 0;
    clk = 0;
    rst = 1;

    #10 rst = 0;
    #10 D = 0;
    #20 D = 1;
    #20 $finish;
end

endmodule
```
SIMULATION OUTPUT
------- paste the output here -------

# RESULT
All flip-flops (SR, D, JK, T) were successfully simulated using Non blocking statements in Verilog HDL. The outputs matched the expected truth table values, demonstrating correct sequential behavior.
