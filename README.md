XTRUDR
======

**BeBoPr++ multi I/O expansion board.**

|![](http://imageshack.com/a/img673/1347/RP8xGJ.jpg)|
|:-:|
|*XTRUDR carrier populated with 3 stepper drivers and ADC module*|


## Introduction

The **XTRUDR** board offers four extra analog inputs, four extra PWM outputs and three additional stepper motor drivers. The form factor and BeBoPr++ interface is identical to the **PEPPER** and **TAKE-5** expansion boards. The **XTRUDR** can either connect directly to a BeBoPr, or via a DECAMUX in combination with another expansion board for even more I/O.

This board gives the needed extra I/O to use a four channel extruder like the [**Kraken**](http://e3d-online.com/The-Kraken) in combination with a [**BeBoPr++**](https://github.com/modmaker/BeBoPr-plus-plus). Populating only part of the board gives a way to add only the I/O needed and minimize the costs. 

The picture above shows the three stepper drivers on the left side and the four PWM power outputs on the right side. Separate power inputs for steppers and heater outputs. The small PCB in the upper left corner is the [analog input module from Adafruits](http://www.adafruit.com/products/1083).

## DIY / Open Source

|![](http://www.oshwa.org/wp-content/uploads/2014/03/oshw-logo-100-px.png)| This is another free PCB design expanding the BeBoPr++|
|----|:------|
The PCB design files are freely available to get PCBs manufactured. The XTRUDER can also be [**ordered directly from OSH Park**](https://oshpark.com/shared_projects/wKJb03ND) (in a set of 3). Or the [**Gerber files**]() can be used with most other PCB manufacturers.

Besides the PCB, no special parts are used. The [**BOM**]() contains a list of used parts with numbers for ordering directly from Farnell or Mouser. 

## Easy to Assemble

The XTRUDR uses only though hole parts and anyone with basic soldering skills will be able to assemble this board successfully. The stepper drivers and analog input module do use SMD parts but these come as already assembled modules and plug directly into the sockets on the board.

For this assembly an angled pin header was mounted onto the module and a 10-pin socket onto the PCB. But it is also possible to make a fixed connection by soldering the pin header to both boards.

|![](http://imagizer.imageshack.us/v2/280x200q90/661/js7rV0.jpg)|![](http://imagizer.imageshack.us/v2/480x400q90/537/bNfJ9r.jpg)|
|----|:------|

The leftmost picture shows the ADS1015 module with the (angled) pin header. The SMD components hide behind the connector pins. The board on the picture is actually the (ADS1115) 16-bit version that is pin compatible with the 12-bit (ADS1015) module. It's more expensive though and a bit slower in use.

The other picture shows the ADS1015 module located behind some connectors (on the right side). In front of the module are the four analog inputs, the thermistor (4k7) pull-up resistors, and a (white) 4-pin connector that connects 1:1 to the BeBoPr++'s I2C bus (J22A). The (black) polarized header is for the 16-wire ribbon cable connection to the BeBoPr++ (or DECAMUX).

![](http://imagizer.imageshack.us/v2/480x320q90/908/4HbEop.jpg)
On the 'heater output' side of the board there are four TO-220 power FETs, four red LEDs, the FET drivers and the connections for the extruder power and heaters. The PWM outputs are wired as low side switches to a common (ground) connection. The four screw terminals connect to the four heater elements, the power input header to the heater supply. The positive side of the heater supply can be routed directly to the heaters.

## Test results
- The stepper drivers and configuration jumpers are working (tested with three PanuCatt SD8825 modules).
- The PWM outputs needed some fixes (see 'bugs' below) but seem to function properly after that. These still need to be tested using proper loads though. The drivers, LEDs and FETs are functioning.
- The BeBoPr I/O enable global override safety is working for steppers and PWM outputs. 

## Bugs
Two [patches](http://imageshack.com/a/img661/4517/6Y3Fr1.jpg) are needed for the R0 board:
- A (missing) pull-up resistor has to be mounted on the back side of the board.
- A jumper wire is needed to fix a missing ground connection in the layout.
