# AKAI LPD8 MK2
Contains info and mods for LPD8 MK2.

There's a lot of information about the device available on the Internet. However, much of it is outdated or the links have expired. This is not intended to be an original source. It's a catalogue of the resources that got my MK2 up and running in 2026.

# Ableton
According to some random Reddit comment, MK1 works with Ableton out of the box. I haven't checked because I don't have the unit.

MK2 can send notes out of the box in Note mode. However, the knobs do not work - they simply send MIDI commands that are not assigned anywhere in Ableton by default. Of course, you can map the knobs via the MIDI key mapping inside the Ableton UI. But these knobs will always control the same device knob, no matter which track is armed.

## Fixing the knobs
To make LPD8 work as a control surface so that the knobs control whichever device/effect we've selected, we need to configure Ableton.

We have several options:
 - UserConfiguration.txt, a simple config that maps MIDI numbers to Ableton features.
 - [MIDIRemoteScripts](https://github.com/gluon/AbletonLive12_MIDIRemoteScripts), Python code that can handle the same with additional customizations.

If you only need to make the knobs work, #1 is the way to go. I initially went down the #2 rabbit hole, but only because I hadn't found #1.

### UserConfiguration.txt
Here you need to map MIDI codes to the features you want them to trigger.

The full process is described below, or you can download the "JR Akai LPD8" directory and put it into "/Users/<username>/Library/Preferences/Ableton/Live 12.3.1/User Remote Scripts" (you need to replace the username with your home directory and the version of Live).

To find which MIDI code is being triggered by a given knob or pad:
 - Add or select a MIDI track in Ableton.
 - Add "MIDI Monitor" MIDI effect. If you switch to Flow mode, you'll see the last few commands.
 - You'll see the codes when you use a knob/pad. (e.g. knob #1 is 70)

Create custom UserConfiguration.txt:
 - Open "/Users/<username>/Library/Preferences/Ableton/Live 12.3.1/User Remote Scripts" (you need to replace the username with your home directory and the version of Live).
 - This directory contains an example of UserConfiguration.txt.
 - Create a new directory, e.g. "JR Akai LPD8"
 - Copy the generic UserConfiguration.txt to "JR Akai LPD8/UserConfiguration.txt".

Assign the codes:
 - Open "JR Akai LPD8/UserConfiguration.txt"
 - Find "Encoder1" and assign the MIDI code you found in the previous step to it (e.g. knob1 = 70)
 - Assign the rest of the Encoders: Encoder2=71, Encoder3=72, ...

Restart Ableton. The knobs should control whichever device/effect is currently selected.

# Configure 2nd program on pads
LPD8 MK2 has 4 predefined banks, but they all seem to be the same, so you need to assign them first.

Each bank is a separate configuration where you can assign the device to send different MIDI codes, and then make these codes do different things in your DAW. You can quickly switch between banks using the Program button on LPD8, which opens up various opportunities and custom configurations.

We'll only assign the 2nd program to send different notes, but you can do a lot beyond that if you want:
 - Open "Akai Professional LPD8 Mk2 Program Editor"
 - You'll see that Program 1 uses codes for pads from 36 to 43.
 - Press Get on Program 2
 - And continue the enumeration: pad1=44, pad2=45, ...
 - Press Send on Program 2

Now you can switch between Program 1 and 2 on LPD8 and play different notes. This means, for example in Ableton, you can now trigger the upper 2 rows of samples in your Drum Rack.

# Pads Sensitivity Mod
LPD8 has pretty nice pads, however, they are not very sensitive out of the box. It took me a lot of vigor to trigger them, and sometimes the hits wouldn't register. It's disappointing that you need to mod a device after you just bought it, but there are not many alternative options, especially in this price range.

To address these issues, we can add a little bit of tape under the pads to make them trigger faster.

I haven't found a video for LPD8 MK2 specifically, but there are videos of MK1 and MPK devices that have exactly the same pads (and problems :)).

Below are 2 videos explaining how to apply the tape mod:
 - [LPD8 MK1](https://youtu.be/-5f14UJYKAc?si=d-CLebBGGYJzXwx6)
 - [MPK Mini](https://www.youtube.com/watch?v=bvn5VNtbZ2k)

Note: for LPD8 MK2 I was only able to apply 1 layer of tape. With 2 or 3 layers of tape, when I assembled the unit, some of the pads were always pressed (especially Pad5).

With 1 layer of tape, I'd still like to have a little bit more sensitivity so that I could just lightly tap on the pads, but it's much better than it used to be.

I also tried adding a second layer only in the middle, keeping 1 on the sides, like this:
1 2 ... 2 1
1 2 ... 2 1

However, this would still trigger some of the pads when assembled.

If you find a way to push the sensitivity further, let me know, and I'm happy to update the guide.