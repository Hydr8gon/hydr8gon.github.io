---
layout: post
title:  "Slowly but Surely"
date:   2019-05-31 21:16:00 -0500
categories: noods
---

Well, we're getting a bit closer. I haven't done a whole lot since last time (been a bit tired out from the first three weeks) but I've been trying to do a little bit every day to keep progress steady. 

Most importantly, I've decided to rename the project! The new name is NooDS, which can be pronounced as "new DS" or "nudes", whichever you prefer. I swear I'm not naming it after pornography though! Actually, I do have a reason for calling it this.

![Noodle](/images/blog/2019-05-31/1.png)

This is Noodle, my newest friendo! I got her less than a week ago. I know not everyone is a huge fan of snakes, but I swear to you she is the sweetest little girl you'll ever meet. Now, the name might still be subject to change; I was also considering NooDleS, but I'll leave it as NooDS for now.

Regarding progress, the most noteworthy addition from last time is interrupts, which are extremely important; most notably they allow programs to wait for V-blank, which normally happens on each frame of a program to implement V-sync. The interrupts on their own were pretty easy to implement because they're exceptions, and I've already implemented software exceptions, so it was more or less a copy paste from that. But of course, there were some unrelated bugs that were making other things break when I first tried to add them. After I got everything working though, there were some fun results!

![ARMWrestler](/images/blog/2019-05-31/2.png)

This is ARMWrestler, a CPU test program for the DS. As you can see, it's showing a few problems that I need to look into. But the program works! And it certainly shows some more interesting results than the stuff I showed last time. It uses the basic VRAM display mode, which surprised me. I guess they did that to make it easy to run on new emulators, which is nice.

At this point it seemed like other homebrews might be booting, but unable to display anything because they're using the layer/object-based display mode, which I have yet to implement. It's a fair bit more complicated than simply drawing raw color values, but I've started looking into it and planning my implementation. To test my theory that things are running, I hacked some display code together specifically to run [Mx5](https://gamebrew.org/wiki/Mx5), a homebrew demo I found that looked simple enough. It actually uses a background layer as a simple raw bitmap display much like the VRAM display mode, so it was easy to get working.

![Mx5](/images/blog/2019-05-31/3.png)

Lo and behold, it really was running behind that blank screen! Sure, it's another pattern, but it's a fairly complex pattern. It even looks 3D! Of course, it isn't, and actual 3D support is still pretty far off. But this means that once I get some actual work done on the main display mode, a bunch of other homebrew could potentially start working as well.

Oh, and I've also got a Windows build working, because before it was just Linux. At some point I plan on attaching test builds to these progress updates for some extra fun. Of course, you can always compile your own builds from the source on [GitHub](https://github.com/Hydr8gon/NooDS) as well.

Well, that's all I have for now. Next time we'll definitely start seeing some more traditional homebrew working, like games and such. Oh, and melonDS 0.8 was just released, so if you're following my Switch port of that I should have the update ready soon. Though of course, eventually NooDS will overtake melonDS as the superior emulator and its Switch port will be obsolete >:)
