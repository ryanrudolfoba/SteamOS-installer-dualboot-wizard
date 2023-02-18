# Steam Deck - Modified Valve SteamOS Installer Script with Dual Boot Wizard


## About

This is based on the official Valve SteamOS recovery image. I've modified the script to automatically prepare and create the partitions needed for a dual boot Windows setup.

The script will ask how much disk space to allocate for the SteamOS /home partition and then assign the remaining free space for Windows.

The script has sanity checks and if it is not met, no changes will be made and it will exit immediately. If the sanity checks are met then it proceeds to reimage the NVME drive and allocate the /home partition based from the selection of the end user, and finally assigns the remaining free space for Windows.


## Disclaimer
1. Do this at your own risk!
2. This is for educational and research purposes only!

## What's New (as of February 18 2023)
1. added 768Gib and 1536Gib options for SteamOS /home partition
2. added CUSTOM option - end user can enter his own preferred size for SteamOS /home partition

## Old Changelog - February 10 2023
1. Initial Release

## But Why?!?
I created / modified the official Valve SteamOS recovery image script to solve this particular problem [(click here for details.)](https://help.steampowered.com/en/faqs/view/6121-eccd-d643-baa8)

![image](https://user-images.githubusercontent.com/98122529/217654660-360ce075-1d55-488b-8dc7-8a12eb36bfa7.png)

Now I can easily install SteamOS and Windows without manually resizing / creating partitions!

## Screenshots
**Main Screen - Select how much space to allocate to SteamOS /home partition**
![image](https://user-images.githubusercontent.com/98122529/219874357-fddf841d-51c2-48f6-95a5-4ddcd1c53e32.png)

**CUSTOM - end user can enter his own preferred size for SteamOS /home partition**
![image](https://user-images.githubusercontent.com/98122529/219874434-b80ac205-fa94-4e09-84c6-2162edf4d976.png)


**Ready to proceed with the reimage - 16GiB will be allocated for SteamOS /home partition**
![image](https://user-images.githubusercontent.com/98122529/217666125-637985c4-c3e7-46ed-b2e0-3212197a97e6.png)

## Requirements
1. SteamOS Recovery Image.
2. USB flash drive for Steam Recovery Image. Recommended size is at least 8GB.


## Instructions
1. [Follow this steps to create the official SteamOS Recovery image.](https://help.steampowered.com/en/faqs/view/1b71-edf2-eb6d-2bb3)
2. Once the SteamOS Recovery image is created, plug it in to the USB C port of the Steam Deck (or USB C hub / dock if you are using one).
3. While the Steam Deck is powered off, press the VOLDOWN + POWER button until you hear a chime.
4. The boot menu will appear, select the USB drive that contains the SteamOS Recovery image and press A button (or enter on the keyboard).
5. Wait until the SteamOS recovery image boots into the desktop.
6. Connect the Steam Deck to your wifi connection.
7. Open konsole terminal and clone the repository that contains the scripts.

    cd ~/
    
    git clone https://github.com/ryanrudolfoba/SteamOS-installer-dualboot-wizard.git
 
8. Execute the script!

    cd ~/SteamOS-installer-dualboot-wizard
    
    chmod +x steamos-installer-dualboot-wizard.sh
    
    sudo ./steamos-installer-dualboot-wizard.sh
    ![image](https://user-images.githubusercontent.com/98122529/217664831-9583a219-9a69-4c7e-868f-66041218cd2d.png)

    
9. The main screen will appear. Choose how much space you want to allocate to SteamOS. If you changed your mind and just want to exit the script, just press EXIT / CANCEL while it is highlighted on 0.

![image](https://user-images.githubusercontent.com/98122529/219874391-83f3779d-616e-4d77-b071-10d8e32cf276.png)


10. On this example I want to allocate 16GiB to SteamOS /home partition. Click the selection for 16GiB and press OK.
![image](https://user-images.githubusercontent.com/98122529/217665993-e846945e-aa45-4aac-9ed1-9fd839d1eb69.png)
 
11. This is your last chance to backout - press CANCEL to exit, otherwise press PROCEED and wait until the reimage is complete.

    ![image](https://user-images.githubusercontent.com/98122529/217666125-637985c4-c3e7-46ed-b2e0-3212197a97e6.png)
    
12. Reimage in progress. Wait until it is complete. This will depend on the speed of your USB flash drive.

    ![image](https://user-images.githubusercontent.com/98122529/217666462-cc08f59b-6c05-4fdb-9b69-d140e013484a.png)
    
13. Once the reimage is complete, press proceed to reboot the Steam Deck.

    ![image](https://user-images.githubusercontent.com/98122529/217666778-c8d115d1-f0d0-4bbe-9253-30fa99500e74.png)

13. SteamOS will continue to load. Do the initial SteamOS setup - language, timezone and wifi.
14. Once SteamOS boots to game mode, power off the Steam Deck and insert the flash drive that contains the Windows installer.
15. While the Steam Deck is powered OFF, press VOLDOWN + POWER and then select the USB flashdrive.
16. Windows installer will load and once it arrives on the screen to select the target destination - there will already be a free space that can be used for Windows! It also shows the 16GiB partition that I have allocated for SteamOS.

    ![image](https://user-images.githubusercontent.com/98122529/217674130-a7528fc7-497b-4993-a1b6-33f5546137ca.png)

## Future Plans
Integrate Clover or rEFInd as part of the dual boot wizard.
