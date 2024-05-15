SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM:
To simulate and synthesis SR, JK, T, D - FLIPFLOPS, COUNTERS design using vivado.

# APPARATUS REQUIRED:
vivado 2023.2

# PROCEDURE
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# LOGIC DIAGRAM
# SR FLIPFLOP
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/75511305-e7c5-44f9-bf9f-138d9953dc57)


# JK FLIPFLOP
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/4ed85ad9-e265-4d79-a4f3-250064c42279)


# T FLIPFLOP
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/2db4955d-95ad-4188-99b6-d292ab98827a)


# D FLIPFLOP
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/d1aa22f4-53db-4242-a3cb-c3b958901c1b)


# COUNTER
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/3ee72b3a-f547-4483-ac95-59215a7b7404)


# VERILOG CODE
# SR FLIPFLOP:
module srff(clk,j,k,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule

# JK FLIPFLOP:
module jkff(clk,j,k,rst,q );

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule

# T FLIPFLOP:
module tff(clk,reset,t,q);

input clk,reset,t;

output reg q;

always @(posedge clk)

begin

if(reset==1)

q=0;

else

begin

if(t==0)

q=q;

else

q=~q;

end

end

endmodule

# D FLIPFLOP:
module dff(clk,d,rst,q );

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule

# UPDOWN COUNTER:
module updown(clk,rst,up_down,count);

input clk,rst,up_down;

output reg[3:0]count;

always@(posedge clk)

begin

if(rst==1)

count <= 4'b0000;

else if (up_down == 1'b1)

count <= count + 1'b1;

else

count <= count-1'b1;

end

endmodule

# MOD 10 COUNTER:
module mod(clk,rst,count);

input clk,rst;

output reg[3:0]count;

always @(posedge clk)

begin

if(rst==1 | count==4'b1001)

count <= 4'b0000;

else

count <= count +1;

end

endmodule

# RIPPLE COUNTER:
module ripplecounter(clk,rst,q);

input clk,rst;

output [3:0]q;

tff tff1(q[0],clk,rst);

tff tff2(q[1],q[0],rst);

tff tff3(q[2],q[1],rst);

tff tff4(q[3],q[2],rst);

endmodule

module tff(q,clk,rst);

input clk,rst;

output q;

wire d;

dff df1(q,d,clk,rst);

not n1(d,q);

endmodule

module dff(q,d,clk,rst);

input d,clk,rst;

output q;

reg q;

always@(posedge clk or posedge rst)

begin

if(rst)

q=1'b10;

else

q=d;

end

endmodule

# OUTPUT WAVEFORM
# SR flipflop:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/5a83f8ff-2d6b-49eb-8d7c-eb20c03f7b33)

# JK flipflop:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/1c03b5de-0175-4b20-b754-01831e3f3f71)

# T flipflop:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/3f2e3264-ba5f-45de-a5dd-3bf79ef1655e)

# D flipflop:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/adb4db94-1d88-429e-89fe-fcec58f0e8b9)

# Updown counter:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/97c58c11-9c32-4731-ad39-06a2bb938754)

# Mod 10 counter:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/3b1272d3-ca6f-49c4-af92-b419e0c48ce9)

# Ripple counter:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-4/assets/162343019/6c663575-4083-4d2e-952f-1cde87232fe0)


# RESULT
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
