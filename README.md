# Linux Terminal Command Cheatsheet | **[Created by yesmaybenookay](https://github.com/yesmaybenookay)**

---

## Table of Contents:

1. [Description]()
2. [Formatting Legend]()
3. [Antivirus / Security]()
4. [Tools / Useful Commands]()
5. [One Word Tools / Useful Commands]()
6. [Fun Terminal Commands]()
7. [One Word and Short Commands]()
8. [Footnotes]()

---

## Description

The Linux Terminal Command Cheatsheet is my collection of cheatsheets I've made for various command line tools. The contents here only cover a small portion of what some of these tools can do so be sure to explore more with ```[command] --help``` or ```man [command]```. Additionally, I've tried to include at least one URL linking to additional info / help for each tool. 

---

## Formatting Legend:

### Program Name: (*Short Explanation*)

[Helpful Link](https://github.com)

* Notes / Useful Information `PATH/TO/CONFIG_FILE/FOR/EXAMPLE/.config`

**Command Template**

```sh
sample_command --sample_option # For some programs, I've created a template for ease of use
```

**Commands / Edited Template Variations**

```sh
sample_command --sample_option --sample_option_2 # Commands, each line being a new command (some are in succession to the command above).
```

---

## Antivirus / Security:

### ClamAV: (*Antivirus*)

[How to Install and use ClamAV](https://linuxhint.com/install_clamav_ubuntu/)

```sh
sudo freshclam -v          # Updates ClamAV's Database
sudo clamscan -r -i /      # Begins scan and only prints infected files
```

### Maldet: (*Malware detection and removal*)

[Maldet Commands](https://blog.first2host.co.uk/maldet-commands/)

```sh
sudo maldet -u                       # Updates malware detection signatures
sudo maldet -d                       # Updates Maldet
sudo maldet -a /path/to/folder/file  # Scans path to folder / file
```

### Rootkit Hunter: (*Identifies rootkits and potential threats*)

[How to Use Rootkit Hunter](https://blackhattutorial.com/how-to-use-rkhunter-to-guard-against-rootkits/)

```sh
sudo rkhunter --update     # This and the second command fill Rootkit Hunter's database properties
sudo rkhunter --propupd
sudo rkhunter --check      # Starts scanning the entire file system
```

---

## Tools / Useful Commands:

### browsh: (*Text-based web browser capable of displaying graphics*)

[browsh](https://www.brow.sh/)

* Config file Location: `$HOME/.config/browsh/config.toml`

```sh
curl -o browsh.rpm -L https://github.com/browsh-org/browsh/releases/download/v1.6.4/browsh_1.6.4_linux_amd64.rpm
sudo rpm -Uvh ./browsh.rpm
rm ./browsh.rpm
browsh
```

### Date and Time *Display live date and time*

```sh
while true; do echo -ne "`date`\r"; done
```

### dd: (*Creates a bootable drive*)

```sh
$ dd if=/home/user/Downloads/ubuntu.iso of=/dev/sdb1 bs=512M; sync
```

### dict: (*Dictionary / thesaurus*)

[Dictd – Using a Linux Command Line Dictionary](https://www.putorius.net/linux-command-line-dictionary.html#list-available-databases)

```sh
sudo dnf install dictd -y            # Installs dictd
sudo dnf install gnome-dictionary -y # Installs local databases for offline use
dict [word]                          # Searches the Internet for definitions and thesaurus entries
dict -d [dictionary] [word]          # Uses local dictionary database
dict -D                              # Lists all available local dictionaries
dict -i [dictionary]                 # Shows information about a dictionary
dict -d [fd-eng-2ND_LANG] [word]     # Shows translations
dict -d trans [word]                 # Shows translations in every available dictionary
dict -d moby-thesaurus [word]        # Shows Moby Thesaurus entries
```

### livecd-iso-to-disk (*Bootable drive creation only available on Fedora*)

[Creating and using a live installation image](https://docs.fedoraproject.org/en-US/quick-docs/creating-and-using-a-live-installation-image/)
[livecd-tools Documentation](https://github.com/livecd-tools/livecd-tools/blob/main/docs/livecd-iso-to-disk.pod)
[^1: Expanded livecd-iso-to-disk Cheatsheet]

**Template**

```sh
sudo livecd-iso-to-disk --format --reset-mbr --home-size-mb HOMESIZEMB --overlay-size-mb OVERLAYSIZEMB DISKIMAGE.iso /dev/DISKLABEL
```

**Create a bootable USB stick in the directory the ISO is located:**

*replace "X" in "sdX" with the target drive, ex. "sdc"*

```sh
sudo livecd-iso-to-disk --format --reset-mbr Fedora-Security-Live-x86_64-34-1.2.iso /dev/sdX
```

### mariadb: *MySQL Alternative*

```sh
sudo systemctl start mariadb
sudo systemctl stop mariadb
```

### [speedread](https://github.com/pasky/speedread) *Learn to speedread*

*Displays a body of text one word at a time to train speedreading ability. To help you get used to speedreading, the default setting is 250 words per minute.*

```sh
cat tea.txt | ./speedread -w 250
```

* *[ - slow down by 10%*
* *] - speed up by 10%*
* *space - pause (and show the last two lines of context)*

---

## One Word Tools / Useful Commands: 

```sh
cal # Calendar
```

```sh
factor # "factor [number]"
```

```sh
pi # "pi [number]"
```
```sh
w # Shows information about current users such as name and login time
```

```sh
wikit # Search Wikipedia
```

---

## Fun Terminal Commands:

### espeak: *Text to speech*

```sh
espeak -a 200 -g 11 -p 99 "TYPE YOUR TEXT HERE" -s 110 -v en-us
espeak -a 200 -g 11 -p 99 -s 110 -v en-us ""
```

*Decent Voices*
 * af
 * en
 * en-us
 * ru
 * vi
 * vi-hue
 * vi-sgn
 * zh
 * zh-yue

### lolcat: *Outputs text with a rainbow effect*

```sh
lolcat [OPTION]... [FILE]...
```

---

## One Word and Short Commands:

```sh
banner # Banner [your text here] - Bannerizes inputted text
cmatrix # Creates a matrix code rain effect in your terminal
cowsay # ASCII cow with a customizable message
figlet # figlet [your text here] - Bannerizes inputted text
fortune # Spits out a random "fortune"
oneko # A cat [or a few other bitmaps] which follows your mouse
sl # A locamotive in your terminal
telnet towel.blinkenlights.nl # ASCII Star Wars: A New Hope
toilet # toilet [your text here] - Bannerizes inputted text
yes # "yes [your text here]" - Repeats your text until interrupt
```

---

## Footnotes

[^1]: Expanded livecd-iso-to-disk Cheatsheet

    [*Full Documentation*](https://docs.fedoraproject.org/en-US/quick-docs/creating-and-using-a-live-installation-image/)

    **Limited Lifetime of Persistent Overlay**

    One very important note about using the "primary" persistent overlay for system changes is that due to the way it's currently implemented (as a Device-mapper copy-on-write snapshot), every single change to it (writes AND deletes) subtracts from its free space, so it will eventually be "used up" and your USB stick will no longer boot [see this dm-devel discussion](http://thread.gmane.org/gmane.linux.kernel.device-mapper.devel/14644) and [this page](https://fedoraproject.org/wiki/LiveOS_image#Overlay_recovery) (for emergency recovery). Because of these limitations, it is advisable to use the system-level persistence sparingly, for configuration changes and important security updates only. Or, if you have sufficient disk space available, changes to the LiveOS root filesystem snapshot can be merged into a new copy of the root filesystem. See [this page section](https://fedoraproject.org/wiki/LiveOS_image#Merge_overlay_into_new_image) for instructions.

    See [this section](https://fedoraproject.org/wiki/User:Nicolassatragno/liveUSB#Mounting_a_Live_USB_filesystem) for mounting the root filesystem outside of a boot.

    For normal, write-many storage (vs the write-once overlay), use the ```--home-size-mb``` option to create a home directory filesystem for personal files. The home.img can be re-used and loop mounted outside of the Live USB environment.