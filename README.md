# ERG DASH testbed overview and how-tos
## Testbed picture
![IMG_3650](https://github.com/user-attachments/assets/dbf73375-3ff2-4ca1-a368-761e4e9decb7)

- All <span style="color:red">RED</span> cables connect interfaces in the network 137.50.17.0/24 (the public "Internet" network)
- All <span style="color:blue">BLUE</span> cables connect interfaces in the network 192.168.99.0/24 (the private "local" network)
- There is one <span style="color:yellow">YELLOW</span> cable indicating a "mirror" interface, which mirrors traffic intended for the quic/dash server (coming from both internet and local paths)  to the pcap-store.

## Testbed components
- QUIC/DASH server (dash): A machine running Debian 13. It serves a DASH video over TCP using the web server Apache 2, and over QUIC using Cloudflare's Quiche library. The server is available over the Internet at https://dash.erg.abdn.ac.uk. To access it locally, its address on the local network is 192.168.99.100.
- Delay Emulator (delay-em-1): A machine running FreeBSD 13. It allows setting up a Bandwidth and Delay to emulate various wireless links. Its address on the local network is 192.168.99.1 (it also acts as a router and will hand out IP addresses in the range 192.168.99.152 to 192.168.99.200).
- Client switch (client-sw): An 8 port Netgear switch; Plugging into any of the first 4 ports will allow you to connect to any of the testbed components on their local interfaces, set up emulation and run experiments on the local network.
- Copy Switch (copy-sw): An HP 24-port switch. This is required to mirror the traffic intended for the quic/dash server (coming from both internet and local paths) to the pcap-store. The researcher will not need to plug into this switch, but it may be useful to know ports 1-8 are configured for the local network, 9-16 on the Internet network, and port 20 is the mirror interface.
- PCAP Store (pcap-store): An APU4 board running Debian 13. The researcher can connect to it on its local IP address, 192.168.99.151. It receives mirror traffic on interface enp3s0.
  
## Testbed diagram
<img width="1957" height="1857" alt="testbed-oct-25" src="https://github.com/user-attachments/assets/676c4b9a-b179-4bd6-8b1a-9cf9d14b7d2a" />


Download the diagram: [testbed-oct-25.pdf](https://github.com/user-attachments/files/25049991/testbed-oct-25.pdf)
