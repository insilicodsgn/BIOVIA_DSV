# BIOVIA_DSV
BIOVIA Discovery Studio Visualizer Linux (Ubuntu) Installation Guide

**STEP 1**

sudo apt install binwalk  
sudo apt install libpcre2-16-0

**STEP 2**

cd Downloads
mkdir BIOVIA_DS2025Client_extracted 
cd BIOVIA_DS2025Client_extracted 
bash ../BIOVIA_DS2025Client.bin --target .
sed -i 's/echoe/echo/g' install_DSClient.sh
bash install_DSClient.sh
#When prompted, simply press the Enter key. You'll need to press Enter three times in a row.

**STEP 3** (Note: From this point on, you need to replace “ege” with your own username.)

cd /home/ege/BIOVIA/DiscoveryStudio2025/lp_installer
binwalk lp_setup_linux.sh
binwalk -e lp_setup_linux.sh
cd /home/ege/BIOVIA/DiscoveryStudio2025/lp_installer/_lp_setup_linux.sh.extracted #replace ege with your own username
mkdir unpacked_2502  
cp 2502.gz unpacked_2502/  
cd unpacked_2502  
gunzip 2502.gz  
tar -xf 2502
sed -i 's/echoe/echo/g' install_lp.sh
bash install_lp.sh #press enter three times
cp /home/ege/BIOVIA/BIOVIA_LicensePack/linux/lib/libls_license64_g850.so ~/BIOVIA/DiscoveryStudio2025/lib/ 
**STEP 4**
nano ~/BIOVIA/DiscoveryStudio2025/start_ds.sh
#!/bin/bash
export LD_LIBRARY_PATH=/home/ege/BIOVIA/DiscoveryStudio2025/lib:$LD_LIBRARY_PATH
/home/ege/BIOVIA/DiscoveryStudio2025/bin/DiscoveryStudio2025

chmod +x ~/BIOVIA/DiscoveryStudio2025/start_ds.sh
mv ~/Desktop/discoverystudio2025.desktop ~/.local/share/applications/

nano ~/.local/share/applications/discoverystudio2025.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=Discovery Studio 2025
Comment=BIOVIA Discovery Studio 2025
Exec=/home/ege/BIOVIA/DiscoveryStudio2025/start_ds.sh
Icon=/home/ege/BIOVIA/DiscoveryStudio2025/share/PluginDescriptors/Icons/Container/appicon.png
Path=/home/ege/BIOVIA/DiscoveryStudio2025
Terminal=false
Categories=Science;Education;

cp ~/.local/share/applications/discoverystudio2025.desktop ~/Desktop/
chmod +x ~/Desktop/discoverystudio2025.desktop 
After this process, we right-click on the DSV icon on the desktop (which might appear as a broken file with an X mark in the corner) and click on "Allow Launching". This way, the DSV software is installed on our Linux (Ubuntu) system.



