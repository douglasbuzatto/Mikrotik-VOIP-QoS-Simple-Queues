Another bit of helpful code for Mikrotik. We were getting some crackling on our VOIP phone system when the internet connection was maxed out, the following code let phone traffic run smoothly, based on the UDP ports the VOIP service uses. Adjust to your VOIP providers ports, and adjust your LAN targets as needed.

There are a few concepts to be aware of:

Connection Marks — an identifying marker applied by the router to a connection passing through it. Markers are used for other rules to affect these connections.
Packet Marks — an identifying market applied by the router, to the packets inside of a given connection. Markers will be used to escalate the priority of our RTP (Audio) Packets.
SIP – VOIP Control Signalling Channels — e.g., Source phone > Target Phone + Extension, everything about the phone call.
RTP – VOIP Audio Data — e.g. Compressed AAC audio content sent from the phone in packets.
Mikrotik Queues — Basically, Quality of Service (QoS) pools of bandwidth, and reserving speed for a specific type of traffic (VOIP first, web-downloads last).
Mikrotik Parent Queues — A total “pool” of available bandwidth, to be provided to children.
Mikrotik Child Queues — A reserved portion of bandwidth assigned to a type of traffic that child is handling.
Note — If you have FastTrack enabled, it tends to bypass Queues, you may need to disable FastTrack to enforce your Queues, which may drastically increase CPU usage under high loads. For our RB3011-RM, running at 100Mbps, we hit 10-15% CPU load with fast-track disabled.
