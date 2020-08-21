# pop-os-setup-xps
Setup steps for Pop! OS on Dell XPS 13 9300

## Appearance

1. Install Gnome Tweak Tool `sudo apt install gnome-tweak-tool`
2. In Gnome Tweak Tool, disable: Desktop Icons
3. In Gnome Tweak Tool, enable: Battery Percentage (Top Bar), Weekday (Top Bar), Week Numbers (Top Bar)
4. Install [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
5. In Gnome Tweak Tool > Extensions > Dock to Dash, set: Position to Bottom, Hide favorite applications, Hide application icon, Shrink dash, Icon size: 64, Window Counter indicators to Dashes, Opacity 50%, Force straight corner

### Reduce title bar height

`sudo gedit ~/.config/gtk-3.0/gtk.css`

```
headerbar entry,
headerbar spinbutton,
headerbar button,
headerbar separator {
    margin-top: 0px; /* same as headerbar side padding for nicer proportions */
    margin-bottom: 0px;
}

headerbar {
    min-height: 24px;
    padding-left: 2px; /* same as childrens vertical margins for nicer proportions */
    padding-right: 2px;
    margin: 0px; /* same as headerbar side padding for nicer proportions */
    padding: 0px;
  }
  
  /* No line below the title bar */
.ssd .titlebar {
    border-width: 0;
    box-shadow: none;
}
```

### Enable fractional scaling

`gsettings set org.gnome.mutter experimental-features "['x11-randr-fractional-scaling']"

## Power Management

1. Install tlp `sudo apt install tlp tlp-rdw`
2. Install Powertop `sudo apt install powertop` [Steps](https://support.system76.com/articles/battery/)
3. Install [Caffeine](https://extensions.gnome.org/extension/517/caffeine/)

## Fan Management

[Instructions](https://medium.com/@mijorus/thermal-tweaks-on-dell-laptops-running-linux-769c8c80022e)

## Terminal

- Change copy+paste shortcuts

## Coding Environment

1. Set git credentials: `git config --global user.name "Dennis Schoepf" && git config --global user.email "dennis@schoepf.co"`
2. Set up ssh keys `ssh-keygen`
3. Install [zsh](https://github.com/ohmyzsh/ohmyzsh)

## Browser

1. [Install Brave](https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux) 
2. Add extensions: 1Password, React DevTools

## Pop Shop

Install:

- VS Code
- Spotify
- Flameshot
- Ferdi

## I/O

1. Install [fusuma](https://github.com/iberianpig/fusuma)
2. Add `fusuma --daemon`in Startup Applications
3. `sudo gedit ~/.config/fusuma/config.yml` with the following content:

```
swipe:
  3:
    left:
      command: 'xdotool key super'
    up:
      command: 'xdotool key super+Up'
    down:
      command: 'xdotool key super+Down'

threshold:
  swipe: 0.5

interval:
  swipe: 0.2
```

## Authentication

### Fingerprint reader

```
sudo sh -c 'cat > /etc/apt/sources.list.d/focal-dell.list << EOF
deb http://dell.archive.canonical.com/updates/ focal-dell public
# deb-src http://dell.archive.canonical.com/updates/ focal-dell public

deb http://dell.archive.canonical.com/updates/ focal-oem public
# deb-src http://dell.archive.canonical.com/updates/ focal-oem public

deb http://dell.archive.canonical.com/updates/ focal-somerville public
# deb-src http://dell.archive.canonical.com/updates/ focal-somerville public

deb http://dell.archive.canonical.com/updates/ focal-somerville-melisa public
# deb-src http://dell.archive.canonical.com/updates focal-somerville-melisa public
EOF'
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9FDA6BED73CDC22
sudo apt update -qq

sudo apt install oem-somerville-melisa-meta libfprint-2-tod1-goodix oem-somerville-meta tlp-config -y
```
Then restart.
