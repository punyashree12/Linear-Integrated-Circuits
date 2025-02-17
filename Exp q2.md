**EXP NO -1** 

##                                                              **Analysis of CS Amplifier**
##

##  ii . Aim:
 To analyze a common-source (CS) amplifier with current source load specifications of nmos  500nm technology and pmos 180n, 1.8 V supply voltage, and a power budget of 50 μW through DC analysis, transient analysis, and AC analysis, and to extract parameters such as DC operating point, DC analysis, gain, bandwidth, and power.



## Components used:


1. NMOS/PMOS Transistor (CMOSN/CMOSP-nmso4/pmos4)
2. Voltage Source ( Vg- 0.9V, VDD – 1.8v , Vb-1.3)
3. Power supply 50μW
4. Ground
5. CONNECTING wires

 
## Theory:

A diode-connected MOSFET transistor is always in saturation, meaning it serves as a constant current source and amplifier. Understanding how this device works involves three primary types of analysis: DC Analysis, AC Analysis, and Transient Analysis.
![Image](https://github.com/user-attachments/assets/431b5374-8478-4a23-b663-da346a1a1462)

**DC Analysis**

In DC Analysis, we ensure that the MOSFET operates in the saturation region and calculate the DC operating point, which is crucial for preventing signal distortion. This analysis helps determine the correct biasing resistors needed to maintain a stable operating point despite fluctuations in other parameters, ensuring the device functions optimally.



**AC Analysis**


AC Analysis, or small signal analysis, focuses on determining the gain and frequency response of the amplifier circuit. The gain is given by the formula Av=-gmRd. This analysis allows us to understand how the circuit amplifies small signals and how it behaves across different frequencies, which is key for designing effective amplifiers. The frequency response helps in identifying the bandwidth and stability of the amplifier.
The drain current in a diode-connected MOSFET transistor is given by the formula ID=1/2[μnCoxW/L(VGS−Vth)^2]where Vov=Vgs−Vth and kn=unCoxWL This equation shows the relationship between the current flowing through the transistor and the voltage applied, taking into account the device parameters and dimensions. Understanding this relationship is fundamental for designing and analyzing MOSFET-based circuits.

**Transient Analysis**

Transient Analysis is used to examine how the circuit responds to time-varying signals. This type of analysis is essential for identifying issues such as signal distortion and phase shifts between the input and output. It's particularly important in high-speed applications like communication systems where precise timing is critical. By performing transient analysis, we can ensure the circuit performs reliably under dynamic conditions.


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
      ID= 27.7μA

      ID=1/2[μnCoxW/L(VGS−Vth)^2] 
     NMOS  L=500nm  W=487nm  (Vary width to get the current)

     ID=1/2[μpCoxW/L(VSG−Vth)^2]
     PMOS  L=180nm  W=75μm
      
      To get bias voltage Vb
        WKT VS=1.8v , Vt=-0.399v
           VSG>VT FOR CHANNEL FORMATION
         Therfore we get VG<1.4v
         
      Qpoint (1.69v,27μA)



## Results:
   
  **1. DC Analysis:**
 
   SIMULATION :
       
![Image](https://github.com/user-attachments/assets/fc5f92c3-94ed-4ff3-ab77-c54b3ea52d86)



**DC OPERATING POINT:**
  
  NMOS

         Id(M1)    :	 27μA

         Vd(vout)  :	  1.69v

        VG(n003)   :	 0.9v
 
         VT        :   -0.399v



##
   pmos4

         Id(M4)   :	 27μA

         Vb(n002) :	 1.3v

         Vd(vout) :	 1.69v

         VS(n001) :	 1.8v

   Q POINT (1.69v , 27μA)



##

**2. TRANSIENT ANALYSIS :**

   
SIMULATION ;

**CIRCUIT DIAGRAM**
![Image](https://github.com/user-attachments/assets/fa85ccf9-8160-4da9-8df2-a88bd58d15b8)


  
   INPUT VOLTAGE:
![Image](https://github.com/user-attachments/assets/5571ee31-6b5b-46c9-8850-076fa4953663)
OUTPUT VOLTAGE:

![Image](https://github.com/user-attachments/assets/9721a32f-c3d5-457d-9c53-702042333e61)

INPUT/ OUTPUT VOLTAGE :

![Image](https://github.com/user-attachments/assets/294c7b27-149d-4894-99b4-50da2edc1b9b)
            
             Vinp-p = 100mv

             Voutp-p=0.27
             
             gain (Av) = voup-p/Vinp
          
                      Av  = -2.7
-ve sign indicates 180degree phase shift between input and output voltages      

**3. AC Analysis:**

SIMULATION;

   CIRCUIT DIAGRAM:
![Image](https://github.com/user-attachments/assets/86b3285d-16d0-406e-8b28-2ec4543c5e4a)

FREQUENCY RESPONSE:

![Image](https://github.com/user-attachments/assets/c9aac35b-c7dd-456a-b233-6112c5ee3ea5)


![Image](https://github.com/user-attachments/assets/86f4c66d-a37f-4e95-8b83-192710359e97)


Gain_dB: MAX(20*log10(V(vout)/V(n003)))=(30.4574451698dB,179.7608949°) FROM 0.1 TO 1e+12


Gain: MAX(mag(V(vout)))=(7.00564561068dB,0°) FROM 0.1 TO 1e+12


value3dB: Gain/sqrt(2)=(3.99534565404dB,0°)


BW=1e+12 FROM 0.1 TO 1e+12


**INFERENCE:** 

 
The current flowing through a MOSFET is directly proportional to its width, and it varies with changes in the width. When the MOSFET operates in saturation, it functions as an effective amplifier, producing the desired negative gain according to the equation Av=−gm×RD  . Achieving Q point stability in the saturation region is crucial for linear amplification. The MOSFET's gain increases significantly in the mid-band frequency range during small-signal analysis.

Transient analysis evaluates the circuit's response to time-domain signals, highlighting how quickly it responds to changes, which is vital for high-speed applications. AC analysis is instrumental in designing circuits with the desired gain, ensuring proper impedance matching, and understanding the frequency response and small-signal behavior.

Based on the given data, the DC operating point of the circuit has been established for both NMOS and PMOS transistors, each with an identical drain current of 27μA, and the corresponding operating point being 1.69V. The voltage gain of the circuit is calculated to be -2.7, indicating an inversion of the output signal with respect to the input signal. Detailed gain analysis reveals a peak gain of 30.457 dB at a phase of 179.76°, spanning a frequency range from 0.1 Hz to 1e+12 Hz. The maximum magnitude of the gain is noted as 7.005 dB at 0° phase within the same frequency range. Additionally, the value of the gain at -3 dB is determined to be approximately 3.995 dB. The bandwidth of the circuit is notably expansive, covering a frequency spectrum from 0.1 Hz to 1e+12 Hz, which implies the circuit maintains its performance across an exceptionally wide range of frequencies. These results collectively showcase the circuit's capability to amplify signals effectively while operating over a vast frequency bandwidth. 

