# Python libraries

This document contains instruction to set up Python 3 as default interpreter and list basic libraries to install in the system.

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

All the Python libraries to install are available in the file [requirements.txt](requirements.txt). To install all, run the following command:

```
pip install -r requirements.txt
```