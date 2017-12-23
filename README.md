# Connect wan automatically at boot and after a disconnection on OpenWrt
OpenWrt is an open source project for embedded operating system based on Linux, primarily used on embedded devices to route network traffic. I install OpenWrt on my Netgear DGN3500, an ADSL2+ gateway with wireless acccess point integrated. Finally the wifi signal is strong but the internet connection does not go up at boot or after a disconnection.


## Found solutions
I find the following solutions: to schedule the reboot and the reconnections by cron (https://www.youtube.com/watch?v=PfqGr15D4JM), to write a script to reconnect after a disconnection (https://gist.github.com/navhaxs/8029bea3420cdbb11047 https://gist.github.com/ninadpchaudhari/6561841ffc3667b1e5ee) or to insert the command "ifup wan" in the file "/etc/init.d/network".


## Recomended solution
To take all the advantages of the previous solutions i write the script "wanup" to connect the wan and i call its at boot and after the disconnection. To call the script "wanup" at boot you can insert the command "/bin/sh /etc/wanup" int file "/etc/init.d/network" at the end of function "service_running". To call the script "wanup" after a disconnection you can create a script for hotplug and place it in "/etc/hotplug.d/iface".
