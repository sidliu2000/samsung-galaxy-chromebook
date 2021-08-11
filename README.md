# Samsung Galaxy Chromebook

This simple page documents my experience with Samsung Galaxy Chromebook. Samsung Galaxy Chromebook is a great performmance laptop, comparable to other capable Windows laptops. The specs are impressive (comparing to chromebooks, slightly above average comparing to other Windows laptops). Screen is gorgeous, performance is top notch, and the included pen is a delight to use. That's why I couldn't resist the bargain when I saw Best Buy had a practically new one for sale for $450 (just the laptop and charger) in March, 2021. I wish that the battery would last longer and hard drive is bigger, given my intention of using this as my Linux development laptop. Overall, much better deal comparing to the Samsung Galaxy Chromebook 2 (botched).

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

<ol>
<li>Built-in <b>Linux Developer Environment</b> is a containerized VM. Although it is quite usable, it is a virtual machine environment. Performance penalty will incur. There are still some things need to be ironed out, such as missing icons. </li>

<li><b>Chromebrew</b> (https://github.com/skycocker/chromebrew) is a chromebook package manager much like apt or dnf. In general, I feel that the disadvantage of size and complexity of the tool outweights its benefits. It works well for the situations where you need a couple of must-have tools.</li>

<li><b>Crouton</b> (https://github.com/dnschneid/crouton) is a chroot environment, much closer to native Chromeos. The performance difference is almost negligible. I also like the fact that it is somewhat isolated from the chromeos. In addition to xiwi which provides a X11 on chromeos, sommelier (https://github.com/jcdang/chromeos-ubuntu-sommelier) is available as well. Sommelier solution provides a more integrated solution and allows running Linux X11 and Xwayland apps seamlessly.</li>

</ol>

I run the following crouton to install Debian Bullseye:

      crouton -r bullseye -t x11,xorg,xiwi,cli-extra,audio,keyboard,extension,xfce
      
To be continued.

3) <b>Running Windows VM</b>

<img src="chromebook-windows.png" alt="Chromebook Windows 11">

Why? Firstly, because I can! :) Secondly, it's for those occasions that Windows is the only supported option.

Go into chroot by running:
      
      sudo startcli

Get more packages for qemu:

      sudo apt install qemu qemu-kvm qemu-system-gui

This is the qemu command line options I use to run Windows 11 VM:

      qemu-system-x86_64 \
        -m 4096 \
        -smp 2 \
        -vga qxl \
        -display default,show-cursor=on \
        -usb \
        -device usb-tablet \
        -device usb-mouse \
        -machine type=q35,accel=kvm \
        -bios /usr/share/OVMF/OVMF_CODE.fd \
        -boot order=c \
        -cdrom /home/<user>/Downloads/VM/virtio-win-0.1.190.iso \
        -drive file=/home/<user>/Downloads/VM/win11.qcow2,if=virtio \
        -drive file=/home/<user>/Downloads/VM/data.qcow2,if=virtio \
        -cpu Skylake-Client-IBRS
        
To be continued.

4) <b>SSD Upgrade</b>

I got a Western Digital CH SN530 1TB 2230 NVME SSD, after seeing this video https://www.youtube.com/watch?v=QAyFRj-gORI.

Unfortunately, after running Recovery and messing around with it, the laptop gives "Chrome OS is missing or damaged" and unable to proceed further. I tried to install different operating systems such as Windows 10 and Ubuntu 21.04 on it on a different laptop, with success. I think it might be due to the WD 1TB uses 4096 physical sector size, causing trouble for Chromeos UEFI booting. This might be in the firmware or something. Just my wild guess.
      
For now, I will just put this SSD into a NVME enclosure, and use it as a portable USB.

5) <b>Firmware Upgrade</b>

Samsung Galaxy Chromebook has a UEFI Firmware (Full ROM) available now here https://mrchromebox.tech/#devices. What that means is that, if you install this UEFI firmware, you will have to blow away ChromeOS. I am not ready to do that just yet, because I am not sure if I could recover back to Chromeos, and I am actually a fan of Chromeos. I had a older Samsung Chromebook 3 that has support for RW_LEGACY Firmware. I tried out the <a href="https://galliumos.org/">GalliumOS</a> on it and it works quite good, but I eventually recovered back to Chromeos.
