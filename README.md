# Themes for Linux by REV3NT3CH

These themes fully apply to Grub, Plymouth Bootanimation, GDM login screen / LightDM, Desktop Environment and Icons. 

Screenshots can be found <a href="https://github.com/REV3NT3CH/REV3NThemes/blob/master/screenshots/screenshots.md">here</a>

# Instructions

<mark>For basic instruction I have used R3D3MP710N as the default example in some of the commands used below. If you want to use another theme. Change the commands with R3D3MP710N to the name of the theme you want to apply when neccessary.</mark>

### Dependencies & Prerequisites

```
sudo apt-get install python3-lxml libglib2.0-dev dconf-cli git
```
```
git clone https://github.com/REV3NT3CH/REV3NThemes.git && git clone --depth=1 https://github.com/realmazharhussain/gdm-tools.git && git clone https://github.com/worron/ACYLS.git ~/.icons/ACYLS
```

### Place themes in respectable folders

```
sudo cp -R ~/REV3NThemes/themes /usr/share && sudo cp -R ~/REV3NThemes/themes/*/ ~/.themes && sudo cp -R ~/REV3NThemes/themes ~/.local/share && sudo cp -R ~/REV3NThemes/grub/themes /usr/share/grub && sudo cp -R ~/REV3NThemes/plymouth/themes /usr/share/plymouth && cp -R ~/REV3NThemes/wallpapers ~/Pictures && cp ~/.icons/ACYLS/desktop/acyls.desktop ~/.local/share/applications
```

### Set up the icons to match the theme

cd back to the home directory before entering next command:

```
python3 ~/.icons/ACYLS/scripts/run.py
```

At this point you can then set and apply the colors and designs for the icons (Theme colors below):

- B34ST: ![#0080dc](https://placehold.co/15x15/0080dc/0080dc.png) `#0080dc`
- BAZZ0N: ![#00FFF5](https://placehold.co/15x15/00FFF5/00FFF5.png) `#00FFF5`
- F4110U7: ![#12FF12](https://placehold.co/15x15/12FF12/12FF12.png) `#12FF12`
- N4710N: ![#A5ACAF](https://placehold.co/15x15/A5ACAF/A5ACAF.png) `#A5ACAF`
- R3D3MP710N: ![#DC0000](https://placehold.co/15x15/DC0000/DC0000.png) `#DC0000`
- UND3RT4K3R: ![#90009F](https://placehold.co/15x15/90009f/90009f.png) `#90009F`
- W45P: ![#FFE700](https://placehold.co/15x15/FFE700/FFE700.png) `#FFE700`

Once finished selecting the styles and colors you can now close out of this program.

## $\color{#FF0000}{\text{For Installation On Linux Mint!!!}}$

<details>
<summary>Click here for further instructions</summary>

### Set Desktop wallpaper

```
gsettings set org.cinnamon.desktop.background picture-uri file://$HOME/Pictures/wallpapers/R3D3MP710N/background.png
```

### Switch to the built in LightDM GTK Greeter login screen

```
sudo dpkg-reconfigure lightdm && sudo systemctl enable lightdm --now && sudo tee /etc/lightdm/lightdm.conf << 'EOF' >> /dev/null
[Seat:*]
greeter-session=lightdm-gtk-greeter
EOF
```

```
sudo cp -R ~/REV3NThemes/wallpapers /usr/share/backgrounds/REV3NThemes && sudo sed -i 's|background=/usr/share/backgrounds/linuxmint/default_background.jpg|background=/usr/share/backgrounds/REV3NThemes/R3D3MP710N/background.png|' /etc/lightdm/lightdm-gtk-greeter.conf.d/99_linuxmint.conf && sudo sed -i 's|theme-name=Mint-X|theme-name=R3D3MP710N|' /etc/lightdm/lightdm-gtk-greeter.conf.d/99_linuxmint.conf && sudo sed -i 's|icon-theme-name=Mint-X|icon-theme-name=ACYLS|' /etc/lightdm/lightdm-gtk-greeter.conf.d/99_linuxmint.conf

```

### Update Grub & Bootanimation to match theme

```
sudo sed -i '$a GRUB_THEME=/usr/share/grub/themes/R3D3MP710N/theme.txt' /etc/default/grub
```

```
sudo update-grub && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/B34ST/B34ST.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/BAZZ0N/BAZZ0N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/F4110U7/F4110U7.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/N4710N/N4710N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/R3D3MP710N/R3D3MP710N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/UND3RT4K3R/UND3RT4K3R.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/W45P/W45P.plymouth 100
```
```
sudo update-alternatives --config default.plymouth
```

After running the above command select the number associated with the theme you want:

```
sudo update-initramfs -u
```

### Set Desktop Theme & Icons universally in the following location

Go to Start Menu > Preferences > Themes > Then select your themes & icons from the menu options.

After Applying the theme it is recommended to run Alt + F2 to run a command then type the letter r and press enter to refresh the desktop environment

</details>

## $\color{#FF0000}{\text{For Installation On Linux Zorin!!!}}$
<details>
<summary>Click here for further instructions</summary>

### Set Desktop wallpaper

```
gsettings set org.gnome.desktop.background picture-uri file://$HOME/Pictures/wallpapers/R3D3MP710N/background.png
```

### Set the theme & background of gdm3 login screen

```
cd gdm-tools
```
```
./install.sh
```
```
set-gdm-theme backup update
```
```
set-gdm-theme set R3D3MP710N
```
```
set-gdm-theme set -b ~/Pictures/wallpapers/R3D3MP710N/background.png
```
### Update Grub & Bootanimation to match theme
```
sudo sed -i 's|GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt|GRUB_THEME=/usr/share/grub/themes/R3D3MP710N/theme.txt|' /etc/default/grub
```
```
sudo cp -R ~/REV3NThemes/plymouth/images/R3D3MP710N/* /usr/share/plymouth
```
```
sudo update-grub && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/B34ST/B34ST.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/BAZZ0N/BAZZ0N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/F4110U7/F4110U7.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/N4710N/N4710N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/R3D3MP710N/R3D3MP710N.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/UND3RT4K3R/UND3RT4K3R.plymouth 100 && sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/W45P/W45P.plymouth 100
```
```
sudo update-alternatives --config default.plymouth
```
After running the above command select the number associated with the theme you want:
```
sudo update-initramfs -u
```

### Set Desktop Theme & Icons universally in the following location

Go to Start Menu > Zorin Appearance > Themes > Other > Then select your themes & icons from the menu options.

After Applying the theme it is recommended to run Alt + F2 to run a command then type the letter r and press enter to refresh the desktop environment

</details>

# Credits & Thanks
Credits to the Zorin team for the Zorin-Dark themes, Grub theme and Plymouth theme I based this off of found here https://github.com/ZorinOS/zorin-desktop-themes 

Credits to the Linux Mint team for the Mint-X and Mint-Y themes I based the gtk3 themes off of.

Credits to realmazharhussain for the gdm tools used in the instructions and can be found here https://github.com/realmazharhussain/gdm-tools

Credits to worron for his work and contributions to ACYLS icons that are used in the instructions and found here https://github.com/worron/ACYLS

Credits to mystica-264 on deviantart for the dual hexagon pattern used in the wallpapers

Huge THANK YOU to the open-source community for all the amazing projects we create and achieve.
