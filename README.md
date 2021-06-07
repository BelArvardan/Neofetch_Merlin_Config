# Neofetch Merlin Config
My custom configuration file for neofetch using ascii art made by [Adithyan-KV](https://github.com/Adithyan-KV).

## Preview
![ASCII-wizard-preview](/Preview/Merlin_on_Tilix.png)

## Additions to Neofetch Config usinng the [prin](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info#prin) option

### Lutris Games
- Uses the 

### Sound Server
-

### Alternate method to display terminal font on Tilix 
-

### ProtonVpn Server
-


## Additional software required to use my configuration

- [protonvpn-cli](https://protonvpn.com/support/linux-ubuntu-vpn-setup)
- [Lutris](https://github.com/lutris/lutris)
- [ripgrep](https://github.com/BurntSushi/ripgrep)
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)

## How to use

### Installing Additional software/dependancies.
In Ubuntu can can install these packages with the following commands:

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
#### Nerd nerd-fonts
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

### Use W3M on Terminal Emulators that support inline images
`neofetch --config /home/$USER/.config/neofetch/config-w3m.conf`
or
`neofetch --backend w3m --source /home/$USER/.config/neofetch/images/space-wizard-car.jpeg`

## Conclusions
- Neofetch is a fun and useful tool which is widely used and highly customizable.
- Hopefully my config example will inspire others to create new useful customizations.
- My additions are very simple and slightly hacky, so I'm sure others can easily create new and amazing additions. 

## Note
- This is the 1st project I have posted in several years.
- Any comments or suggestions are welcome.
- Enjoy