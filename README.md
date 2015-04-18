## Cyber Defense Competition Network Traffic Visualization
This display was developed to display network traffic in real time during the 2015 Palmetto Cyber Defense Competition. Packets sent back and forth between the 8 Blue Teams and 1 Red Team are visualized on the screen and vary in size and color based on protocol and packet size. The visual code is inspired by the 2014 DefCon CTF display by [LegitBS](https://github.com/legitbs/finals-2014) under *tablemap*. As such, I kept the same license, but their code was really only used as reference. Click [here](https://www.youtube.com/watch?v=VnnHz2Izbz0) for a demo on YouTube.

### Install
The following commands should be run to install all the dependencies required (tested on Ubuntu 14.10 x64):
```
# sudo apt-get install python-scapy python-pip redis-server
# sudo pip install tornado tornado-redis redis netaddr
```
Make sure in **/etc/redis/redis.conf** to change *bind 127.0.0.1* to *bind 0.0.0.0* if you plan on putting the **DataServer** component on a different machine than the **DisplayServer** component.

Additionally, make sure that the WebSocket address in **/DisplayServer/index.html** points back to the IP address of the **DisplayServer**. This way the browser knows the address of the WebSocket.

Finally, if you want to run this, you need to modify the IP address ranges of the Blue Teams and Red Team in the **DataServer** to match those that you're using. It is possible to provide a single IP address as a valid range when testing if you use a /32 subnet mask. Note, however, that if you are testing this on your LAN, you'll want to make 1 machine your Red Team, and the rest your Blue Teams and you MUST comment out the Blue Team same subnet detection in the **DataServer**. If you look at the code, you'll see a comment where this is. Otherwise the **DataServer** will realize that all your traffic is in the same subnet and shouldn't be displayed. 

### Setup
The recommended setup to run this during a competition is in whatever configuration you can dedicate 3 interfaces (at least 2 physical) to this software. The **DataServer** should have 2 interfaces, one that gets a direct mirror port out of the switch all your traffic is going through, and an interface to connect to the **DisplayServer**. This is the same interface that the Redis Database should be listening on as well. The **DisplayServer** is recommended to have 2 interfaces as well, 1 interface that connects back to the **DataServer** and Redis database, and a separate interface that viewers can access via a browser. The interface that the **DisplayServer** and **DataServer** use to communicate can be localhost. 

To actually view the traffic, get everything up and running and connect a browser to the IP address of the **DisplayServer** on port 8888. In my experience, Chrome is the best browser.

### Bugs, Feedback, and Questions
If you find any errors or bugs, please let me know. Questions and feedback are welcome, and can be sent to sjcappella at gmail dot com, or you can open an issue on this repository.
