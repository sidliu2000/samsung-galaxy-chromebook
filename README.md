# samsung-galaxy-chromebook

Samsung Galaxy Chromebook is a great performmance laptop, comparable to other capable Windows laptops. The specs are impressive. Screen is gorgeous, performance is top notch. Pen is a delight to use. That's why I couldn't resist the bargain when I saw Best Buy had a practically new one for sale for $450 (just the laptop and charger) in March, 2021. I wish that the battery would last longer and hard drive is bigger, given my intention of using this as my Linux development laptop. 

1) <b>Specifications</b>

Processor / Chipset: Intel® Core™ i5-10210U Processor(1.60 GHz up to 4.20 GHz 6 MB L3 Cache)<br>
Color: Mercury Gray<br>
Display: 13.3" UHD AMOLED Display (3840 x 2160) with Touch Screen Panel, 360 degree rotating display<br>
Memory: 8 GB LPDDR3 Memory (On BD 8 GB)<br>
Hard Drive: 256 GB SSD NVME 2230<br>
Graphics: Intel® UHD Graphics<br>
Sound: Stereo Speakers ( 2 W x 2 ), Internal Digital Dual Array Mic + Mono Mic, 1 Headphone out/Mic-in Combo<br>
Camera: 1M Camera (front), 8M Camera (on keyboard deck)<br>
Wireless: Wi-Fi 6 (Gig+), 802.11 ax 2x2, Comet Lake PCH-LP CNVi WiFi, Bluetooth<br>
Touch Pad: Island-type keyboard (Backlit keyboard), PEN<br>
Spill Resistant:3cc<br>
Ports: 2 USB-C® [up to 5Gbps*, 4K display out with optional adapter, Charging] USB3.0, UFS & MicroSD Combo<br>
Battery: 4Cell/Li-ion 6390mAh, 8hrs<br>
Power: 49.2 Wh (Typical), 65 W / 45 W USB-C® Adapter*<br>
Security & Safety: TPM, FingerPrint Reader<br>
Certification: ENERGY STAR® Certified<br>
Included in Box Accessories: Adapter, Pen Tip/Tweezer, Quick Start Guide, Warranty Card<br>
Dimensions & Weight: (L x W x H) 11.92" x 8.0" x 0.39", Weight: 2.29<br>
Warranty: 1 Year<br>

2) <b>Running Linux</b>

I prefer running Linux directly, using Crouton, after comparing built-in Linux Developer Environment and using Chromebrew.

<li>Built-in Linux Developer Environment is containerized VM, although it is quite usable, but it is a virtual machine environment nonetheless. Performance penalty will incur. 

<li>Chromebrew (https://github.com/skycocker/chromebrew) is a chromebook package manager much like apt or dnf. In general, I feel that the disadvantage of size and complexity of the tool outweights its benefits. It works well for the situations where you need a couple of must-have tools.

<li>Crouton (https://github.com/dnschneid/crouton) is a chroot environment, much closer to native Chromeos. The performance difference is almost negligible. I also like the fact that it is somewhat isolated from the chromeos. In addition to xiwi which provides a X11 on chromeos, sommelier (https://github.com/jcdang/chromeos-ubuntu-sommelier) is available as well. Sommelier solution provides a more integrated solution and allows running Linux apps seamlessly.

I run the following crouton to install Debian Bullseye:
      crouton -r bullseye -t x11,xorg,xiwi,cli-extra,audio,keyboard,extension,xfce
  
3) <b>SSD Upgrade</b>

I got a Western Digital 1TB NVME 2230 SSD, after seeing this video https://www.youtube.com/watch?v=QAyFRj-gORI.

Unfortunately, after running Recovery and messing around with it, the laptop gives "Chrome OS is missing or damaged" and unable to proceed further. I tried to install different operating systems such as Windows 10 and Ubuntu 21.04 on it on a different laptop, with success. I think it might be due to the WD 1TB uses 4096 physical sector size, causing trouble for Chromeos UEFI booting. This might be in the firmware or something. Just my wild guess.
