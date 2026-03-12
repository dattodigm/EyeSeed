https://learn.adafruit.com/monster-mask-augmented-eyes-toon-hat/overview

# MONSTER M4SK Toon Hat

Turning augmented reality on its head

![Image for user pburgess](https://secure.gravatar.com/avatar/7d19195b95e1d03ac4c6437aeaed9d15?s=100)

by [Phillip Burgess](https://learn.adafruit.com/u/pburgess)

published September 10, 2019, last edited March 08, 2024

posted in [Wearables](https://learn.adafruit.com/category/wearables) [LCDs & Displays](https://learn.adafruit.com/category/lcds-and-displays)/ [Graphic TFTs](https://learn.adafruit.com/category/graphic-tfts)

[ Save](https://learn.adafruit.com/guides/2712/favorites) [ Link Note](https://learn.adafruit.com/guides/2712/user_page_associations/new) [ Download](https://cdn-learn.adafruit.com/downloads/pdf/monster-mask-augmented-eyes-toon-hat.pdf)

## Overview

*Augmented reality* is a popular tech buzzword right now…the concept of of overlaying graphics or information over the world you see. In this project we turn that idea around…overlaying the graphics *on you!*

[![wearables_selfie.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/656/medium800/wearables_selfie.jpg?1568047545)](https://learn.adafruit.com/assets/80656)

We’ll use a mix of very new and very old tech. The Adafruit [**MONSTER M4SK**](https://www.adafruit.com/product/4343) board for the new tech…and for the old, [***Pepper’s ghost\***](https://en.wikipedia.org/wiki/Pepper's_ghost) is a 19th century parlor trick for making objects appear to float in space.

With some careful setup of lighting, positions and angles, and using a sheet of glass…not even special half-mirrored glass, just plain ol’ glass…real and reflected objects seem to occupy the same space. The reflection has a slight transparency to it, hence the “ghost” in the name.



Will this block my vision?



I wear glasses. Is that a problem?



My eye spacing isn’t average. Can this work for me?

[![wearables_Peppers_ghost_low_angle.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/655/medium800/wearables_Peppers_ghost_low_angle.jpg?1568046023)](https://learn.adafruit.com/assets/80655)

Image Credit: Wapcaplet at English Wikipedia. [CC BY-SA 3.0]

Some well-known applications of Pepper’s ghost include Disneyland’s *Haunted Mansion* ride and the “holograms” of a few high-profile concerts. The same principle is used in teleprompters and heads-up displays…you see a combination of transmitted and reflected light. That’s what we’re doing here. But rather than *you* seeing the reflected image, *everyone else* does…it’s invisible to the wearer and doesn’t block your view.

# Items You’ll Need

[![wearables_cheap-hats.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/536/medium640/wearables_cheap-hats.jpg?1567717915)](https://learn.adafruit.com/assets/80536)

[![wearables_cheap-hats.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/536/medium640/wearables_cheap-hats.jpg?1567717915)](https://learn.adafruit.com/assets/80536)

[![wearables_doomhat.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/542/medium640/wearables_doomhat.jpg?1567718872)](https://learn.adafruit.com/assets/80542)

**A hat!** The ideal hat for this project has a **level brim** (not sloped) with sufficient **firmness** to support the electronics (e.g. a flopsy wizard hat *wouldn’t* work). The local seasonal costume shop had several suitable options for $10 or less.

Pick something that suits a character or theme you’d like to portray. I had something specific in mind and got [this](https://www.amazon.com/gp/product/B07JZZNBFG)[ wide-brimmed fedora on Amazon](https://www.amazon.com/gp/product/B07JZZNBFG) for about $15 and replaced the hat band with some black ribbon. It’s not an *exact* match, but close enough for folks to make the connection.

[![wearables_m4skboard.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/543/medium640/wearables_m4skboard.jpg?1567719322)](https://learn.adafruit.com/assets/80543)

An [Adafruit **MONSTER M4SK** board](https://www.adafruit.com/product/4343).

*(But see the “No MONSTER M4SK?” section below…alternatives are possible!)*

[![wearables_screen-protector-package.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/544/medium640/wearables_screen-protector-package.jpg?1567719757)](https://learn.adafruit.com/assets/80544)

A **tempered glass** cell phone **screen protector**. I picked up [this 3-pack on Amazon](https://www.amazon.com/gp/product/B07TB62DWM) for the iPhone Xs because it was cheap and a good size…iPhone Xs Max works well also…there might be even better options with a smaller (or no) notch.

This is a fungible item you can get practically *anywhere* now (drugstores and so forth). Two important things to look for:

- **Tempered glass**, *not* the flimsy plastic sticker type!
- **Glossy**, *not* an anti-glare matte surface!

[![wearables_batt1.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/546/medium640/wearables_batt1.jpg?1567726247)](https://learn.adafruit.com/assets/80546)

[![wearables_batt1.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/546/medium640/wearables_batt1.jpg?1567726247)](https://learn.adafruit.com/assets/80546)

[![wearables_batt2.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/547/medium640/wearables_batt2.jpg?1567726252)](https://learn.adafruit.com/assets/80547)

[![wearables_batt3.jpg](https://cdn-learn.adafruit.com/assets/assets/000/080/548/medium640/wearables_batt3.jpg?1567726258)](https://learn.adafruit.com/assets/80548)

A **battery** of some sort. Perhaps a good capacity [Lithium Ion battery](https://www.adafruit.com/product/1781) if you’re planning on a long run time. This may require a [battery extension cable](https://www.adafruit.com/product/1131) depending where parts fit in the completed project.

You might already have or could use a [USB battery bank](https://www.adafruit.com/product/1959) if the placement of the MONSTER M4SK board allows adequate clearance for the connection. This approach may require a slim 90° micro-B USB cable that we don’t have…but [here’s something on Amazon](https://www.amazon.com/gp/product/B07CBTVR8G) that might work.

**Last item and NOT SOLD IN STORES:** *creativity* and a *willingness to improvise* with *whatever craft materials and tools you have access to.* That might be 3D printing, some Sugru or just some hot glue and a couple well-placed LEGO bricks…it need not be rocket science.

# Common Sense Please

This project involves a **DELICATE SHEET of GLASS, RIGHT OVER YOUR EYES**. Clearly this is *not* something to wear in a rowdy environment, or a setting where you might trip and fall on your face, and so forth. Please exercise good judgment. **You’ll have to take some accountability for your actions.**

You *can* use a piece of acrylic or Lexan as an alternative, but it produces a slightly blurry double-image. If going this route, you do *not* want half-mirrored plastic. Just plain clear. You need your own face to show through unobstructed.

# Best for Controlled Settings

The illusion works best with **subdued lighting**. Not complete darkness, as your own face is part of the act, and that requires some light. But not out in the sun or in bright interior light either, or the reflection is just washed out. It’s not the right effect for every venue.

It also helps if you are average height, and interacting eye-to-eye. The gag is hidden under the brim of a hat…so if you’re tall, or if you’re interacting with kids or seated people looking up at you, the illusion falls apart.

# No MONSTER M4SK? No problem!

The MONSTER M4SK is an all-in-one board, no soldering, and easy to customize with new graphics. But the illusion we present here is just as effective with *any* illuminated type of display…perhaps you’ve built our [Teensy Eyes](https://learn.adafruit.com/animated-electronic-eyes-using-teensy-3-1) or [Pi Eyes](https://learn.adafruit.com/animated-snake-eyes-bonnet-for-raspberry-pi) in the past…or any other OLED or backlit LCD device. Or a smartphone display (if you can provide your own software or graphics). [Even LED matrices if you want a low-res robot effect](https://learn.adafruit.com/animating-multiple-led-backpacks).

The key is that **black pixels are transparent**, showing through to your face, while **lit pixels appear progressively more opaque**.

It could even work with a couple of “LED throwies” if you just want a glowing eyes effect (*Dune,* werewolf, etc.)