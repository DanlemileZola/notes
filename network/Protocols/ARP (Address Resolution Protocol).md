*ARP is the mapping of L3 address to L2 address. In other words : mapping of IP addresses to [MAC](MAC) addresses.*[](https://www.practicalnetworking.net/series/arp/address-resolution-protocol/)

# Basic 

On **same network**, if device A want to communicate with device B (knowing it's IP address), it broadcast to the network a request " Whose x.x.x.x IP address is it ? I need your MAC address . There is mine. "
All device on network (including the default gateway e.g router) will receive that request and drop it if not concerned. 

Device B will then reply " It's my IP address, there is my MAC address ", in unicast to device A. 
Device A will then update its ARP table.

If the final destination is on **foreign network**, the initial ARP request will not be directly address to device B (since device A know that x.x.x.x IP address is not on same network in that case).
In that case, the request is broadcast using the router IP addresses (and dropped by other devices) which reply by its own MAC address. 

But how does device A manage to send its packet to the correct end device ? 