# Exp-5
# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

### Step 2 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.
# Program
# Alu_32bit
```
module alu_32bit_case(y,a,b,f);
input [31:0]a;
input [31:0]b;
input [2:0]f;
output reg [31:0]y;
always@(*)
begin
case(f)
3'b000:y=a&b; //AND Operation
3'b001:y=a|b; //OR Operation
3'b010:y=~(a&b); //NAND Operation
3'b011:y=~(a|b); //NOR Operation
3'b100:y=a^b; //XOR Operation
3'b101:y=~(a^b); //XNOR Operation
3'b110:y=~a; //NOT of a
3'b111:y=~b; //NOT of b
endcase
end
endmodule
```
# run.tcl
```
read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib
read_hdl alu_32bit.v
elaborate
 
syn_generic
report_area
syn_map
report_area
syn_opt
report_area 

report_area > alu_32bit_area.txt
report_power > alu_32bit_power.txt
report_area > alu_32bit_cell.txt
report_gates > alu_32bit_gates.txt

write_hdl > alu_32bit_netlist.v

gui_show
```

# Synthesis RTL Schematic :
![WhatsApp Image 2024-11-18 at 13 15 36_a57ac305](https://github.com/user-attachments/assets/f11819f0-7e9b-496f-b87b-caeed696fec6)
# Area report:
![WhatsApp Image 2024-11-18 at 13 19 06_60853f20](https://github.com/user-attachments/assets/a6d57e27-5988-4bbd-9c7d-4a1176b1f635)
# Power Report:
![WhatsApp Image 2024-11-18 at 13 19 25_47b1a0af](https://github.com/user-attachments/assets/db687649-8d97-45b3-9961-67cb81c439e0)
# Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
