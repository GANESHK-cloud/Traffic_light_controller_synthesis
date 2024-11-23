#     #     Exp-No:6 - Traffic light Controller-Synthesize the Gate Level Netlist and tabulate Area ,Power and timing reports.(Using Genus in Cadence)
##    Aim:

  Synthesize Traffic Light Controller design using Constraints and analyse area and Power reports.

##   Tool Required:

  Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

  Synthesis: Genus

##  Step 1: Getting Started

  Synthesis requires three files as follows,

    ◦ Liberty Files (.lib)

    ◦ Verilog/VHDL Files (.v or .vhdl or .vhd)


##  Step 2 : Creating an SDC File

  • In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

  • The SDC File must contain the following commands;

    create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

    set_clock_transition -rise 0.1 [get_clocks "clk"]

    set_clock_transition -fall 0.1 [get_clocks "clk"]

    set_clock_uncertainty 0.01 [get_ports "clk"]

    set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

    set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

    i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

    ii, iii → Sets Clock Rise and Fall time to 100ps.

    iv → Sets Clock Uncertainty to 10ps.

    v, vi → Sets the maximum limit for I/O port delay to 1ps.


##  Step 3 : Performing Synthesis

  The Liberty files are present in the library path,

    • The Available technology nodes are 180nm ,90nm and 45nm.

    • In the terminal, initialise the tools with the following commands if a new terminal is being used.

    ◦ csh

    ◦ source /cadence/install/cshrc

    • The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

    • Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.


##  Synthesis RTL Schematic :


![2](https://github.com/user-attachments/assets/c2b6c4ab-6f1d-483f-baae-e1d37c23638f)



##  Area report:


![Screenshot 2024-11-21 150834](https://github.com/user-attachments/assets/d53dc8b4-0058-4f01-8456-f6aef0c60ab9)








##  Power Report:

![Screenshot 2024-11-23 074758](https://github.com/user-attachments/assets/3555a8df-1c98-4888-94a1-308fc398bc20)



##  Timing Report:

![Screenshot 2024-11-23 074413](https://github.com/user-attachments/assets/f35c4365-e236-45b1-9d92-1e87a8884d0a)



##  Result:

  The generic netlist of Traffic Light Controller has been created, and area, power and timing reports have been tabulated and generated using Genus.
