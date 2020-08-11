
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
  * Full icon theme download link : [Sweet-folders](https://www.opendesktop.org/p/1284047)
    ```
    tar -xf Sweet-Red-Filled-tar.xz -C /usr/share/icons
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
    
  + Android Studio
    ```
    sudo apt install default-jdk
    sudo snap install android-studio --classic
    ```
    
  + Ananconda
    ```
    ```
    
  + Go
    ```
    ```
        
  + Kotlin 
    ```
    ```
  + Git
    ```
    ```
    
# UIM 
  ```
  sudo apt install uim uim-byeoru 
  ```
  
# TLP

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
