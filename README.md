# Linux Terminal Command Cheatsheet:

**[Created by yesmaybenookay](https://github.com/yesmaybenookay)**

---

## Table of Contents:

1. [Description](https://github.com/yesmaybenookay/terminal-cheatsheet#description)
2. [Formatting Legend](https://github.com/yesmaybenookay/terminal-cheatsheet#formatting-legend)
3. [Antivirus / Security](https://github.com/yesmaybenookay/terminal-cheatsheet#antivirus--security)
4. [Tools / Useful Commands](https://github.com/yesmaybenookay/terminal-cheatsheet#tools--useful-commands)
5. [One Word Tools / Useful Commands](https://github.com/yesmaybenookay/terminal-cheatsheet#one-word-tools--useful-commands)
6. [Fun Terminal Commands](https://github.com/yesmaybenookay/terminal-cheatsheet#fun-terminal-commands)
7. [One Word and Short Commands](https://github.com/yesmaybenookay/terminal-cheatsheet#one-word-and-short-commands)
8. [Footnotes](https://github.com/yesmaybenookay/terminal-cheatsheet#footnotes)

---

## Description:

The Linux Terminal Command Cheatsheet is my collection of cheatsheets I've made for various command line tools I use on Fedora Linux. The contents here only cover a small portion of what some of these tools can do so be sure to explore more with ```[command] --help``` or ```man [command]```. Additionally, I've tried to include at least one URL linking to additional info / help for each tool.

---

## Formatting Legend:

### Program Name:

(*Short Explanation*)

[Helpful Link]()

* Notes / Useful Information `PATH/TO/CONFIG_FILE/FOR/EXAMPLE/.config`

Template for Copying and Pasting:

```sh
sample_command --sample_option
```

Prefilled Template Variations:

```sh
sample_command --sample_option --sample_option_2
```

---

## Antivirus / Security:

### ClamAV:

(*Antivirus*)

[How to Install and use ClamAV](https://linuxhint.com/install_clamav_ubuntu/)

Update ClamAV's Database (*"-v" is for verbose*):

```sh
sudo freshclam -v
```

Begin scan and display infected files (*"-r" is for recursive, "-i" is for displaying infected files only*):

```sh
sudo clamscan -r -i /DIRECTORY_TO_SCAN
```

### Maldet:

(*Malware detection and removal*)

[Maldet Commands](https://blog.first2host.co.uk/maldet-commands/)

Update malware detection signatures:

```sh
sudo maldet -u
```

Update Maldet:

```sh
sudo maldet -d
```

Scan path to folder / file:

```sh
sudo maldet -a /PATH/TO/FOLDER/FILE
```

### Rootkit Hunter:

(*Identify rootkits and potential threats*)

[How to Use Rootkit Hunter](https://blackhattutorial.com/how-to-use-rkhunter-to-guard-against-rootkits/)

Fill Rootkit Hunter's database properties:

```sh
sudo rkhunter --update
```

```sh
sudo rkhunter --propupd
```

Start scanning the entire file system:

```sh
sudo rkhunter --check
```

---

## Tools / Useful Commands:

### [browsh](https://github.com/browsh-org/browsh):

(*Text-based web browser capable of displaying graphics*)

[Browsh Website](https://www.brow.sh/)

* Config file Location: `$HOME/.config/browsh/config.toml`

```sh
browsh
```

### Date and Time:

(*Display live date and time*)

```sh
while true; do echo -ne "`date`\r"; done
```

### dict:

(*Dictionary / thesaurus*)

[Dictd – Using a Linux Command Line Dictionary](https://www.putorius.net/linux-command-line-dictionary.html#list-available-databases)

* In all dict commands below, replace "WORD" with a word of your choosing  and "DICTIONARY" with the dictionary you want to use (*list installed dictionaries with* ```dict -D```):

Install dictd:

```sh
sudo dnf install dictd -y
```

Install local databases for offline use:

```sh
sudo dnf install gnome-dictionary -y
```

Search the Internet for definitions and thesaurus entries:

```sh
dict WORD
```

Use local dictionary database:

```sh
dict -d DICTIONARY WORD
```

List all available local dictionaries:

* There are bilingual dictionaries for translating as well as other interesting ones such as ```moby-thesaurus``` ([Moby Thesaurus](https://moby-thesaurus.org/)) and ```devil``` ([The Devil's Dictionary](https://en.wikipedia.org/wiki/The_Devil%27s_Dictionary)).

```sh
dict -D
```

Show information about a dictionary:

```sh
dict -i DICTIONARY
```

Show translations in every available bilingual dictionary:

```sh
dict -d trans WORD
```

Show translations in every available dictionary:

```sh
dict -d all WORD
```

Show [Moby Thesaurus](https://moby-thesaurus.org/) entries:

```sh
dict -d moby-thesaurus WORD
```

### livecd-iso-to-disk:

(*Bootable drive creation only available on Fedora*)

* [Creating and using a live installation image](https://docs.fedoraproject.org/en-US/quick-docs/creating-and-using-a-live-installation-image/)
* [livecd-tools Documentation](https://github.com/livecd-tools/livecd-tools/blob/main/docs/livecd-iso-to-disk.pod)
* *I'm confused about using* ```--home-size-mb``` *and* ```--overlay-size-mb``` *so please reach out if you can help. (See [1. Notes on Persistence](https://github.com/yesmaybenookay/terminal-cheatsheet#1-notes-on-persistence))* 
* Replace "DISKIMAGE" with the name of the ISO you want to use
* Replace "DISKLABEL" with the label of the disk you want to use (*use* ```df``` *or* ```lsblk``` *to find the correct disk label*)

```sh
sudo livecd-iso-to-disk --format --reset-mbr DISKIMAGE.iso /dev/DISKLABEL
```

### mariadb:

(*MySQL Alternative*)

Start MariaDB:

```sh
sudo systemctl start mariadb
```

Stop MariaDB:

```sh
sudo systemctl stop mariadb
```

### [speedread](https://github.com/pasky/speedread):

(*Learn to speedread*)

* Start at the default words per minute ("-w 250") (*250 wpm is a good speed for absolute beginners.*)
* Press "[" to slow down by 10%
* Press "]" to speed up by 10%
* Press "space" to pause and show the last two lines of context

```sh
cat FILENAME.txt | ./speedread -w 250
```

---

## One Word Tools / Useful Commands: 

### cal:

(*Calendar for the current month*)

```sh
cal
```

### factor:

(*Display factors of a number*)

* Replace "NUMBER" with a number

```sh
factor NUMBER
```

### w:

(*Display information about current users such as name and login time*)

```sh
w
```

---

## Fun Terminal Commands:

### espeak:

(*Text to speech*)

Speak YOURTEXT:

```sh
espeak "YOURTEXT"
```

My template (*"-a" is for amplitude, -g is for word gap, "-p" is for pitch, -s is speed in word per minute, and -v is for voice*):

```sh
espeak -a 200 -g 11 -p 99 "YOURTEXT" -s 110 -v en-us
```

Use [```godspeaks```](https://github.com/yesmaybenookay/terminal-cheatsheet#godspeaks) to generate text to speak:

```sh
python godspeaks.py | espeak -a 200 -g 11 -p 99 -s 110 -v en-us
```

*My favorite voices:*

 * af
 * en
 * en-us
 * ru
 * vi
 * vi-hue
 * vi-sgn
 * zh
 * zh-yue

### [godspeaks](https://github.com/rethyxyz/godspeaks):

(*rethyxyz's Python port of Terry A. Davis's (R.I.P.) God Speaks a.k.a. God Says program.*)

Generate 31 words / phrases:

```sh
python godspeaks.py
```

Interactive Mode (*Generate 3 sets of 31 words / phrases with an option to generate 3 more sets*):

```sh
python GodSpeaks.py
```

Works great with Phosphor in XScreenSaver:

```sh
phosphor -root -scale 3 -ticks 5 -delay 35000 -program "cd /PATH/TO/GodSpeaks/ && python godspeaks.py" -fg red
```

Also works great with [espeak](https://github.com/yesmaybenookay/terminal-cheatsheet#espeak):

```sh
python godspeaks.py | espeak -a 200 -g 11 -p 99 -s 110 -v en-us
```

---

## One Word and Short Commands:

### banner

(*Bannerize inputted text*)

* Replace YOURTEXT with what you want to bannerize

```sh
banner YOURTEXT
```

### cmatrix

(*Create a matrix code rain effect in your terminal*)

```sh
cmatrix
```

### figlet

(*Bannerize inputted text*)

* Replace YOURTEXT with what you want to bannerize

```sh
figlet YOURTEXT
```

### fortune

(*Display a random "fortune"*)

```sh
fortune
```

Works great with Phosphor in XScreenSaver:

* [2. Phosphor XScreenSaver Settings for fortune](https://github.com/yesmaybenookay/terminal-cheatsheet#2-phosphor-xscreensaver-settings-for-fortune)

### oneko

(*A cat [or one of a few other bitmaps] which follows your mouse*)

```sh
oneko
```

### sl

(*A locamotive in your terminal*)

```sh
sl
```

### Telnet Star Wars

(*The full movie, Star Wars: A New Hope, displayed with ASCII characters*)

```sh
telnet towel.blinkenlights.nl
```

### toilet

(*Bannerize inputted text*)

* Replace YOURTEXT with what you want to bannerize

```sh
toilet YOURTEXT
```

### yes

(*Repeatedly display your text until interrupted*)

```sh
yes YOURTEXT
```

---

## Footnotes

### 1. Notes on Persistence

**Limited Lifetime of Persistent Overlay**

One very important note about using the "primary" persistent overlay for system changes is that due to the way it's currently implemented (as a Device-mapper copy-on-write snapshot), every single change to it (writes AND deletes) subtracts from its free space, so it will eventually be "used up" and your USB stick will no longer boot [see this dm-devel discussion](http://thread.gmane.org/gmane.linux.kernel.device-mapper.devel/14644) and [this page](https://fedoraproject.org/wiki/LiveOS_image#Overlay_recovery) (for emergency recovery). Because of these limitations, it is advisable to use the system-level persistence sparingly, for configuration changes and important security updates only. Or, if you have sufficient disk space available, changes to the LiveOS root filesystem snapshot can be merged into a new copy of the root filesystem. See [this page section](https://fedoraproject.org/wiki/LiveOS_image#Merge_overlay_into_new_image) for instructions.

See [this section](https://fedoraproject.org/wiki/User:Nicolassatragno/liveUSB#Mounting_a_Live_USB_filesystem) for mounting the root filesystem outside of a boot.

For normal, write-many storage (vs the write-once overlay), use the ```--home-size-mb``` option to create a home directory filesystem for personal files. The home.img can be re-used and loop mounted outside of the Live USB environment.

[*Full Documentation*](https://docs.fedoraproject.org/en-US/quick-docs/creating-and-using-a-live-installation-image/)

### 2. Phosphor XScreenSaver Settings for fortune

* Open XScreenSaver > Phosphor > Settings > Advanced > Copy and Paste the following code:

```sh
phosphor -root -scale 2 -ticks 5 -delay 35000 -program "fortune" -fg red
```
