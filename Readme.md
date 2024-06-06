# notice: this guide is UNFINISHED, for now use the old one that uses lutris in the main branch



##### requirements
- bottles and flatseal installed via [flatpak](https://flatpak.org/)
- dxvk-gplaasync (to improve direct-x renderer performance)
- system and drivers (including vulkan) are installed and up to date
- discord app installed with [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux)

##### notes
this is tested on my arch linux host, but it should work for other distros
##### First steps
###### updating your system

this is recommended so you can get latest fixes and packages, type these commands in your teminal depending on your distro

on debian/ubuntu, do:
```
sudo apt update && sudo apt upgrade
```

on fedora, do:
```
sudo dnf update && sudo dnf upgrade
```

on opensuse, do:
```
sudo zypper refresh && sudo zypper update
```

on arch based distros (manjaro, endeavour os, etc..) do:
```
sudo pacman -Syu
```

###### installing bottles

assuming you have installed flatpak as explained [here](https://flatpak.org/setup/), you can now install bottles from the app center you have (gnome softwares, kde discover, software manager, etc)
or if you like CLI method, just type this into terminal
```
flatpak install flathub com.usebottles.bottles
```

##### bottles post-install

###### prerequests

launch bottles and wait for the setup to finish, after that go to the 3-dots > preferences > dll components, scroll down to install the latest version of dxvk-gplasync as you see in this video


###### bottle creation and settings

press on the plus icon or the (create new) button, choose a name for it **and choose custom instead of gaming** and change the architecture to 32bit so the game displays somehting other than black screen
then wait it to finish

after it finishes, change some options like what you see in pictures

*discreate graphics is optional, yet recommended*

![image](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/4de1a0db-ac52-4f25-bed1-83941b013dec)

![image](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/b7621ff2-9b40-4180-9e42-68b7c53b50ac)

![image](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/8b6fc007-30a1-49d7-ac39-463106582a33)

![image](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/7b9dc2b0-047f-456f-ac41-3d88274eb743)

![image](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/114e1abb-d99e-4e36-9e0f-65a4ca665b23)


##### installing the game

##### installing mario multiverse

###### before we start
flatpak apps are isolated by nature, so it won't be able to access every folder like normal apps, including mario multiverse one, so we need to make a folder for MM and allow bottles to access it

1. make a directory for MM, let's create a one in documents folder and call it MM
2. open flatseal, navigate to bottles, scroll down to filesystem section, in (other files) click on the puls icon and enter the MM path you can get it by right clicking on MM folder and finding the info section or something similar, if the path doesn't include the MM folder name, you have to include it yourself (don't forgot to add a / if it doesn't exist at the end of previous directory)
3. close flatseal for now, and restart bottles
4. to make accessing the folder easier in bottles, go to the bottle you made > settings, scroll down until you find (manage drives), open it and add a drive and paste the path there (don't forgot what did i say above)

1. download both of the downloader and the dlls and extract them inside the MM folder we've created earlier
2. go to [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux) github page and download it from the latest release, as shown here, and extract it to MM folder
3. at the end of the bottle page, from legacy wine tools, select explorer
4. go to the mm directory we have created using the drive letter, then click on GenerateDiscordToken.exe (don't worry, even MM settings mentiones it)
![Pasted image 20240329020908](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/dcdf6085-1b46-452a-a506-3841fba356ca)
5. after it succesfully finish, close the generatediscordtoken.exe and open MarioDownloader_for_username.exe, do what it says and wait for it to download (pasting can be done by right click > edit > paste)
6. the screen of the game itself is currently black, to fix it click on (run excutable) button, change filter from (supported excutable, all files) to (all files) and open mario config, change the game's renderer from opengl to directx or directx-hd, then close and reopen the game

##### map editor and dxvk

if you want to create levels, it is recommended to follow this section, otherwise the performance well be poor

things you need :
- flatpak installed
- proton-up gui
- vulkan supported and installed

###### 1: installing proton-up qt for dxvk-async
 proton up is an application to install different runners and component to enhance the gaming experience we will use it for installing dxvk-async, make sure you have flatpak installed (tutorial [here](https://flatpak.org/setup/))
 after you install flatpak, either use the installed application center (except for ubuntu software, use gnome software instead) and search for proton
 or use the command line :
 `flatpak install flathub net.davidotek.pupgui2`
 with protonup installed you can install dxvk-async
##### 2: installing dxvk-async
dxvk-async is modified version of dxvk with some patches to improve performance, i (and the dxvk-async maintainer) MUST note that t's NOT recommended for multiplayer games, or there's a chance you'll get BANNED, use it only on singleplayer

to install it, launch protonup-qt, change (install for) to lutris  (bitrate is low idk why) 

[Screencast_20240331_201506.webm](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/f793edf0-1ad1-484f-a318-ebe4611e3f5d)


click on add version and select DXVK-async and choose install 

[Screencast_20240331_201722.webm](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/1bef621e-c940-48e8-b8df-898bf6be376e)

now open lutris, choose mario multiverse, click the arrow next to play and choose configure
in system options, scroll down to environment variable, and add these options with values

| key                | value |
| ------------------ | ----- |
| DXVK_ASYNC         | 1     |
| DXVK_GPLASYNCCACHE | 1     |

![Pasted image 20240331202244](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/604956eb-50d1-458f-bcd6-9865f7ef6e02)

click on save, and now you should have better performance when using direct x as a render


##### known problems
- when using direct-x as a render for the main game, maximizing the window will result in a worse performance, i don't know a fix for that


### credits
- [u/Curious_Increase_592](https://www.reddit.com/user/Curious_Increase_592/), a member from the great [r/linux_gaming](https://www.reddit.com/r/linux_gaming/) for suggesting dxvk-gplasync
- @ henrydc (on discord) for most of the guide, otherwise, it will take longer time to figure out the method
