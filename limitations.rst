.. _limitations:

Appendix B. Limitations
=======================

1) On some special monitors, some modes may cause screen garbage
   and other display issue. This is probably due to the timing passed by Xorg
   that cannot work well with the monitor. In this case, please delete the "#"
   before the corresponding Modeline in section "Monitor" of file "xorg.conf".
   For example, for mode "1680x1050", we can enable its modeline::

     Modeline "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 10591089 -hsync +vsync

   then switch to this mode.
     
2) Support smooth video playback of 720P on 1280x1024 display mode.

3) If making action to the playing video or moving mouse over the video,
   this video will not sound and be blocked.

4) XVID video will sometimes show garbage.

5) Some VC1 video files may become static when seek or having audio
   playback abnormal issue, it can be reproduced on x86 platform with SW
   decoder (Totem). It is demuxer issue.

6) If I frame is too long, some video files may pause for a few seconds
   after seek and resume, since demuxer could not locate I frame.

7) It is slow when switching between window mode and fullscreen mode.

8) There is no PWM frequency control. In other words, the backlight
brightness can’t be modified.
