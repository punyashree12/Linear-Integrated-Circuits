 **EXP NO -1** 

##                                                              **Analysis of CS Amplifier**
##

##  i . Aim:
 To analyze a common-source (CS) amplifier with resistive load specifications of 500nm technology, 1.8 V supply voltage, and a power budget of 50 μW through DC analysis, transient analysis, and AC analysis, and to extract parameters such as DC operating point, DC analysis, gain, bandwidth, and power.



## Components used:


1. NMOS Transistor (CMOSN-nmso4)
2. Voltage Source ( VG - 0.9V, VDD – 1.8v)
3. Resistors (5K OHM)
4. Ground
5. CONNECTING wires

 
## Theory:

 In a common-source amplifier, the input signal is applied to the gate terminal of an NMOS (or PMOS) transistor, and the output is taken from the drain terminal. The source terminal is common to both the input and the output and is typically connected to ground.
 

![Image](https://github.com/user-attachments/assets/069c5dcc-2cda-440c-9c55-cef3b257bbbf)

**DC Analysis**

In the DC analysis of a common-source MOSFET amplifier, it is crucial to bias the MOSFET in the saturation region to ensure it functions as an amplifier. This is typically achieved using a voltage divider network that sets the gate-source voltage (V_GS). The DC operating point, also known as the Q-point, is determined by the gate-source voltage and the drain current (I_D). Selecting an appropriate Q-point ensures that the MOSFET operates in the saturation region for the entire input signal range, allowing for linear amplification without distortion. Proper biasing and setting of the Q-point are essential to maintain the desired performance of the amplifier.

**AC Analysis**

![Image](https://github.com/user-attachments/assets/957ca293-da43-4c12-9851-f20b0055feac)

In the context of a common-source MOSFET amplifier, the voltage gain (Av )is given by the ratio of the output voltage change to the input voltage change, and it is approximately Av≈−gm×RD , where (gm) is the transconductance of the transistor. The bandwidth of the amplifier, which determines the range of frequencies over which the amplifier maintains a nearly constant gain, is influenced by the RC time constants in the circuit. Finally, the power consumption of the amplifier is primarily determined by the supply voltage (VDD) and the drain current (ID), which together dictate the overall power usage of the device. Understanding these parameters is crucial for designing an efficient and effective common-source MOSFET amplifier. In AC analysis, the MOSFET is represented by its small-signal equivalent circuit, which includes parameters such as transconductance (gm) .These parameters help in modeling the behavior of the MOSFET under small-signal conditions. The voltage gain (Av) of the common-source amplifier is determined by the ratio of the output voltage to the input voltage. This gain is influenced by the transconductance of the MOSFET, which indicates how effectively the device can control the output current, and the load resistance, which impacts how much of the output signal is delivered to the load. 

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

 Since power dissipation is 50μw and supply voltage is 1.8v
  
   WKT  P=VI

      I= P/V
      ID= 27μA
      ID=1/2[μnCoxW/L(VGS−Vth)^2]
      L=500n  W=487n  (Vary width to get the current)

      Qpoint (1.66v,27μA)



## Results:
   
  **1. DC Analysis:**
 
   SIMULATION :
       
![Image](https://github.com/user-attachments/assets/65f2e23b-5773-40d2-b9aa-cf142530e094)



**DC OPERATING POINT:**

         Id(M1)    :	 27μA

         Vd(n003)  :	  1.66192

        VG(n002)   :	 0.9v
 
         VT        :   0.366v
To operate mosfet in saturation region VGD<Vt

              
          
            VGD = VG -VD
                = 0.9 – 1.66192
            VGD = -0.76192

Since **VGD<VT**  MOSFET OPERATES IN **SATURATION REGION** .

##

**2. TRANSIENT ANALYSIS :**

   theortically,
  
       gain(Av)≈ −gm × RD

      where gm = 2ID/Vov     Vov=Vgs-Vt
              Av = -(2* 27.6μ/(0.9-0.366) *5000)
              Av = -0.516
SIMULATION ;

**CIRCUIT DIAGRAM**

   ![Image](https://github.com/user-attachments/assets/9bd473ec-539f-4a19-add8-c101b68b579f)

  
   INPUT VOLTAGE:

![Image](https://github.com/user-attachments/assets/0ee00d74-87d5-4665-8380-489760a15505)

OUTPUT VOLTAGE:

![Image](https://github.com/user-attachments/assets/8016463d-6e99-4c22-b763-9121f0133adb)

INPUT/ OUTPUT VOLTAGE :

![Image](https://github.com/user-attachments/assets/505f643d-f18b-43bb-89f8-df9c8daf4ceb)
From graph;
            
             Vinp-p = 100mv

             Voutp-p=0.05
             
             gain (Av) = voup-p/Vinp
          
                      Av  = -0.5
-ve sign indicates 180degree phase shift between input and output voltages      

**3. AC Analysis:**

SIMULATION;

   CIRCUIT DIAGRAM:
![Image](https://github.com/user-attachments/assets/b1101857-530d-4abe-90b7-1ec342968c69)

FREQUENCY RESPONSE:

![Image](https://github.com/user-attachments/assets/0fa94555-0294-43f2-ba73-cc5e22b03ab5)

![Image](https://github.com/user-attachments/assets/4f5b687e-4cdf-4083-bca6-c944125a85eb)








Gain_dB: 20*log10(V(vout)/V(n002))=(28.9094027074dB,101.944229391°) at 1000



**INFERENCE:** 

 
The current flowing through a MOSFET is directly proportional to its width, and it varies with changes in the width. When the MOSFET operates in saturation, it functions as an effective amplifier, producing the desired negative gain according to the equation Av=−gm×RD  . Achieving Q point stability in the saturation region is crucial for linear amplification. The MOSFET's gain increases significantly in the mid-band frequency range during small-signal analysis.

Transient analysis evaluates the circuit's response to time-domain signals, highlighting how quickly it responds to changes, which is vital for high-speed applications. AC analysis is instrumental in designing circuits with the desired gain, ensuring proper impedance matching, and understanding the frequency response and small-signal behavior.

From the DC operating point analysis, we observe that the MOSFET has a drain current (Id) of 27.7277 µA, a gate voltage (VG) of 0.9 V, and a drain voltage (Vd) of 1.77227 V, confirming operation in the saturation region since VGD=−0.87227 V is less than the threshold voltage (VT) of 0.366 V. Using transconductance (gm) derived as 2ID\Vov with an overdrive voltage of 0.534 V, we calculate gm≈0.104mS. Consequently, the theoretical voltage gain is approximately -0.52, which closely aligns with the graph-based observation of a gain of -0.5, derived from an input peak-to-peak voltage of 100 mV and an output peak-to-peak voltage of 50 mV. This slight discrepancy may be due to measurement or rounding differences but overall confirms the expected behavior of the system.
