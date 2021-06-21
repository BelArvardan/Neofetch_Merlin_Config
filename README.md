# Neofetch Merlin Config

- The following is my custom configuration file for [Neofetch](https://github.com/dylanaraps/neofetch) using ascii art made by [Adithyan-KV](https://github.com/Adithyan-KV) and several additional perameters using the 
`prin` option in Neofetch. 

- My Terminal Emulator of choice is [Tilix](https://github.com/gnunn1/tilix) and therefore some of my customizations are tilix specific.

## Contents

- [Preview](#preview)
- [Additional Software Required](#additional-software-required)
- [Additions to Neofetch Config](#additions-to-neofetch-config)
- [Sources](#sources)
- [Thoughts](#thoughts)

## Preview
### Merlin Acsii Preview
![ASCII-wizard-preview](/Preview/Merlin_on_Tilix.png)
### PipBoy Acsii Preview
![ASCII-pipboy-preview](/Preview/PipBoy_on_Tilix.png)

## Additional Software Required

- [protonvpn-cli](https://protonvpn.com/support/linux-ubuntu-vpn-setup)
- [lutris](https://github.com/lutris/lutris)
- [ripgrep](https://github.com/BurntSushi/ripgrep)
- [nerd-fonts](https://github.com/ryanoasis/nerd-fonts)
- [efibootmgr](https://github.com/rhboot/efibootmgr)

### Installing Additional software/dependancies.
In Ubuntu and debian these packages can be installed easily with the following commands:

#### protonvpn-cli
```
wget https://protonvpn.com/download/protonvpn-stable-release_1.0.1-1_all.deb
sudo dpkg -i protonvpn-stable-release_1.0.1-1_all.deb
sudo apt-get update
sudo apt-get install protonvpn
```
#### Lutris
```
sudo apt-get update
sudo apt-get install lutris
```
#### RipGrep
```
sudo apt-get update
sudo apt-get install ripgrep
```
#### EFI Boot Manager 
```
sudo apt-get update
sudo apt-get install efibootmgr
```
#### Nerd Fonts
```
git clone https://github.com/ryanoasis/nerd-fonts.git
cd nerd-fonts
```
##### Install all nerd fonts
`./iinstall.sh`
##### Install individual font or fonts
`./install.sh <FontName>`
###### Example:
```
./install.sh CodeNewRoman
./install.sh ProggyClean
```

## Additions to Neofetch Config
- This is done usinng the [prin](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info#prin) option

### Bootloader
`prin "異Bootloader" "$(efibootmgr | rg "Boot`efibootmgr | rg "BootOrder" | cut -c12-15`" | cut -c11-)"``
- uses [efibootmgr](https://github.com/rhboot/efibootmgr) and grep or ripgrep to find the default 1st bootloader then grep again using that number string to determine the default bootloaders label.

### Lutris Games
`prin " Lutris Games" "$(ls /home/$USER/.local/share/lutris/banners | wc -l)"`
- Uses the `ls` and `wc` commands to show how many games I have installed on [Lutris](https://github.com/lutris/lutris)

### Sound Server
`prin "墳Sound Server" "$(pactl info | rg 'Server Name' | cut -c13-)"`
- I have started using Pipewire as a sound Server and since its still new and part incorporated into my distro by default it is important to make sure the system is still using it.
- I use `pactl info` with `grep` or `rg`(ripgrep) to make sure pipewire is working properly.

### Alternate method to display terminal font on Tilix
`prin " Terminal Font" "$(dconf dump /com/gexperts/Tilix/profiles/[Profile String]/ | rg "font" --max-count=1 | cut -c6-)"`
- For whatever reason the `term_font` function doesn't work on tilix. I'm not sure why.
- See the [Neofetch Wiki](https://github.com/dylanaraps/neofetch/wiki/Terminal-and-Terminal-Font-detection) for more info about this.
- As a result I am using `dconf dump` with `grep` or `rg`(ripgrep) to find this infomation.
- this requires you to find the string assosiated with your Tilix profile using the command 
`dconf dump /com/gexperts/Tilix/profiles`

![Find-tilix-profile-string](/Preview/Tilix_Profile_String.png)

- This implementation is problematic and may not alsways work. However it has worked for me so far.

### ProtonVpn Server
`prin "旅 ProtonVPN Server" "$(protonvpn-cli s | rg "Server" --max-count=1 | cut -c11-)"`
- This simply displays which ProtonVPN Server I am connected to too.

### Added glyphs to all function labels
- This is accomplished by installing any [nerd font](https://github.com/ryanoasis/nerd-fonts).
- Set installed nerd-font as the font used by your terminal emulator
- In Tilix this can be done by opening Preferences, Selecting your profile. checking the box for "Custom Font" and selecting whichever Nerd Font that's installed.
- In other Terminal Emulators you may have to edit a config file manually.
    - In kitty open `/home/$USER/.config/kitty/kitty.conf` in your editor of choice.
    - In Alacritty the config file is located in `/home/$USER/.config/alacritty/alacritty.yml`

## How to use

### Clone the repo or download its contents
`git clone https://github.com/BelArvardan/Neofetch_Merlin_Config /home/$USER/.config/neofetch`

## run neofetch
`neofetch`

### Run with Custom Config File or Custom Image
#### Custom configuration
`neofetch --config /path/to/config`
###### Example:
`neofetch --config /home/$USER/.config/neofetch/config-w3m.conf`

#### Custom Image
`neofetch --source /path/to/img`
###### Example:
`neofetch --source /home/$USER/.config/neofetch/ascii/skull.txt`

![ASCII-skull-preview](/Preview/Skull_on_Tilix.png)

### For Terminal Emulators that support inline images
`neofetch --config /home/$USER/.config/neofetch/config-w3m.conf`
or
`neofetch --w3m source --source /home/$USER/.config/neofetch/images/space-wizard-car.jpeg`

### Example using [Kitty](https://github.com/kovidgoyal/kitty)
`neofetch --kitty source /home/$USER/.config/neofetch/images/space-wizard-car.jpeg`

![Image-wizard-preview](/Preview/Space_Wizard_on_Kitty.png)

## Sources

### Acsii
- [merlin.txt](https://github.com/Adithyan-KV/neofetch_ascii/blob/master/merlin.txt) designed by [Adithyan-KV](https://github.com/Adithyan-KV).
- [pipboy.txt](https://www.reddit.com/r/Fallout/comments/2b1feu/pipboy_ascii_art/) found on [r/Fallout](https://www.reddit.com/r/Fallout).
- [skull.txt](https://github.com/Adithyan-KV/neofetch_ascii/blob/master/skull.txt)  designed by [Adithyan-KV](https://github.com/Adithyan-KV).
- [vampire.txt](https://www.asciiart.eu/mythology/monsters) found on [asciiart.eu](https://www.asciiart.eu)
- [viking.txt](https://asciiart.website/index.php?art=people/vikings) found on [asciiart.website](https://asciiart.website)
### Images
- [space-wizard-car.jpeg](https://www.reddit.com/r/SS13/comments/3szzdx/the_average_wizard_round) found on [r/SS13](https://www.reddit.com/r/SS13/)
### Other Tools
- [Goph](https://mayccoll.github.io/Gogh/) An easy way to install many terminal color themes.

## Thoughts
- Neofetch is a fun and useful tool which is widely used and highly customizable.
- Hopefully my config example will inspire others to create new useful customizations.
- My additions are very simple and slightly hacky, so I'm sure others can easily create new and amazing additions. 
- This is the 1st project I have posted in several years.
- Any comments or suggestions are welcome.
