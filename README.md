EXP.NO: 04  

DATE: 26/03/2024

SIMULATION OF IMPLEMENTATION SEQUENTIAL LOGIC CIRCUITS


AIM: To simulate the following circuits using Vivado 2023.2.

1) SR Flip Flop

2) JK Flip Flop

3) T- Flip Flop

4) D-Flip Flop

5) Up-down Counter

6) Mod10 Counter

7) Ripple Carry Counter 

APPARATUS REQUIRED: 
VIVADO 2023.2

PROCEDURE: 

STEP:1 Start the Vivado, Select and Name the New project. 

STEP:2 Select the device family, device, package and speed. 

STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. 

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax. 

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

SR FLIP FLOP:

LOGIC DIAGRAM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/bab44006-70a7-4a65-8bb4-4f16304a28ed)


VERILOG CODE:

module sr(s,r,clk,rst,q);

input s,r,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else 

begin

case ({s,r})

2'b00: q = q;

2'b01: q = 1'b0;

2'b10: q = 1'b1;

2'b11: q = 1'bx;

endcase

end

end

endmodule

OUTPUT WAVEFORM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/a954a3e2-b876-4d37-a152-5f0a391e03e2)


JK FLIP FLOP:

LOGIC DIAGRAM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/b7b36f12-4e47-41db-b9e7-73928dc0fc57)

 
VERILOG CODE:

module jk(j,k,clk,rst,q);

input j,k,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else 

begin

case ({j,k})

2'b00: q = q;

2'b01: q = 1'b0;

2'b10: q = 1'b1;

2'b11: q = ~q;

endcase

end

end

endmodule

OUTPUT WAVEFORM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/ec5e7e59-561c-4cfd-ac0c-95ea8c650aa2)

 

T-FLIP FLOP:
LOGIC DIAGRAM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/d9b43fed-9bc9-45d0-810b-9e66cab17fa7)

 
VERILOG CODE:

module t(t,clk,rst,q);

input t,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else if (t==0)
q=q;
else
q=~q;
end
endmodule

OUTPUT WAVEFORM:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/33d7e0f4-f19d-40ee-8719-536f579bdfe1)

 
D-FLIP FLOP:

LOGIC DIAGRAM:

 ![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/9b4145fb-ed07-4125-b1a8-c607ed0cfd00)


VERILOG CODE:

module d(d,clk,rst,q);

input d,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else

q=d;

end

endmodule

OUTPUT WAVEFORM:

 ![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/f5fa2dc3-e631-4ada-a88f-520afe6ea4a5)


UPDOWN COUNTER:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/12b53cbd-bb4f-4bfe-8fac-23f93b30385d)

 


VERILOG CODE:

module updowncounter(clk,rst,updown,out);

input clk,rst,updown;

output reg [3:0]out;

always @(posedge clk)

begin

if (rst==1)

out=4'b0000;

else if (updown==1)

out=out+1;

else

out=out-1;

end

endmodule


OUTPUT WAVEFORM:
 
![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/d1835c8c-f32a-4638-99c7-8f4200bb18c9)

 
MOD 10 COUNTER:

![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/81f1a7bd-156a-405f-953c-ea5192d8eb72)

 
VERILOG CODE:

module mod10counter(clk,rst,out);

input clk,rst;

output reg [3:0]out;

always @(posedge clk)

begin

if (rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule

OUTPUT WAVEFORM:

 ![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/aa746858-453d-489e-b9f0-bad6ff08dad3)


RIPPLE CARRY COUNTER:

LOGIC DIAGRAM:

 ![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/1c09e2c1-41e1-4847-87b4-a08bb04f6b1a)


VERILOG CODE :

module ripple_carry_counter(q, clk, reset);

output [3:0] q;

input clk, reset;

T_FF tff0(q[0], clk, reset);

T_FF tff1(q[1], q[0], reset);

T_FF tff2(q[2], q[1], reset);

T_FF tff3(q[3], q[2], reset);

endmodule

module T_FF(q, clk, reset);

output q;

input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q); 

endmodule


module D_FF(q, d, clk, reset);

output q;

input d, clk, reset;

reg q;

always @(posedge reset or negedge clk)

if (reset)

q = 1'b0;

else

q = d;

endmodule

OUTPUT WAVEFORM:

 ![image](https://github.com/Karthikeyan8296/VLSI-EXP-4/assets/165583967/5f11551e-bb62-49a9-a0d3-f61b11172e61)



RESULT:
	Thus the simulation of sequential circuits is done and outputs are verified
Successfully.

