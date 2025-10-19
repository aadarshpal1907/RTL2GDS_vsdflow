# India RISC-V Chip Tapeout Programm 

# RTL2GDS_vsdflow
<details>
<summary><strong>Week0 - Tools Installation</strong></summary>

---
    
### 1. Yosys Installation
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 13-46-18" src="https://github.com/user-attachments/assets/7011b588-b732-4acb-8e85-19fcfec18e85" />
<b>✅ Yosys Successfully Installed</b>
</p>

---
***

### 2. Iverilog

```
$ sudo apt-get install iverilog
```
<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 14-08-04" src="https://github.com/user-attachments/assets/c8f656ad-aefc-405a-989c-8e554f7795ff" />
<b> ✅ Iverilog Successfully Installed</b>
</p>

***
---

### 3. GTKWave
```
$ sudo apt update
$ sudo apt install gtkwave
```
<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 14-14-41" src="https://github.com/user-attachments/assets/4b9eab4c-2880-442a-b614-ce829813c7ef" />
<b> ✅ GTKWave Successfully Installed</b>
</p>

---
***

### 4. Ngspice 

```
$ sudo apt update
$ sudo apt install ngspice
```
<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 17-23-36" src="https://github.com/user-attachments/assets/199fee54-344e-4421-a951-2269e95398f0" />
<b> ✅ Ngspice Successfully Installed </b>
</p>

---
***

### 5. Magic vlsi
```
# Install required dependencies
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev

# Clone Magic repository
git clone https://github.com/RTimothyEdwards/magic
cd magic

# Configure build
./configure

# Build Magic
make

# Install system-wide
sudo make install
```
<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-20 17-29-23" src="https://github.com/user-attachments/assets/d9cf5be0-dc8e-4a48-9df4-fbe4efc29a87" />
<b> ✅ Magic VLSI Successfully Installed </b>
</p>

******

</details>

<details>
<summary><strong> Week1 </strong></summary>
    
### RTL design and synthesis 

<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-27 20-45-52" src="https://github.com/user-attachments/assets/e6532707-b67f-4eb0-beea-456eca1dcdd1" />
<b> Netlist for Yosys </b>
</p>

***

<p align="center">
<img width="1920" height="1080" alt="Screenshot from 2025-09-27 21-06-36" src="https://github.com/user-attachments/assets/f2415e3b-c4bc-40b2-b9ec-2eac7802374f" />
<b>iverilog & gtkwave implimentation  
  example 2x1 mux o/p wave  </b>
</p>

***


</details>

<details> <summary><strong> Week2 </strong></summary>

## Overview
The **VSDBabySoC** is a simple SoC (System-on-Chip) design incorporating a RISC-V processor (`rvmyth`), a PLL (Phase-Locked Loop) module (`pll`), and a DAC (Digital-to-Analog Converter) module (`dac`). This project demonstrates integration of these IP cores and aims to simulate and verify the design behavior using pre-synthesis and post-synthesis simulations.

## Project Structure
- `src/include/` - Contains header files (`*.vh`) with necessary macros or parameter definitions.
- `src/module/` - Contains Verilog files for each module in the SoC design.
- `output/` - Directory where compiled outputs and simulation files will be generated.

## Requirements
Ensure you have **Icarus Verilog** installed for compilation and **GTKWave** for viewing waveform files. This project assumes a Unix-like environment (macOS/Linux).

## Step-by-Step Guide

### 1. Setup and Prepare Project Directory
Clone or set up the directory structure as follows:
```txt
VSDBabySoC/
├── src/
│   ├── include/
│   │   ├── sandpiper.vh
│   │   └── other header files...
│   ├── module/
│   │   ├── vsdbabysoc.v      # Top-level module integrating all components
│   │   ├── rvmyth.v          # RISC-V core module
│   │   ├── avsdpll.v         # PLL module
│   │   ├── avsddac.v         # DAC module
│   │   └── testbench.v       # Testbench for simulation
└── output/
└── compiled_tlv/         # Holds compiled intermediate files if needed
```

### Module Descriptions

<details>
   <summary><strong>2.1 vsdbabysoc.v (Top-Level SoC Module)</strong></summary>
      This is the top-level module that integrates the rvmyth, pll, and dac modules.<br>
   [VSDBabySoC](https://github.com/manili/VSDBabySoC.git)
      
   
      - Inputs:
         - reset: Resets the core processor.
         - VCO_IN, ENb_CP, ENb_VCO, REF: PLL control signals.
         - VREFH: DAC reference voltage.
      - Outputs:
         - OUT: Analog output from DAC.
         - Connections:
         - RV_TO_DAC - A 10-bit bus that connects the RISC-V core output to the DAC input.
         - CLK - The clock signal generated by the PLL.
      
</details>

   <details>
     <summary><strong>2.2 rvmyth.v (RISC-V Core)</strong></summary>
     The rvmyth module is a simple RISC-V based processor. It outputs a 10-bit digital signal (OUT) to be converted by the DAC.<br>
     [rvmyth](https://github.com/kunalg123/rvmyth/)
      
      Inputs:
         - CLK: Clock signal generated by the PLL.
         - reset: Initializes or resets the processor.
      Outputs:
         - OUT: A 10-bit digital signal representing processed data to be sent to the DAC.
         
   </details>

   <details>
     <summary><strong>2.3 avsdpll.v (PLL Module)</strong></summary>
     The pll module is a phase-locked loop that generates a stable clock (CLK) for the RISC-V core.<br>
     [Introduction](https://github.com/ireneann713/PLL.git)
     [avsdpll](https://github.com/lakshmi-sathi/avsdpll_1v8.git)
      
      Inputs:
         - VCO_IN, ENb_CP, ENb_VCO, REF: Control and reference signals for PLL operation.
      Output:
         - CLK: A stable clock signal for synchronizing the core and other modules.
         
         
   </details>

   <details>
     <summary><strong>2.4 avsddac.v (DAC Module)</strong></summary>
     The dac module converts the 10-bit digital signal from the rvmyth core to an analog output.<br>
     [avsddac](https://github.com/vsdip/rvmyth_avsddac_interface.git)
      
      Inputs:
         - D: A 10-bit digital input from the processor.
         - VREFH: Reference voltage for the DAC.
      Output:
         - OUT: Analog output signal.

         
   </details>

### Testbench
The testbench.v file is a test module to verify the functionality of vsdbabysoc. It includes signal initialization, clock generation, and waveform dumping for both pre-synthesis and post-synthesis simulations.
Waveform Output:
   - pre_synth_sim.vcd or post_synth_sim.vcd files generated based on simulation conditions.

### Simulation Steps
#### Pre-Synthesis Simulation
Run the following command to perform a pre-synthesis simulation:

```tcl
iverilog -o output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v src/module/vsdbabysoc.v
cd output/pre_synth_sim
./pre_synth_sim.out
```
<img width="1920" height="1080" alt="Screenshot from 2025-10-10 17-07-07" src="https://github.com/user-attachments/assets/3b720326-6576-44c8-a089-ed015f61cf4a" />


**Explanation:**
   - -DPRE_SYNTH_SIM: Defines the PRE_SYNTH_SIM macro for conditional compilation in the testbench.
   - The resulting pre_synth_sim.vcd file can be viewed in GTKWave.

#### Viewing Waveform in GTKWave
After running the simulation, open the VCD file in GTKWave:
`gtkwave output/pre_synth_sim/pre_synth_sim.vcd`

#### Post-Synthesis Simulation
To run a post-synthesis simulation, use:
```tcl
iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v output/synthesized/vsdbabysoc.synth.v
cd output/post_synth_sim
./post_synth_sim.out
```

### Trouble shooting tips

   - Module Redefinition: If you encounter redefinition errors, ensure modules are included only once, either in the testbench or in the command line.
   - Path Issues: Verify paths specified with -I are correct. Use full paths if relative paths cause errors.

## Yosys final report
<img width="1920" height="1080" alt="Screenshot from 2025-10-10 17-00-30" src="https://github.com/user-attachments/assets/885545e5-e6f2-4e11-8545-b1a1c9c70733" />


  
</details>

<details> <summary><strong> Week3 </strong></summary>

# GLS OF BABYSOC
## POST-SYNTHESIS SIMULATION

### Purpose of GLS:
Gate-Level Simulation is used to verify the functionality of a design after the synthesis process. Unlike behavioral or RTL (Register Transfer Level) simulations, which are performed at a higher level of abstraction, GLS works on the netlist generated post-synthesis. This netlist includes the actual gates and connections used to implement the design.

### Key Aspects of GLS for BabySoC:
1. **Verification with Timing Information:**
   - GLS is performed using Standard Delay Format (SDF) files to ensure timing correctness.
   - This checks if the SoC behaves as expected under real-world timing constraints.

2. **Design Validation Post-Synthesis:**
   - Confirms that the design's logical behavior remains correct after mapping it to the gate-level representation.
   - Ensures that the design is free from issues like metastability or glitches.

3. **Simulation Tools:**
   - Tools like Icarus Verilog or a similar simulator can be used for compiling and running the gate-level netlist.
   - Waveforms are typically analyzed using GTKWave.

4. **Importance for BabySoC:**
   - BabySoC consists of multiple modules like the RISC-V processor, PLL, and DAC. GLS ensures that these modules interact correctly and meet the timing requirements in the synthesized design.


Here is the step-by-step execution plan for running the  commands manually:
---
### **Step 1: Load the Top-Level Design and Supporting Modules**
```bash
yosys
```

Inside the Yosys shell, run:
```yosys
read_verilog /home/aadarsh/VSDBabySoC/src/module/vsdbabysoc.v
read_verilog -I /home/aadarsh/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/rvmyth.v
read_verilog -I /home/aadarsh/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/clk_gate.v

```
<img width="1920" height="1080" alt="Screenshot from 2025-10-13 20-05-36" src="https://github.com/user-attachments/assets/bf116938-1ca6-4b98-975f-2def17c85dfd" />

### **Step 2: Load the Liberty Files for Synthesis**
Inside the same Yosys shell, run:
```yosys
read_liberty -lib /home/aadarsh/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -lib /home/aadarsh/VSDBabySoC/src/lib/avsddac.lib
read_liberty -lib /home/aadarsh/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="1215" height="377" alt="Screenshot from 2025-10-13 20-07-40" src="https://github.com/user-attachments/assets/97ea1cd7-617a-423f-ac61-033710300cc0" />

---

### **Step 3: Run Synthesis Targeting `vsdbabysoc`**
```yosys
synth -top vsdbabysoc
```
<img width="1920" height="1080" alt="Screenshot from 2025-10-13 20-09-43" src="https://github.com/user-attachments/assets/b237be12-bb00-46f9-8c2c-1802e2c03ce0" />
<img width="1914" height="510" alt="Screenshot from 2025-10-13 20-10-12" src="https://github.com/user-attachments/assets/4d327783-8765-42be-8ca9-4c709d95ace6" />

---

### **Step 4: Map D Flip-Flops to Standard Cells**
```yosys
dfflibmap -liberty /home/aadarsh/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<img width="1138" height="647" alt="Screenshot from 2025-10-13 20-12-05" src="https://github.com/user-attachments/assets/b1527035-f71b-4e00-9e2f-55182aede59d" /> 

---

### **Step 5: Perform Optimization and Technology Mapping**
```yosys
opt
```
<img width="1920" height="1080" alt="Screenshot from 2025-10-13 20-13-19" src="https://github.com/user-attachments/assets/2f095e01-68f2-426b-b29e-b76ed50dc53d" />

---



### **Step 6: Check Statistics**
```yosys
stat
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM (3)](https://github.com/user-attachments/assets/292c9093-9a6d-417e-b094-0b8a6e27e7c3)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (2)](https://github.com/user-attachments/assets/ce8ad45b-92ae-4cc8-a4dd-0f52028e078e)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (1)](https://github.com/user-attachments/assets/e1741767-2b83-4d88-909e-e5d4c73411f4)

---

### **Step 7: Write the Synthesized Netlist** 
```yosys
write_verilog -noattr /home/aadarsh/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM](https://github.com/user-attachments/assets/1e0444b4-ad66-4798-b7f7-7bc1e13cf88a)

---

</details>

<details> <summary><strong> Week4 </strong></summary> 

***

<details>
    
In MOSFET device characterization, multiple experiments are conducted to understand its electrical behavior under different operating conditions. Each experiment provides insight into specific physical parameters and performance characteristics that are crucial for circuit design.

***

1️⃣ Id vs Vds (Output Characteristics)

This experiment measures the drain current (Id) as a function of the drain-to-source voltage (Vds) for different gate-to-source voltages (Vgs).
✅ Purpose:

To analyze the MOSFET’s behavior in linear (ohmic) and saturation regions.

To determine the transition between regions.

To calculate parameters like output resistance (ro) and channel modulation (λ).

***

2️⃣ Id vs Vgs (Transfer Characteristics)

This experiment plots drain current (Id) versus gate-to-source voltage (Vgs) at a fixed Vds.
✅ Purpose:

To determine threshold voltage (Vth).

To understand the device’s transconductance (gm) and gate control over the channel.

To analyze how Id increases with gate bias in saturation.

***


3️⃣ VTC (Voltage Transfer Characteristics) of CMOS Inverter

In this test, the output voltage (Vout) of a CMOS inverter is measured against varying input voltage (Vin).
✅ Purpose:

To analyze the switching behavior of the inverter.

To find noise margins (NMH, NML).

To determine the inverter threshold voltage (Vm).

To evaluate the logic gain and switching region sharpness.

***

4️⃣ Transconductance Evaluation (gm vs Vgs or gm vs Id)

This involves extracting gm as Vgs or Id is varied.
✅ Purpose:

To evaluate how efficiently the MOSFET converts gate voltage variations into drain current.

To optimize the device for analog circuit applications like amplifiers.

***

5️⃣ Subthreshold Region (Id vs Vgs in Log Scale)

This is performed at low Vgs values with logarithmic Id scaling.
✅ Purpose:

To analyze MOSFET behavior in weak inversion.

To extract subthreshold slope (SS) and understand leakage currents, important for low-power design.

*** 

6️⃣ Capacitance Measurements (Cgs, Cgd vs Vgs)

Capacitances are measured as Vgs is varied.
✅ Purpose:

To evaluate charging/discharging time in digital circuits.

To analyze delay, speed, and AC performance.

</details>



<img width="1920" height="1080" alt="Screenshot from 2025-10-19 00-17-36" src="https://github.com/user-attachments/assets/c590c399-7d27-4088-b031-ed50c414c94c" />

***

<img width="1920" height="1080" alt="Screenshot from 2025-10-19 00-29-07" src="https://github.com/user-attachments/assets/6347dedf-8e8c-49b0-918d-a9768ba83b8b" />

***

<img width="1920" height="1080" alt="Screenshot from 2025-10-19 00-41-26" src="https://github.com/user-attachments/assets/6750f9e1-c0d2-44e3-bce8-368ca98da4dd" />
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 00-48-26" src="https://github.com/user-attachments/assets/bcbf885a-2985-44ba-b049-04229116a785" />

***
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 00-50-36" src="https://github.com/user-attachments/assets/d7f9784c-7033-4cfe-878c-3090404991f0" />


### noise margin

<img width="227" height="222" alt="image" src="https://github.com/user-attachments/assets/77ebeec7-1a7f-4b7b-9578-991350993352" />

<img width="1920" height="1080" alt="Screenshot from 2025-10-19 20-33-28" src="https://github.com/user-attachments/assets/28d83b4c-3bd6-4f6b-a6dd-a62b1b378a4a" />

***
### power supply variation
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 20-54-42" src="https://github.com/user-attachments/assets/61e8c9fc-6c23-4dda-afd3-e3099bf60668" />

***

### Device variation 
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 21-01-22" src="https://github.com/user-attachments/assets/76399f7d-0a3a-4e1e-a7ac-efbdb9bb3c33" />

</details>






