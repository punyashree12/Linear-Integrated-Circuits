**EXP NO -6** 

##                                                              **Current Mirrorr**
##

##  i . Aim:

![Image](https://github.com/user-attachments/assets/e676a625-f94d-4f75-b241-971e4e6e735f)



## Components used:


1. NMOS/PMOS Transistor
2. Voltage Source
3. Current source
4. Ground
5. CONNECTING wires


 
## Theory:

Part 1: Current Mirror as an Active Load

The current mirror circuit is one of the widely used designs in IC design to provide a stable biasing current for multiple transistors at once. Ideally, we would bias each transistor using a current source, to ensure stability, but since this is not feasible, we use the current mirror design and set the corresponding (W/L) ratio of each transistor according to how much ID we need to flow in that transistor.
![Image](https://github.com/user-attachments/assets/266b7dbb-df9b-464b-97ee-d413a421859a)
As we can see, using a single IRef, we can bias the transistor MRef, using which we can set the current flowing through M1, making it act as an active load, and use it to as our ID value in further transistors.




## Procedure:
 •	Open LTspice  and create a new schematic by selecting File > New Schematic.

•	Select the Components required to design a Common Source Amplifier  such as NMOS,voltage source, wire, and ground. 

•	Connect the components as shown in the above fig.1

•	Set Component Values by Right-clicking on each component to set their values 

•	Go to edit option select spice directive and attach tsmc018.lib file

•	To run the simulation click on  run button
##

•	To get DC Operating Point Analysis
1.	Click on Simulate > confiure analysis
2.	Select DC op pnt and click OK
3.	Place the .op directive on your schematic and stop time as 5m
4.	Run the Simulation
5.	Click the Run button (the running man icon)
6.	The DC operating point voltages and currents will be displayed in a table
##

•	To get AC operating Point analysis
1.	Right-click on the voltage source and select sine function set AC Amplitude to 50mv, frequency to 1KHz, DC offset to 0.9v
2.	Click on Simulate > configure analysis
3.	Select AC Analysis.
4.	Enter the type of sweep decade, number of points 20,  start frequency 0.1 Hz, and stop frequency 1T Hz.
5.	Click OK and place the .ac directive on your schematic.
6.	Run the Simulation
7.	Click the Run button
8.	The AC analysis results will be displayed to get the waveform click on input/output voltage.
##

•	To get Transient Analysis
1.	Click on Simulate > configure analysis
2.	Select Transient and enter the stop time (5milliseconds).
3.	Click OK and place the .tran directive on your schematic.
4.	Run the Simulation:
5.	Click the Run button.
6.	The transient analysis results will be displayed  to get waveform  click on output /input volatges.

## calculation:

we can see Itotal = P/VDD = 1 mW /1.8 V = 0.555 mA

Next, we know that Itotal = Iref + IX, where IX = ID. Since the (W/L) ratio specified to us is 1:1, IX + Iref = (Itotal/2) = 0.2777 mA. In the next question, where (W/L) ratio is 1:2, the value of IX = (Itotal/3).

Next, we need to calculate how much input voltage we will need to give the N-channel MOSFET, for it to work as an amplifier (with gain ≥ 10 V/V).

We know that AV = -gmRout = -gm(ro1||ro2), where ro1, ro2 are the dynamic output resistances of the NMOS, PMOS respectively, due to channel length modulation.

Since we know that ro1 = 1/λ1ID1, ro2 = 1/λ2ID2, where ID1 = ID2 = ID.

ro1 || ro2 = 1/ID (λ1 + λ2) = 1/ (0.277 x 10-3 x (1.382 + 1.329)) = 1331.65 Ω = 1.331 kΩ

Note that values for λ1, λ2 have been obtained from the TSMC 180 nm process technology .lib file, where the parameter for these values is PCLM (Channel Length Modulation Parameter).

We can also write gm as 2ID/VOV. Finally, substituting all of this back into our original equation, we get,

AV = (2ID/VOV). Rout, from which we can calculate VOV as 0.0737V.

VGS = VOV + Vt = 0.0737 + 0.496 = 0.569V

Therefore, our input voltage for the NMOS is 0.569 V.

## Circuit Diagram


![Image](https://github.com/user-attachments/assets/ec2151bc-207c-4274-8590-bd2b55cb9e2c)

For the P-channel MOSFETs, M1, M2: - W = 10 µm, L = 180 nm

For the N-channel MOSFETs, M3: - W = 31.23 µm, L = 180 nm

## Results:
   
  **1. DC Analysis:**



**Simulation:**


 
![Image](https://github.com/user-attachments/assets/2124627b-08b2-4005-a3a1-26cbe95d6614)

From here, we can see that the simulation is closely matching with our calculated values, since the current flowing through the NMOS (M3), PMOS (M1, M2) are nearly identical. From this, we can verify whether the circuit is following our power requirements, which is a key part in the design of any IC or chip.

P = Itotal * VDD = 0.55401 mA * 1.8 V = 0.9972 mW, which is within our power budget.


##



**2. TRANSIENT ANALYSIS :**

Next, we move on to transient analysis, where we can verify whether our V/V gain requirement is satisfied or not. To do this, we will configure our input voltage, Vin and convert it into a sinusoidal input with DC offset of 0.569V.

   
SIMULATION ;

**CIRCUIT DIAGRAM**

![Image](https://github.com/user-attachments/assets/cfb4e771-c3f1-4b11-a726-49a39abb3b6d)
  
![Image](https://github.com/user-attachments/assets/25d519bb-6c35-4d1c-8b95-1d2a646a9b95)

From here, we can see that the peak output voltage is 1.2381 V, for an input peak voltage of 10 mV. Now, we can calculate our gain, and verify our whether our gain requirement is satisfied or not.

AV = Vout/Vin = (0.96 – 1.2381)/(10 mV) = -27.81 V/V = 28.884 dB

This definitely satisfies our gain requirement, since we needed a V/V gain of ≥ 10 V/V.
   


**3. AC Analysis:**



SIMULATION;

![Image](https://github.com/user-attachments/assets/a2dc6a56-4ee7-447c-953b-8bd073272c14)


From here, we can see our 3 dB BW = 629.997 MHz – 0 = 629.997 MHz

The midband gain we are obtaining from our frequency response, i.e., 29.298 dB is also similar to the value we calculated, 28.884 dB.


##

**Circuit 2**: Ratio of 1:2 using L = 180 nm

For ratio of 1:2, then Iref = Itotal/3 = 0.183 mA


## Results:
   
  **1. DC Analysis:**


 








**CIRCUIT DIAGRAM**
![Image](https://github.com/user-attachments/assets/36341e18-89e7-49bc-8dcf-a9ee00b479c5)

Simulation:

![Image](https://github.com/user-attachments/assets/ef1fd5cb-432a-4c65-ad36-38d31dd0d55b)
##

**2. TRANSIENT ANALYSIS :**
![Image](https://github.com/user-attachments/assets/b88b0cd1-9409-433e-afa9-9e1a827e2815)

Gain (V/V) = (1.26006-0.96)/ (-10 mV) = 30.006 V/V = 29.544 dB for an input voltage of 10 mV peak voltage, frequency of 1 kHz, sine wave. Let us perform the frequency response to verify this.






      


**3. AC Analysis:**

![Image](https://github.com/user-attachments/assets/3acb08f2-d3f2-45df-b60a-43277c4844ad)

From here, we can see that our midband gain is around 29.325 dB, which is a close match with our calculated value of 29.544 dB, which gives a V/V gain of around 29.25 V/V, not that far off from our calculated gain of 30.006 V/V.

ii. Analysis using L = 500 nm

1:1 using L = 500 nm

![Image](https://github.com/user-attachments/assets/d02fcd10-2213-457d-aeb4-51c4b3f64438)

For CMOSN (M3), W = 65.19 µm, L = 500 nm

For CMOSP (M1, M2), W = 10 µm, L = 500 nm





 



   
  **1. DC Analysis:**






**Simulation:**

![Image](https://github.com/user-attachments/assets/d74acce0-91f8-48c2-87d6-bd79c1e580c2)


**2. TRANSIENT ANALYSIS :**

   
SIMULATION ;

![Image](https://github.com/user-attachments/assets/c08a1671-5737-4771-a763-3009ccb09607)






**3. AC Analysis:**
![Image](https://github.com/user-attachments/assets/a933724e-1040-44be-9ecb-351167d71c3f)

Gain = 37.87023 dB, 3 dB BW = 122.329 MHz

ii. Circuit 2: Ratio of 1:2 using L = 500 nm

For CMOSN (M3), W = 85.243 µm, L = 500 nm

For CMOSP (M1), W = 10 µm, L = 500 nm

For CMOSP (M2), W = 20 µm, L = 500 nm




**DC Analysis** 




![Image](https://github.com/user-attachments/assets/461ecaa9-e3c5-4b20-8219-c84ddd14d1b5)
**Transient Analysis**

![Image](https://github.com/user-attachments/assets/f8e723d8-2f42-4a3b-a358-e383ae096daf)

Gain (V/V) = -62.063 V/V = 35.855 dB

**AC Analysis**
![Image](https://github.com/user-attachments/assets/a55767d5-dfc6-4795-9906-c596e12ad5cd)


    3 dB BW = 93.0732 MHz, Gain (dB) = 38.015 dB


**ii.** Analysis using L = 1 µm

Ratio of 1:1
For CMOSN (M3), W = 93.35 µm, L = 1 µm

For CMOSP (M1), W = 10 µm, L = 1 µm

For CMOSP (M2), W = 10 µm, L = 1 µm


![Image](https://github.com/user-attachments/assets/72c7e36d-a015-4acf-b172-b068f0ccbcdc)

**DC Analysis** 



![Image](https://github.com/user-attachments/assets/009c4cbf-226c-4616-8b55-cee6cfc36f2f)
**Transient Analysis**
![Image](https://github.com/user-attachments/assets/6250ac05-3b87-4078-a973-31b4de6c5352)
Gain (V/V) = -60 V/V = 35.563 dB

**AC Analysis**

![Image](https://github.com/user-attachments/assets/ec83b222-5f20-4637-ba1e-2e7d6e61fa7d)


     3 dB BW = 98.90171 MHz, Gain (dB) = 35.481 dB


ii. Analysis using L = 1 µm

Ratio of 1:2
For CMOSN (M3), W = 121.51 µm, L = 1 µm

For CMOSP (M1), W = 20 µm, L = 1 µm

For CMOSP (M2), W = 10 µm, L = 1 µm

![Image](https://github.com/user-attachments/assets/d47a98b0-c9f5-459e-abfd-b04bb3b21d17)


**DC Analysis** 


![Image](https://github.com/user-attachments/assets/36ac08fa-7a59-411e-ae7c-e0b8501a4503)

**Transient Analysis**

![Image](https://github.com/user-attachments/assets/5e2e6585-a357-4b1d-a43b-4f0fdb3b7f32)


**AC Analysis**
![Image](https://github.com/user-attachments/assets/9bed2220-2883-4cce-bc5b-37911eb5958b)

      3 dB BW = 57.2524 MHz, Gain (dB) = 38.69341 dB



Table of Comparisons


![Image](https://github.com/user-attachments/assets/40f752c8-01a6-4543-86d3-f44ab0a44b3d)




Part 2: Differential Amplifier

Now that we have understood the basics of the current mirror, we will move onto using it to design our differential amplifier, using the same parameters that we designed for the differential amplifier simulation.


![Image](https://github.com/user-attachments/assets/051f41e4-4993-4cf7-ad5d-6920f64d0cad)



For the N-channel MOSFETs (CMOSN), the W/L ratios are as follows: -

M1, W = 108.5 µm, L = 180 nm

M2, W = 108.5 µm, L = 180 nm

M3, W = 22.42 µm, L = 180 nm

M6, W = 10 µm, L = 180 nm

The reason for the (W/L) ratio of M3 being more than double that of M6 is because the current flowing through M3 should be double than the current of M6, i.e., IM3 = 1.222 mA, while IM6 = 0.611 mA.

This is also the same reason why M4, M5 have the same (W/L) ratios, so that equal amounts of current flows through both transistors.

For the P-channel MOSFETs (CMOSP), the W/L ratios are as follows: -

M4, W = 52 µm, L = 180 nm

M5, W = 52 µm, L = 180 nm

M6, W = 10 µm, L = 180 nm


**DC Analysis** 


![Image](https://github.com/user-attachments/assets/afe11788-3c12-44e1-9556-90c18d5bb4bf)

As we can see, for our (W/L) ratios, the values we obtain from the DC analysis closely match the ones we require.


Transient Analysis

![Image](https://github.com/user-attachments/assets/29a2b47d-d538-4e72-bd24-46d0e78416f8)











We have supplied a differential input of 10 mV peak voltage, 1 kHz frequency, sine wave. The input is differential, i.e., only to the gate of M1, since the output of a differential amplifier is the difference in drain voltages of M1, M2. Since the output is a difference, if we supply common input, the amplifier will reject the signal and provides very little to no gain (ideally).

Av = (1.092 – 0.95)/ (-10 mV) = -14.2 V/V = 23.045 dB

**Results and Inferences**

The experiment demonstrates several important characteristics of current mirror circuits with varying channel lengths and W/L ratios:

1.Gain-Bandwidth Trade-off

There is a clear inverse relationship between gain and bandwidth across the different channel lengths. The 180 nm designs show modest gain (~29 dB) but exceptional bandwidth (>600 MHz), while the 1 μm designs provide much higher gain (~35-39 dB) at the expense of reduced bandwidth (<100 MHz).

2.Channel Length Effects

Increasing the channel length from 180 nm to 500 nm and then to 1 μm results in:

1.Increased gain: Due to reduced channel length modulation effects (λ) in longer channel devices, resulting in higher output resistance.

2.Decreased bandwidth: Due to increased parasitic capacitances associated with larger transistor dimensions.

3.Larger transistor widths required: NMOS widths had to be significantly increased (31 μm → 121 μm) to maintain the same current levels.

3.W/L Ratio Impact

The 1:2 ratio consistently outperforms the 1:1 ratio in terms of gain across all channel lengths:

1.For 180 nm: Modest improvement (29.298 dB → 29.325 dB)

2.For 500 nm: Slight improvement (37.87 dB → 38.015 dB)

3.For 1 μm: More significant improvement (35.481 dB → 38.693 dB)

The current mirror circuit's performance can thus be tailored to specific application needs by selecting appropriate channel lengths and W/L ratios, with clear trade-offs between gain, bandwidth, and silicon area (as evidenced by the increasing transistor widths required for longer channel designs).







