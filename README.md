# ThinkVantage Menu

This repository contains a script for a Rofi-based utility menu I created for my ThinkPad X230, to give the ThinkVantage button some cool functionality.

This script isn't specific to ThinkPad X230s or the ThinkVantage button; you can use it on any hardware! Just keep in mind that a few bits of functionality are specific to Linux Mint or my ThinkPad's hardware, so you may need to adjust some stuff for your system.

## Requirements

This section highlights the package requirements needed to run all the functions in the menu. Some Flatpak packages can be swapped out for APT package equivalents, and vice versa.

Standard system utilities provided by a normal Linux Mint installation (`bash`, `systemd`, `coreutils`, `grep`, `sed`, `awk`, `procps`, `util-linux`, etc.) are assumed to already be present.

### APT packages

```bash
sudo apt install rofi libnotify-bin gnome-terminal xdotool x11-utils brightnessctl copyq xclip hardinfo baobab gnome-disk-utility gnome-logs lm-sensors network-manager network-manager-gnome wavemon blueman gufw iw iputils-ping dnsutils iproute2 pavucontrol fsearch pulseaudio-utils wireshark timeshift qalculate-gtk gpick gucharmap flatpak
```

- `rofi` — menu interface
- `libnotify-bin` — desktop notifications (`notify-send`)
- `gnome-terminal` — terminal windows used by menu utilities
- `xdotool` — active-window detection and activation
- `x11-utils` — provides `xwininfo`, `xprop` and `xkill`
- `brightnessctl` — display brightness control
- `xcalib` — calibrate X display colours
- `copyq` — clipboard history
- `xclip` — reading and clearing the X11 clipboard
- `hardinfo` — hardware information
- `baobab` — disk usage analyser
- `gnome-disk-utility` — GNOME Disks
- `gnome-logs` — graphical system log viewer
- `lm-sensors` — hardware temperature/sensor monitoring
- `network-manager` — provides `nmcli` and `nmtui`
- `network-manager-gnome` — advanced network connection editor
- `wavemon` — wireless network monitor
- `blueman` — Bluetooth manager
- `gufw` — graphical firewall configuration
- `iw` — wireless interface information
- `iputils-ping` — `ping`
- `dnsutils` — DNS lookup tools such as `dig`
- `iproute2` — provides `ip` and `ss`
- `pavucontrol` — advanced audio controls
- `pulseaudio-utils` — provides `pactl`
- `wireshark` — packet capture and network analysis
- `timeshift` — system snapshot utility
- `qalculate-gtk` — calculator
- `gpick` — colour picker
- `gucharmap` — character map
- `flatpak` — required for applications installed through Flatpak

### Flatpak packages

```bash
flatpak install flathub io.missioncenter.MissionCenter io.github.thetumultuousunicornofdarkness.cpu-x com.github.wwmm.easyeffects org.localsend.localsend_app com.github.tchx84.Flatseal
```

- `io.missioncenter.MissionCenter` - Windows-style task manager
- `io.github.thetumultuousunicornofdarkness.cpu-x` - CPU-Z equivalent for Linux
- `com.github.wwmm.easyeffects` - audio effects for Pipewire applications
- `org.localsend.localsend_app` - share files to local devices
- `com.github.tchx84.Flatseal` - manage Flatpak package permissions
- `io.github.cboxdoerfer.FSearch` - advanced file and directory searching

### Mint-specific packages

These packages usually come included with Linux Mint. If you're setting this up on a different distribution, you should substitute these in the script for your system equivalents.

- `cinnamon` — Cinnamon itself and `cinnamon-settings`
- `cinnamon-screensaver` — screen locking
- `cinnamon-session` — logout/session controls
- `nemo` — file manager
- `xed` — text editor
- `mintupdate` — Update Manager
- `warpinator` — local file sharing

## Setup

1. Clone the repository or [download the script directly](https://raw.githubusercontent.com/ashprids/thinkvantage-menu/refs/heads/main/thinkvantage).
2. Move the script to a permanent location
      - I personally store the script in `~/.local/bin` but you can put it anywhere
3. Give the script execute permissions (`chmod +x thinkvantage`)
4. Install the required packages listed above
5. Configure the keyboard shortcut. On Linux Mint:
      1. Search for "Keyboard" and open the settings
      2. Navigate to "Shortcuts"
      3. Click on "Custom Shortcuts" > "Add custom shortcut"
      4. Enter a name. In the "Command" section, put the **absolute** location of your script *(e.g. `/home/username/.local/bin/thinkvantage`)*
      5. Under "Keyboard bindings", double-click one of the `unassigned` options and press the button(s) you wish to assign to the menu

## Rofi Customization

You can select a Rofi theme using the command:

```bash
rofi-theme-selector
```

Check out [this repository by newmanls](https://github.com/newmanls/rofi-themes-collection) for additional themes and how to install them.

## Permissions

Some of the applications/functions require specific permissions to run *(for example, to use the brightness control settings, the user must be in the `video` group)*. I won't highlight which functions require specific permissions because I'm lazy, but the script will notify you if it can't execute any commands.
