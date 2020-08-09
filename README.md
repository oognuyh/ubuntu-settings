
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
  * matter grub theme download link : [grub-theme-matter](https://github.com/mateosss/matter#download)
  * Install grub-customizer
    ```
    sudo apt-get install grub-customizer
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
    sudo apt install openjdk-11-jdk
    sudo add-apt-repository ppa:maarten-fonville/android-studio
    sudo apt update
    sudo apt install android-studio
    ```
    
  + Ananconda
    ```
    ```
    
  + Go
    ```
    ```
    
  + Java
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

# Bluetooth
