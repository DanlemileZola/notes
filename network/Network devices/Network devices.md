*The OSI reference model was developed to help disparate devices communicate on networks.
Device may be classified by the level of the OSI model at which they operate. *
# Layer 1 devices

The [[analog modem]] **modulates** a digital signal into an analog signal and **demodulates** the return signal to allow for network communication. 

Computer <-- digital --> \[Modem] <-- analog --> Internet. 

The [[hub]] receives a network signal on a port and replicates that signal out all of the remaining ports. Work as a concentrator/repeater. 

They are use to create connections between network segments 
via the [[Public Switched Telephone Network (PSTN)]] using the 
[[Plain Old Telephone System (POTS)]].

# Layer 2 devices

The [[switch]] utilizes an [[Application-Specific Integrated Chip (ASIC)]] to learn which devices are connected to which ports via the devices Layer 2 [[MAC address]]. When the switch receives network traffic, it will only forward that traffic to the specified MAC address. 
The [[Wireless Access Point (WAP)]] is used to bridge wireless network segments with wired network segments. 
Both only communicate with the local network. 

# Layer 3 devices

The [[Multi-Layer Switch (MLS)]] operates at more than just Layer 2 of the [[OSI model]]. The most common MLS is the Layer 3 switch. The ASIC chip is programmed to handle more than just the Layer 2 MAC address, dealing with routing too. 
The [[router]] is the most common device used to connect different networks together. It utilizes software programming to learn about routes between networks, making it more efficient.
Both communicate with local and non-local networks.

# Security devices 

Operating as the first line of defense, there is the [[firewall]], which can be an appliance or software based. It blocks packets from entering of leaving the network, through one or two methods: stateless inspection (it examine each packets against a set of rule) or stateful inspection (only examine the state of connection between networks).
An [[Intrusion Detection System (IDS)]] are passive and identify when a network breach or attack against the network is occurring. It evaluates all traffic against a set of standards : signature based (evaluates for know malware or attack signatures), anomaly based (evaluates for suspicious changes) or policy based (evaluates network traffic against a specific declared security policy).
An [[Intrusion Prevention System (IPS)]] is placed inline with network traffic and will take action when malicious activities are detected to actively stop it. All traffic flows through the IPS and evaluates against a set of standards. 

# Optimization and performances devices 

A [[load balancer]] (also know as a content switch or content filter) is a network appliance that will balance requests across multiple devices that contain the same data to avoid overloading. 
A [[proxy]] server acts on behalf of a client device to fulfill requests to retrieve data. It can also be used to limit what requests are fulfilled. 
