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

#June 4th: Finished PCB, Ready to Begin on the CAD Model
Today I tried to fix the errors from yesterday in which the ground fill wasn't working. After some time on Stackexchange, it turns out it's because I'm using a 2 layer board and so the pour is getting interrupted by traces and pins and stuff. So I had two options, 4 layer PCB ($$$) or use stitching vias and bascially move around the traces so I can use vias to connect the different parts. While this isn't ideal because it's kinda sketchy but it's better than manually rounting the ground and hoping it all fits, so I think it's a upgrade for the budget.
Anyway's I put my Jintendo (Jason + Nintendo) logo on the back, here's some pics!
![image](https://github.com/user-attachments/assets/5441ba1e-72d8-4efa-82f9-25167c93894b)
![image](https://github.com/user-attachments/assets/97748030-a033-4c84-a70f-d21ecf72f82c)
![image](https://github.com/user-attachments/assets/35ca61a9-0940-4901-8d4a-6e238483d89e)

**Total time spent: 4h**

#June 5th: Fixed the Zones More, Started on CAD
Someone replied to me about the fill zones and said even though DRC wasn't giving me any problems, they saw that there are still huge unconnected chunks, and so I used stitching vias, and now it doesn't look chunky anymore.
![image](https://github.com/user-attachments/assets/fd5fc295-23bf-499b-883e-496a444cf66e)
I'm pretty proud of how it looks and I'm gonna export it into Fusion before I break something haha.
I downloaded the STEP files for all the parts that I could find, however something interesting that I found was that Adafruit tends to prefer giving Fritzing and EagleCad files over 3D files, and if you wanted the 3D file you could submit a issue in the CAD github page (and it's a github page that they don't mention at all unless you go to Digikey).
Oh yeah and there was no 3D files whatsoever for the resistive touchscreen TFT display with the breakout board so I changed it to the capacitive touch version for the same price which had way more resources available. It didn't change anything because I was never gonna hook up the touchscreen either way and the rest of the wiring is all the same.
However a pet peeve for the new display is that the right bezel is off center...
Anyways I wasn't able to get the official model for the USB charging board and I couldn't find anyone who made one so I got the EagleCAD file, plopped it into Fusion and added the USB and JST ports myself (with models from the internet). 
I then placed all the parts in Fusion where I made a mockup of how I was gonna put the parts. This took a while, as I constantly referred back to my schematic and making sure it's routed in an efficient way.
I ended up having to put my battery off center as I had to fit the charger board, voltage booster, and amplifier in the bottom portion of the board. I wanted the console to be mainly bottom heavy because I felt like it would feel weird if the top of the device was like way heavier than the rest.
It took a bit of working around but I think I have a basic design that would work. 
![image](https://github.com/user-attachments/assets/3de50bae-7316-48b1-9cb9-be33a61d33bd)
![image](https://github.com/user-attachments/assets/a2a30779-c4dd-4fb2-942a-685503c7c925)
I also started on an outline so I can begin extruding the board parts.

**Total time spent: 10h**

#June 6-7th: Moved some buttons on the PCB, finished layout of casing, and buttom layer, need to finish top portion and maybe button covers.
Sorry guys I was a bit lazy yesterday to journal so I'm gonna combine it.
What I basically did was first try different combinations to put the different boards in without making it too big or oddly shaped. I needed to separate the console into 3 parts vertically as I have 2 pairs of triggers on left and right sides, and because my console is vertically aligned, there can't be anything behind the triggers (or else you would have to shove your fingers through a small gap).
I also realized my right set of buttons were off center, along with start select, I didn't notice this earlier because I knew the right side of the board was longer (with the power and special keys) but then I realized it looked weird if they weren't together. So I fixed that.
Here's some pictures of the console now.
![image](https://github.com/user-attachments/assets/4263298a-d3cc-4c68-bd03-6276aa6fa60e)
![image](https://github.com/user-attachments/assets/936c14fa-7b44-4437-b5c7-de138ae1ba12)
![image](https://github.com/user-attachments/assets/0475fca5-c308-4790-9c4a-9ffc80052134)
And because I don't wanna spend too much money on screws and stuff, I'm using pegs for most of the boards that basically have a top part and a bottom part, and the top part will basically hold it in place as long as the to and bottom are secured, so I only need like 4 screws total.

**Total time spent over 2 days: 12h**

#June 8-9th: Finished Case, Ready to Submit
Once again I was kinda tired, and I didn't really do much yesterday. But anyways I finished the case, there are some parts that could be better, but honestly Fusion was not working with me so this is the best I could do. For example, I wanted to have some button caps, but that was too complicated and I wasn't sure if the prints would look good, especially since I would need TPU for that. So I'm leaving the buttons exposed and some part of the PCB exposed. I tried to make a cover for the trigger buttons but the left side triggers, the I wasn't able to separate the face in Fusion, so I ended up doing something sketchy and using the face from the other side to cut out what I wanted. It's complicated haha.
Anyways I made a lid for the thing and it looks decent. The way I'm gonna fasten the console together is with M2.5X25mm screws on the bottom (yes it's a big boy) with nuts, because I didn't know how to make actual threaded holes and I thought that might be too complicated and what if the threads don't line up or something, so basically it might look clanky, but I want it to work haha.
The top will use smaller nuts as the display part is relatively thin, just look at these pictures.
Here is an image of the two halves.
![image](https://github.com/user-attachments/assets/0ef2a2ad-327d-4fb5-a085-2055bde2942d)
And here's what it looks like rendered together.
![image](https://github.com/user-attachments/assets/a4924b1b-a704-4121-a03f-a9f8fffc7548)
![image](https://github.com/user-attachments/assets/4165f00a-34fa-4430-b13c-a984127049c2)
I'm probably going to add a carved logo on the empty space of the shell.
Text added!
![image](https://github.com/user-attachments/assets/442239de-d9a1-4a9e-af27-8833ce5ace86)
![image](https://github.com/user-attachments/assets/02dd081e-51e0-47b0-8712-141aabbf25af)

**Total time spent over 2 days: 8h**
