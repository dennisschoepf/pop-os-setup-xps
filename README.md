# pop-os-setup-xps
Setup steps for Pop! OS on Dell XPS 13 9300

## Appearance

1. Install Gnome Tweak Tool `sudo apt install gnome-tweak-tool`
2. In Gnome Tweak Tool, disable: Desktop Icons
3. In Gnome Tweak Tool, enable: Battery Percentage (Top Bar), Weekday (Top Bar), Week Numbers (Top Bar)
4. Install [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
5. In Gnome Tweak Tool > Extensions > Dock to Dash, set: Position to Bottom, Hide favorite applications, Hide application icon, Shrink dash, Icon size: 64, Window Counter indicators to Dashes, Opacity 50%, Force straight corner

## Power Management

1. Install tlp `sudo apt install tlp tlp-rdw`
2. Install Powertop `sudo apt install powertop` [Steps](https://support.system76.com/articles/battery/)
3. Install [Caffeine](https://extensions.gnome.org/extension/517/caffeine/)

## Fan Management

[Instructions](https://medium.com/@mijorus/thermal-tweaks-on-dell-laptops-running-linux-769c8c80022e)

## Terminal

## Coding Environment

1. Set git credentials: `git config --global user.name "Dennis Schoepf" && git config --global user.email "dennis@schoepf.co"`
2. Set up ssh keys `ssh-keygen`

## Browser

1. [Install Brave](https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux) 
2. Add extensions: 1Password, React DevTools

## Pop Shop

Install:

- VS Code
- Spotify
- Flameshot
- Ferdi

