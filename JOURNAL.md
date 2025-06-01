---
title: "Jintendo Slab"
author: "Jason Zhang"
description: "It's gonna be a slab shaped console (kinda like a 2DS cuz I'm too lazy to learn how to make hinges) that you can play retro games on, will have battery, powered by RPI Z2W"
created_at: "2025-05-31"
---
# May 31th: Research on parts and making a plan!
Spent time researching how I'm gonna make all this since I never made a PCB or anything before
I made a spreadsheet with parts and prices https://docs.google.com/spreadsheets/d/1hn2z8ekfqbGUfXvgOQFQ-BLUxkavOTLEDDJ-F8h76a0/edit?usp=sharing
I'm just gonna note down my thoughts here haha
Originally found a Pisugar 2 for my charging thing, but then I realized that you could just use an Adafruit battery with a charging circuit, a power guage thing, and you basically can get the same thing done for cheaper.
What is a boost converter?? I guess I need to find something to change the 3.7-4.2V of the battery to 5V for the RPI.
I believe I finished a power circuit for my device
2000mAH battery is connected to a lipo charge circuit that also has an output, that is conencted to a battery guage (so i can measure my battery percentage), which is conencted to the voltage booster so it can be at 5v 2amps for the raspberry pi
Also listed out the basic other parts, but haven't done much looking into them as in any other accessories I might need for those.

**Total time spent: 2h**

# June 1st: More Research, rethinking previous decisions
So apparently there's something called SMD/SMT which is like basically small form factor but had to attach, now I switched over the prebuilt breakout boards from last update for like microchips and I was gonna make a single PCB for everything all custom (cuz I thought using breakout boards might be kinda cheating) but then apparently SMD stuff is really hard to solder. I think for the resistors/transistors/LEDs I could just use normal parts, but for the microchips I might have to get it done at the PCB factory or learn how to do it.
Who knew it was gonna be this complicated. I'm referencing the Pi-Tin project that alexren mentioned, but I dunno, it's still so hard, cuz I want to make some changes.
I replaced some of the things due to SMD being complicated, so if a through hole variant is available, I'll use that, but since for the charge circuit, most charge controllers are SMD, I'm using the Adafruit one again, and I'm using a powerboost for the voltage converter, as the powerboost also has a low battery light so I can use that instead of getting comparators myself and wiring that up. For the display connector, I got an Adafruit breakout board, I'm probably gonna solder things on.
Also decided to use a cheaper speaker, it's the one used in Pi-Tin, it also is smaller, which I hope will fit better.
 **Total time spent: 3h**
