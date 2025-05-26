# Network Port Discovery and Packet Analysis

## Objective  
Learn to discover open ports on devices in your local network to understand network exposure and analyze network traffic to identify potential security risks.

## Warning  
This document and the associated tools are intended for educational purposes only.
Unauthorized scanning or analysis of networks without permission is illegal and unethical. Always ensure you have explicit permission to test or analyze any network.
---

## Tools  
- **Nmap** (Network Mapper) - a free and open-source network scanning tool.  
- **Wireshark** (optional) - a powerful network protocol analyzer for packet capture and analysis.  

----
### Step 1: Installing Tools
### Nmap  

Kali Linux usually comes with Nmap pre-installed. To verify, run:  

```bash

nmap --version
## If not installed, you can install it via:
sudo apt-get update
sudo apt-get install nmap
````

### Wireshark (Optional)
To install Wireshark, run:
````bash
sudo apt-get install wireshark
````
Note: You might need to configure permissions for non-root users to capture packets.

## Step 2: Discovering Open Ports with Nmap

### 2.1 Find your local IP range

Run the following command to identify your local IP address and subnet mask:
````bash
ip addr
````
Look for your active network interface (e.g., eth0, wlan0) and note the IP with subnet mask, e.g., 192.168.1.100/24. The subnet mask (/24) specifies the IP range, usually something like 192.168.1.0/24.

You may also check the routing table:
````bash
ip route
````

### 2.2 Run a TCP SYN Port Scan

Use Nmap to scan for open TCP ports in your local IP range with the TCP SYN scan (-sS):
````bash
nmap -sS 192.168.1.0/24
````
Replace 192.168.1.0/24 with your actual subnet.
This scan sends SYN packets to ports to detect which are open without completing the TCP handshake, making it stealthier.

### 2.3 Save Scan Results
Save the scan output to a text file for later review:
````bash
nmap -sS 192.168.1.0/24 -oN scan_results.txt
````

Save as an HTML file:
````bash
nmap -sS 192.168.1.0/24 -oH scan_results.html
````

### 2.4 Analyze Scan Results

    Note the IP addresses of devices responding and their open ports.
    Research common services running on those ports (see IANA Service Name and Transport Protocol Port Number Registry).
    Identify any unusual or unnecessary open ports that could represent security risks.

## Step 3: Analyzing Network Traffic with Wireshark (Optional)

### 3.1 Launch Wireshark

Open Wireshark with root privileges:
````bash
sudo wireshark
````

````This opens the GUI for packet analysis.````

### 3.2 Select Your Network Interface
Choose the correct network interface from the list (e.g., eth0, wlan0) for capturing packets.

### 3.3 Start Packet Capture
Click the Start capturing packets button (green shark fin icon) or press Ctrl+E to begin capturing live traffic on that interface.

### 3.4 Apply Capture Filters
Wireshark captures everything by default. To focus, use capture filters or display filters.
Common display filters:

   ````bash
 Filter by protocol:
    tcp
    udp
    icmp
    http
    dns
````
Filter by IP address:
````bash
ip.addr == 192.168.1.100
````
Filter by port:
````bash
tcp.port == 80
udp.port == 53
````

### 3.5 Analyze Packets

Wireshark displays packets in three panes:

    Packet List (top): Summary of each packet captured.
    Packet Details (middle): Hierarchical breakdown of packet headers and protocols.
    Packet Bytes (bottom): Raw data in hexadecimal and ASCII.

Click a packet in the top pane to explore details.

### 3.6 Follow TCP/UDP Streams

To see an entire conversation between source and destination:

    Right-click a TCP/UDP packet.
    Select Follow -> TCP Stream or UDP Stream.

This reconstruction allows you to read the full data exchange.

### 3.7 Stop and Save Capture
````bash 
    Press Ctrl+E or click the red square button to stop capturing.
    Save the capture file via File -> Save As..., using .pcap or .pcapng format for later analysis.
````

# Summary
This document provides a comprehensive guide to scanning your local network for open ports using Nmap and analyzing network traffic using Wireshark. 
These skills help to understand network exposure and discover potential attack surfaces to improve your network security.




# Network Port Discovery and Packet Analysis



## Objective  
Learn to discover open ports on devices in your local network to understand network exposure and analyze network traffic to identify potential security risks.

---

## Tools  
- **Nmap** (Network Mapper) - a free and open-source network scanning tool.  
- **Wireshark** (optional) - a powerful network protocol analyzer for packet capture and analysis.  

---

## Step 1: Installing Tools

### Nmap  
Kali Linux usually comes with Nmap pre-installed. To verify, run:  
```bash
nmap --version
    
