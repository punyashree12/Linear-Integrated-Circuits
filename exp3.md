**EXP NO -3** 

##                                                              **DIFFERENTIAL Amplifier**
##

##  i . Aim:
Design and analyse the differential amplifier for the following specifications:

VDD = 3.3 V, P ≤ 3 mW, ViCM = 1.72 V, VOCM = 1.81 V, Vp = 0.7 V.

Perform DC analysis, transient analysis, frequency response, extract parameters.



## Components used:


1. NMOS Transistor
2. Voltage Source
3. Resistors 
4. Ground
5. CONNECTING wires


 
## Theory:

 The MOS differential pair is a type of amplifier configuration, which consists of two perfectly matched MOSFETs, with identical source resistances, and matching or common inputs. The output voltage will be the difference between the two drain source voltages (VD) of the MOSFETs.

While we can construct the differential pair using BJTs as well, for this experiment, we will focus on using MOSFETs. The basic building for any op-amp is the differential amplifier, or diff-amp. Therefore, understanding this circuit is crucial to any further understanding of the op-amp.



![Image](https://github.com/user-attachments/assets/160b589d-fd42-4c9d-95be-fd22b5805975)
This is the basic configuration of the diff-amp, with common-mode input voltage VCM, and identically matched transistors, Q1, Q2. From the figure, we can see the current flowing through each transistor is half the value of the current source, I, i.e., ID1 = ID2 = I/2.

The reason for the current source being present, is to allow for a steady, constant current, ensuring the transistors are operating in saturation, at an ideal operating point, to ensure amplification. It also ensures identical current flows through both the MOSFETs, which is crucial, since we need them to be perfectly matched. We will simulate this circuit later, but first, instead of a current source, we will use a resistor RSS, and perform DC, transient and AC analysis.




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
![Image](https://github.com/user-attachments/assets/cbb739af-9ff9-4b37-80ad-1f8a73821976)

This is the circuit we will have to design, and calculate the values of RSS, RD1, RD2.

Given: VDD = 3.3 V, P ≤ 3 mW, ViCM = 1.72 V, VOCM = 1.81 V, Vp = 0.7 V.

P = 3.3 mW = VDD x I = 1.8 x I

I = 3 mW / 3.3 V = 0.9mA 

ID1 = ID2 = I/2 = 0.45 mA 

RD = (VDD - VOCM)/ID1 = 3.3kΩ

RSS = Vp / I = 0.7 V / 0.9 mA = 0.77k Ω 

From our analysis, we have now calculated the values –

RD1 = RD2 = 3.3kΩ

RSS = 0.77kΩ





## Results:
   
  **1. DC Analysis:**


  Since we know the VDS, VGS values, we can calculate whether the MOSFETs are operating in saturation or not. This is crucial, because if the MOSFETs begin to operate in triode, the output gets clipped, which is not what we need.

The condition for saturation is that VDS < VOV, i.e., VDS < VGS - Vth, where Vth is the threshold voltage of the MOSFET, which is obtained from the TSMC 180 nm process technology .lib file. This can be included in the simulation, by adding the SPICE directive, .lib tsmc018.lib.

We can calculate if the MOSFET is operating in saturation, by using the relation VGD < Vth, which is the simplification of the saturation region condition.

VGD = (1.72 – 1.81) V = -0.09 V

Vth = 0.3966 V

For the MOSFETs, we have used W =2.4199µm, L = 180 nm.

From this, we can see VGD is negative, while Vth is greater than zero, satisfying our condition for saturation. Therefore, we can safely say the MOSFET is in saturation, and can act as an amplifier.

While we have determined that the MOSFET is in saturation, we need to an ensure an ideal Q-point, to make sure that the waveform does not appear distorted or get clipped off.


**Simulation:**


 
  ![Image](https://github.com/user-attachments/assets/e2c41cd4-5847-428a-8176-ab67cde54b47)


**DC OPERATING POINT:**

         Id(M1)    :	 0.9mA

         Vd(n003)  :	  1.81V

        VG(n002)   :	 1.72V
 
         VT        :   0.366V
To operate mosfet in saturation region VGD<Vt

              
          
            VGD = VG -VD
                = 1.72v – 1.81
            VGD = -0.09V

Since **VGD<VT**  MOSFET OPERATES IN **SATURATION REGION** .

 As we can see that VD1 = VD2 = 1.81 V, which is matching with our necessary requirements. ID1 = ID2 = 0.449 mA, ISS = 0.89mA which also matches with our requirements. Vp = 0.7 V, which also agrees with our analysis.

Next, we can calculate the power and verify whether or not we are within our power budget.

P = VDD. Iss = 3.3 V x 0.89 mA = 2.937 mW, which satisfies our power budget.
##

**2. TRANSIENT ANALYSIS :**

To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 1.72V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain.

To perform this analysis, we need to configure the voltage source V3, for the MOSFET M2, by setting a sine wave, with DC offset = 1.72 V , Amplitude = 50 mV, Frequency = 1 kHz.

For transient analysis, set the stop time equal to 5 ms, and then compare the output and input voltages

   
SIMULATION ;

**CIRCUIT DIAGRAM**

  ![Image](https://github.com/user-attachments/assets/452b1d5c-536c-456a-b42d-7ab6f32d5a22)
  
   INPUT VOLTAGE:

![Image](https://github.com/user-attachments/assets/1d89c9d7-194b-40ee-8124-70301541ec5e)



 OUTPUT VOLTAGE :

![Image](https://github.com/user-attachments/assets/4387d722-4f4f-4cbd-a8ed-79923d376a51)


![Image](https://github.com/user-attachments/assets/8a961923-517f-4e3e-a09a-3c90862e1010)

From this figure, we can see that there is a 180° phase shift, VD1 represented by the RED curve, is inverted compared to the input, VGS, which is represented by the blue curve.

Now, we can calculate the  gain, and use it to calculate the dB gain, and verify it with AC small signal analysis.






            
             Vin=1.7679-1.72=0.0479v

             Vout=1.8704-1.81=0.0604v
             
             gain (Av) = vout/Vin
          
                      Av  = -1.26
-ve sign indicates 180degree phase shift between input and output voltages      


**3. AC Analysis:**

To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation.

SIMULATION;

   CIRCUIT DIAGRAM:
 ![Image](https://github.com/user-attachments/assets/452b1d5c-536c-456a-b42d-7ab6f32d5a22)


FREQUENCY RESPONSE:

   Calculating the dB gain, by using the formula, A’v = 20log10(Av), we get,
   
   
            theortically 
         Gain_dB: 20*log10(Vout/Vin)= 2.00 dB


![Image](https://github.com/user-attachments/assets/a86ba8de-476b-4998-8ac0-939036223569)



     from graph Gain in dB= 1.88dB



 From here we can see that the midband gain is 6.80 dB, with a phase shift of 173.459°, which matches approximately with our calculated value of the midband gain.


##



**Next**, we move onto another variation of the differential amplifier. The only change we will be making is using a **Current source instead of the RSS resistor**, at the bottom of the circuit. There are quite a few **advantages of this configuration, such as **increasing the common mode rejection ratio**, making the amplifier more **immune to noise and fluctuations**.

Another advantage is that the current source provides a constant current tail current, preventing variations in transistor operating points due to fluctuations in power supply, or temperature change, maintaining the stability of the circuit.

To build this circuit, we will use a current source of value ID1 + ID2 = **I = 0.9mA**. We can then perform DC, AC, transient analysis, observe our readings and compare it to the circuit with RSS.

Since we have already completed our analysis and calculated RD values, we need not do it again, instead we can check if the output voltages are the same, and vary any parameters accordingly.

## Results:
   
  **1. DC Analysis:**


 





**Simulation:**


![Image](https://github.com/user-attachments/assets/b1b93677-3ff3-442c-b814-aad7586828a6)

**DC OPERATING POINT:**

         Id(M1)    :	 0.9mA

         Vd(n003)  :	  1.81V

        VG(n002)   :	 1.72V
 
         VT        :   0.366V
To operate mosfet in saturation region VGD<Vt

              
          
            VGD = VG -VD
                = 1.72v – 1.81
            VGD = -0.09V

Since **VGD<VT**  MOSFET OPERATES IN **SATURATION REGION** .

 As we can see that VD1 = VD2 = 1.81 V, which is matching with our necessary requirements. ID1 = ID2 = 0.45 mA, ISS = 0.9mA which also matches with our requirements. Vp = 0.69V, which also agrees with our analysis.

Next, we can calculate the power and verify whether or not we are within our power budget.

P = VDD. Iss = 3.3 V x 0.9 mA = 2.97 mW, which satisfies our power budget.
##

**2. TRANSIENT ANALYSIS :**

To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 1.72V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain.

To perform this analysis, we need to configure the voltage source V3, for the MOSFET M2, by setting a sine wave, with DC offset = 1.72 V , Amplitude = 50 mV, Frequency = 1 kHz.

For transient analysis, set the stop time equal to 5 ms, and then compare the output and input voltages

   
SIMULATION ;

**CIRCUIT DIAGRAM**

  ![Image](https://github.com/user-attachments/assets/62243e82-3968-4cf6-a855-209b06663736)
  
   INPUT VOLTAGE:

![Image](https://github.com/user-attachments/assets/a6f56149-9e9d-4cda-a367-a6555d1d866e)


 OUTPUT VOLTAGE :
![Image](https://github.com/user-attachments/assets/6c8c48b3-724c-4f42-b0c8-2b27143a2252)

![Image](https://github.com/user-attachments/assets/01357f98-e424-4b76-8e6d-87d5fe937bb8)


From this figure, we can see that there is a 180° phase shift, VD1 represented by the RED curve, is inverted compared to the input, VGS, which is represented by the blue curve.

Now, we can calculate the  gain, and use it to calculate the dB gain, and verify it with AC small signal analysis.






            
             Vin=1.7684-1.72=0.0484v

             Vout=1.8858-1.81=0.0758v
             
             gain (Av) = vout/Vin
          
                      Av  = -1.56
-ve sign indicates 180degree phase shift between input and output voltages      


**3. AC Analysis:**

To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation.

SIMULATION;

   CIRCUIT DIAGRAM:
![Image](https://github.com/user-attachments/assets/e886bc0b-cfff-4b8d-b73a-4cff81c3afbd)

FREQUENCY RESPONSE:

   Calculating the dB gain, by using the formula, A’v = 20log10(Av), we get,
   
   
            theortically 
         Gain_dB: 20*log10(Vout/Vin)=3.86dB

![Image](https://github.com/user-attachments/assets/65661153-1322-4c66-b273-cfefcf9830b9)



     from graph Gain in dB= 3.87dB



 From here we can see that the midband gain is 3.87 dB, with a phase shift of 170.075°, which matches approximately with our calculated value of the midband gain.

 ##

Now, we will move to the final circuit, where we will replace the **current source , with a NMOS Transistor**. The reason we do this, is due to the fact that the NMOS can behave as a constant current source when operating in the saturation region, so **it can act as a constant current source, when the input gate voltage VG is applied to drive the MOSFET into saturation**.


## Results:
   
  **1. DC Analysis:**






**Simulation:**

 
![Image](https://github.com/user-attachments/assets/8e74b8fb-bd44-4fb3-8c83-4b3a5819cf64)

**DC OPERATING POINT:**

         Id(M1)    :	 0.899mA

         Vd(n003)  :	  1.81V

        VG(n002)   :	 1.72V
 
         VT        :   0.366V
To operate mosfet in saturation region VGD<Vt

              
          
            VGD = VG -VD
                = 1.72v – 1.81
            VGD = -0.09V

Since **VGD<VT**  MOSFET OPERATES IN **SATURATION REGION** .

 As we can see that VD1 = VD2 = 1.81 V, which is matching with our necessary requirements. ID1 = ID2 = 0.449 mA, ISS = 0.89mA which also matches with our requirements. Vp = 0.69V, which also agrees with our analysis.

Next, we can calculate the power and verify whether or not we are within our power budget.

P = VDD. Iss = 3.3 V x 0.89 mA = 2.937 mW, which satisfies our power budget.
##

**2. TRANSIENT ANALYSIS :**

To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 1.72V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain.

To perform this analysis, we need to configure the voltage source V3, for the MOSFET M2, by setting a sine wave, with DC offset = 1.72 V , Amplitude = 50 mV, Frequency = 1 kHz.

For transient analysis, set the stop time equal to 5 ms, and then compare the output and input voltages

   
SIMULATION ;

**CIRCUIT DIAGRAM**

  ![Image](https://github.com/user-attachments/assets/beb243e3-35f5-4c28-9f9b-ebdccb569591)
   INPUT VOLTAGE:
![Image](https://github.com/user-attachments/assets/889c492b-d0aa-41ba-ab4f-f1de12266bdc)
 OUTPUT VOLTAGE :
![Image](https://github.com/user-attachments/assets/a190dcc0-91c2-4a51-842e-179f80b93515)

![Image](https://github.com/user-attachments/assets/91127aae-b7d5-4728-8be3-2a7f916366ed)

From this figure, we can see that there is a 180° phase shift, VD1 represented by the RED curve, is inverted compared to the input, VGS, which is represented by the blue curve.

Now, we can calculate the  gain, and use it to calculate the dB gain, and verify it with AC small signal analysis.






            
             Vin=1.7684-1.72=0.0484v

             Vout=1.8914-1.81=0.0814v
             
             gain (Av) = vout/Vin
          
                      Av  = -1.68
-ve sign indicates 180degree phase shift between input and output voltages      


**3. AC Analysis:**

To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation.

SIMULATION;

   CIRCUIT DIAGRAM:
![Image](https://github.com/user-attachments/assets/fc119156-aa42-4477-8044-5347691beada)

FREQUENCY RESPONSE:

   Calculating the dB gain, by using the formula, A’v = 20log10(Av), we get,
   
   
            theortically 
         Gain_dB: 20*log10(Vout/Vin)=4.50dB

![Image](https://github.com/user-attachments/assets/7601d2a4-99c1-47ee-8285-126112614eb0)


     from graph Gain in dB= 4.47dB



 From here we can see that the midband gain is 4.47dB, with a phase shift of 169.624°, which matches approximately with our calculated value of the midband gain.




**INFERENCE:** 

 
The current flowing through a MOSFET is directly proportional to its width, and it varies with changes in the width. When the MOSFET operates in saturation, it functions as an effective amplifier, producing the desired negative gain according to the equation Av=−gm×RD  . Achieving Q point stability in the saturation region is crucial for linear amplification. The MOSFET's gain increases significantly in the mid-band frequency range during small-signal analysis.

Transient analysis evaluates the circuit's response to time-domain signals, highlighting how quickly it responds to changes, which is vital for high-speed applications. AC analysis is instrumental in designing circuits with the desired gain, ensuring proper impedance matching, and understanding the frequency response and small-signal behavior.

From the DC operating point analysis, we observe that the MOSFET has a drain current (Id) of 27.7277 µA, a gate voltage (VG) of 0.9 V, and a drain voltage (Vd) of 1.77227 V, confirming operation in the saturation region since VGD=−0.87227 V is less than the threshold voltage (VT) of 0.366 V. Using transconductance (gm) derived as 2ID\Vov with an overdrive voltage of 0.534 V, we calculate gm≈0.104mS. Consequently, the theoretical voltage gain is approximately -0.52, which closely aligns with the graph-based observation of a gain of -0.5, derived from an input peak-to-peak voltage of 100 mV and an output peak-to-peak voltage of 50 mV. This slight discrepancy may be due to measurement or rounding differences but overall confirms the expected behavior of the system.


