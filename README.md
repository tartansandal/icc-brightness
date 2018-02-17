# ICC Brightness

###Control OLED display brightness by applying ICC color profiles.


## Introduction

This tool is a work-around for displays whose brightness contol is not
supported by the linux kernel. It preforms well on OLED displays,
since these have very dark black point and their power consumption is
relative to the brightness of the viewed content.

This tool can be used on an LCD display, but in that case you really want
to control the brightness directly using the display backlight.

Specifically icc-brightness was developed for the
Lenovo ThinkPad X1 Yoga OLED display.


## Build and install

The build requires the liblcms2 development package:
```
$ sudo apt install liblcms2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  liblcms2-dev
...
```

Build and run the tool to see all options:
```
$ make
gcc -W -Wall icc-brightness-gen.c -l lcms2 -o icc-brightness-gen
$ ./icc-brightness
Control OLED display brightness by applying ICC color profiles.
  
icc-brightness brightness max-brightness - set brightness manually
icc-brightness apply - apply brightness from system setting
icc-brightness watch - continuously update to system setting
```

You can install to auto-start a daemon when logging-in to a Gnome session:
```
$ sudo make install
cp icc-brightness-gen /usr/local/bin/
cp icc-brightness /usr/local/bin/
cp icc-brightness.desktop /usr/share/gnome/autostart/
```

The daemon will start on your next login.
You can change brightness using the brightness key or any other method
that controls the display "backlight".