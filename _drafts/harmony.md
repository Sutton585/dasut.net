---
layout: post
title:  "Logitech Harmony Hub - Inital Thoughts"
date:   2016-09-24 22:41:00 -0400
categories: posts
---

- Table of Contents
{:toc}

## Goals

### Short-term:

- Remove Clutter
Current "controllers" on my workstation:
	- Keyboard
		- Connected to PC via Bluetooth
	- Mouse
		- Connected to PC via Bluetooth
	- Television Remote
		- Infrared
	- Sound System Remote
		- Infrared Remote
	- Amazon Fire TV Remote
		- Connects to Fire TV via Bluetooth
	- LED Strip Behind Television
	- LED Lights on Shelf
- cool functionality
	- Single-button access to all devices
	- Integration with things like IFTTT for future functionality
- some level of automation
	- Using this as a hub not only for media, but also for lighting and air conditioning.

### Long-term:

- integration with more robust automation systems
- value and longevity with or without future additions.

## How this product helps toward those goals

I can't get rid of the keyboard or mouse, but for the rest, I'd much rather have a single remote. Nothing revolutionary about a universal remote, but the more home automation stuff I can start squeezing in, hopefully I'll be able to expand on it in the future.

### Structure of an "Activity"
First of all, activities are primary used by the big three buttons on the top of the remote. I hit the button, it fires off an activity like "watch FireTV" and here's an example of what my Activity might look like under-the hood.

Calling the "Activity"
- Ensure TV is powered on
- Ensure TV input selected is HDMI1 
- Ensure Sound Equipment is powered on 
- Ensure Sound Equipment input "digital input" is selected 
- Power on Light 1 
- Power on Light 2 

Ending the Activity
- Ensure TV is powered off
- Ensure Sound Equipment is powered off. 
- Ensure Light 1 is powered off. 
- Ensure Light 2 is powered off. 
- Ensure Air Conditioner is powered off. 

### How the exit sequences cause issues
One you've established which devices are involved with an activity, it asks some basic questions about what you need them to do (for example "which input source do you want your TV to go to?"). The "activity" then makes a bunch of assumptions, and most of them are not editable. The biggest of which is the exit sequence, I'll explain why.

Let's say you have an activity "Turn off the lights" and an activity "Watch TV". They involve exactly the devices you would imagine they involve. Here's how the scenario plays out.

- Press button for "Watch TV"
	- The system goes through it's whole sequence, turns on the TV, makes sure the correct input is selected, et cetera.
- Press the button for "Turn off the lights"
	- The system realizes it's time to end the first activity so it can start the second activity.
		- Your TV shuts off
		- Your sound system turns off
	- Now it goes through it's sequence for "Turn off the lights"

See the problem? Those non-editable exit functions play havoc with intuitively building tasks or "activities". Also, the main buttons on the top of the remote only exist to launch activities, so you are forced into that paradigm.

### Solutions?

So how do I get around this huge limitation? Well, at first glance the problem is just creating an inconvenience, but is not a show-stopper. Maybe you're already coming up with a solution that involves creating multiple activities, each one with a unique permutation of which devices you need at any given time. Activities like 

- "turn on the lights, and turn on the TV"
- "turn on the TV but not the lights"
- "turn on the TV and the Air Conditioner, but no lights"
- "Turn on Just the Air conditioner and TV"

It's already getting out of control. Remember, you really only have those three buttons to launch the activities from anyway. I suppose you could customize it so that each number on the remote corresponded to a different permutation. Then you're juggling all that in your head. Yikes.

The real solution (or at least the best option I've seen so far) is to get around the activity limitations by convincing your device that everything is a single device. Hold on, we're going down a weird rabbit hole now.

### Harmony's IR "learning"

One of the great features on this device is how it's able to be "taught" commands from any Infrared remote control, and then replicate those commands from it's IR blaster base. This is what enabled me to teach it the commands for my air conditioner and LED lights. However, this can be exploited somewhat.

I've "taught" my harmony device that there are a few actions my TV can do that it hasn't listed. I then teach it commands like "power on LED" by telling harmony that the TV will execute this action when you send this command. Then I point my IR remote for the LEDs at it and hit power. So, from then on out, harmony thinks it's sending the TV a signal, but really it's just using the signal from the LED controller. I can repeat this with each IR controller. It now thinks that my TV has a command "turn on air conditioner".

This enables me to limit my number of activities to about 2 (Watch TV, Switch to PC), then once I've done one of those two actions, I manually map buttons on the remote to actions like:

- "turn on LED 1"
- "turn off LED 1"
- "turn on/off LED 2" (because this one doesn't have dedicated "on" and "off" buttons, just one "power" button)
- "Turn on/off AC"
- "Turn up AC"
- "Turn Down AC"

### Limitations with current solution

Alright, so now our remote can do everything we need, right? Well, there are still some strong limitations.

- Commands only work within activities
- The "Home Control" section of buttons are not usable unless you've added specific branded devices.
- The only way to integrate Alexa, is via IFTTT which can only support activities, not individual commands.


### Commands only work within activities

Now that our system has two activities (TV, PC) and we've manually programmed buttons on either of these activities to do the same thing, what happens when I don't feel like turning on the TV, but I still want to play with the air conditioner?

No dice. Until you've fired off an activity, there's no context for the rest of the buttons, you can't just program them to ALWAYS do a specific thing, regardless of activity.

There's one exception to this, as far as I'm aware. The "Home Control" buttons on the remote. These are intended to do things like toggle lights, adjust temperature on air conditioners, that sort of thing. The buttons are intuitively placed, and offer a lot of great functionality. So why don't we just use those?

### The "Home Control" buttons only control very specific branded devices

Phillips Hue devices, Nest brand thermostats, and certain other devices are controllable with these buttons. These buttons are not able to be used for ANYTHING else. Especially if it's just something that uses Infrared commands.

I don't have any of those branded devices, so that button real estate and great functionality is just dead to me. Nothing I can do. What a waste.

### How this limits my planned integration with Alexa/Echo devices

The primary concern here is that Alexa commands can fire off an activity and nothing else. This means that we'd have to return to the solution of having a activity programmed for each permutation of device combinations. Then we'd have to give each activity a specific code-word we'd have to remember for the purposes of telling the echo what to do.

Another concern is that even when we configure to do this, we do it through an abstraction. We have to utilize the program IFTTT (previously called "if this, then that") which introduces a bit of lag as it has to query yet another online resource for a command.

Even assuming we're okay with all these tradeoffs, there's another big one in the way Alexa works in general. You aren't going to be able to have any commands in an intuitive or conversational way. You have to structure commands like this:

"Alexa, trigger turn on TV"

This is not customizable, it needs to here these words to do these actions (in parenthesis is how it's interpreted):

- "Alexa" (wake up I'm about to tell you to do something)
	- not flexible, you can either have it respond to Alexa or Echo. This would be a great thing to be able to customize. I'd love to be able to say "Computer, play Sopranos" and then just relax and watch some TV.
- "trigger" (we're using a IFTTT command)
	- not flexible, "trigger" is the required word to let it know you're using IFTTT.
- "turn on TV" (find the activity IFTTT associated with this phrase and fire it, or don't, no need to alert user)
	- semi-flexible, it's really just whatever you named the action in IFTTT.

## Overall thoughts
## Next Steps
The obvious next step for me seems to be amazon echo or dot. The big drawback is that I'm trying to invest in amazon's walled-garden, but the devices don't really interact with each other in the way I'm looking for. 
Ideally, I'd be able to tell the echo "play season one of Deadwood on HBO" and it would know to convey the command to the fireTV. In reality, they don't really communicate it seems, sort of killing the single interface for the whole home.
The exception is that I can tie specific commands to harmony actions through IFTTT, so I'd have to deal with the above-detailed limitations of the activity structure as well as learning to do exact commands like "trigger turn on TV" or "trigger turn off lights". Essentially, a non-intuitive and less functional version of my physical remote.