# Arctiq-GPS Journal

Time after timelapse crash:
### 19 hours
Time with total hours
### 21 hours

## Power, Storage, and a reference schematic that is actually just malware
Started the week routing the boost converter, fuel gauge and SD card. That was the plan anyway. Burned through approximately 87 reddit threads, 12 mutually contradictory application notes and 3 datasheets only to realise that the entire schematic was garbage. Not only did I transpose two resistor values, nobody anywhere ever mentions that none of the example component values work if your trace is longer than 2mm. Five hours completely wasted. Only win: I caught this before I ordered boards. That would have been a week waiting for a very expensive coaster.

Time: 5.2h

## RF, Audio, and the GPS module that hates me personally
Things marginally improved once I moved onto the Neo M9N, audio codec and mic amp. GPS ate almost all of this block. Nobody warns you that you can get everything else perfect and the entire board will still be useless because you routed the antenna trace 0.5mm too close to a ground via.

RF does not negotiate. RF does not care about your deadline. RF will brick your entire board for fun. I triple checked the 50 ohm impedance calculation four separate times. It is still probably wrong.

Time: 3.1h. 2.9 of that was staring at the impedance calculator.


## CM4 Layout Shuffle
Broke out most of the peripherals to the CM4 connector. 90% of this session was just dragging components around the screen going "where the F**K do I put this". Constantly alt-tabbing between schematic and PCB editor. This is the single worst habit you can have doing layout. I knew this. I did it anyway. By the end I had a rat's nest that looked like someone spilled spaghetti on the editor.
(editors note: this is funny as hell bro. i am criticizing my own work :rofl:)
Time: 1.4h. No net useful work accomplished.


## The Rush
Realised at 10pm that if I didn't finish this by the end of the week I was going to blow the project deadline. So I turned my brain off, and started smashing keys and traces together. 
Not the best idea but it did help, somewhat. (no it didnt. please lord i wasted like 8 hours fixing half of this work)

## The Reckoning
Hit save. Ran DRC.

517 errors. 319 warnings. I counted.

Every single one was clearance. I crammed everything so tight half the silkscreens and traces were practically touching. Spent the next two entire evenings just moving every component 1mm to the right. No new features. No improvements. Just damage control.

Time: 8.7h. I want that time back.

## Validation and Simulation
DRC is finally clean (NOT, well it is but like the errors are negligible). Ran SI sims on every high speed bus, checked power and ground plane impedance, went through every net one by one. For a first attempt at something this size it could be an awful lot worse.

Only real unforced error was the SD card traces which I routed all the way across the board for absolutely no reason. I knew that was wrong the second I finished routing them. Fixed it now. As far as I can tell, this board should actually boot. There is approximately a 95% chance this is correct.

So I proceeded to move half of the board around and move the sd card slot closer.

Addendum 1:12am: Just noticed I swapped TX and RX on the GPS. Fixed. God damnit.
another addendum 2:40am, god my parents are gonna kill me: I used BLIND VIAS for almost all power and GND traces. WHY DID NOBODY EDUCATE ME ON THE COST. Thankfully 
