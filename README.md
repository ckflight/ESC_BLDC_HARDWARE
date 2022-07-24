# ESC_BLDC_HARDWARE

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


