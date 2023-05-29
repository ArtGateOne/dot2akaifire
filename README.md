# dot2akaifire
Nodejs code to control dot2 wia akai fire midi controller

This is the very early version of the code to control dot2 using the Akai Fire controller.

It's quite an interesting controller because, apart from many RGB buttons, it also has encoders. Although we don't have the ability to control the encoders in dot2 as in MA2, I managed to work around it somehow.

The code, just like in my previous projects, is based on web remote communication. Therefore, to make it work, you need to enable web remote and set the password to "remote".

To run the code, you will need to have Node.js installed, specifically version 14.17.0, which this package was prepared for.

How to run:

Download and install Node.js 14.17.0 from this link --> https://nodejs.org/dist/v14.17.0/node-v14.17.0-x64.msi
Download my code.
Run dot2 and enable web remote.
Run my code (execute dot2akaifire.js using node.exe from the Node.js package - you can do this by right-clicking, selecting "Run with" or "Open with," and choosing node.exe - make sure to set it as the default program for this type of file)
That's it. If the command prompt window is open, the program is running correctly. However, if the window closes, it means an error occurred. In that case, it's best to run my code in the command prompt (CMD) and see what error message is displayed in the window.

Remember not to have the MIDI controller used by another program or set as "in" or "out" in dot2 MIDI settings!

This is a very early version of the code for Fire, but it's stable enough and works quite well.


Configuration - open the dot2akaifire.js file in Notepad and find the line //CONFIG

//CONFIG

midi_in = 'FL STUDIO FIRE';     //midi in device name

midi_out = 'FL STUDIO FIRE';    //midi out device name

colors = 0; //auto color 0 = off, 1 = on (program get color from executor name)

blink = 0;  //blink run executor 0 = off, 1 = on (blink work only when colors mode is on)

page_flash = 0; // 0=off (normal switch pages), 1=on (klick and hold page button, when release button - back to page 1);


//------------------

Here, you can choose whether the controls automatically change color and whether the running executors should blink.

Below are the encoder attributes for User1 and User2, as well as the XY coordinates for mouse emulation. The current coordinates are calculated for a full HD resolution of 1920x1080.

Usage:

The first button on the left allows you to select the encoder mode.

If you choose Channel (default),
the encoders control our speed master 1 - 4.

In Mixer mode,
the encoders work as a mouse - touching them moves the cursor to XY, and rotating them controls a parameter. Unfortunately, this functionality is not good and can be frustrating, but I left it in case someone finds it useful.

In User1 mode,
the encoders control the attributes defined in the configuration below (you can, of course, change them).
By default, they are set to PAN, TILT, FOCUS, and ZOOM.

For User2, the attributes are:

RED, GREEN, BLUE, and WHITE.

The Patter buttons allow you to change the brightness of the keys.

The Browser button - B.O.

Encoder Select - Grand Master + toggle B.O.

The Grid buttons are toggles for ProgTime and ExecTime (they don't have feedback from the program, they simply switch on/off).

The Mute/Solo buttons (green dots) are used to select the PAGE (1 - 4). The controls display the current selection state.

The main RGB buttons are, of course, the upper part of B-Wing2 and B-Wing1.

They light up automatically.

A button is dimmed if the corresponding executor is empty.
Amber color indicates a saved executor.
Green color indicates a running executor.

If the colors option is enabled, the buttons will change color if the executor name is in the color database.

Change the executor name to Red, Orange, Sea Green, White, or Black, and you will see that the MIDI buttons automatically change color.

If the blink option is enabled, the running controls will blink.

1.0.75

STEP/ACCENT Button = HOLD to extra fuction

Rate1 function - Hold STEP/ACCENT & click [SNAP, TAP, OVERVIEW, or SHIFT] ro ewset Speed Master BPM

Delete executor function - Hold STEP/ACCENT + HOLD ALT & click executor (if leds on right side highlight - click STOP/Coundown button to confirm)

Store function - HOLD REC/LoopRec & click executor (if leds on right side highlight - confirm option [Merge] [Remove] [Overwrite] [Create second Cue])

StoreLook function - Hold STEP/ACCENT + Hold REC  - now u can release shift & click on executor (if leds on right side highlight - confirm option [Merge] [Remove] [Overwrite] [Create second Cue])


1.1.43
In this version, full support for all keys has been implemented.
The handling of the Learn and Rate1 functions has been changed to the bottom keys [SNAP, TAP, OVERVIEW, SHIFT].

Encoders in CHANNEL mode smoothly control the speed of Master 1-4.

The keys [SNAP, TAP, OVERVIEW, SHIFT] control the Learn function for the Speed Master.

The buttons can blink at the BPM frequency of the Speed Master - in this case, you should assign Speed Master 1-4 to Executors 716-713. If you assign them correctly, the keys will light up yellow.
If the BPM key is lit yellow, it means the BPM is lower or higher than 60 - the key will blink. If the Speed Master is in the STOP position, the key will light up red.

If you press and hold the ACCENT key and then click [SNAP, TAP, OVERVIEW, or SHIFT], the keys will reset the BPM (Rate1) for the corresponding Speed Master.
