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
