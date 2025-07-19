# Chapter 11: Secure Network Architecture and Components

- [Study Essentials](#study-essentials)
- [OSI Model](#osi-model)
  - [History of the OSI Model](#history-of-the-osi-model)
  - [OSI Functionality](#osi-functionality)
  - [Encapsulation/Deencapsulation](#encapsulationdeencapsulation)
  - [OSI Layers](#osi-layers)
- [TCP/IP Model](#tcpip-model)
- [Analyzing Network Traffic](#analyzing-network-traffic)
- [Common Application Layer Protocols](#common-application-layer-protocols)
- [Transport Layer Protocols](#transport-layer-protocols)
- [Domain Name System](#domain-name-system)
  - [DNS Poisoning](#dns-poisoning)
  - [Domain Hijacking](#domain-hijacking)
- [Internet Protocol (IP) Networking](#internet-protocol-ip-networking)
  - [IPv4 vs. IPv6](#ipv4-vs-ipv6)
  - [IP Classes](#ip-classes)
  - [ICMP](#icmp)
  - [IGMP](#igmp)
- [ARP Concerns](#arp-concerns)
- [Secure Communication Protocols](#secure-communication-protocols)
- [Implications of Multilayer Protocols](#implications-of-multilayer-protocols)
  - [Converged Protocols](#converged-protocols)
  - [Voice over Internet Protocol (VoIP)](#voice-over-internet-protocol-voip)
  - [Software-Defined Network](#software-defined-network)
- [Segmentation](#segmentation)
- [Edge Networks](#edge-networks)
- [Wireless Networks](#wireless-networks)
  - [Securing the SSID](#securing-the-ssid)
  - [Wireless Channels](#wireless-channels)
  - [Conducting a Site Survey](#conducting-a-site-survey)
  - [Wireless Security](#wireless-security)
  - [Wi-Fi Protected Setup (WPS)](#wi-fi-protected-setup-wps)
  - [Wireless MAC Filter](#wireless-mac-filter)
  - [Wireless Antenna Management](#wireless-antenna-management)
  - [Using Captive Portals](#using-captive-portals)
  - [General Wi-Fi Security Procedure](#general-wi-fi-security-procedure)
  - [Wireless Communications](#wireless-communications)
  - [Wireless Attacks](#wireless-attacks)
- [Satellite Communications](#satellite-communications)
- [Cellular Networks](#cellular-networks)
- [Content Distribution Networks (CDNs)](#content-distribution-networks-cdns)
- [Secure Network Components](#secure-network-components)
  - [Secure Operation of Hardware](#secure-operation-of-hardware)
  - [Common Network Equipment](#common-network-equipment)
  - [Network Access Control](#network-access-control)
  - [Firewalls](#firewalls)
  - [Endpoint Security](#endpoint-security)
  - [Cabling, Topology, and Transmission Media Technology](#cabling-topology-and-transmission-media-technology)
  - [Transmission Media](#transmission-media)
  - [Transport Architecture](#transport-architecture)
  - [Network Topologies](#network-topologies)
  - [Ethernet](#ethernet)
  - [Sub-Technologies](#sub-technologies)
- [Summary](#summary)

## Study Essentials
| Key Point (first sentence) | Details (remaining content) |
|---|---|
| Know the OSI model layers. | The OSI layers are as follows: Application, Presentation, Session, Transport, Network, Data Link, and Physical. |
| Know the network container names. | The network containers are: OSI layers 7–5 protocol data unit (PDU), Layer 4 segment (TCP) or a datagram (UDP), Layer 3 packet, Layer 2 frame, and Layer 1 bits. |
| Understand the MAC address. | Media Access Control (MAC) address is a 6-byte (48-bit) binary address written in hexadecimal notation, aka hardware address, physical address, the NIC address, and the Ethernet address. The first 3 bytes (24 bits) of the address is the organizationally unique identifier (OUI), which denotes the vendor or manufacturer. |
| Understand the TCP/IP model. | Also known as DARPA or the DOD model, the model has four layers: Application (also known as Process), Transport (also known as Host-to-Host), Internet (sometimes known as Internetworking), and Link (although the terms Network Interface and sometimes Network Access are used). |
| Understand DNS. | The Domain Name System (DNS) is the hierarchical naming scheme used in both public and private networks. DNS links human-friendly fully qualified domain names (FQDNs) and IP addresses together. DNSSEC and DoH are DNS security features. |
| Understand DNS poisoning. | DNS poisoning is the act of falsifying the DNS information used by a client to reach a desired system. It can be accomplished through a rogue DNS server, pharming, altering a hosts file, corrupting IP configuration, DNS query spoofing, and proxy falsification. |
| Know about ARP. | Address Resolution Protocol (ARP) is essential to the interoperability of logical and physical addressing schemes. ARP is used to resolve IP addresses into MAC addresses. Also, know about ARP poisoning. |
| Know about micro-segmentation. | Micro-segmentation is dividing up an internal network into numerous subzones, potentially as small as a single device, such as a high-value server or even a client or endpoint device. Each zone is separated from the others by internal segmentation firewalls (ISFWs), subnets, or VLANs. |
| Know about edge networks. | An edge network is a carefully designed data architecture that strategically allocates computing resources to edge devices within a network. This design helps distribute processing power demands away from central servers, empowering the devices to handle a significant portion of the processing workload. |
| Understand the various wireless technologies. | Cell phones, Bluetooth (802.15.1 and Bluetooth SIG), and Wi-Fi wireless networking (802.11) are all called wireless technologies, even though they are all different. Be aware of their differences, strengths, and weaknesses. Understand the basics of securing 802.11 networking. Know about RFID, NFC, satellite, narrow-band, and Zigbee. |
| Understand site surveys. | A site survey is a formal assessment of wireless signal strength, quality, and interference using an RF signal detector. A site survey is performed by placing a wireless base station in a desired location and then collecting signal measurements from throughout the area. |
| Understand WPS attacks. | Wi-Fi Protected Setup (WPS) is intended to simplify the effort involved in adding new clients to a secured wireless network. It operates by automatically connecting the first new wireless client to seek the network once WPS is triggered. |
| Understand captive portals. | A captive portal is an authentication technique that redirects a newly connected client to a web-based portal access control page. |
| Know wireless attacks. | Attacks include war driving, wireless scanners/crackers, rogue access points, evil twin, disassociation, jamming, IV abuse, and replay. |
| Be familiar with CDNs. | A content distribution network (CDN), or content delivery network, is a collection of resource services deployed in numerous data centers across the Internet to provide low latency, high performance, and high availability of the hosted content. |
| Understand NAC. | Network access control (NAC) is the concept of controlling access to an environment through strict adherence to and enforcement of security policy. Know about 802.1X, preadmission, postadmission, agent-based, and agentless. |
| Understand the various types of firewalls. | There are several types of firewalls: static packet filtering, application-level, circuit-level, stateful inspection, NGFW, and ISFW. Also, know about virtual firewall, filters/rules/ACLs/tuples, bastion host, ingress, egress, RTBH, stateless versus stateful, WAF, SWG, TCP wrapper, DPI, and content and URL filtering. |
| Know about proxies. | A proxy server is used to mediate between clients and servers. Proxies are most often used in the context of providing clients on a private network with internet access while protecting the identity of the clients. Know about forward, reverse, transparent, and nontransparent. |
| Understand endpoint security. | Endpoint security is the concept that each individual device must maintain local security whether or not its network or telecommunications channels also provide security. Endpoint detection and response (EDR) is a combination of firewall, intrusion detection system (IDS), and antimalware. Managed detection and response (MDR) combines EDR with Security information and event management (SIEM), network traffic analysis (NTA), and network IDS. Endpoint protection platform (EPP) is an intrusion prevention system (IPS) variant of EDR. Extended detection and response (XDR) is the combination of EDR, MDR, and EPP often with cloud-based remote monitoring and analysis. |
| Be familiar with the common LAN technologies. | The most common LAN technology is Ethernet. Also, be familiar with analog versus digital communications; synchronous versus asynchronous communications; duplexing; baseband versus broadband communications; broadcast, multicast, unicast, anycast, and geocast communications; CSMA, CSMA/CD, and CSMA/CA; token passing; and polling. |

## OSI Model
The Open Systems Interconnection (OSI) Reference Model is a **7-layer conceptual framework** that standardizes the functions of a telecommunication or computing system without regard to its underlying internal structure. By mapping protocols, hardware, and security controls to specific layers, security professionals can **pin-point vulnerabilities** 🔍 and apply appropriate countermeasures.

### History of the OSI Model
* **1970–1973** — DARPA develops the **TCP/IP (ARPANET) model**, proving large-scale packet switching.  
* **Late 1970s** — The **International Organization for Standardization (ISO)** begins work on a vendor-neutral model to ensure interoperability.  
* **1984** — ISO publishes **ISO 7498**, formally defining the 7-layer OSI model.  
* Despite never replacing TCP/IP in practice, the OSI model became the **universal teaching & troubleshooting reference** for network design, diagnostics, and security.

### OSI Functionality
* **Vertical abstraction:** Each layer offers _services_ to the layer above and relies on _services_ from the layer below.  
* **Peer-layer communication:** Logical conversations occur **horizontally** between matching layers on different hosts (e.g., Transport ↔ Transport).  
* **Modularity:** Designers can upgrade or secure one layer (e.g., add TLS at Layer 4) without rewriting the entire stack.  
* **Vendor neutrality:** Interfaces are defined by open standards, allowing multi-vendor equipment to interoperate.

### Encapsulation/Deencapsulation
| Phase | Action | Resulting Protocol Data Unit (PDU) | Security Considerations |
|-------|--------|------------------------------------|-------------------------|
| **Encapsulation ↓** | Each layer **adds a header** (and sometimes a footer) to the payload from the layer above. | Bit → Frame → Packet → Segment/Datagram → PDU | Headers can reveal metadata (e.g., IP addresses) 🎯; encrypt or tunnel when confidentiality is required. |
| **Transmission ↔** | Physical media (copper, fiber, RF) carry the **bit stream**. | Bits | Physical attacks (tap, EMI) require shielding, TEMPEST, fiber, or link encryption. |
| **Deencapsulation ↑** | Each layer **strips its own header/footer**, passing the payload up. | Reverses PDU order | Integrity checks (CRC, checksum, MAC) ensure data was not altered in transit. |

> :memo: **Mnemonic**  
> “**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing” (top → bottom)  
> “**P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way” (bottom → top)

### OSI Layers
Below is a “one-page” reference table—learn it cold for the exam:

| # | Layer | PDU Name | Key Duties | Example Protocols / Tech | Devices Commonly Operating Here | Security Focus |
|---|-------|----------|-----------|--------------------------|---------------------------------|----------------|
| 7 | **Application** | PDU | Interface for user apps & services (HTTP, FTP). | HTTP, SMTP, SNMP, SSH | Proxies, DLP gateways | Input validation, authN, app firewalls |
| 6 | **Presentation** | PDU | Syntax/format transformation, **encryption**, compression. | TLS/SSL, ASN.1, MIME | SSL accelerators | Cipher selection, key mgmt, data sanitization |
| 5 | **Session** | PDU | Builds, maintains, tears down **sessions**; dialog control (simplex/half/full-duplex). | NetBIOS, RPC, PPTP control | Session border controllers | Token/session hijack prevention, timeout policy |
| 4 | **Transport** | **Segment** (TCP) / **Datagram** (UDP) | End-to-end reliability, flow/error control, **ports**. | TCP, UDP, TLS, QUIC | Firewalls, load balancers | Port filtering, stateful inspection, DoS mitigation |
| 3 | **Network** | **Packet** | Logical addressing (**IP**), routing, fragmentation. | IPv4/IPv6, ICMP, IPsec, OSPF | Routers, Layer-3 switches | ACLs, route authentication, anti-spoofing |
| 2 | **Data Link** | **Frame** | MAC addressing, LAN switching, CRC, VLANs. | Ethernet (802.3), ARP, PPP, STP | Switches, bridges, NICs | Port security, STP guard, MAC filtering |
| 1 | **Physical** | **Bits** | Signaling, voltages, cables, radios, optics. | UTP, fiber, 802.11 RF, DSL | Hubs, repeaters, media converters | Cabling locks, shielding, TEMPEST, CCTV |

#### Key Layer-Specific Notes
* **Layer 7 – Application**  
  * The _protocols_ live here, **not the apps themselves**. Ex: a browser (software) uses HTTP/HTTPS (Layer 7 protocol).  
  * Common attacks: XSS, CSRF, SQLi—apply secure coding, WAFs, and content security policy (CSP).

* **Layer 6 – Presentation**  
  * Handles **serialization** (e.g., JSON ↔ binary), character sets (UTF-8), and **encryption** 🗝️.  
  * In pure TCP/IP, many Presentation functions are folded into application libraries or TLS.

* **Layer 5 – Session**  
  * Maintains checkpoints for long transfers (useful for resuming).  
  * Modern TCP stacks blur Session into Transport, but exam questions still treat it as distinct.

* **Layer 4 – Transport**  
  * **TCP** = connection-oriented, reliable (SYN → SYN-ACK → ACK handshake).  
  * **UDP** = connectionless, best-effort; popular for VoIP/gaming.  
  * **TLS** most often operates here (encrypts entire Transport payload, including app headers).

* **Layer 3 – Network**  
  * Implements **CIDR, subnetting, routing protocols**.  
  * Firewalls use packet attributes (src/dst IP, protocol) for **stateless ACLs**; stateful devices track connections.  
  * **ICMP** = control/status (ping, traceroute). Block or rate-limit to reduce mapping & DoS vectors.

* **Layer 2 – Data Link**  
  * **MAC flooding** & **ARP spoofing** exploit switch behavior—mitigate with port security, DHCP snooping.  
  * VLAN hopping attacks abuse trunk misconfig; enforce tagging policies, disable unused ports.

* **Layer 1 – Physical**  
  * Threats include wiretapping, EMI, eavesdropping, hardware tampering.  
  * Countermeasures: **fiber optic** cabling, conduit, Faraday cages, redundant links, environmental controls.

### Quick-Look Comparison Table: PDUs, Addresses & Devices
| OSI Layer | PDU | Address Type | Representative Devices | Notable Attack Examples |
|-----------|-----|--------------|------------------------|-------------------------|
| 7–5 | (PDU) | — | Reverse proxy, API gateway | Header injection, replay |
| 4 | Segment / Datagram | **Port number** | Stateful firewall, load balancer | SYN flood, UDP amplification |
| 3 | Packet | **IP address** | Router, IPS/IDS | IP spoofing, BGP hijack |
| 2 | Frame | **MAC address** | Switch, bridge | ARP poisoning, MAC flooding |
| 1 | Bits | — | Hub, repeater | Tap, signal interference |

### Exam Tips ✨
1. **Map security controls to layers**—e.g., WAF (7), IPSec (3), 802.1X (2).  
2. **Remember PDU names & headers**; expect “Which layer converts frames to bits?” style MCQs.  
3. Be able to **differentiate TCP vs. UDP** characteristics and where TLS fits.  
4. Know that some OSI layers are **“missing” in TCP/IP** (Presentation & Session functions absorbed by others).  
5. Practice tracing an attack: identify at **which layer** detection/prevention should occur.

## TCP/IP Model
The **Transmission Control Protocol / Internet Protocol (TCP/IP) model**—also called the DARPA or DoD model—maps real-world protocols into **four layers** (Application, Transport, Internet, Link). Although simpler than the seven-layer OSI reference model, TCP/IP covers the same functional space. Remember that **exam questions often switch context between OSI and TCP/IP names—be ready to translate.**

| TCP/IP Layer | Rough OSI Equivalent(s) | Core Responsibilities | Representative Protocols | Key Security Concerns |
|--------------|------------------------|-----------------------|--------------------------|-----------------------|
| Application  | OSI Layers 7-5 | User-level services, data formatting, session management | HTTP/HTTPS, SMTP, DNS, SNMP, FTP, SSH | Input validation, authN/Z, encryption, hardening default creds |
| Transport    | OSI Layer 4 | End-to-end connections, reliability, ports | **TCP, UDP, TLS, QUIC** | SYN floods, port scanning 🔍, weak ciphers |
| Internet     | OSI Layer 3 | Logical addressing, routing, fragmentation | IPv4/IPv6, ICMP, IPsec, OSPF, BGP | IP spoofing, route hijacking, ICMP tunneling |
| Link         | OSI Layers 2-1 | Physical signaling, MAC addressing, framing | Ethernet, Wi-Fi, PPP | ARP spoofing, VLAN hopping, wiretapping |

**Security implications**  
* Designed for resilience and interoperability, not confidentiality—many protocols default to **plaintext**.  
* Common stack flaws: buffer overflows, sequence-number prediction, fragment attacks, oversized packets, SYN floods, AitM hijacking.  
* Mitigations: stateful firewalls, header-sanity checks, IPS, TLS/IPsec, network segmentation.

**Exam tip 📝**  
Expect “Which TCP/IP layer handles <task>?” or “Map protocol X to its OSI layer”—practice bidirectional mapping tables.

## Analyzing Network Traffic
Network-traffic analysis supports **troubleshooting, performance tuning, and threat detection** but can also enable eavesdropping.

### Protocol Analyzers (Sniffers)
* Capture frames/packets by placing the NIC into **promiscuous mode** (ignores destination MAC).  
* Tools range from open-source **Wireshark** to enterprise platforms (NetWitness, Omnipeek, NetScout).  
* Offer **capture filters** (decide what to save) and **display filters** (decide what to show).

| Feature | Benefit | Security Caveat |
|---------|---------|-----------------|
| Hex + ASCII decode | Deep inspection down to bit level | Exposure of sensitive payloads 👀 |
| Reassembly | View full TCP streams | Attackers can hide fragments; ensure IDS reassembles too |
| Automated heuristics | Detect malformed packets, known IoCs | Heuristics lag behind zero-day techniques |

**Legal & ethical considerations**  
Capturing traffic may violate privacy laws or employer policies—obtain written authorization & follow “least-capture necessary” principles.

**Exam tip 📝**  
Know distinctions: **sniffer** (raw capture) vs. **protocol analyzer** (decode/interpretation). Expect questions on promiscuous vs. monitor mode and filter types.

## Common Application Layer Protocols
Application-layer protocols run over TCP, UDP, or both. Memorize **default ports, secure replacements, and primary risks**:

| Protocol | Default Port(s) | Purpose | Secure Alternative / Hardening | Typical Risks |
|----------|-----------------|---------|--------------------------------|---------------|
| Telnet | TCP 23 | Remote CLI | **SSH** (TCP 22) | Plaintext creds, AitM |
| FTP | TCP 21 (control), 20/ephemeral (data) | File transfer | **SFTP (SSH)** or **FTPS (TLS)** | Cleartext, bounce attack |
| TFTP | UDP 69 | Simple file transfer (no auth) | Avoid or tunnel in VPN | Config theft, malware drops |
| SMTP | TCP 25 | E-mail relay | **SMTPS (STARTTLS 587 / 465)** | Spoofing, header injection |
| POP3 | TCP 110 | Pull mail, local storage | **POPS (995)** | Cleartext creds |
| IMAP4 | TCP 143 | Pull mail, server storage | **IMAPS (993)** | Credential theft |
| DHCP | UDP 67/68 | Dynamic IP config | DHCP snooping, MAC binding | Rogue server, exhaustion |
| HTTP | TCP 80 | Web content | **HTTPS (443)** | Session hijack, XSS |
| HTTPS | TCP 443 | TLS-secured HTTP | Harden ciphers, HSTS | Weak TLS versions |
| LPD | TCP 515 | Print spooling | Use IPsec/VPN | Job manipulation |
| X Window | TCP 6000-6063 | Remote GUI | VPN, SSH -X | Keystroke snoop |
| NFS | TCP 2049 | File sharing | NFSv4 + Kerberos | UID spoof, cleartext |
| SNMP | UDP 161/162 | Network management | **SNMPv3** (auth+enc) | Community string brute force |

**Exam tip 📝**  
Port numbers and secure replacements are high-frequency test items—flash-card them. Recognize that many “legacy” protocols must be wrapped in SSH, TLS, or VPN tunnels for compliance.

## Transport Layer Protocols
Transport-layer mechanisms provide **multiplexing, reliability, and connection management** via ports.

### Port Ranges
* **Well-Known / Service Ports 0-1023** — reserved for servers (e.g., 80 HTTP).  
* **Registered 1024-49 151** — vendor-registered apps.  
* **Dynamic/Ephemeral 49 152-65 535** — client source ports; OS may use any >1023.

A *socket* = **IP address + port**; enables multiple sessions on one host.

### TCP vs. UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Type | Connection-oriented, reliable | Connectionless, best-effort |
| Handshake | 3-way (SYN → SYN/ACK → ACK) | None |
| Acknowledgment | Yes (per window) | Optional checksum only |
| Sequencing & Reorder | Built-in | None |
| Overhead | Higher 📦 | Minimal |
| Use Cases | File transfer, web, mail | VoIP, streaming, DNS |
| Teardown | FIN/ACK graceful or RST abrupt | No formal teardown |
| Common Attacks | SYN flood, session hijack, RST spoof | UDP flood, amplification |

> **FIN vs. RST**  
> *FIN* = orderly close; *RST* = immediate abort—RST storms can be used to forcibly drop sessions.

### Additional Transport-Layer Protocols
* **TLS (Transport Layer Security)** — Encrypts segments; negotiates cipher suites, provides integrity & optional client auth.  
* **QUIC** — Google protocol combining TLS 1.3 + UDP for faster handshakes, used by HTTP/3.  
* **SCTP** — Stream Control Transmission Protocol, supports multihoming & multi-streaming; niche but exam-worthy.

### Reliability & Flow Control
* **Sliding window** adjusts segment count based on ACK feedback.  
* **Congestion control** (slow-start, AIMD) prevents network collapse—study algorithms for advanced questions.

**Exam tip 📝**  
Expect scenario questions asking whether to pick TCP or UDP given requirements (e.g., “mission-critical database sync” → TCP; “VoIP call” → UDP). Memorize the three-way handshake flag order and FIN vs. RST behavior.

### Quick Reference Cheat Sheet
| Topic to Memorize | One-Liner |
|-------------------|-----------|
| TCP/IP ↔ OSI mapping | Application ↔ 7-5, Transport ↔ 4, Internet ↔ 3, Link ↔ 2-1 |
| Port ranges | 0-1023 well-known, 1024-49151 registered, 49152-65535 ephemeral |
| TCP handshake flags | SYN → SYN/ACK → ACK |
| Secure replacements | Telnet → SSH, FTP → SFTP/FTPS, SNMPv1/v2 → SNMPv3 |
| Sniffer vs. analyzer | Sniffer captures; analyzer decodes/interprets |

### Final Exam Pointers
* Link every **security control** to its layer: TLS (Transport), IPsec (Internet), MAC filtering (Link).  
* Be able to **decode packet flows**: “Client sends SYN, server replies SYN/ACK…” Identify next step.  
* Understand how **misconfigurations** (e.g., open SNMP community, anonymous FTP) translate into real-world exploits.  
* Practice with **Wireshark capture filters** (`tcp.port == 443`) and display filters (`ip.addr == 10.0.0.5`)—terminology appears on exams.

## Domain Name System
DNS converts **human-readable names** to IP addresses and underpins virtually every TCP/IP connection. Knowing its hierarchy and attack surface is critical for CISSP success.

### DNS Poisoning
* **Goal**: Inject false name-to-IP data so users reach attacker-controlled hosts.
* **Vectors**
  * **Rogue DNS server** replies faster than the legitimate one, matching the 16-bit *Query ID (QID)*.
  * **Cache poisoning** inserts bogus records into a recursive resolver; persists until TTL expires.
  * **Hosts-file tampering** overwrites local mappings (highly targeted).
  * **DHCP option spoofing** forces clients to use a malicious resolver.
  * **Pharming**: mass redirection via poisoned caches or hosts files.
* **Defenses**
  * **DNSSEC** 🔑—signs zone data; clients verify signatures.
  * **Split DNS**—separate internal / external zones; block inbound UDP/TCP 53.
  * Strict zone-transfer ACLs; disable AXFR to untrusted IPs.
  * **DoH / ODoH** encrypts and anonymizes client queries.
  * Deploy NIDS to flag unusual TTLs, QID spray, or out-of-bailiwick answers.

### Domain Hijacking
* **Attack**: Unauthorized change of a domain’s registrar record. Methods include stolen creds, XSRF, registrar exploit, or MitM at login.
* **Impact**: Brand damage, credential harvesting, malware hosting.
* **Mitigations**
  * Registrar MFA + hardware tokens.
  * Registry **EPP locks** (clientTransferProhibited, serverUpdateProhibited).
  * Auto-renew with verified payment source.
  * Monitor WHOIS / RDAP changes, set DNSSEC DS records.

> **Homograph attacks** leverage look-alike Unicode characters to register deceptive IDNs (e.g., раypal.com). Use browser punycode display and anti-phishing tools.

## Internet Protocol (IP) Networking

### IPv4 vs. IPv6

| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address size | 32-bit | **128-bit** |
| Notation | Dotted-decimal (192.0.2.1) | Hex/quartet (2001:db8::1) |
| Total addresses | ≈4.3 billion | 3.4 × 10³⁸ (virtually inexhaustible) |
| Built-in security | Add-on IPsec | IPsec mandatory |
| Config | DHCP / manual | SLAAC, DHCPv6 (stateful/stateless) |
| QoS | DiffServ/DSCP (rarely used) | Flow Label + DSCP |
| Transition | Dual-stack, tunneling, NAT-PT | N/A |
| Loopback | 127.0.0.1 | ::1/128 |

*Security pitfalls*: Unfiltered dual-stack opens covert channels; ensure firewalls, IDS, log tools parse IPv6 before enabling.

### IP Classes (Legacy IPv4)
| Class | First Octet Range | Default Mask | Typical Hosts | Notes |
|-------|------------------|--------------|---------------|-------|
| A | 1–126 | 255.0.0.0 (/8) | 16 M | 127.x.x.x = loopback |
| B | 128–191 | 255.255.0.0 (/16) | 65 K | 169.254.x.x = APIPA |
| C | 192–223 | 255.255.255.0 (/24) | 254 | 192.168.0.0/16 private |
| D | 224–239 | n/a | Multicast | IGMP joins |
| E | 240–255 | n/a | Experimental | Rarely routed |

Modern networks use **CIDR / VLSM** to carve variable-length subnets beyond class rules.

### ICMP
* **Purpose**: Health checks, diagnostics (ping, traceroute), error messaging (e.g., Type 3 Destination Unreachable).
* **Security Issues**
  * Bandwidth DoS (Smurf, ping flood), *ping of death*.
  * Recon: OS fingerprinting via TTL and response codes.
* **Hardening**
  * Rate-limit or drop echo requests from untrusted zones.
  * Block outbound Type 13 Timestamp to reduce profiling.

### IGMP
* Enables hosts to **join/leave multicast groups** (Class D 224.0.0.0/4).
* Versions: IGMPv2 (leave messages), IGMPv3 (source-specific multicasting).
* Security: Filter unwanted multicast at switches/routers; disable IGMP snooping if not needed.

### Quick Reference

| Protocol | OSI Layer | Port(s) / ICMP Type | Key Exam Points |
|----------|-----------|---------------------|-----------------|
| DNS | 7-5 | UDP/TCP 53 | Cache poisoning, DNSSEC, split DNS |
| ICMP | 3 | N/A (protocol 1) | Echo, Time Exceeded, unreachable codes |
| IGMP | 3 | N/A (protocol 2) | Multicast join/leave, relies on routers |
| IPv6 | 3 | N/A | 128-bit, SLAAC, mandatory IPsec |

### Exam Insights
* Memorize **DNS record types** (A, AAAA, PTR, MX, CNAME, SOA, NS).
* Know the **TTL vs. Hop-Limit** distinction (IPv4 vs. IPv6).
* Expect scenario questions on **DNSSEC vs. DoH**, and defenses against cache poisoning.
* Be able to compute **CIDR subnets** and identify correct masks for given host counts.
* Recognize typical **ICMP attack signatures** and recommended router ACLs.

## ARP Concerns
Address Resolution Protocol maps an IPv4 **logical address (IP)** ➜ **physical address (MAC)**.  
Because ARP requests/replies are *unauthenticated broadcasts* (EtherType ​0x0806​), they are ripe for abuse.

### Attack Surface
| Technique | How It Works | Impact | Detection / Mitigation |
|-----------|--------------|--------|------------------------|
| **ARP cache poisoning / spoofing** | Attacker replies with forged MAC ↔ IP binding; victim overwrites cache. | Traffic diversion → MitM 🕵️, session hijack, DoS. | Switch **port security**, dynamic ARP inspection, `arpwatch`, host firewall blocking unsolicited replies. |
| **Gratuitous ARP abuse** | Fake unsolicited ARP updates sent periodically. | Persistent spoof without broadcast query. | Same as above; monitor for excess gratuitous ARP. |
| **Static-entry overwrite** | Malicious script inserts non-persistent static entry. | Mis-routes until reboot. | Harden endpoints; allow-list admin scripts; GPO stomps. |

> **Exam tip** — remember: ARP lives at **OSI Layer 2**, carries IP + MAC in Ethernet frame; poisoning countermeasures belong largely to *switch* features.

## Secure Communication Protocols
These protocols wrap ordinary traffic in **encryption + integrity** services to defeat eavesdropping or tampering.

| Protocol | Layer | Purpose | Core Crypto | Notes |
|----------|-------|---------|-------------|-------|
| **IPsec** | 3 | Site-to-site or host VPN | AH (auth) & ESP (enc/auth) | *Transport* vs *Tunnel* mode; native to IPv6. |
| **TLS** | 4 (encaps squeeze) | Encrypt any TCP/UDP app (HTTPS, SMTPS, SIP) | X.509 + symmetric | Supersedes SSL; supports mutual auth. |
| **SSH** | 7→5 | Secure remote shell, port forwarding, SFTP | KEX + symmetric + MAC | Acts as lightweight host-to-host VPN. |
| **Kerberos** | 5 | SSO & mutual auth inside realms | Symmetric tickets, TGT 🗝️ | Relies on time sync; mitigates credential replay. |
| **Signal Protocol** | 7 | End-to-end voice / text | Double-Ratchet + X3DH | Perfect forward secrecy; used in WhatsApp, Signal. |
| **S-RPC** | 7 | AuthN for remote procedures | Digital signatures | Rare outside legacy NFS environments. |

## Implications of Multilayer Protocols
TCP/IP’s **encapsulation** allows stacks of protocols inside others, creating flexibility *and* hidden risk.

### Benefits
* Mix-and-match services (e.g., HTTPS over IPsec over Ethernet).
* Insert encryption at one or many layers.
* Resilient to transport-layer failures.

### Drawbacks
* **Covert channels** can tunnel banned apps (FTP-in-HTTP, Loki ICMP-tunnel).
* Security appliances might inspect only outer header ➜ **filter bypass**.
* VLAN tag hopping or protocol confusion across boundaries.

### Converged Protocols
Melding specialty traffic onto commodity Ethernet/IP.

| Example | What It Encapsulates | Use Case | Security Note |
|---------|----------------------|----------|---------------|
| **SAN / iSCSI** | SCSI commands in TCP | Storage over LAN/WAN | Authenticate initiators; isolate with VLAN / VRF. |
| **InfiniBand over Ethernet (IBoE)** | InfiniBand frames in Ethernet | HPC clusters | Lossless Ethernet (DCB) required. |
| **Compute Express Link (CXL)** | Shared memory / coherency | CPU ⇄ accelerator interconnect | Still emerging—watch firmware updates. |

### Voice over Internet Protocol (VoIP)
* Encapsulates audio (RTP/SRTP) + call-setup (SIP/H.323) into IP packets.  
* Attacks: *vishing*, SPIT, caller-ID spoof, DoS on call-manager, VLAN hopping.  
* **Secure RTP (SRTP)** adds AES + HMAC to audio; deploy with TLS-protected SIP.
* **SIPS**, the secure version of the Session Initialization Protocol for VoIP, adds TLS encryption to keep the session initialization process secure.

### Software-Defined Network (SDN)
* **Separates** *control plane* (decisions) from *data plane* (forwarding).  
* Central **controller** programs commodity switches via southbound APIs (e.g., OpenFlow); exposes northbound REST APIs to apps.  
* Partner concept: **NFV** virtualizes firewall, load-balancer, IDS as VM/containers.

| Benefit | Risk |
|---------|------|
| Vendor neutrality; instant path updates; fine-grained micro-segmentation 🚀 | Controller = single point of compromise; require AAA, TLS, role-based APIs |

## Segmentation
Dividing a network improves performance *and* limits blast radius.

### Methods
| Type | Implemented With | Main Goal |
|------|-----------------|-----------|
| **Physical** | Separate cabling, switches, *air-gap* | Absolute isolation 🔐 |
| **In-band (logical)** | Shared infra + VLANs, VPNs | Traffic separation, easier ops |
| **Out-of-band** | Mgmt network, IPMI | Protect control traffic |
| **Micro-segmentation** | Distributed firewalls, VXLAN, SDN | Per-workload policy; zero trust alignment |

| Technology | Primary Purpose | Isolation Scope | Typical Deployment / Use Case | Key Security Benefit | Notes & Limitations |
|------------|-----------------|-----------------|------------------------------|----------------------|---------------------|
| **VLAN** (Virtual Local Area Network) | Logically separate Layer-2 broadcast domains on a switch | Department, floor, or functional group | Enterprise campus networks; VoIP vs. data separation | Limits broadcast traffic; basic segmentation without extra hardware | Requires Layer-3 device for inter-VLAN routing; VLAN hopping attacks if misconfigured |
| **VPN** (Virtual Private Network) | Create an encrypted tunnel over untrusted networks | User-to-site or site-to-site | Remote access for teleworkers; branch office connectivity | Confidentiality & integrity across the Internet | Adds latency; relies on end-point security configurations |
| **VRF** (Virtual Routing & Forwarding) | Maintain multiple independent routing tables on one router | Customer, tenant, or service instance | Service-provider MPLS backbones; large enterprises with overlapping IP ranges | Prevents route leakage; per-tenant traffic separation | Operates at Layer-3 only; still shares physical interfaces unless combined with ACL/QoS |
| **VDOM** (Virtual Domain) / Virtual System | Virtualize firewall/switch into multiple logical devices | Business unit or customer | Next-gen firewalls offering per-tenant policy sets | Dedicated rule-base and logs per domain; strong admin separation | Consumes physical resources; mis-config between contexts can expose gaps |
| **VPC** (Virtual Private Cloud) | Provide isolated, software-defined network inside a public cloud | Entire cloud tenant network | AWS VPC, Azure VNets—multi-tier app hosting | Subnet-level ACLs, security groups, route-tables under tenant control | Still resides on provider’s shared fabric; egress filtering often extra |
| **Micro-segmentation** | Fine-grained, workload-level isolation (Zero Trust) | Single VM, container, or endpoint | Software-defined overlays (e.g., VMware NSX, Kubernetes network policies) | East-west traffic filtering; least-privilege at workload granularity 🔐 | Policy sprawl risk; heavy reliance on automation & visibility tools |

## Edge Networks
Moves compute/storage **closer to users or sensors** to cut latency.

| Concept | Description | Security Focus |
|---------|-------------|----------------|
| **Edge ingress** | Points where outside data enters edge cluster | DDoS filtering, TLS offload |
| **Edge egress** | Outbound path to Internet or core | Data-loss prevention, route validation |
| **Edge peering** | Direct inter-edge traffic exchange | Mutual BGP filters, shared threat intel |

Edge + CDN + 5G = ultra-low-latency apps (AR/VR, autonomous vehicles). Guard controller APIs and ensure consistent patching of widely-deployed edge nodes.

### Quick-look Cheat Sheet
| Topic | One-liner to Memorize |
|-------|----------------------|
| ARP attacks | **Layer 2**; stops with port security or DAI. |
| IPsec modes | *Transport* = encrypt payload; *Tunnel* = encrypt entire IP. |
| TLS handshake | ClientHello → ServerHello → cert → key exchange → Finished. |
| SDN directions | **Southbound** = controller→switch; **Northbound** = controller→apps. |
| VXLAN | Encapsulates layer-2 frames in UDP to span layer-3. |

## Wireless Networks
Wi-Fi (IEEE 802.11) enables “unbounded” connectivity but expands the attack surface with RF interception, rogue access points, and RF jamming. Two deployment styles exist: **ad hoc/Wi-Fi Direct** (peer-to-peer) and **infrastructure** (AP-centric). Infrastructure can be standalone, wired-extension, enterprise-extended (ESSID roaming), or bridge. AP form factors: **fat (stand-alone)** vs. **thin (controller-managed)**.

| Amendment | Wi-Fi Gen | Max Rate* | Band(s) | Key Feature |
|-----------|-----------|-----------|---------|-------------|
| 802.11 | — | 2 Mb/s | 2.4 GHz | Original DSSS/FHSS |
| 802.11b | Wi-Fi 1 | 11 Mb/s | 2.4 GHz | DSSS (CCK) |
| 802.11a | Wi-Fi 2 | 54 Mb/s | 5 GHz | OFDM |
| 802.11g | Wi-Fi 3 | 54 Mb/s | 2.4 GHz | OFDM + legacy compat |
| 802.11n | Wi-Fi 4 | 600 Mb/s | 2.4 / 5 GHz | MIMO |
| 802.11ac | Wi-Fi 5 | 3.5 Gb/s | 5 GHz | MU-MIMO, 80/160 MHz |
| 802.11ax | Wi-Fi 6/6E | 9.6 Gb/s | 1-7.125 GHz | OFDMA, TWT |
| 802.11be | Wi-Fi 7 | 40 Gb/s | 1-7.25 GHz | 320 MHz, 4096-QAM |
\*Theoretical PHY rate, not throughput.

### Securing the SSID
* **Change default SSID** to non-identifying string.
* **Disable beaconing** only for obscurity—SSID is still visible in data frames.
* Use **WPA2/WPA3** with strong passphrases or 802.1X; hiding SSID ≠ security.

### Wireless Channels
* 2.4 GHz: 22 MHz-wide channels, choose **1/6/11** (US) to eliminate overlap.
* 5 GHz: 20 MHz spacing; channels don’t overlap—bond for 40/80/160 MHz.
* 6 GHz (Wi-Fi 6E): contiguous 1.2 GHz spectrum → seven 160 MHz channels.
* Placement rule: stagger adjacent APs on non-overlapping channels to cut CCI.

### Conducting a Site Survey
1. Temporarily position AP → walk test area with RF analyzer (Ekahau, NetAlly).  
2. Record RSSI & SNR; generate **heat map** 🗺️ showing hot/cold zones.  
3. Adjust AP power, antenna type/orientation, or add APs; repeat until SLA met.

### Wireless Security
| Generation | Crypto & Auth | Pre-Shared Mode | Enterprise Mode |
|------------|---------------|-----------------|-----------------|
| WEP | RC4 + 24-bit IV | Static key (cracked <1 min) | N/A |
| WPA | RC4 + **TKIP/LEAP** | PSK (8-63 chars) | 802.1X/EAP-TLS |
| **WPA2** | **AES-CCMP** | WPA2-PSK | WPA2-ENT (EAP) |
| **WPA3** | AES-CCMP-128/192 | **SAE** (Dragonfly) | 802.1X + 192-bit suite |

**General hardening checklist** 🔒  
update FW → change admin pwd → enable WPA2/3 ENT or SAE → rotate keys → isolate WLAN with firewall/VLAN → deploy WIDS/WIPS → force VPN for guests.

### Wi-Fi Protected Setup (WPS)
Designed for push-button/PIN onboarding but **PIN can be brute-forced (<4 hrs)**. Always disable WPS or upgrade firmware where Off truly disables it.

### Wireless MAC Filter
AP allow-list of NIC MACs. Provides minimal security—MACs are broadcast in cleartext and easily spoofed. Use only in small, static environments.

### Wireless Antenna Management
* **Omni** (dipole “rubber duck”) radiates 360°.  
* **Directional** (Yagi, panel, parabolic) focuses beam → extended range & reduced leakage.  
Guidelines: center APs, avoid metal/EMI, tweak power incrementally, document default settings.

### Using Captive Portals
Redirect newcomers to web splash page for AUP consent, voucher, or payment. Enforce HTTPS so credentials are protected; integrate with RADIUS for accounting.

### General Wi-Fi Security Procedure
1. Patch firmware  
2. Change default admin creds & SSID  
3. Activate WPA3-ENT (or WPA2-ENT)  
4. Long PSK ≥ 20 chars if personal mode  
5. Disable WPS & UPnP  
6. Segment WLAN from LAN (firewall/VLAN)  
7. Enable client isolation for guests  
8. Deploy WIDS/WIPS + NIDS  
9. Require VPN for sensitive traffic  
10. Log & monitor all RF events 📈  

### Wireless Communications
#### RF Fundamentals
* Frequency = cycles/sec (Hz). Wi-Fi, Bluetooth, Zigbee operate in 2.4/5/6 GHz ISM bands.
* Multiplexing/efficiency: **FHSS, DSSS, OFDM, OFDMA, MIMO, MU-MIMO**.

#### Bluetooth & BLE
Short-range (≤100 m) 2.4 GHz PAN. Pairing default PINs vulnerable. Attack spectrum:
* **Bluesnarfing** (data theft), **Bluebugging** (remote control), **BLUFFS** (session key break).  
Defense: disable when idle, enforce numeric-comparison/BLE secure connections.

#### RFID / NFC
Passive tags powered by reader field; NFC <4 cm. Risks: skimming, cloning, relay. Use Faraday sleeves, mutual-auth chips, disable NFC when unused.

### Wireless Attacks
| Attack | Method | Mitigation |
|--------|--------|------------|
| **War-driving** | Scan for SSIDs & configs | Disable SSID beacon, WPA3, WIDS |
| **Rogue AP** | Unsanctioned AP inside org | 802.1X, AP whitelist, WIDS sweep |
| **Evil Twin** | Clone SSID/BSSID to hijack clients | Validate certs, prune saved SSIDs, VPN |
| **Disassociation/Deauth** | Spoof mgmt frames → DoS | WPA3 + 802.11w, WIPS |
| **Jamming** | Flood RF to drop SNR | Channel hop, directional antennas, locate source |
| **IV/Re-play** | Exploit weak IVs (WEP) or resend frames | Use AES-CCMP, enable replay-protection |

## Satellite Communications
Satellite links use RF between earth stations and artificial satellites in three main orbital regimes:

| Orbit | Altitude | Footprint | Latency | Typical Use |
|-------|----------|-----------|---------|-------------|
| **LEO** | 160 – 2 000 km | Small | 20–40 ms | Broadband constellations (Starlink), imaging |
| **MEO** | 2 000 – 35 786 km | Medium | 50–150 ms | GPS, some data relays |
| **GEO** | 35 786 km (equatorial) | Very large, stationary | 500 + ms | TV, legacy VSAT, SATCOM |

*Security notes*  
* Downlink/uplink can be intercepted—use end-to-end crypto (IPsec, TLS, FS modulation).  
* GEO delay hinders real-time protocols; choose TCP optimizers or UDP-based transports.

## Cellular Networks
Cellular systems divide coverage into **cells** served by base stations. Generational standards evolve roughly every decade:

| Generation | Core Tech | Peak DL (theoretical) | Encryption | Security Concerns |
|------------|-----------|-----------------------|------------|-------------------|
| 2G (GSM/CDMA) | Circuit/packet mix | 384 kb/s | A5/1, CAVE | Weak ciphers crackable; IMSI catchers |
| 3G (UMTS) | W-CDMA | 2 Mb/s | KASUMI | SS7 signaling attacks |
| 4G (LTE) | OFDMA | 1 Gb/s (static) | AES-128 SNOW | IMSI catching, rogue eNodeB |
| 5G (NR) | OFDMA + mmWave | 10 Gb/s | 256-bit AES, SUCI privacy | Network slicing isolation, SDN core |

**Best practice:** treat carrier link as untrusted; tunnel sensitive data with TLS or a mobile VPN, enforce MDM baseline, and detect rogue base stations (IMSI catchers).

## Content Distribution Networks (CDNs)
A CDN replicates content to many edge PoPs, decreasing RTT and absorbing DDoS.

| Benefit | Security Implication |
|---------|---------------------|
| Reduced latency | TLS off-load must preserve cert trust; HSTS recommended |
| Load absorption | CDN can front-end DDoS but hides real IPs; misconfig leaks origin |
| Geographic fail-over | Must align PoP GDPR / data-sovereignty controls |

Client-side P2P CDN (e.g., BitTorrent-based) shares load but complicates data integrity; implement strong hash verification and signed manifests.

## Secure Network Components
### Secure Operation of Hardware
* **Redundant power** – dual PSUs in 1 + 1 or N + 1 feed; combine with UPS/GENSET.  
* **Warranty & vendor support** – SLA for RMA < 4 h on critical gear.  
* **Hardened firmware** – disable unused services, verify signatures, schedule patch windows.  
* **Environment** – racks with temp/humidity sensors; locking bezels; tamper-evident seals.

### Common Network Equipment
| Device | OSI Layer | Purpose | Security Note |
|--------|-----------|---------|---------------|
| Repeater / Hub | 1 | Boost / fan-out signal | Replaced by switches; no ACL capability |
| Switch | 2 (3 w/ routing) | MAC-based frame forwarding, VLANs | Enable STP guard, DHCP snooping |
| Router | 3 | Route IP packets | Harden with ACLs, BGP auth |
| Multiplexer / Aggregator | 1-2 | Combine multiple links | Ensure QoS isolation |
| Jumpbox | 4-7 | Controlled administrative pivot | MFA, session recording |
| Sensors / Collectors (SoC) | varies | Telemetry to SIEM | Protect key material, validate updates |

### Network Access Control
* **Preadmission** – posture checked *before* granting VLAN.  
* **Postadmission** – continuous monitoring, dynamic quarantine.  
* **Agents** – permanent (service) or dissolvable (CAPTIVE portal).  
* Combine 802.1X (port) + RADIUS attributes for real-time VLAN steering.  
* Align with zero-trust: verify device health + identity each connection.

**Goals**
- Prevent/reduce known attacks directly and zero-day indirectly
- Enforce security policy throughout the network
- Use identities to perform access control

### Firewalls
| Type | Key Characteristics | Typical Layer(s) | Use Case |
|------|---------------------|------------------|----------|
| Static packet filter | ACL on IP/port | 3-4 | Edge routers, RTBH |
| Stateful inspection | Tracks sessions, dynamic rules | 3-5 | Core perimeter |
| Application / WAF | Parses Layer-7 protocol (HTTP, SIP) | 7 | Protect web/API |
| Circuit proxy (SOCKS) | Creates TCP circuit, hides client | 4-5 | Egress control |
| NGFW / UTM | DPI + IPS + URL + AV | multi | Branch offices |
| ISFW | Internal segmentation, micro-seg | 2-7 | Lateral-movement containment |
| Host firewall | Local OS filter | 3-7 | Endpoint hardening |

**Rule management principles**  
* Implicit deny (last rule) – document exceptions.  
* Least privilege – allow required src/dst/port only.  
* Separate *ingress* and *egress* filters: drop RFC 1918 on WAN, enforce DNS/HTTP policy leaving LAN.  
* Log: boot, policy change, service crash, high-rate drops.

**Proxy patterns**  
* **Forward proxy** – client anonymity, outbound filtering.  
* **Reverse proxy** – hides origin, enables TLS termination & caching.  
* **Transparent vs. explicit** – PAC files or inline L2 redirect.

A robust architecture layers perimeter NGFW, DMZ reverse proxies, ISFW for east-west, and host firewalls, all orchestrated by SIEM/SOAR for adaptive response.

#### Firewall Tier Architectures

A firewall architecture’s “tier” is determined by the **number of distinct protected zones (trust levels)** that the firewalling solution isolates from the outside network.  
- **Single-tier:** one protected zone (e.g., only an internal LAN).
- **Two-tier:** two protected zones (e.g., a DMZ and an internal LAN).
- - **Three-tier:** three protected zones (e.g., DMZ, application subnet, and user LAN).  
- **Four-tier (and beyond):** four or more protected zones, each separated by additional firewall layers.

| Tier Count | Typical Topology | Interfaces / Zones | Primary Use Case | Advantages | Limitations / Risks |
|------------|------------------|--------------------|------------------|------------|---------------------|
| **Single-Tier Firewall** | One security appliance (or router w/ ACLs) in front of the internal LAN. | • Outside (Internet)<br>• Inside (LAN) | Small offices, labs, home networks. | • Lowest cost & complexity.<br>• Easy to manage. | • No DMZ—public services sit inside LAN.<br>• Single point of failure.<br>• Limited defense-in-depth. |
| **Two-Tier Firewall** | ① External perimeter firewall/router<br>② Internal firewall; DMZ usually between them (screened subnet). | • Outside<br>• DMZ (public servers)<br>• Inside | SMEs hosting public-facing services (web, mail). | • DMZ isolates public servers.<br>• Two devices offer layered filtering (packet filter + stateful). | • Higher cost and management overhead.<br>• Still shares trust level for all internal hosts. |
| **Three-Tier Firewall** | Cascade of two firewalls **plus** an additional internal segmentation tier (e.g., user LAN vs. server LAN). | • Outside<br>• DMZ<br>• App or Server LAN<br>• Inside (user LAN) | Enterprises needing to isolate critical servers from user workstations. | • Granular trust zones.<br>• Limits lateral movement.<br>• Supports PCI or HIPAA segmentation. | • Routing/ACL complexity.<br>• Potential performance bottlenecks. |
| **Four-Tier Firewall** | Multi-layered “zero-trust” stack, often:<br>1) Edge firewall<br>2) DMZ firewall<br>3) Application firewall / WAF<br>4) Data-center or database firewall | • Outside<br>• DMZ<br>• App Tier<br>• Data Tier<br>• Inside | High-security environments (financial, government) or micro-segmented data centers. | • Defense-in-depth at every OSI layer.<br>• Tight control of east-west traffic.<br>• Meets stringent regulatory demands. | • Highest cost and operational complexity.<br>• Requires rigorous change-management and monitoring. |
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/0f89001e-8ee1-48c9-b055-ec2dfa943f86" />

> **Quick Pointers for CISSP Exam**
> - *Single-tier* = minimal protection; no DMZ.  
> - *Two-tier* = introduces screened subnet (DMZ) with two filtering stages.  
> - *Three-tier* = adds a dedicated internal segmentation layer (often application servers).  
> - *Four-tier* (and beyond) = fine-grained, multi-zone architecture aligned with zero-trust and micro-segmentation principles.

### Endpoint Security
Endpoint security extends the security perimeter to every device—laptop, workstation, mobile, IoT, and server—that touches the network. A single weak host can undermine enterprise controls, so endpoints must enforce **defense-in-depth** locally.

#### Core Controls
| Layer | Technique | Why It Matters |
|-------|-----------|----------------|
| Hardware | UEFI/TPM secure boot, drive encryption (BitLocker, FileVault) | Blocks rootkits, protects data at rest if stolen |
| OS Hardening | Remove bloatware, patch baseline image, enforce least-privilege, application allow-listing | Reduces attack surface; consistent gold image ensures compliance |
| Network | Host firewall, 802.1X supplicant, local IDS/IPS | Stops lateral movement; verifies posture before VLAN access |
| Malware & Threats | EDR/EPP with real-time ML, behavior heuristics, isolated sandbox | Detects file-less attacks and zero-days beyond signature AV |
| Data | DLP agent, full-disk & file/folder encryption, controlled removable-media | Prevents exfiltration and mitigates lost-device risk |
| User | MFA, screen-lock timeouts, security awareness training | Thwarts credential stuffing and shoulder surfing |

**EDR ↔ MDR ↔ XDR**  
* EDR focuses on device telemetry & local response.  
* MDR adds 24×7 outsourced threat-hunting/SOC.  
* XDR unifies endpoint + network + cloud signals into one correlated detection fabric.

#### Endpoint Build Lifecycle
1. **Provision** from master image (CIS-benchmarked).  
2. Register with **MDM/UEM** for continuous configuration.  
3. **Validate posture** via NAC before production VLAN.  
4. Apply **secure policy** (FW, DLP, USB control).  
5. **Monitor & respond** (EDR alerts → SOAR runbooks).  
6. **Retire** devices with cryptographic wipe & asset tracking.

### Cabling, Topology, and Transmission Media Technology
Selecting proper media impacts **throughput, distance, EMI resilience, and physical security**.

#### Twisted-Pair Categories
| Cat | Speed / Signaling | Max Distance* | Typical Use |
|-----|-------------------|---------------|-------------|
| 5e | 1 Gb/s | 100 m | Legacy gigabit |
| 6  | 1 Gb/s (10 Gb/s ≤ 55 m) | 100 m | Standard access layer |
| 6a | 10 Gb/s | 100 m | Data center ToR |
| 7  | 10 Gb/s (shielded) | 100 m | No ANSI/TIA recognition |
| 8  | 25–40 Gb/s (shielded) | 30 m | Switch-to-server links |

\*ANSI/TIA limit for horizontal run.

**Coax (RG-6)** still feeds DOCSIS cable modems; legacy 10Base-2/5 now obsolete.

#### Fiber-Optic Quick View
| Mode | Core Ø | Light Source | Max Dist (10 Gb/s) | Security |
|------|--------|--------------|--------------------|----------|
| **MMF** | 50/62.5 µm | LED/VCSEL 850 nm | 400 m | Lower cost, easier termination |
| **SMF** | 9 µm | Laser 1310/1550 nm | 10 km+ | Immune to EMI, hard to tap |

Dense Wavelength Division Multiplexing (DWDM) enables 40–96 λ channels per strand—massive backbone capacity.

### Transmission Media
Signal quality hinges on **attenuation, EMI/RFI, crosstalk, jitter, SNR**. Countermeasures:

* Twist rate & STP foil (UTP).  
* Fiber’s glass core—no radiated emissions, supports **TEMPEST** requirements.  
* Secure conduits & plenum-rated jackets for physical tamper/fire codes.  
* Encryption (MACsec, TLS, IPsec) to protect data if the medium is tapped.

### Transport Architecture
#### Networking Planes
| Plane | Role | Example Tech |
|-------|------|--------------|
| Data (Forwarding) | Fast packet switching/queuing | ASIC in L3 switch |
| Control | Builds routing/ACL state | OSPF, BGP, SDN OpenFlow |
| Management | Configuration & telemetry | NETCONF, SNMP, REST APIs |

#### Switching Paradigms
| Method | Latency | Error Handling |
|--------|---------|----------------|
| **Cut-through** | µs (reads header only) | CRC errors forwarded |
| **Store-and-forward** | Higher (buffers frame) | Full FCS check, drops bad frames |

Use cut-through inside low-latency HFT pods; store-and-forward at security or WAN edges.

### Network Topologies
| Topology | Pros | Cons | Common Today? |
|----------|------|------|---------------|
| **Star** | Easy fault isolation, scalable | Hub/switch = SPOF | ✅ (Ethernet) |
| **Bus** | Minimal cable | Single trunk failure kills net | ❌ legacy |
| **Ring** | Predictable latency | Break = outage (unless dual) | ❌ (FDDI legacy) |
| **Mesh (full / partial)** | Redundant paths, high resiliency | Costly links | ✅ data-center leaf-spine |
| **Hybrid** | Mix for flexibility | Design complexity | ✅ campus core |

Logical vs. physical can differ: e.g., Ethernet physical star but **logical bus** on a hub.

### Ethernet
IEEE 802.3 defines frame format (MAC header + FCS) and CSMA/CD (half-duplex legacy). Modern switched Ethernet eliminates collisions and supports **full-duplex**.

| Flavor | Medium | Signaling | Max Segment |
|--------|--------|-----------|-------------|
| 100Base-TX | Cat 5 | 4B/5B, MLT-3 | 100 m |
| 1000Base-SX | MMF | 8B/10B | 550 m |
| 10GBase-T | Cat 6/6a | 128-DSQ PAM-16 | 55/100 m |
| 25/40/100GBase-SR4 | MMF MPO | PAM-4 | 70–100 m |

### Sub-Technologies
#### Signaling
* **Digital** (discrete 0/1) vs. **analog** (continuous).  
* **Baseband** (single channel—Ethernet) vs. **broadband** (multiple RF carriers—DOCSIS).

#### Media Access Methods
| Technique | Used By | Collision Strategy |
|-----------|---------|--------------------|
| CSMA/CD | Legacy hub Ethernet | Detect & back-off |
| CSMA/CA | 802.11 Wi-Fi | Avoid with RTS/CTS |
| Token Passing | FDDI, Token Ring | No collisions |
| Polling | Mainframe SNA | Master grants turn |

#### Casting Modes
* **Unicast** – 1 → 1 (TCP).  
* **Broadcast** – 1 → all (ARP).  
* **Multicast** – 1 → many selective (IGMP).  
* **Anycast** – 1 → nearest (DNS root).  
* **Geocast** – 1 → receivers in area (vehicular networks).

### Summary
* **Endpoint security** transforms every device into its own security zone—EDR/XDR and strong hardening are exam-critical.  
* Understand cabling limits: UTP ≤ 100 m, MMF 400 m @ 10 Gb/s, SMF multi-km; fiber resists EMI & tapping.  
* Transport architecture separates **data, control, management planes**; cut-through vs. store-and-forward switching trade latency for integrity.  
* Topologies affect resilience—star dominates LAN, leaf-spine mesh in data centers.  
* Ethernet framing & speeds (10 Mb → 100 Gb+) underpin most wired networks.  
* Sub-technologies (baseband/broadband, CSMA variants, casting types) explain how traffic shares media and reaches recipients.  
Grasp these layers—from wire to workload—to design and defend networks to CISSP expectations. 🚀
