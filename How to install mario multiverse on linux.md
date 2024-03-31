##### requirements
- lutris
- dxvk-async (to use direct-x as a renderer)
- all of your system drivers are installed and up-to-date
- up to date system
- vulkan supported and installed (for dxvk-gplasync functionality, otherwise, use opengl)
- discord app installed with [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux)

##### notes
this is tested on linux-mint virtual machine and my arch linux laptop
different distros can require different steps, i will try to make this guide compatible with other distros
if you want to improve the guide using pull request, you are welcome
##### First steps
###### updating your system

this is recommended so you can get latest fixes and packages

on debian/ubuntu, do:
`sudo apt update && sudo apt upgrade`
in your terminal

on fedora, do:
`sudo dnf update && sudo dnf upgrade`

on opensuse, do:
`sudo zypper refresh && sudo zypper update`

on arch based distros (manjaro, endeavour os, etc..) do:
`sudo pacman -Syu`

###### installing lutris

lutris is an app to install and manage games on linux, including emulators and games shop, and it handles windows games very well

to install it, refer to lutris website, i will put the ubuntu/linux mint guide here since there are too many supported distro, and because it's the most popular one

first of all, got to lutris website (https://lutris.net/downloads), and find ubuntu/elementary section
![[Pasted image 20240327185232.png]]
you will find a github link, click on it and you will find this page
![[Pasted image 20240327185425.png]]
download the deb file from the latest release (as pointed by the cursor)
after downloading, click on what you downloaded, this page will pop up or something similar![[Pasted image 20240327185646.png]]
click on install package, a password popup will appear, fill the password in and it will install

##### after installing lutris

launch lutris and wait for the updates in the bottom left panel to complete
(enable dark mode from the app if some text is unreadable with system's dark mode enabled and restart the app)
open the settings, go to runners section, and find wine
click on the manage versions button![[Pasted image 20240327200252.png]]and install the lates wine-ge version that **doesn't** contain lol in it's name (the lol build made specifically for league of legends)
in my case it is why the cursor is pointing to
![[Pasted image 20240327200340.png]]
switching to the host because of vulkan
now we installed wine-ge, let's move on to install mario multiverse

##### installing the game

###### creating the prefix

a prefix -from my understanding- is a windows like environment to run the game and place its files, the one we will create in lutris is a bit tricky since we will make an empty one

first, press on the plus icon in the corner
![[Pasted image 20240329013308.png]]
and choose (add locally installed game) option
![[Pasted image 20240329013412.png]]
now, in this screen, you only need to input the game name (Mario Multiverse, ofc) and choose the runner (wine, in this case)
now go to game options to add a working directory and prefix path
![[Pasted image 20240329013630.png]]
as for the path, you can place it anywhere, but to keep it organized :
1. create 'Games' folder in the home folder
2. create another folder inside named 'MarioMultiverse' since i'm unsure if space in filename will break it
3. create 3 folder inside the MarioMultiverse folder, which are : (prefix, workingDir, MarioMultiverseFiles)

in working directory field, use the workingDir folder we created
in prefix field, use the prefix folder we created
![[Pasted image 20240329014422.png]]
in runner options, make sure that you use wine-ge as the runner
if you have multiple GPUs installed (or even single gpu like my case), go to system options page and change the vulkan icd loader to match the gpu you want to use
if you didn't find it, enable the advanced switch
![[Pasted image 20240329014852.png]]
now press on save to finish creating an empty prefix, and now we will install mario multiverse

##### installing mario multiverse

1. download both of the downloader and the dlls and extract them inside the MarioMultiverseFiles we've created earlier
2. go to [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux) github page and download it from the latest release, as shown here, and extract it to any folder, let's name it DiscordBuddyRedux for example ![[Screencast_20240329_015340.webm]]
3. in lutris, press on the prefix we created, and then click on wine logo, select wine console option, a prefix configuration update window appear, thats normal and you should wait ![[Screencast_20240329_015654.webm]]
4. navigate to the parent folder by typing `cd ..` , then go to DiscordBuddyRedux by typing `cd DiscordBuddyRedux` ![[Pasted image 20240329020457.png]]
5. type generatediscordtoken.exe to run it
6. you'll need to input you discord email and password don't worry, they won't go to me, and discord buddy redux name is mentioned in mario multiverse settings as shown here ![[Pasted image 20240329020908.png]]
7. good, now open any file manager you have and go to discord buddy folder to copy `discordbuddy.dll` `discordbuddy.ini` `ktwm32.dll` to the (mario multiverse files) folder
8. from lutris press on wine logo and choose wine configuration option, from that window, go to libraries tab and input ktmw32 to the text box and click add, then press ok to close the configuration
9. assuming you closed the wine console wine console, open it again, navigate to the parnt directory by typing `cd ..` , then go to mm files directory by typing `cd MarioMultiverseFiles`
10. run the downloader by typing MarioDownloader_for_username.exe
11. now do as it says (getting the id from the bot, verifying your account), note that pasting is done through rightclick>edit>paste
12. wait for it to finish downloading
13. after it finish, goto to the arrow next to play and select configure, in game options press the 3 dots button next to game executable, navigate to the folder that contains mario multiverse folder, and select Mario.exe, and now you are (almost) ready 2 go

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

to install it, launch protonup-qt, change (install for) to lutris  (bitrate is low idk why) ![[Screencast_20240331_201506.webm]]
click on add version and select DXVK-async and choose install ![[Screencast_20240331_201722.webm]]
now open lutris, choose mario multiverse, click the arrow next to play and choose configure
in system options, scroll down to environment variable, and add these options with values

| key                | value |
| ------------------ | ----- |
| DXVK_ASYNC         | 1     |
| DXVK_GPLASYNCCACHE | 1     |
![[Pasted image 20240331202244.png]]
click on save, and now you should have better performance when using direct x as a render


##### known problems
- when using direct-x as a render for the main game, maximizing the window will result in a worse performance, i don't know a fix for that


### credits
- [u/Curious_Increase_592](https://www.reddit.com/user/Curious_Increase_592/), a member from the great [r/linux_gaming](https://www.reddit.com/r/linux_gaming/) for suggesting dxvk-gplasync