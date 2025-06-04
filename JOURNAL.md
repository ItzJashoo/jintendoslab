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
Okay new update (still June 1st), began work on PCB, not quite sure what I'm doing, but basically because I'm using some breakout boards, I will have to solder wire, but the original design was for the raspberry pi to be soldered onto the headerpoints on the PCB like how Pi-Tin did it, but that means that the pi's headers wont be exposed, so I am creating headers that are on the PCB so I can still connect things with wires.
I found new buttons that are through mount that are slightly different sized, but in the end... who cares!!
Anyways I studied the Pi-Tin PCB until my eyes bleed, so now I basically know how everything connects and works (yeah just after a few hours!)
I got started on my PCB, first plotting out the raspberry pi headers before putting test points for me to solder the audio inputs (the three wires), the display (needs 6), and for the charge circuit, the Pi-Tin did everything custom, but cuz I was using breakout boards, it's gonna be slightly different. They had a cool shutoff thing where after comparators detect the voltage to be too low, it would auto save and shut off, however since I'm using an Adafruit Powerboost 1000 that has a Low Power Output port, I tried to figure out how to make it work. After some research, I made a voltage divider that keeps the voltage below 3.3 (max for RPI GPIO header). This is because the LPO will constantly emit the 4.2V until the voltage is too low (low battery) where a red LED on the board turns on and the LPO voltage drops to zero. This drop to zero is gonna be my signal for the shutoff to connect to the one on the Pi-Tin. However, I think the Pi-Tin circuit is flipped from mine (as in when circuit is LOW, it means good battery, if HIGH, low battery) however I'll see as I look in more.
ANyways here's some pics:
![image](https://github.com/user-attachments/assets/b5d9c1d5-ce2b-43fd-9968-85bee993e3fa)
Oh yeah I learned how to make custom symbols and I'm using NET labels to keep things organized.

 **Total time spent: 8h**

 #June 2nd: Finished Schematic, Working on PCB 
Today I had a meeting with alexren about my project and some questions I had, so I have assurance that my voltage divider (hopefully) works, and I'm able to use that to (hopefully) not fry my Pi. I found alternate buttons again because I wanted to not make my own footprints and 3D models because I'm lazy and I don't wanna mess something up, and that also helped me cut my prices down, however Digikey is talking about Tariffs and I hope they're not TOOO much. Anyways I was confused cuz some of the official button schematics had 4 pins but the right angle button only had 2 pins on the schematic, so I ended up just on the footprint labeling the pads that are internally connected (since buttons contain 2 pairs of connector thingies) as the same thing, so for example, instead of 1 2 3 4 on the footprint I just put 1 1 2 2. Hopefully that works!!
Anyways I also started making my actual PCB, but I do have some questions about mounting the RPI, as in the Pi-Tin thing they basically just soldered it, but their PCB has all the pins as SMD on layer B.mask, but in their footprint on their schematic everything was labeled as through holes on all copper layers, so I'm just hoping for the best, so I'm gonna stick to the through holes and hope that it works like that. 
Here are some pictures:
![image](https://github.com/user-attachments/assets/371e4578-ce07-427f-b1dc-a8e1df776698)
![image](https://github.com/user-attachments/assets/b2e0fba2-8af2-41ff-a869-7d23d5031eb0)

**Total time spent: 7h**

#June 3rd: Finished PCB Design, Need to Work Out the GND Fill
I started off finishing organizing the components and continuing from yesterday. I grouped the parts into where they're supposed to go. I tried to keep the battery things close but I want to put the battery behind the display. I tried to make everything symmetrical and nice.
Wiring is another story, I had trouble routing everything and got stuck at a few pins. So I ended up trying to do a ground pour and only pin the other ones. However, I'm having trouble with the ground pour, I'm gonna watch a tutorial tmrw.
Also the text above the image is something I'm putting on the back silkscreen.
![image](https://github.com/user-attachments/assets/219475dc-8907-4619-80df-3e1e888901e3)
![image](https://github.com/user-attachments/assets/2c3ae544-410f-472c-83be-b1f0f48dac30)
![image](https://github.com/user-attachments/assets/2a266b66-c0a9-4242-b2c6-a25da8024865)
![image](https://github.com/user-attachments/assets/1ef929fb-7dd7-4b32-a635-f56bdce8944d)

**Total time spent: 5h**
