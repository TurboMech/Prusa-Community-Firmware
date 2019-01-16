# 3.5.1 firmware, 7x7 mesh bed leveling, and heatbed 'preheat error' bug fix

### TL;DR: 

This firmware is completely stock except for addition of the 7x7 mesh bed leveling and changes to temperature files to fix the heatbed 'preheat error' bug that arose in 3.5.1.  Still requires g-code changes for 7x7 mesh bed leveling, recommend running a PID tune on the heatbed afterwards as well.  

There is a version for MK3, MK2.5 (RAMBo 1.0 and 1.3 please use the right one for your PCB).  MK2S is not applicable. All sources linked below.

### Long version:  

After upgrading to 3.5.1 with (or without) mesh bed leveling a lot of users have been encountering preheat errors when heating the heatbed above 90C.  This occurred either before printing (heating stage) or while printing when the bed temperature was increased after the first layer.  I encountered this while trying to heat the bed to 140C (modified firmware - not included in the attached versions) even after two successful PID tunes at 140C.

Prusa changed some settings within the temperature files (temperature.h and temperature.cpp) of the firmware from 3.4.1/3.4.2 to 3.5.0/3.5.1.  You can read more about the 'preheat error' bug here:  https://bit.ly/2FuFFQr  I simply reverted the heatbed (only) PID and preheat error settings to how they were in the 3.4.1 version in the temperature.h and temperature.cpp files. 

This firmware also includes the 7x7 mesh bed leveling as posted by Chris Warkocki (see his post here: https://bit.ly/2DdJRlr), which was originally developed by github users stahlfabrik and mionut.  Github link: https://bit.ly/2SXsTNE . This version probes each point 3 times, I prefer this one for redundancy purposes in case a bad measurement was taken (unlikely).  I won't be making a 1 probe point per version, so if the extra 5 seconds per point is bothersome please don't use these versions. 

I was unable to secure a beta tester for MK3 so please have a firmware .hex for backup in case something doesn't work properly.  MK2.5 (RAMBo 1.3) was tested by myself and Fedor Pikus is currently testing it as he ran into the 'preheat error' bug on 3.5.1. 

Happy printing!
