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

### Gate-Level Simulation (GLS) Note

Gate-Level Simulation (GLS) is performed after synthesis to verify the logical correctness of the synthesized netlist. The waveform obtained from GLS is compared with the functional simulation waveform (pre-synthesis). If both outputs match, it confirms that the synthesis process has not introduced any functional errors.

Hence, GLS waveform outputs = Functional simulation outputs, validating that the design’s behavior remains consistent before and after synthesis.


</details>




