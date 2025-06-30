# ElevateLabs-internship-task5

# Task 5: Capture and Analyze network traffic using Wireshark

## Objective
 Capture live network packets and identify basic protocols and traffic types.

---

## Tools Used
- **Wireshark** (packet sniffer & analyzer)
- **Browser and ping command** to generate traffic

---

## Step-by-Step Procedure

### 1. Start Capture
- Opened Wireshark
- Selected active interface(in my case, it was Wi-Fi).
- Clicked the blue **Start Capture** button

### 2. Generate Traffic
- Ran the command `ping google.com` to generate a traffic
- Opened a website on my browser to generate additional traffic
- Wireshark captured traffic from the `ping` as well as broswer


### 3. Stop Capture
- Clicked the red square **Stop** button after a minute

---

## 4. Protocol Filters Applied

### Protocols Observed:

 Protocol | Filter Used | Description
 **HTTP**    `http`       Used for browsing websites 
 **DNS**     `dns`        Resolves domain names to IPs 
 **ICMP**    `icmp`       Used by `ping` to test connectivity 
 **TCP**     `tcp`        Connection-based transport layer 
 **UDP**     `udp`        Datagram oriented transport layer(connection-less)

I've included packet caputure for all filters I applied.
---

### Observation from filters
## TCP(Transmission Control Protocol):
- Captured **3-way handshake**: SYN → SYN-ACK → ACK
- Observed HTTP and DNS traffic encapsulated within TCP sessions.
- Monitored stream reassembly by following a TCP connection.

## UDP(User Datagram Protocol):
- Packets sent without establishing a connection->no retransmissions, no ACKs.
- Captured DNS queries and responses using UDP on port 53.

## HTTP(Hyper-Text-Transfer-Protocol):
- Captured **HTTP GET** and **HTTP response** packets while visiting websites.
- URLs from my browser were also captured.
- Fields analyzed:
  - **Host**: `web.whatsapp.com`
  - **User-Agent**: browser identification
  - **Status Code**: e.g., `200 OK`, `404 Not Found`
- Easily followed streams to view entire browser-to-server conversations.

## DNS(Domain Naming System):
- Query sent from local system to **DNS server** (e.g., `192.168.29.1`) for domain name resolution.
- Typical request: `A` record lookup for `google.com`.
- Response contained:
  - **Resolved IP address** (e.g., `142.250.182.238`)
  - **TTL** value
  - **Response flags** (e.g., recursion available, authoritative answer)

## ICMP(Internet Control Message Protocol):
- Captured during:
  `ping google.com`
- ICMP Echo Request (`Type: 8`) sent to Google’s IP
- ICMP Echo Reply (`Type: 0`) received

## Example Packet Info

- **DNS Query** to `google.com`
- **TCP handshake** (SYN, SYN-ACK, ACK)
- **ICMP Echo request/reply**
- **HTTP** GET method from Reuqest and Response.

---

## Included materials
- `normal-capture.pcapng` (packet capture file)
- A word document showing:
  - Steps for wireshark analysis along with 
  - Filtered protocols (`http`, `dns`, etc.)
- This README.md

---

## Learning Outcome
- Understood how Wireshark captures real-time traffic  
- Learned how to apply filters to isolate protocols  
- Identified key network protocols and their behavior

---

