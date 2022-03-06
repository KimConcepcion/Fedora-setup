# Fedora-setup
Just a collection of config files for my Fedora setup

# Fancontrol
### Prerequisites
* lm-sensors
* pwmconfig
* fancontrol

#### lm-sensors setup
First detect sensors in your system:
$ sudo sensors-detect

Check if detected sensors are correct:
$ sudo sensors

#### pwmconfig
Test all fans in your system and configure min/max temp/rpm for each fan and generate output config file e.g. In /etc/fancontrol
The pwmconfig cmd will guide you through the configuration of each fan. Beware that during each test, each fan will be shortly turned off. 
This might result in an increase in the cpu temperature.  
$ sudo pwmconfig

#### Enable fancontrol as service, to enable fancontrol at startup { Only tested with systemd :-) }
sudo systemctl enable fancontrol.service

#### Restart fancontrol service
sudo systemctl restart fancontrol.service

#### Additional info
The hwmon path might change due to kernel updates etc.
You can scan your sensors again with sensors-detect and redo the fan configuration with pwmconfig to resolve the paths issue.
