---
layout: post
title:  "Logitech Harmony Hub - Inital Thoughts"
date:   2016-09-24 22:41:00 -0400
categories: posts
---
# myHarmony Remote and Hub

## Over-all Goals

### Short-term:

- Remove Clutter
Current "controllers" on my workstation:
	- Keyboard
		- Connected to PC via Bluetooth
	- Mouse
		- Connected to PC via Bluetooth
	- Television Remote
		- Infared
	- Sound System Remote
		- Infared Remote
	- Amazon Fire TV Remote
		- Connects to Fire TV via Bluetooth
	- LED Strip Behind Television
	- LED Lights on Shelf
- cool functionality
	- Single-button access to all devices
	- Integration with things like IFTTT for future functionality
- some level of automation
	- Using this as a hub not only for media, but also for lighting and air conditionting.

### Long-term:

- integration with more robust automation systems
- value and longetivity with or without future additions.

## How this product helps toward those goals

- I can't get rid of the keyboard or mouse, but for the rest, I'd much rather have a single remote. Nothing revolutionary about a universal remote, but the more home automation stuff I can start squeezing in, hopefully I'll be able to expand on it in the future.

## Limitations of this product
- General Activity Structure for the Harmony Software
	- scope, non-compatibility with mutiple actions
	- shut downs

### Structure of an "Activity"
First of all, activities are primary used by the big three buttons on the top of the remote. I hit the button, it fires off an activity like "watch FireTV" and here's an example of what my Activity might look like under-the hood.

| Calling an "Activity"| Ending the Activity|
| --- | --- |
| Ensure TV is powered on.| Ensure TV is powered off.|
| Ensure TV input selected is HDMI1 | Ensure Sound Equipment is powered off. |
| Ensure Sound Equipment is powered on | Ensure Light 1 is powered off. |
| Ensure Sound Equipment input "digital input" is selected | Ensure Light 2 is powered off. |
| Power on Light 1 | Ensure Air Conditioner is powered off. |
| Power on Light 2 | |
| Turn on Air Conditioner | |

how functions don't play well with each other and exit sequences.

Noticing a basic problem?
For such a simple task, why did I involve so much initially?

- Device Limitations
- Reserved buttons
- Needs IFTTT hook to do anything with alexa

## Overall thoughts
## Next Steps
The obvious next step for me seems to be amazon echo or dot. The big drawback is that I'm trying to invest in amazon's walled-garden, but the devices don't really interact with each other in the way I'm looking for. 
Ideally, I'd be able to tell the echo "play season one of Deadwood on HBO" and it would know to convey the command to the fireTV. In reality, they don't really communicate it seems, sort of killing the single interface for the whole home.
The exception is that I can tie specific commands to harmony actions through IFTTT, so I'd have to deal with the above-detailed limitations of the activity structure as well as learning to do exact commands like "trigger turn on TV" or "trigger turn off lights". Essentially, a non-intuitive and less functional version of my physical remote.