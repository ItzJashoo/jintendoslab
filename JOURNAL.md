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
