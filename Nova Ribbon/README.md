# Nova Ribbon
A dynamic hair accessory that responds to the wearer’s brain waves

## Purpose
This project is an exploration of the use of lightweight EEG headsets for non-medical purposes such as dynamic accessories or everyday smart devices. For this project, we will be creating a dynamic hair accessory which rises and falls depending on the user’s level of brain activity.

## Design
This project is inspired by the character Nova Prime from the video game Warframe, made by Digital Extremes, as well as the Muse headband.
<p align="center">
  <img width="542" height="542" src="https://github.com/DreekFire/Electronics/raw/master/Nova%20Ribbon/Nova%20Armor%20Flaps.gif">
</p>
The Prime variant of the Nova warframe possesses armor flaps on her helmet and shoulders which open whenever she performs parkour or casts an ability. 
<p align="center">
  <img width="427" height="341" src="https://github.com/DreekFire/Electronics/raw/master/Nova%20Ribbon/Nova%20Green%20Cropped.png">
</p>
We reimagined the flaps on her helmet as a ribbon, and thus, the initial design for the Nova Ribbon is a hair accessory. Two electrodes are held in place over each of the temples by a headband which reaches around from the back.

## Technical Details
Two electrodes will be placed on either side of the wearer’s head. These electrodes will measure a voltage the same way an EEG headset does. As neurons fire within the brain, the flow of ions will generate an electrical potential between the electrodes, which results in what is known as brain waves. Brain waves are grouped into delta, theta, alpha, beta, and gamma waves in order of low frequency to high requency. In general, the more higher frequency waves there are, the more alert the user is. We are particularly interested in Gamma and Beta waves, as those indicate an active brain. Since brain wave amplitudes are very low, usually under tens of millivolts, we use an instrumentation amplifier to increase their voltage. Amplifying the signal early on will reduce the effect of noise introduced later in the system.
In order to measure the amplitude of Gamma and Beta waves, we use an active high pass filter with a cutoff frequency of 14 Hz, which is approximately the lower bound for Beta waves. This also has the convenient effect of removing any DC components from our signal, while an active filter means we don't have to worry about impedance matching. Next, the signal is sent through a full bridge rectifier to convert it to DC, along with a capacitor to smooth the signal.
We now have a DC signal with a voltage that represents the amplitude of Gamma and Beta waves in the wearer’s brain. We use a comparator to determine if the signal exceeds a certain threshold. Then, whenever the comparator output changes, the transition is detected by a differentiator circuit which activates an H-bridge that powers a pair of micro DC motors to actuate the flaps.
Here is the intended circuit diagram:

## Parts List
### 1 Instrumentation Amplifier: AD623ARZ
One of a series of instrumentation amplifiers made by Analog Devices
AD623 is the model number, ARZ refer to quality under Analog Devices’ naming scheme, packaging, and RoHS compliance, respectively. A is the lower of two grades, Z is compliant, and R refers to tray or tube packaging.
https://www.digikey.com/product-detail/en/AD623ARZ/AD623ARZ-ND/644106 - DigiKey link - cheaper but unknown delivery speeds or shipping costs, $4.53
### 3 Operational Amplifiers: uA741
A commonly used OpAmp made by Texas Instruments.
https://www.amazon.com/Texas-Instrumen-UA741CP-General-Purpose/dp/B01KO48D5K3 - 20 pcs
DIP8 refers to the form factor - 8 pins, pointed downwards, meant to be inserted into ports instead of soldered on top. Opposite of PDIP or just DIP is SOIC, which is flat and is meant to be soldered on top of contacts - C means commercial-grade temperature response, P means plastic casing (for TI at least), $9.67
### Resistor Pack:
https://www.amazon.com/Sparkfun-500-4W-Resistor-Kit/dp/B008MH97I4 - 500pcs, SparkFun is a well-known brand, but this has less resistors with fewer different resistances, $10.82
### Capacitor Pack:
https://www.amazon.com/Elenco-100-Capacitor-Component-Kit/dp/B004YHZDW0 - 100pcs, smaller pack, is apparently a dominant brand for circuit components that Joe Knows is trying to compete with, $14.74
https://www.amazon.com/Joe-Knows-Electronics-Value-Capacitor/dp/B007SVHFXO - 645 pcs, large number of capacitors with many different values. As expected, kind of budget quality though, so it’s recommended to measure the capacitance of each before use, $19.99
### Diode Pack:
https://www.amazon.com/McIgIcM-1N4007-Standard-Through-Rectifier/dp/B071DXGHL7 - 250 pcs, does what diodes do. It’s pretty straightforward (pun intended), $4.99
### Transistor Pack:
https://www.amazon.com/McIgIcM-Transistor-2N2222-2N2907-Assortment/dp/B06XCXX69F - 200 pcs, lots of transistors of different models. Contains both NPN and PNP, $8.98
