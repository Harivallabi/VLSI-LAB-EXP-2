SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

DATE:

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

VERILOG CODE:
```

module encoder(i,o);
input [7:0]i;
output [2:0]o;
or g1(o[0],i[1],i[3],i[5],i[7]);
or g2(o[1],i[2],i[3],i[6],i[7]);
or g3(o[2],i[4],i[5],i[6],i[7]);
endmodule
```

OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/159146834/fded71f0-50ba-40ec-811d-2612b3fc9139)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)

VERILOG CODE:

```
module decoder(a,y);
MULTIPLEXERinput [2:0]a;
output [7:0]y;
wire w0,w1,w2;
not g1(w0,a[0]);
not g2(w1,a[1]);
not g3(w2,a[2]);
and g4(y[0],w0,w1,w2);
and g5(y[1],w2,w1,a[0]);
and g6(y[2],w2,a[1],w0);
and g7(y[3],w2,a[1],a[0]);
and g8(y[4],a[2],w1,w0);
and g9(y[5],a[2],w1,a[0]);
and g10(y[6],a[2],a[1],w0);
and g11(y[7],a[2],a[1],a[0]);
endmodule
```

OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/159146834/c3a937c4-d0e5-4502-ba93-b0a1d510a6ad)



MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)

VERILOG CODE:
```
module mux(d,s,y);
input[7:0]d;
input[2:0]s;
output y;
wire w1,w2,w3,w4,w5,w6,w7,w8,w9,w10,w11;
not g1 (w1,s[2]);
not g2(w2,s[1]);
not g3(w3,s[0]);
and g4(w4,w1,w2,w3,d[0]);
and g5(w5,w1,w2,s[0],d[1]);
and g6(w6,w1,w3,s[1],d[2]);
and g7(w7,w1,s[1],s[0],d[3]);
and g8(w8,w2,w3,s[2],d[4]);
and g9(w9,w2,s[2],s[0],d[5]);
and g10(w10,w3,s[1],s[2],d[6]);
and g11(w11,s[0],s[1],s[2],d[7]);
or g12(y,w4,w5,w6,w7,w8,w9,w10,w11);
endmodule
```
OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/159146834/08ca7380-9a7e-4081-83a2-a76c6b22788e)



DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)

VERILOG CODE:
```
module demux8x1(d,s,y);
input d;
input [2:0]s;
output [7:0]y;
wire w1,w2,w3;
not g1(w1,s[0]);
not g2(w2,s[1]);
not g3(w3,s[2]);
and g4(y[0],d,w1,w2,w3);
and g5(y[1],d,w1,s[0],w3);
and g6(y[2],d,w3,s[1],w1);
and g7(y[3],d,s[0],s[1],w3);
and g8(y[4],d,s[2],w1,w2);
and g9(y[5],d,s[2],s[0],w2);
and g10(y[6],d,w1,s[1],s[2]);
and g11(y[7],d,s[2],s[1],s[0]);
endmodule
```

OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/159146834/8a635270-661b-4f73-8580-96511df8dbe4)



MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)

VERILOG CODE:
```
module magnitude(a,b,greater,lesser,equal);
input[2:0]a,b;
output reg greater,lesser,equal;
always @(*)
begin
if (a>b)
begin
greater=1'b1;
lesser=1'b0;
equal=1'b0;
end
else if(a<b)
begin
greater=1'b0;
lesser=1'b1;
equal=1'b0;
end
else
begin
greater=1'b0;
lesser=1'b0;
equal=1'b1;
end
end
endmodule
```

OUTPUT:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/159146834/11c7ef7a-4aac-4542-959f-cbfbe988bfe3)


  
PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.


RESULT

Thus ,the given encoder, decoder, multiplexer, demultiplexer, magnitude comparator are simulated and synthesis are executed successfully.


