+++
date = "2013-01-26T09:32:45-04:00"
draft = false
title = "Brightness issue in Linux mint 14"
tags = ["hack", "linux mint", "terminal", "ubuntu"]
+++
    
I recently installed linux mint 14 (Nadia)   in my office laptop (HP Notebook 450 ). after installation when I booted into the os , the screen brightness was set very very low which I was able to adjust using the brightness function key.  Later I had the same problem when Ubuntu 12.10  was installed on the same laptop.  So here is a permanent fix for the issue.

* Current brightness value  is stored in  `/sys/class/backlight/acpi_video0/brightness`  file.
* Maximum brightness value is  stored in  `/sys/class/backlight/acpi_video0/max_brightness` file.
* Add the following line to `/etc/rc.local` init script. ( If you want know what this file is, check this [stackexchange question](https://unix.stackexchange.com/questions/49626/purpose-and-typical-usage-of-etc-rc-local))

```
cat /sys/class/backlight/acpi_video0/max_brightness > /sys/class/backlight/acpi_video0/brightness 
```