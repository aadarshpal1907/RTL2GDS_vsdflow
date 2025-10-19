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

***
### noise margin

<img width="227" height="222" alt="image" src="https://github.com/user-attachments/assets/77ebeec7-1a7f-4b7b-9578-991350993352" />

<img width="1920" height="1080" alt="Screenshot from 2025-10-19 20-33-28" src="https://github.com/user-attachments/assets/28d83b4c-3bd6-4f6b-a6dd-a62b1b378a4a" />

***
### power supply variation
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 20-54-42" src="https://github.com/user-attachments/assets/61e8c9fc-6c23-4dda-afd3-e3099bf60668" />

***

### Device variation 
<img width="1920" height="1080" alt="Screenshot from 2025-10-19 21-01-22" src="https://github.com/user-attachments/assets/76399f7d-0a3a-4e1e-a7ac-efbdb9bb3c33" />
