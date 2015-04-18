# Cyber Defense Competition Network Traffic Visualization
This display was developed to display network traffic in real time during the 2015 Palmetto Cyber Defense Competition. Packets sent back and forth between the 8 Blue Teams and 1 Red Team are visualized on the screen and vary in size and color based on protocol and packet size. The visual code is inspired by the 2014 DefCon CTF display by [LegitBS](https://github.com/legitbs/finals-2014) under *tablemap*. As such, I kept the same license, but their code was really only used as reference. 

## Install
The following command should be run to install all the dependencies required (tested on Ubuntu 14.10 x64):
```
# sudo apt-get install python-scapy python-pip redis-server
# sudo pip install tornado tornado-redis redis netaddr
```
Make sure in **/etc/redis/redis.conf** to change *bind 127.0.0.1* to *bind 0.0.0.0* if you plan on putting the **DataServer** component on a different machine than the **DisplayServer** component.

Additionally, make sure that the WebSocket address in **/DisplayServer/index.html** points back to the IP address of the DisplayServer. This way the browser knows the address of the WebSocket.

Finally, if you want to run this, you need to modify the IP address ranges of the Blue Teams and Red Team in the DataServer to match those that you're using. It is possible to provide a single IP address as a valid range when testing if you use a /32 subnet mask.

## Bugs, Feedback, and Questions
If you find any errors or bugs, please let me know. Questions and feedback are welcome, and can be sent to sjcappella at gmail dot com, or you can open an issue on this repository.
