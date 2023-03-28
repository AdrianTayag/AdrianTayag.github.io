---
layout: post
title: "Unboxing: Sirkito Switch Debouncing Module"
categories: unboxing, review
---
![Overview](/_assets/switch_debounce/product_shot2.png)

### Switch Debouncing Module by Sirkito

Way back 2019, me and my college friends started Sirkito - an electronics components reseller in UPLB. I'd say it was quite successful, turning a profit in less than a semester and having a decent customer base. I'm tempted to tell more about Sirkito, but I think it deserves its own blog post.

![FB Post](/_assets/switch_debounce/fb_post.png)

Over time, we decided to manufacture our (first and last) in-house module: a switch debouncing module used as input for 74LSxx TTL based projects in our college.

### How it works

The module is composed of a 555 Timer circuit configured in monostable mode: 

![Monostable](/_assets/switch_debounce/monostable.png)

[Source](https://www.electronics-tutorials.ws/waveforms/555_timer.html)

By using the monostable output of the module, the customer should be able to generate clean square wave signals as input to their projects.

More importantly, the module disregards any additional triggers until the monostable output is done - which effectively debounces the switch inputs.

### Schematic

![Schematic](/_assets/switch_debounce/pcb_schematic.png)

Some errata on the schematic:
- R1 should be 470k Ohm
- R2 should be 10k Ohm

We basically used the reference circuit and applied our own resistor values to achieve the desired pulse time. Basing from the schematic, the pulse time would be:

    T = 1.1 * R1 * C1
      = 1.1 * 470000 * 0.000001
      = 0.517s

The debounce length of 0.5s is more than enough for even the worst of switches. I believe we also considered using the resistor / capacitor values that were not frequently bought by the customers.

### Build

![Board](/_assets/switch_debounce/pcb_routing.png)

Since we're manually producing these modules, we used our own inventory of through hole components for easier assembly. Component placement was optimized for minimal PCB footprint.

![PCB](/_assets/switch_debounce/raw_pcb.png)

With the module dimensions, the lower part of the PCB still has the space for 4 or 5 more modules. However, we decided to only go for 10 modules for the first run.

We prepared the PCB by blocking out the traces through heat pressing photo paper to the raw PCB and submerging it to a tub of ferric chloride.

### Finished product

![Module](/_assets/switch_debounce/product_shot1.png)

We also created a test circuit composing of a 2 bit counter with the module's output connected to the clock line. Unfortunately, I wasn't able to 

Looking back at it, there are definitely cheaper ways to debounce a switch. But this module was a surefire way to add a clean input signal to an existing project.
