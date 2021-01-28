# raspberry

## Install raspbian lite
1. Download the image of the OS at https://www.raspberrypi.org/software/operating-systems/
2. Download Balena Etcher (https://www.balena.io/etcher/) and use it to copy the image into the microSD
3. Put the microSD into the Raspberry and switch it on
4. Default credential to access:
   * user: pi
   * pass: raspberry


## Configure keyboard
To configure the keyboard layout launch:
```
sudo raspi-config
```

Then select *Localization Option*, *Keyboard*, and look for the desired layout.


## Change the default user
Add a new user:
```
sudo adduser <your user>
```

Give sudoers permission to the new user:
```
sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi <your user>
```

Now, delete the pi user:
```
sudo pkill -u pi
sudo deluser pi
sudo deluser -remove-home pi
```

Provide password to sudo:
```
sudo visudo /etc/sudoers.d/010_pi-nopasswd
```

Then, Nano will open. Substitute what is there with:
```
<your user> ALL=(ALL) PASSWD: ALL
```


## Connect to wifi
To configure the wifi launch:
```
sudo raspi-config
```

Select *Localization Option*, *WLAN Country*, and select your country. Then, go back to the home menu of the configurator, and select *System Options*, *Wireless LAN*, and put the name of your network (SSID) and the password.


## Change hostname
To change the name of the machine (hostname), run the configurator:
```
sudo raspi-config
```

Then select *System Options*, *Hostname*, and change it. Reboot at the end.


## Enable ssh to log to the raspberry from another device
Enable ssh on the machine:
```
sudo systemctl enable ssh
sudo systemctl start ssh
```

And then, to connect within the same network from another device:
```
ssh <your user>@<new hostname>
```


## Install basic packages
First, update the index:
```
sudo apt-get update
```

Then install the following:
```
sudo apt install git
sudo apt install python3-pip
sudo apt-get install libatlas-base-dev
```


## Set Python 3 as base interpreter
It is necessary to create alternative interpreters to handle it correctly. The command to install new alternatives is:
```
sudo update-alternatives --install /usr/bin/python python /usr/bin/<Python interpreter> <priority>
```

To install such alternatives:
```
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 2
```

For pip, do exactly the same:
```
sudo update-alternatives --install /usr/bin/pip pip /usr/bin/pip3 1
```

## Install Python libraries
```
pip install jupyterlab
pip install pandas
pip install numpy
pip install requests
pip install python-Levenshtein
pip install networkx
```
