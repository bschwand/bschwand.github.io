---
layout: single
title:  "Revive a 30-min rebooting asus laptop"
date:   2024-06-03 11:28:00 +0200
categories: PC
tags: PC BIOS ME
header:
  teaser: "assets/images/IMG_20240521_133716.jpg"
---

I recovered an asus laptop for free (Asus n550JK). After adding an SSD
and maxing the RAM, it makes for a very usable Laptop. Not a speed
demon, but with the integrated Nvidia m850 GPU, it is perfectly
capable of running a few games quite well.

Unfortunately, it soon became apparent that it had some kind of
problem, as it would suddenly shutdown. I mean, turn off at once, no
warning.  I initially thought it was some thermal issue and thus
completely took it apart, cleaned and replaced the thermal paste on
CPU and GPU.  To no avail, it still would shutdown after a while.

To tell a long story short, I became suspiscious once I noticed it
would turn off after 30 minutes, on the nose, no matter the gpu/cpu
load. idle or running full GPU benchmark... same 30 minutes runtime.

After a lot of googleing, I found this [me
cleaner](https://github.com/corna/me_cleaner) which described the
symptoms I was seeing as a side effect of F***ed-up intel Management
Engine firmware.  There it is !  Then later I found this forum
[badcaps](https://www.badcaps.net/forum/troubleshooting-hardware-devices-and-electronics-theory/troubleshooting-laptops-tablets-and-mobile-devices/bios-requests-only/91555-bios-guides-methods-resources-and-tools?t=103526)

Which eventually lead me to the absolutely excellent
[winraid](https://winraid.level1techs.com/t/guide-clean-dumped-intel-engine-cs-me-cs-txe-regions-with-data-initialization/31277)

Now, it looked like the guide and software on winraid forum was more
up to date and actually recommended to not use me_cleaner as it did
not process some elements of the original bios and could lead to
trouble.

Anyway, following the massive guide I decided to extract the BIOS from
the laptop SPI flash chip. Which worked, the chip was recognized and a
nice 8MB image
extracted. Unfortunately... [MEAnalyzer](https://github.com/platomav/MEAnalyzer)
did not find the images I extracted to be valid. That was very weird
as successive images would be byte identical, and generally when there
is some issue with reading the chip in-circuit, the images would get
corrupted or give inconsistent result.  Eventually I threw my arms in
the air and decided to desolder the damn chip to make sure nothing
interfered with it. Which of course lead to side project number 2:
to make a sop-8 desoldering tip. I do have hot air rework tools, however
to do this properly and without overheating, it would be better to
pull the motherboard out so it can be pre-heated, and all chips around
the desoldering area should be protected with kapton or foil. Seems a
special soldering tip would be a lot less work and faster.

And here it is, just some copper sheet cut and rolled around my soldering iron tip

![desoldering tip](/assets/images/IMG_20240610_220019.jpg)

Thanks to this, desoldering took 2 seconds. And then, finally the bios
images extracted were valid !

Now following the guides above it was a breeze to modify the bios
image. Although there was one little step I had to do differently. The
instructions tell you to keep the flash software open, replace one
file, then go on and generate the bios image. That did not work for
me. Instead, at the point where I would be replacing the file, I had
to save into an XML file, quit the software, replace the image
(region) file, restart the software and load the saved xml file. Then
the BIOS image would be generated without error. YMMV.

Last step: reprogram the flash chip, and resolder. With that done,
this laptop has now stopped turning off and runs perfectly fine for
however long I want.

More trash to gold ! ok well...