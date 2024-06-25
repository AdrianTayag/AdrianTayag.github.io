---
layout: post
title: "Repair: Kyowa KW-3631 Induction Cooker"
categories: teardown, repair
---
![Induction_cooker](/assets/induction_cooker/Front.jpg)

### A decade old Induction Cooker

Recently, my induction cooker / stove suddenly stopped turning on. Possibly a sign to start writing a post on teardowns again.

This stove was bought around 2014-2015 for my college dorm use. Along with a rice cooker of the same brand - which I also still use to this day. 

For readers' context, turning on the stove for cooking just requires a single press of the ON/OFF button.

This will immediately start heating your pan with a preset of "Chafing dish" and a temperature setting of 250 degrees Celsius. Afterwards, you'll be able to select your cooking presets, setup timers, and adjust the temperature.

### Issue: Non-responsive to power button press

The issue is immediately apparent since the single button press to start cooking is now non-responsive. Thus rendering the user to be unable to use the stove in any way.

After checking the internet for similar issues, the common root cause is a defective ON/OFF button. Since this button serves as the only entry / exit to operate the machine, it is always pressed whenever the stove is used.

### The Teardown

![Back](/assets/induction_cooker/Back.jpg)

Since this is a home appliance without any water resistance ratings and minimal safety features, opening it up is just a matter of removing all the screws on the bottom side of the stove. Four screws are hidden inside the feet, but are also easily accessible by removing the rubber covering it.

![Top](/assets/induction_cooker/Top_side.jpg)

The top part containing the UI, buttons, and cooking surface is pretty simple. The button board interfaces with the coil driver with a 5 pin JST connector

![Coil](/assets/induction_cooker/Coil_side.jpg)

The bottom part contains the induction coil, the coil driver, and the cooling fan for the product. 

### The repair

![Coil](/assets/induction_cooker/Button_PCB_front.jpg)

The tact switch for the ON/OFF button is located at the lower right of the PCB, which is mounted to the casing via screws. Probing the ON/OFF tact switch, it remained OPEN regardless of the switch state. 

The single layer PCB utilizes through hole components (except for the single SMT IC part) which allows for very easy repairs. The repair is pretty straightforward. The manufacturer also opted to use a common tact switch dimension - which I have on hand as spares. 

Aside from replacing the switch, the internals were also cleaned up. 

### Interesting bits

![LED_IC](/assets/induction_cooker/IC.jpg)

Managing error codes + timer in led IC

How did it manage to communicate with the coil driver with only 5 wires?

Button matrix?

### How induction cooking works

### References

[TM1668 LED Keypad driver datasheet](https://www.lcsc.com/datasheet/lcsc_datasheet_1809211425_TM-Shenzhen-Titan-Micro-Elec-TM1668_C50291.pdf)