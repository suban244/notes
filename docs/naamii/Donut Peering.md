# Internet Infrastructure
Initially internet was designed with only a few nodes and with packets that could be taken apart and put together in sequence. Also there was open connection between nodes for packet transmission.
With the increase in usage of internet, it has evolved to millions of nodes and the packet needs to travel through multiple networks before it gets delivered. The packet then may get dropped, lost, or get rerouted to a different route making putting together packets difficult. 
### Tier 1 Networks
These are the original networks. They have settlement-free peering with one another. They have massive routing tables and can send traffic throughout the internet.
- Since peering is free of cost, the is cost effective to send traffic through Tier other 1 networks
### Tier 2 networks
A network that primarily peers with other networks but also purchases IP transit to a portion of the internet. These networks are the most common providers are the closest to the 'edge', end users, for example: cable providers and regional ISPs. 
### Video Streaming Data
Video streaming will require a constant stream of data.The more networks video data has to travel between networks, the less quality the video will be, mainly because of packet loss and delays. 
### Traditional Tier 1 Routing

Traditionally the internet relied on inter-network infrastructure and peering between Tier 1 networks, which acted as backbone providers. Tier 2 networks payed Tier 1 networks to access their one networks.
For example an ISP user, say of *Broadband Provider*, wants to receive data hosted by *Content Provider*. The data query is 
1) Transmitted upstream by *Broadband provider*
2) Transmitted to a Tier 1 provider, from whom *Broadband provider* is taking service
3) Transmitted to a Tier 2 provider, from whom *Content Provider* is taking service
4) To the *content provider* network
![[Pasted image 20231210095058.png]]
### Case for direct peering
Tier 2 networks pay to sending traffic through the Tier 1 network, which is also slow, and more prone to packet loss. Conversely, it would make more sense to directly peer with other Tier 2 networks to exchange traffic. The cost stays, but each packet would need less hops and there will be less packet loss, thus better service to the end users.
![[Pasted image 20231210095041.png]]

Mzima Networks, leverages this to provide streaming content more efficiently. It peers with both 
- **Tier 2 networks**:  for faster, cost effective and less error prone delivery
- **Tier 1 network**: To make sure there are no holes in the routing table
This helps create a donut shaped network shown here.
![[Pasted image 20231210093229.png]]
This structure provides
- less packet loss and latency for end users
- lower costs
- resiliency through multiple connections.
#### Case Study of Babulous, a Streaming Content Provider
It used this technology provides by Mzima Networks to stream content to its users, at high speeds, ensure that there are no pauses or other issues during music streaming.