# BLHELI_S Electronic Speed Controller Hardware Design

#### ESC Information:

 * BLDC 3 phase motor speed controller hardware design working with open source BLHeli_S C configuration firmware C_H_30.

 * The ESC is tested on a real quadcopter with brushless motors at 40 Ampere current rating. 
 
 * TPN2R703NL Power MOSFETs are used on this design, which are capable of delivering current up to 45 Ampere for normal operation and 90 Ampere peak for short pulse.
 
 * MP1907 High Frequency Half Bridge Gate driver is used for controlling the Power MOSFETs. High power MOSFET transistors have high Q and capacitance values. To open the gate it requires high amount of current in short amount of time where current requirement decreases exponentially. This is the reason for using a Gate Driver. Also an extra gate resistor is populated at the input of MOSFET gate pin.
 
 $$ Igate(max) = {Vgate \over Rgate} $$

        4S Lipo Battery Vgate = 16V, Rgate = 10 Ohm and Igate(max) = 1.5A
 
 $$ Igate = {Qfet \over Tswitch} $$
 
         For a MOSFET with Qtotal = 50nC Tswtich = 500nS and Igate(needed) = 0.1A.
         Therefore, a 100 Ohm gate resistor is populated.

 * Phase C has current bar trace. Or it can be done with extra solder on the trace.

![esc1](https://user-images.githubusercontent.com/61315249/103273741-14269f00-49d1-11eb-8cd9-0c20945b51e4.png)

![esc1](https://user-images.githubusercontent.com/61315249/82239872-240dd900-9942-11ea-98cc-d76186299321.png)

![esc2](https://user-images.githubusercontent.com/61315249/82239863-2112e880-9942-11ea-8ac3-22ef7c3397df.png)

# BLHELI_S Firmware Flashing Guide

When esc is new assembled the EFM8BB2 does not have BLHeli_S Bootloader.
For the first time flashing, 4wire interface is used by using C2CK, C2D, 3.3v and GND pins where it will load both bootloader and firmware to esc.
After this step, esc can be flashed with 1-Wire interface (Esc's pwm pin).

####Flashing ESC for the first time.

1. Open "Make interfaces" section
2. Select the Arduino board that will be used as programmer.
3. Click "Arduino 4way-interface" and flash it to arduino.
   (Now arduino became a 4wire programmer)

4. Select "SILABS C2 (4way if)"
5. Connect Arduino to Custom ESC
       GND to GND 
       3.3v to 3.3v
       Arduino Pin12 to C2D 
       Arduino Pin11 to C2CK
6. Open ESC Setup section and connect to esc and click Flash BLHeli
   (choose suitable version, my custom quadcopter esc v2 is working with C type)

Now the esc is both flashed with blheli bootloader and the blheli firmware, 
therefore 1wire interface can be used which is the esc's pwm pin. 
Or flight controller can be used in passthrough mode.
