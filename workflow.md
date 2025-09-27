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
<img width="1920" height="1080" alt="Screenshot from 2025-09-27 21-06-36" src="https://github.com/user-attachments/assets/f2415e3b-c4bc-40b2-b9ec-2eac7802374f" />
<b>iverilog & gtkwave implimentation </b>
</p>

***

    
</details>





