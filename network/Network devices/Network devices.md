*The OSI reference model was developed to help disparate devices communicate on networks.
Device may be classified by the level of the OSI model at which they operate. *
# Layer 1 devices

The [analog modem](analog%20modem) **modulates** a digital signal into an analog signal and **demodulates** the return signal to allow for network communication. 

Computer <-- digital --> \[Modem] <-- analog --> Internet. 

The [hub](hub) receives a network signal on a port and replicates that signal out all of the remaining ports. Work as a concentrator/repeater. 

They are use to create connections between network segments 
via the [Public Switched Telephone Network (PSTN)](Public%20Switched%20Telephone%20Network%20(PSTN)) using the 
[Plain Old Telephone System (POTS)](Plain%20Old%20Telephone%20System%20(POTS)).

# Layer 2 devices

The [switch](switch) utilizes an [Application-Specific Integrated Chip (ASIC)](Application-Specific%20Integrated%20Chip%20(ASIC)) to learn which devices are connected to which ports via the devices Layer 2 [MAC address](MAC%20address). When the switch receives network traffic, it will only forward that traffic to the specified MAC address. 
The [Wireless Access Point (WAP)](Wireless%20Access%20Point%20(WAP)) is used to bridge wireless network segments with wired network segments. 
Both only communicate with the local network. 

# Layer 3 devices

The [Multi-Layer Switch (MLS)](Multi-Layer%20Switch%20(MLS)) operates at more than just Layer 2 of the [OSI model](OSI%20model.md). The most common MLS is the Layer 3 switch. The ASIC chip is programmed to handle more than just the Layer 2 MAC address, dealing with routing too. 
The [router](router) is the most common device used to connect different networks together. It utilizes software programming to learn about routes between networks, making it more efficient.
Both communicate with local and non-local networks.

# Security devices 

Operating as the first line of defense, there is the [firewall](firewall), which can be an appliance or software based. It blocks packets from entering of leaving the network, through one or two methods: stateless inspection (it examine each packets against a set of rule) or stateful inspection (only examine the state of connection between networks).
An [Intrusion Detection System (IDS)](Intrusion%20Detection%20System%20(IDS)) are passive and identify when a network breach or attack against the network is occurring. It evaluates all traffic against a set of standards : signature based (evaluates for know malware or attack signatures), anomaly based (evaluates for suspicious changes) or policy based (evaluates network traffic against a specific declared security policy).
An [Intrusion Prevention System (IPS)](Intrusion%20Prevention%20System%20(IPS)) is placed inline with network traffic and will take action when malicious activities are detected to actively stop it. All traffic flows through the IPS and evaluates against a set of standards. 

# Optimization and performances devices 

A [load balancer](load%20balancer) (also know as a content switch or content filter) is a network appliance that will balance requests across multiple devices that contain the same data to avoid overloading. 
A [proxy](proxy) server acts on behalf of a client device to fulfill requests to retrieve data. It can also be used to limit what requests are fulfilled. 
