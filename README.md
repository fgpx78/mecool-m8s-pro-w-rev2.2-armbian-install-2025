# MeCool m8s pro w (rev2.2) - How to install Armbian in 2025
I bought an m8s pro w (from now on m8s or mecool) for 2 dollars on an auction site. Given the Amlogic S905W processor, my intention was to install Linux and make it a very small home server to host 2 simple LAMP websites.

The experience has been very frustrating, though, and after a couple of days, I finally managed to make it work. The documentation online either refers to old images, or is not clear enough. 
**Actually, it turns out that nowadays Armbian boots seamlessly on m8s s905w, without ANY MODIFICATION to the image burnt on the USB key / SD card.**

That's why I decided to make a comprehensive guide / HOW TO.

## My device
First of all, this is my device: a MeCool m8s pro W with a rev 2.2 board (blue).

![mecool-m8s-pro-w-rev2 2](https://github.com/user-attachments/assets/faeaaf60-8be8-4809-a807-4b590b728f4a)

This board revision **does not have a reset button** . You can short the two pins as in the following image:

![pins_to_short](https://github.com/user-attachments/assets/35840c22-fb42-47c8-bc37-e70c3118d6fd)

or solder a button to them as I did - inspired by a YouTube Hindi video which I can't find anymore (sorry, man!)

![added reset button](https://github.com/user-attachments/assets/04c64d39-7306-465f-8d32-a24402720d25)

If you want to run Armbian on a removable device as I did, you'll need to use the reset button a lot. Basically, for every restart.

## Finding the right image in the noise
There's a lot of noise on the internet. The only two releases I found that worked on my device were

- Armbian_25.11.0_amlogic_s905w_bookworm_5.15.196_server_2025.11.15.img.gz
- Armbian_25.11.0_amlogic_s905w_trixie_6.1.158_server_2025.11.15.img.gz
from https://github.com/ophub/amlogic-s9xxx-armbian/releases

I tried the installation on
- 32 Gb USB key (connected to the first port close to the power socket)
- 4 Gb SD card
- 32 Gb SD card
- 64 Gb SD card
with no particular issue.

## Reset procedure
From now on, with RESET I mean _"short the two pins indicated above and keep them shorted while you connect the power to the tv box, and for 8-10 seconds afterwards"_
A RESET should:
- boot the Android Recovery Menu, if there is no bootable USB/SD card device inserted.
- boot from USB/SD card otherwise (sometimes after 2 or 3 restarts / passages from the MeCool logo)

## How to boot Armbian?
- Download one of the images above.
- Use Balena Etcher to burn it to your preferred device, a USB key or an SD card - you'll lose all data on it, make a backup!
- Detach power from the m8s
- Attach a network cable
- Insert the USB/SD card
- RESET as described above
- Wait, wait, wait. In my case HDMI output DOES NOT WORK when booting Armbian (Maybe because my monitor has too high a resolution?). Everything seems dead, but if you give it enough time (10-15 minutes) it should eventually run.

## How to connect?
Since I don't have any HDMI output, I used SSH from a Windows PC in the same network. First, I used Angry IP (https://angryip.org) to discover the IP of the device - which sill have name ARMBIAN.

<img width="771" height="224" alt="angryip" src="https://github.com/user-attachments/assets/bbbdb5d0-f9b1-4f82-8f45-42e2e6283671" />

Then I used ssh root@[ip found of the device in angryip] to connect to it, with the standard password 1234.
This starts the configuration wizard:

<img width="976" height="584" alt="armbian-runs" src="https://github.com/user-attachments/assets/945b88e9-b077-433b-87d6-86453f45bdcb" />

From now on, you're on your own :)
ENJOY!






