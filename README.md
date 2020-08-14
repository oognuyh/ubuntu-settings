
# Settings After installing Ubuntu 20.04 

DELL XPS 13 9380 + EGPU(RTX 2060)   
- - - - - - - - - - - - - - - - - 

```
sudo apt-get upgrade && sudo apt-get update
```

- - - - - - - - - - - - - - - - - 
# NVIDIA Graphic Driver
Installing NVIDIA DRiver using "Software & updates" app.
  ```
  sudo nvidia-xconfig --prime 
  ```
Edit /etc/X11/xorg.conf and add a line 'Option "AllowExternalGpus" "True" to the device section.
  ```
  Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce RTX 2060"
    BusID          "PCI:60:0:0"
    Option         "AllowExternalGpus" "True"
  EndSection
  ```
Identify the built in GPU.
  ```
  lspci | grep VGA
  00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620
  ```
Add a section for intel graphics.
  ```
  Section "Device"
    Identifier    "iris"
    Driver        "modesetting"
    BusID         "PCI:0:2:0"
  EndSection
  ```  
* Reference : [Setting Up an eGPU on Ubuntu](https://medium.com/@mattkubilus/setting-up-an-egpu-on-ubuntu-c87d4c04cea4)
  
# GRUB Theme  
  * matter grub theme download link : [matter-theme](https://github.com/mateosss/matter#download)
  * Install grub-customizer
    ```
    sudo apt-get install grub-customizer
    ```

# GTK3 Theme
  * ant nebula theme download link : [ant-nebula-theme](https://www.gnome-look.org/p/1099856/)
    ```
    tar -xf Ant-Nebula.tar -C /usr/share/themes
    ```
  * Full icon theme download link : [Qogir-icon-theme](https://www.gnome-look.org/p/1296407/)
    ```
    tar -xf Qoir-icon-theme.tar.xz -C /usr/share/icons
    ```
    
# gnome tweak  
  ```
  sudo apt install gnome-tweak-tool
  ```
  
# Development Tools  
  + Visual Studio Code
    ```
    sudo snap install --classic code
    ```
   
  + Ananconda  
    copy the latest version link from [Anaconda](https://www.anaconda.com/products/individual)
    ```
    wget 'link'
    bash 'installed.sh'
    ```
    
  + Android Studio
    ```
    sudo apt install default-jdk
    sudo snap install android-studio --classic
    ```
    
  + Kotlin 
    ```
    sudo snap install kotlin --classic
    ```
   
  + Go
    ```
    sudo snap install go --classic
    ```
          
  + Git
    ```
    sudo apt install git
    ```
    
# UIM 
  ```
  sudo apt install uim uim-byeoru 
  ```
  
# TLP
  ```
  sudo add-apt-repository ppa:linrunner/tlp
  sudo apt-get update
  sudo apt-get install tlp tlp-rdw
  sudo tlp start
  ```
  
# Wine 
  + kakaotalk
  + hwp
  + microsoft office
  
# Timezone
  ```
  timedatectl set-local-rtc 1
  ```
  Open /etc/default/rcS and add "UTC=no" so that the changes can take effect after rebooting.
  ```
  UTC=no
  ```

# Bluetooth  
1. Pair all devices with Ubuntu and then pair Windows  
2. Copy Windows paring keys   
3. Change info in Ubutnu  
  + Pairing key only  
    ```
    sudo vim /var/lib/bluetooth/'receiver MAC address'/'device MAC address'/info
    ```
    change 'Key' in 'LineKey' to copied key to upper case after removing seperator  
  
  + BLE with Public/Static Address  
    ```
    mv /var/lib/bluetooth/'receiver MAC address'/'device MAC address' /var/lib/bluetooth/'receiver MAC address'/'the latest Static(Random) address'
    ```
    change 'Key' in 'LongTermKey' to copied LTK,   
    'Rand' in 'LongTermKey' to copied ERand to decimal after flipping over,  
    'EDiv' in 'LongTermKey' to copied EDIV to decimal,  
    'Key' in 'IdentityResolvingKey'to copied IRK  
    
  + BLE with CSRK  
    ```
    sudo vim /var/lib/bluetooth/'receiver MAC address'/'device MAC address'/info
    ```
    change 'Key' in 'LocalSignatureKey' to copied CSRK,  
    'Counter' in 'LocalSignatureKey' to copied OutboundSignCounter  
    
4. restart the bluetooth service
  ```
  sudo systemctl restart bluetooth
  ```
  
* Reference : (multiboot-sharing-bluetooth)[https://nounique.github.io/development/multiboot-sharing-bluetooth/]  

# Youtube Music
  ```
  sudo snap install youtube-music-desktop-app
  ```

# Reboot to Windows 
  Add a function in your ~/.bashrc 
  ```
  rebootw() {
    WINDOWS_TITLE=$(grep -i windows /boot/grub/grub.cfg | cut -d "'" -f 2)
    sudo grub-reboot "$WINDOWS_TITLE" && sudo reboot
  }
  ```
