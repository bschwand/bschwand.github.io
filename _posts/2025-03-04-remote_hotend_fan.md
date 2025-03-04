---
layout: single
title:  "Remote hotend fan, part 2"
date:   2025-02-02 12:57:00 +0200
categories: 3D-print
tags: delta remote_hotend_fan
header:
  teaser: "/assets/images/brushless_fan/fan_motor_shroud.png"
classes: wide
---
In part one of my creating a [remote hotend fan system](https://blog.tinkerbox.org/3d-print/PWM_to_0-5VDC/), I made an interface to control a brushless high-power hairdryer fan with a normal PWM fan output. Next step was to physically install that fan and hook it to the hotend.

First part is to make some kind of holder for the fan, which can be installed at the top of the printer.
![brushless fan enclosure](/assets/images/brushless_fan/fan_motor_shroud.png)

As you can see, the interface board installs directly on the shroud. The fan shroud itself is installed in a board affixed on the top of the printer.

Next, we need some way to direct the airflow onto the hotend.

My initial idea was to make some kind of semi-rigid structure that I would wrap with fabric. The fabric I chose is a kind that is used to make umbrellas and tents: very light, thin, water and air proof.

Here is what I tried:
- a spring-like structure made from PLA filament. This worked more or less but it has issues, it does not keep its shape well, and it is very difficult to insert into a fabric tube or sock. When stretching it, it also rotates and kinks easily, leading to airflow block.

- I made some kind of mesh-like structure by cutting plastic sheet and rolling it up (similar to expanded steel mesh). That was not rigid enough and also was very bad for aiflow. I could not affix the fabric properly either.

I think ideally, some highly flexible mesh could work but it would need a variable diameter and maybe highly rigid and flexible material, like carbon fiber. I have an idea of printing directly such mesh on a mandrel (cylinder or cone) but to do that I would need an additional rotating axis on my 3D printer.
Another idea is to print a mandrel with guides for a string, then essentially knitting carbon fiber on it and wetting it with epoxy, 

In the end, I made a kind of elastic "sock", by sewing elastic thread on the fabric.

![installed fan sock](/assets/images/brushless_fan/IMG_20250214_152853.jpg)

Not really ideal as the sock crumples a lot, but the fan power is so great that it's really not a problem.

I'll revisit that sock once I add a rotary axis to the printer so that I can print tubes and cones horizontally to directly print a support meash. Alternatively, if using a mandrel and winding carbon fiber on it, this could be printed vertically so I might try this next. Not urgent though.
Next thing i will do, is to remove the print part cooling fan and instead use a shroud to modulate and redirect the flow of air coming across the hotend, towards the part being printed.

{% include video id="b32DKuH9-Ho" provider="youtube" %}
