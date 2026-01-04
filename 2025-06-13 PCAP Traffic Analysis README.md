# How a SOC Analyst would Analyse a Suspected Malicious PCAP file?

- So basically this walktheough is all about examining a suspected malicious PCAP File like a professional SOC Analyst would.
- So Basically I followed a route to cut out all unnecessary unwanted noise lile unwanted legitimate ports, protocols and IP address because all we need is the victim and the prime suspect.

## Phase 1 - Protocol Hierarchy Analysis.

<img src="/images/1.png">

### Actions Taken

- **Reviewed Statistics ➡️ Protocol Hierarchy**

### Findings.

- TCP is having the high packer percent compared to UDP. Basically it is suspicious because inside TCP we could see the TLS is mostly used.
- There is only Minimal UDP use, and there is no abnormal protocol mix.

> Traffic is stateful and encrypted, inconsistent with random noise or scanning and indicative of persistent communication.

## Phase 2 - Endpoint Identification.

<img src="/images/2.png">

### Actions Taken.

- **Reviewed Statistics ➡️ Endpoints ➡️ IPV4**
- Sorted by packet count and byte volume.

### Findings.

- Identified that **10.6.13.133** was theinfected internal IP address because it generated the highest number of packets and bytes.
- Also Identified that **83.137.149.15** was the external IP address because it also generated huge number of packets and bytes.

> Internal host 10.6.13.133 identified as the infected endpoint communicating heavily with external host 83.137.149.15. Giving hint that its either beaconing oe exfiltration.

## Phase 3 - DNS Analysis.

<img src="/images/3.png">

### Actions Taken.

- Applied Filter:
  
  ```bash
  ip.addr == 10.6.13.133 && dns
  ```

### Findings

- DNS queries looks legitimate because the domains are all legitimate like:

  - Microsoft, Bing, Azure, Skype, Windows Update
 
- No random or high-entropy domain names is visible.
- No suspicious TLDs or repeated unknown domains are also not visible.

> DNS activity is noisy but legitimate. No evidence of DGA or DNS-based command-and-control. DNS ruled out as the C2 channel.

## Phase 4 - TLS / HTTP Analysis

<img src="4.png">

### Actions Taken.

- Applied Filter:

  ```bash
  ip.addr == 10.6.13.133 && (tls || http)
  ```
### Findings

- After scrolling a bit we discovered that repeated connections between **10.6.13.133** and **83.137.149.15**.
- TLS 1.2 sessions with continuous encrypted application data.
- No normal web browsing patterns (no multiple domains, no asset loading).

> Encrypted TLS traffic indicates direct command-and-control communication rather than user-driven web activity.
