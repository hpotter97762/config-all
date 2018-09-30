# config-all
All configuration files I have ever generated for any application or for linux

# sublime build
Put sublime build and snippet files in sublime-text/Packages/User/ folder
In case of Linux Sublime-text: .config/sublime-text/

# audio control
Install pavucontrol and pulseaudio
Unmute speakers from input and output devices tab in pavucontrol

# Brightness conrol:
run: sudo find /sys/ -type f -iname '*brightness*'
One of the output will be like : /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness

Then run: sudo ln -s /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight /sys/class/backlight
Output -:ln: failed to create symbolic link '/sys/class/backlight/intel_backlight': File exists
Reboot the system afterwards
if still not resolved create a file /etc/X11/xorg.conf with following content:
Section "Device"
        Identifier  "Intel Graphics" 
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
EndSection
Now reboot

#suspend service
This is to first lock the system with i3lock and then suspend the system.
Add the suspend@aditya.service file in /lib/systemd/system folder.
Run systemctl enable suspend@aditya.service

