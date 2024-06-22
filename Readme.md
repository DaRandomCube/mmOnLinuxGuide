
installing mario multiverse on linux is tricky mainly due to the discord verification and the installer being a cli app


##### requirements
- bottles and flatseal installed via [flatpak](https://flatpak.org/)
- dxvk-gplaasync (to improve direct-x renderer performance)
- system and drivers (including vulkan) are installed and up to date
- discord app installed for verification code, obviously
- [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux) for making discord verification work

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

launch bottles and wait for the setup to finish
go to the 3-dots > preferences, select dll components tab, scroll down to install the latest version of **dxvk-gplasync** as you see in this video, since MM editor perofrmance is bad on regular dxvk
**desclaimar: never use dxvk-gplasync with multiplayer/online games, as it might ban you, regular dxvk works fine with those games**
switch to runners tab, open "soda" card and install soda 8.0-2, as open gl in MM doesn't work with newer version


###### bottle creation and settings

press on the plus icon or the (create new) button and name it, choose gaming instead of applications
after it finishes, goto the bottle > settings and change the runner to soda 8.0-2
![Screenshot_20240622_215944](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/e3738834-ae42-4a32-9339-436da3757236)
make sure that the dxvk option is set to dxvk-gplasync and not to the regular dxvk, did you read the desclaimar anyway?
go down to (dll overrides) and add 'ktmw32' as a new override, keep it (Native, then builtin) unchanged
after you close the pop-up, goto the (environment variables) and add both `DXVK_ASYNC` and `DXVK_GPLASYNCCACHE` with the value of "1" as shown in this video


[](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/85d3687b-2466-4cb4-9439-5f7900aae08e)


##### installing the game

##### installing mario multiverse

###### fixing bottles isolation

flatpak apps are isolated by nature, so it won't be able to access every folder like normal apps, including mario multiverse one, so we need to make a folder for MM and allow bottles to access it

1. make a directory for MM, let's create a one in documents folder and call it MM for example
2. open flatseal, navigate to bottles, scroll down to filesystem section, in (other files) click on the puls icon and enter the MM path and `xdg-data/applications` to be able to add desktop enteries
 
you can get the path by right clicking on MM folder and finding the info section or something similar, if the path doesn't include the MM folder name, you have to include it yourself (don't forgot to add a / if it doesn't exist at the end of previous directory) or you can input the directory manually

3. close flatseal for now, and restart bottles
4. to make accessing the folder easier in bottles, go to the bottle you made > settings, scroll down until you find (manage drives), open it and add a drive and paste the path there (don't forgot what did i say above)

###### the actual install

1. download both of the downloader and the dlls and extract them inside the MM folder we've created earlier
2. go to [DiscordBuddyRedux](https://github.com/batteryshark/DiscordBuddyRedux) github page and download it from the latest release, as shown here, and extract it to MM folder
3. at the end of the bottle page, from legacy wine tools, select explorer
4. go to the mm directory we have created using the drive letter, then click on GenerateDiscordToken.exe (don't worry, even MM settings mentiones it)
![Pasted image 20240329020908](https://github.com/DaRandomCube/mmOnLinuxGuide/assets/93283139/dcdf6085-1b46-452a-a506-3841fba356ca)
5. after it succesfully finish, close the generatediscordtoken.exe and open MarioDownloader_for_username.exe, do what it says and wait for it to download (pasting can be done by right click > edit > paste)

###### adding desktop enteries

1. you will need to add the game's exes you want by pressing on "add shortcuts..." and selecting the exes
2. from the 3-dots menu of each shortcut and clicking (add desktop enetry)
3. that it, enjoy

##### known problems
- when using direct-x as a render for the main game, maximizing the window will result in a worse performance, i don't know a fix for that, use opengl instead

### credits
- [u/Curious_Increase_592](https://www.reddit.com/user/Curious_Increase_592/), a member from the great [r/linux_gaming](https://www.reddit.com/r/linux_gaming/) for suggesting dxvk-gplasync
- @ henrydc (on discord) for most of the guide, otherwise, it will take longer time to figure out the method
- everyone who made the tools used in the guide 
