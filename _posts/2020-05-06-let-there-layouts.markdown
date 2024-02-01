---
layout: post
title:  "Let There be Layouts"
date:   2020-05-06 21:11:00 -0500
categories: noods
---

Whew, looks like I made it in time for this month's progress post! As I mentioned in the last one, I was busy with exams this past month. I was also very "busy" with Animal Crossing... but I did manage to get some work done on NooDS! Let's take a look, shall we?

The biggest addition (as you may have guessed from the title) is screen layouts. Screen layouts are nothing new for DS emulators; in fact, some might even consider them essential. There are a few things that bugged me about the layout options in other emulators though, so I tried to design mine to be better. My personal favorite is the integer scaling option; I like the look of unfiltered pixels, but they just look so bad when they're not scaled properly! The integer scaling option works with all of the other options, including enlarging one screen or the other. Speaking of, I worked a little magic there as well. After scaling the large screen to the maximum size, the small screen is scaled to fill the remaining space, as opposed to being locked to a 1:1 scale. I find this works really well when paired with integer scaling and the horizontal screen arrangement. Finally, there's the screen gap. Instead of having fixed pixel values for the gap size, it scales with the screens to keep the ratio intact. In the case where the screens are different sizes, the gap will be based on an average of the two scales. And of course there's rotation, although there wasn't much I could revolutionize in that department. The possibilities are (not really) endless, but here are a few fun things you can try:

![Best layout](/images/blog/2020-05-06/1.png)

![Rotation](/images/blog/2020-05-06/2.png)

![Big gap](/images/blog/2020-05-06/3.png)

And, of course, all of these options are available on the Switch build as well. On the topic of the Switch, something interesting happened there. After making a seemingly innocent change to reduce memory usage in the GPU code, the Switch build magically got a significant speed boost! I can only assume that this has something to do with the CPU cache; the improved code must be able to fit within the cache, while the old code couldn't. It may still not be able to run much more than Yoshi's Island DS at full speed, but it's starting to get speeds comparable to my port of melonDS on the Switch, which gives me hope that NooDS will be a worthy competitor once I write an ARM64 JIT for it.

Before I wrap this up, there is one last thing that I think is worth mentioning. The 3D renderer got some improvements to its interpolation and coordinate scaling, resulting in more accurate output. It's by no means pixel perfect yet, but it's a step in the right direction! The below comparison shows both of the improvements fairly well. On the left is before, and on the right is after. Most notably, the jaggy artifact on the road caused by the old interpolation formula is gone, and the player sprite is scaled correctly and is no longer missing any pixels. These improvements can be seen in most 3D games, to varying degrees.

![3D improvements](/images/blog/2020-05-06/4.png)

And that's all I have to show for this month; now we're at the part where I list the things I want to do but probably won't have done before the next post. I did attempt a WiFi stub, but I don't have it working enough to pass any initialization yet. In the meantime, I added a bit of a hack that stalls the initialization, giving you enough time to select your save in the gen 4 Pokémon games, if you're quick enough. It's nice to have those games easily accessible for testing now, but a proper stub is definitely still on the to-do list. Anything else mentioned in the last post that I haven't got to yet is also still on the table. School's out now, and my job status is uncertain, so I may find myself with more time to work on NooDS if I can keep my motivation up. I guess there's nothing left but to wait and see where this month takes us. See you next time!
