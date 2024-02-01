---
layout: post
title:  "Adventuring into 3D"
date:   2019-12-06 23:47:00 -0500
categories: noods
---

I've been a bit busy (and lazy), but this past month I've been working away on the 3D engine for NooDS when I find time. I was pretty intimidated at first, since I've never worked with 3D before, and I did pretty terrible in my linear algebra course... Luckily, it didn't end up being as difficult as I had expected.

The DS has two 3D-related engines: the geometry engine and the rendering engine. The geometry engine takes care of, well, geometry, and then it passes polygon information to the rendering engine for it to be drawn on the screen. I started with the geometry engine, which was tedious due to its crazy amount of registers, but not challenging. Writing the geometry engine was pretty similar to writing a CPU interpreter; commands, along with parameters, are passed to the geometry engine via the registers, and then it executes these commands to manipulate data such as vertices and matrices. Setting up the geometry engine and related interrupts was enough to get games to stop hanging when trying to use 3D, but of course, actually rendering things is far more interesting.

The first step for the rendering engine was to make sure that the geometry engine was actually producing sane data to be rendered. Before vertex data is passed to the rendering engine, it needs to be multiplied by a position matrix, which moves it around in the 3D space, and then by a projection matrix, which maps the 3D coordinates to a 2D plane for the player's viewing pleasure. The vertices then have to be normalized, and then stretched to fit the 256x192 resolution of one of the DS's screens. To make sure everything was working correctly, I wrote some quick code to simply draw dots at all of the vertices. Thanks to my poor linear algebra skills, I had a bit more trouble here than I should have, but I eventually got some promising results. I'll let my friend Dialga demonstrate:

![Dialga dots](/images/blog/2019-12-06/1.png)

Hey, that almost looks like actual graphics! It's worth noting that some vertices are still missing here, because I hadn't implemented all of the geometry engine's vertex commands yet. But regardless, things seemed to be working reasonably enough. Up next was drawing lines between the vertices. This didn't prove too difficult:

![Dialga lines](/images/blog/2019-12-06/2.png)

Looking good! Considering that I had no prior experience with this sort of thing, I was pretty happy with how far I had gotten. Of course, the next (and probably most important) step is actually filling in the polygons. I loosely followed an algorithm I found online for the triangles, but for the quads I had to be a bit more creative. After all, direct quad rendering is pretty uncommon, especially in modern GPUs. I also set up vertex color interpolation, and Z-buffering to prevent polygons in the back from being rendered in the front. Both of these were surprisingly simple, and I was able to figure them out on my own. Without lighting or textures, our friend Dialga is simply colored white now, so here are some more interesting examples to show off these new additions:

![Filled geometry](/images/blog/2019-12-06/3.png)

So now it's finally starting to look like NooDS has a proper 3D renderer. The next steps include texture support and lighting, as well as fixing the remaining geometry engine bugs. I showed off cases here where things are working properly, but a lot of games still have exploding vertices or even completely missing graphics. Something else I'd like to do is switch to 18-bit color precision. The DS's 2D engine uses 15-bit precision, so I've been sticking to that out of ease, but the 3D engine uses 18-bit precision. Surprisingly, the big DS emulators, NO$GBA and DeSmuME, only use 15-bit precision; I'd like NooDS to follow in the footsteps of melonDS in this regard. It'll make that choppy color interpolation look better, so why not?

In other news, I now have automatic builds set up for Linux, macOS, Windows, and Switch. Thanks to GitHub for its amazing new Actions feature, as well as Nspace on Discord for helping me get the macOS build working! You can find the latest builds by clicking the checkmark icon next to the most recent commit on GitHub. Well, that's all for now; the next time I post it'll probably be to show off a mostly usable 3D renderer. See you then!
