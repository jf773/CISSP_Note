# Chapter 12: Secure Communications and Network Attacks

- [Study Essentials](#study-essentials)
- [Protocol Security Mechanisms](#protocol-security-mechanisms)
  - [Authentication Protocols](#authentication-protocols)
  - [Port Security](#port-security)
  - [Quality of Service (QoS)](#quality-of-service-qos)
- [Secure Voice Communications](#secure-voice-communications)
  - [Public Switched Telephone Network](#public-switched-telephone-network)
  - [Voice over Internet Protocol (VoIP)](#voice-over-internet-protocol-voip)
  - [Vishing and Phreaking](#vishing-and-phreaking)
  - [PBX Fraud and Abuse](#pbx-fraud-and-abuse)
- [Remote Access Security Management](#remote-access-security-management)
  - [Remote Access and Telecommuting Technologies](#remote-access-and-telecommuting-technologies)
  - [Remote Connection Security](#remote-connection-security)
  - [Plan a Remote Access Security Policy](#plan-a-remote-access-security-policy)
  - [Network Administrative Functions](#network-administrative-functions)
- [Multimedia Collaboration](#multimedia-collaboration)
  - [Remote Meeting](#remote-meeting)
  - [Instant Messaging and Chat](#instant-messaging-and-chat)
- [Monitoring and Management](#monitoring-and-management)
- [Load Balancing](#load-balancing)
  - [Virtual IP Addresses](#virtual-ip-addresses)
  - [Active-Active vs. Active-Passive](#active-active-vs-active-passive)
- [Manage Email Security](#manage-email-security)
  - [Email Security Goals](#email-security-goals)
  - [Understand Email Security Issues](#understand-email-security-issues)
  - [Email Security Solutions](#email-security-solutions)
- [Virtual Private Network](#virtual-private-network)
  - [Tunneling](#tunneling)
  - [How VPNs Work](#how-vpns-work)
  - [Always-On](#always-on)
  - [Split Tunnel vs. Full Tunnel](#split-tunnel-vs-full-tunnel)
  - [Common VPN Protocols](#common-vpn-protocols)
- [Switching and Virtual LANs](#switching-and-virtual-lans)
  - [MAC Flooding Attack](#mac-flooding-attack)
  - [MAC Cloning](#mac-cloning)
- [Network Address Translation](#network-address-translation)
  - [Private IP Addresses](#private-ip-addresses)
  - [Stateful NAT](#stateful-nat)
  - [Automatic Private IP Addressing](#automatic-private-ip-addressing)
- [Third-Party Connectivity](#third-party-connectivity)
- [Switching Technologies](#switching-technologies)
  - [Circuit Switching](#circuit-switching)
  - [Packet Switching](#packet-switching)
  - [Virtual Circuits](#virtual-circuits)
- [WAN Technologies](#wan-technologies)
- [Fiber-Optic Links](#fiber-optic-links)
- [Prevent or Mitigate Network Attacks](#prevent-or-mitigate-network-attacks)
  - [Eavesdropping](#eavesdropping)
  - [Modification Attacks](#modification-attacks)
- [Summary](#summary)

## Study Essentials
| Key Concept | Details |
|-------------|---------|
| **Understand PPP.** | Point-to-Point Protocol (PPP) is an encapsulation protocol designed to support the transmission of IP traffic over dial-up or point-to-point links. The original PPP options for authentication were PAP, CHAP, and EAP. |
| **Define PAP, CHAP, and EAP.** | Password Authentication Protocol (PAP) transmits usernames and passwords in cleartext. Challenge Handshake Authentication Protocol (CHAP) performs authentication using a challenge-response dialogue that cannot be replayed. Extensible Authentication Protocol (EAP) allows customized authentication security solutions. |
| **Understand IEEE 802.1X.** | IEEE 802.1X defines the use of encapsulated EAP to support a wide range of authentication options for LAN connections. The IEEE 802.1X standard is formally named “Port-Based Network Access Control.” |
| **Know about port security.** | Port security can mean the physical control of all connection points, such as RJ-45 wall jacks or device ports. Port security is the management of TCP and User Datagram Protocol (UDP) ports. Port security can also refer to the need to authenticate to a port before being allowed to communicate through or across the port (i.e., IEEE 802.1X). |
| **Understand voice communications security.** | Voice communications are vulnerable to many attacks, especially as voice communications become an important part of network services. You can obtain confidentiality by using encrypted communications. Countermeasures must be deployed to protect against interception, eavesdropping, tapping, and other types of exploitation. |
| **Know the threats associated with PBX systems and the countermeasures to PBX fraud.** | Countermeasures to PBX fraud and abuse include many of the same precautions you would employ to protect a typical computer network: logical or technical controls, administrative controls, and physical controls. |
| **Understand the security issues related to VoIP.** | VoIP is at risk for caller ID spoofing, vishing, call-manager software/firmware attacks, phone hardware attacks, DoS, AitM/MitM/on-path attacks, spoofing, and switch hopping. |
| **Recognize what phreaking is.** | Phreaking is a specific type of attack in which various types of technology are used to circumvent the telephone system to make free long-distance calls, to alter the function of telephone service, to steal specialized services, or to cause service disruptions. A phreaker is an attacker who performs phreaking. |
| **Understand the issues of remote access security management.** | Remote access security management requires that security system designers address the hardware and software components of an implementation along with issues related to policy, work tasks, and encryption. |
| **Know various issues related to remote access security.** | Be familiar with remote access, dial-up connections, screen scrapers, virtual applications/desktops, and general telecommuting security concerns. |
| **Understand multimedia collaboration.** | Multimedia collaboration is the use of various multimedia-supporting communication solutions to enhance distance collaboration and communications. |
| **Know the purpose of load balancers.** | The purpose of load balancing is to obtain more optimal infrastructure utilization, minimize response time, maximize throughput, reduce overloading, and eliminate bottlenecks. A load balancer is used to spread or distribute network traffic load across several network links or network devices. |
| **Understand active/active.** | An active-active system is a form of load balancing that uses all available pathways or systems during normal operations but that has reduced capacity in adverse conditions. |
| **Understand active/passive.** | An active-passive system is a form of load balancing that keeps some pathways or systems in an unused dormant state during normal operations. It is able to maintain consistent capacity during abnormal conditions. |
| **Understand virtualized networks.** | A virtualized network or network virtualization is the combination of hardware and software networking components into a single integrated entity. Examples include software-defined networks (SDNs), VLANs, VPNs, virtual switches, virtual SANs, guest operating systems, port isolation, and NAT. |
| **Define tunneling.** | Tunneling is the encapsulation of a protocol-deliverable message within a second protocol. The second protocol often performs encryption to protect the message contents. |
| **Understand VPNs.** | VPNs are based on encrypted tunneling. They can offer authentication and data protection as a point-to-point solution. Common VPN protocols are PPTP, L2TP, SSH, TLS, and IPSec. |
| **Understand split vs. full tunnel.** | A split tunnel is a VPN configuration that allows a VPN-connected client system (i.e., remote node) to access both the organizational network over the VPN and the Internet directly at the same time. A full tunnel is a VPN configuration in which all of the client's traffic is sent to the organizational network over the VPN link, and then any Internet-destined traffic is routed out of the organizational network's proxy or firewall interface to the Internet. |
| **Be able to explain NAT.** | NAT protects the addressing scheme of a private network, allows the use of the private IP addresses, and enables multiple internal clients to obtain Internet access through a few public IP addresses. NAT is supported by many security border devices, such as firewalls, routers, gateways, WAPs, and proxies. |
| **Know about third-party connectivity.** | Most organizations interact with outside third-party providers. Most of these external entities do not need to interact directly with an organization's IT/IS. However, for those few that do, it is important to consider the risks and ramifications. This includes partnerships, cloud services, and remote workers. |
| **Understand the difference between packet switching and circuit switching.** | In circuit switching, a dedicated physical pathway is created between the two communicating parties. Packet switching occurs when the message or communication is broken up into small segments and sent across the intermediary networks to the destination. Within packet-switching systems are two types of communication paths, or virtual circuits: permanent virtual circuits (PVCs) and switched virtual circuits (SVCs). |
| **Understand the various network attacks and countermeasures associated with communications security.** | Communication systems are vulnerable to many attacks, including distributed denial-of-service (DDoS), eavesdropping, impersonation, replay, modification, spoofing, and ARP and DNS attacks. Be able to supply effective countermeasures for each. |


## Protocol Security Mechanisms
Communications security 🛡️ preserves **confidentiality, integrity, and availability (CIA)** as data traverses a network. TCP/IP’s inherent weaknesses are mitigated by supplementary security mechanisms—especially **authentication protocols**, **port security**, and **quality-of-service (QoS)** controls.

### Authentication Protocols
Mechanisms that verify a subject’s identity before a connection or service is granted.

#### Point-to-Point Protocol (PPP) Foundation
PPP (RFC 1661) encapsulates IP over serial or dial-up links, providing framing, error detection, option negotiation, and authentication handshakes.

| PPP Legacy | Drawbacks | Modern Replacement |
|------------|-----------|--------------------|
| SLIP | No auth, half-duplex, manual link control | PPP adds full-duplex, LCP negotiation, and optional auth |

#### Core PPP Authentication Options
| Method | Process | Strengths | Weaknesses | CISSP Tip |
|--------|---------|-----------|------------|-----------|
| PAP | Username & password sent **in clear text** | Simple | No encryption ➜ susceptible to sniffing | Rarely acceptable except in VPN fallback labs |
| CHAP | Server sends random challenge ➜ client returns hash | - One-way handshake blocks replay<br>- Periodic re-auth during session | Relies on MD5 (deprecated) | Prefer MS-CHAPv2 or EAP-based methods |
| MS-CHAPv2 | Microsoft update to CHAP | Stronger cryptography & optional session encryption | Proprietary; still weaker than TLS-based EAP | Use only if EAP-TLS unavailable |

#### Extensible Authentication Protocol (EAP) Framework
An **IETF framework**—not a single protocol—allowing pluggable authentication types.

| EAP Variant | Transport Protection | Typical Use | Current Guidance |
|-------------|----------------------|-------------|------------------|
| EAP-TLS | TLS tunnel & mutual certs | Enterprise Wi-Fi, 802.1X | ⭐ Gold standard (strong mutual auth) |
| PEAP | TLS tunnel around EAP | Wi-Fi with username/password | Secure if server cert validated |
| EAP-TTLS | TLS tunnel ➜ legacy inner auth | Mixed environments | Good when replacing PEAP |
| EAP-FAST | Protected PAC tunnel | Cisco gear | Acceptable; less overhead than PEAP |
| LEAP | None (legacy) | Old Cisco WLAN | ❌ Insecure—avoid |
| EAP-SIM / AKA | SIM challenge | Mobile devices | Carrier networks |
| EAP-MD5 | Clear-text username, MD5 hash | Early PPP | ❌ Deprecated |
| EAP-NOOB | Out-of-band bootstrap (QR, NFC) | IoT onboarding | Emerging |
| EAP-POTP (Protected One-Time Password) | No native encryption; relies on outer method (e.g., PEAP, EAP-TTLS) to wrap traffic in TLS | Hardware/software OTP tokens for one-way or mutual authentication in 802.1X WLAN or VPN deployments | Still acceptable when a TLS tunnel is enforced, but adoption is limited; prefer EAP-TLS or PEAP + TLS where possible for broader support and certificate-based security |

> **Exam hint:** Remember that **EAP defines message format**; security depends on the *method* chosen.

##### IEEE 802.1X Port-Based NAC
* Acts as an **EAP over LAN** wrapper.
* Controls switch, VPN, or Wi-Fi ports until supplicant authenticates.
* Vulnerabilities: man-in-the-middle during initial handshakes; mitigate with secure EAP methods and mid-session re-auth.

### Port Security
Safeguards that restrict physical or logical ports to trusted devices and services.

#### Physical Port Control
* Disable/lock unused wall jacks, patch-panel ports, and switch interfaces.
* Use smart patch panels to detect MAC changes and rogue devices.

#### Logical Port (TCP/UDP) Hardening
* Close all unnecessary service ports; enable only required daemons.
* Employ stateful firewalls/IPS to thwart port scanning and send **bogus** replies (port-scan deception).

#### Authentication to a Port
* 802.1X NAC enforces auth **before** granting Layer 2 access—often integrated with RADIUS/TACACS+.

| Port Security Technique | OSI Layer | Protects Against | Key Tools |
|-------------------------|-----------|------------------|-----------|
| Disable unused switch ports | 1/2 | Rogue plugs | Switch config |
| MAC binding / sticky MAC | 2 | Device spoofing | Switch “port-security” |
| 802.1X + RADIUS | 2 | Unauthorized hosts | Supplicant + authenticator |
| Host-based firewall rules | 4 | Port scans, service abuse | OS firewall, iptables |
| Application-layer gateway | 7 | Protocol misuse | NGFW / proxy |

### Quality of Service (QoS)
Policies ensuring vital traffic keeps flowing—**availability** is a security goal.

#### Performance Metrics
* **Bandwidth** – capacity (bps).
* **Latency** – one-way delay (⏱️).
* **Jitter** – variance in latency (🎢).
* **Packet Loss** – dropped frames (%).
* **Throughput** – actual delivered data.
* **Signal-to-Noise Ratio (SNR)** – link quality.

| Metric | Cause of Degradation | Impact | Countermeasure |
|--------|---------------------|--------|----------------|
| High latency | Long routes, congestion | VoIP lag | Prioritize RTP |
| Jitter | Queuing, variable load | Video stutter | Buffering, shaping |
| Packet loss | Errors, drops | Retransmits | FEC, redundancy |
| Low SNR | Interference | Wireless errors | Channel change |

#### QoS Techniques
* **Classification & Marking** – DSCP/ToS bits tag priority classes.
* **Queuing** – priority, weighted fair, or low-latency queues.
* **Traffic Shaping/Policing** – throttle bulk data; guarantee voice.
* **Admission Control** – deny new flows when capacity exceeded.
* **Path Diversity** – route critical apps over redundant links.

> **Security tie-in:** A DoS flood can exhaust queues—QoS policies can isolate malicious traffic and preserve business-critical services.

#### Transparency
QoS (and other controls) should be **transparent**—minimal user impact and no obvious bypass cues.

### Study Essentials ✨
* **Know PPP auth order:** PAP (clear-text) ⟶ CHAP (challenge) ⟶ EAP (framework).  
* **EAP-TLS = strongest**; **LEAP / EAP-MD5 = obsolete**.  
* **802.1X** is not Wi-Fi-specific; any switch or VPN port can leverage it.  
* **Port security** spans *physical* jack lockdowns, *logical* service hardening, and *authenticated* access (802.1X).  
* **QoS protects availability**—a core CISSP objective—by managing bandwidth, latency, jitter, and loss.  
* Remember linkage between **QoS** and **DoS mitigation** in exam scenarios.

## Secure Voice Communications
Telephony risks overlap IT security as voice increasingly rides converged IP networks. Know how each platform works, where it is weak, and the specific countermeasures the CISSP exam expects.

### Public Switched Telephone Network (PSTN)
Traditional analog/digital circuit-switched voice (a.k.a. POTS).  
* **Vulnerabilities**: physical wire-tapping, line-side eavesdropping, caller-ID spoofing, long-distance toll fraud.  
* **Controls**  
  * Physical security of demarc, wiring closets, punch-down blocks.  
  * End-to-end voice encryption devices (e.g., secure phones/STU-III equivalents).  
  * Contract clauses that push security obligations to the carrier.  
  * Disable unneeded analog modems; audit any left as backups.

**Demarc** – Point of Demarcation (POD): Where the ISP (Internet Service Provider) terminates their phone/internet lines and your network begins; most buildings only have one.

### Voice over Internet Protocol (VoIP)
Encapsulates voice in IP packets (RTP/UDP). Signaling via **SIP**, **H.323**, **MGCP**, or proprietary protocols.

| Aspect | PSTN | VoIP |
|--------|------|------|
| Switching | Circuit | Packet |
| Confidentiality | Rare (requires inline crypto) | **SRTP** for media, **SIPS (TLS)** for signaling |
| Integrity | Physical tamper | Checksums, TLS | 
| Availability threats | Cut line, PBX abuse | DoS, RTP flood, VLAN hopping |
| Identity spoof | Caller-ID | Caller-ID **and** SIP header manipulation |

#### VoIP Threats 🚨
* SIP registration hijack
* Toll fraud via compromised SIP credentials
* **SPIT** (Spam over Internet Telephony)
* RTP injection or replay
* Man-in-the-Middle at gateway transitions
* Poor default passwords on ATAs/IP phones

#### VoIP Countermeasures
* Encrypt: **SRTP**, **ZRTP**, **TLS**-protected SIP.
* Separate voice VLAN; apply QoS + ACLs.
* Session Border Controller (SBC) for NAT traversal & security policy.
* Strong device/password policies; firmware patching 📆.
* Logging and CDR analysis for anomalous call patterns.

### Vishing and Phreaking
* **Vishing** = Voice phishing (social-engineering by phone) 📞.
  * Cheap VoIP + spoofed numbers = believable pretexts.
  * Train users to verify, use call-back procedures, distrust CLI.  
* **Phreaking** = Attacking telephony systems to avoid charges or disrupt.
  * Blue/black boxes (tone injection), SIM cloning, SS7 exploits.
  * Counter: carrier fraud monitoring, blocking premium/international prefixes, audit logs.

### PBX Fraud and Abuse
Enterprise switch connecting many extensions to few trunks.

**Typical Attacks**
1. Remote dial-in (DISA) abuse → long-distance fraud.
2. Unauthorized voicemail access ➜ password reset, message theft.
3. Configuration tampering (call-forward to premium numbers).

**Defenses**
* DISA with MFA or scrap it entirely.
* Change vendor defaults, disable unused codes/features.
* Least-privilege on extension classes of service.
* Continuous CDR review; alert on after-hours or high-cost calls.
* Keep PBX OS/firmware patched; isolate on secure management VLAN.

## Remote Access Security Management
Remote access extends the attack surface; policies must balance productivity with CIA.

### Remote Access and Telecommuting Technologies
| Category | Examples | Key Security Control |
|----------|----------|----------------------|
| **Service-Specific** | Outlook-Web-Access, SSH-Git | App-level TLS, WAF |
| **Remote Control** | RDP, VNC, TeamViewer | Network-level MFA, clipboard/file transfer rules |
| **Remote Node** | IPSec/SSL VPN client, LTE router | NAC posture check, split-vs-full tunnel governance |
| **Thin/Virtual Desktop** | VDI, DaaS, HTML5 gateway | Harden broker, isolate VDI network, record sessions |
| **Legacy Dial-up** | PSTN modem, ISDN | Callback, CHAP/EAP-TLS, unlisted numbers |

### Remote Connection Security 🔒
1. **Strong Authentication** – MFA (token + password), certificate-based EAP-TLS.  
2. **Confidentiality** – Tunnel encryption (IPSec ESP, SSL/TLS, WireGuard).  
3. **Integrity & Replay Protection** – IPSec AH, TLS sequence numbers.  
4. **Endpoint Hygiene** – NAC, antimalware, full-disk crypto, screen-lock.  
5. **Least Privilege** – ACLs limiting reachable subnets/ports.  
6. **Monitoring** – Log concentrators, geo-velocity alerts, session recording.

### Plan a Remote Access Security Policy
* **Approved Technologies** – Specify allowed VPN protocols, remote-desktop stacks, mobile apps.  
* **Encryption Standards** – Minimum TLS 1.3 / AES-256-GCM; prohibit PPTP & RC4.  
* **Authentication Workflow** – Centralized AAA (RADIUS/TACACS+), federation (SAML/OIDC).  
* **User Eligibility & Roles** – Who may connect, from where, at what times.  
* **Endpoint Requirements** – Patch level, anti-virus, no shared accounts, device compliance checks.  
* **Support & Incident Response** – Help-desk pin resets, lost device procedures, forensic capture.  
* **Audit & Metrics** – Log retention, periodic access review, VPN utilization reports.  
* **Change Management** – Document new gateways, cert rollover, key lifetimes.  
* **Acceptable Use** – Prohibit split-tunnel for admins; forbid storing data locally if not encrypted.

### Network Administrative Functions
Remote administration lets ops staff manage gear off-site—great for uptime, dangerous if mis-secured.

**Typical Tasks**
* Device configuration (SSH/NETCONF)
* Firmware upgrades & patching
* Log/metric collection (SNMPv3, Syslog over TLS)
* Backup, restore, topology changes
* Incident triage & containment

**Best-Practice Safeguards**
| Control | Rationale |
|---------|-----------|
| Jump-box / bastion host | Single hardened ingress point with audit trail |
| Privileged Access Management (PAM) | Just-in-time credentials, session recording |
| Out-of-Band (OOB) mgmt network | Maintain control during main-net outage |
| Mandatory SSHv2 w/ key auth | Encrypt + authenticate CLI sessions |
| Role-based admin accounts | Segregation of duties |
| Change-control workflow | Prevent config drift, enable rollback |
| Time-based ACLs | Block admin access after hours unless emergency |

> **Exam tip:** Any remote administrative path must meet *equal or stronger* security than standard user VPNs—think MFA, encryption, and full logging.

### Study Essentials ✨
* PSTN = circuit; VoIP = packet ➜ different threat models; know **SRTP** + **SIP-TLS**.  
* **Vishing** (social) vs. **Phreaking** (technical) – train users vs. harden systems.  
* **PBX fraud** often exploits default DISA or voicemail PINs—disable or lock down.  
* Remote access types: **service-specific, remote-control, remote-node**—CISSP loves definitions.  
* A sound remote access policy calls for **MFA, encryption, endpoint health, logging**, and **least privilege**.  
* Remote admin must flow through controlled channels (jump-host, SSH, PAM) with complete auditability.

## Multimedia Collaboration
Collaboration suites blend voice, video, chat, screen-share, and shared documents so distributed teams can work as if co-located. Security controls must equal on-premises protections—even when endpoints are off-site 🌐.

### Remote Meeting
Virtual-meeting platforms (e.g., Zoom, Webex, Teams, Meet) support synchronous video, VoIP, whiteboards, and file exchange.

| Security Question | Why It Matters | Best-Practice Control |
|-------------------|---------------|-----------------------|
| **Authentication** method? | Prevents impostors joining | Enforce SSO + MFA, waiting rooms |
| **Encryption** scope? | Confidentiality in transit | Prefer end-to-end AES-GCM; disable legacy TLS |
| **Session controls** | Data leakage, Zoombombing | Lock meetings, unique IDs, lobby moderation |
| **Recording & storage** | Privacy obligations | Granular recording rights; encrypted cloud vault |
| **Logging/Audit** | Incident response | Centralized log export (SIEM) |

> **CISSP note:** Evaluate SaaS conferencing providers against policy, regulatory, and data-residency requirements before adoption.

### Instant Messaging and Chat
IM/Chat (Slack, Mattermost, Signal, XMPP, IRC variants) enables real-time text, emojis, file uploads, and sometimes voice/video.

* **Threats:** Clear-text transport, weak auth, social-engineering, malware via file uploads, credential theft via OAuth apps.  
* **Controls:**  
  * TLS 1.3 for server–client traffic.  
  * MFA; SCIM/JIT provisioning for account lifecycle.  
  * Retention & e-discovery rules (GDPR, HIPAA).  
  * DLP scanning; file-type restrictions; anti-malware sandbox.  
  * Enterprise key-management (EKM) if end-to-end encryption required.

## Monitoring and Management
Continuous visibility ensures the network remains performant and secure 👁️.

| Discipline | Purpose | Key Tools/Methods |
|------------|---------|-------------------|
| **Network observability** | Infer internal state from logs, metrics, traces | SNMPv3, NetFlow/IPFIX, sFlow, OpenTelemetry |
| **Traffic shaping / QoS** | Prioritize latency-sensitive apps, prevent congestion | Policy-based queuing, token bucket, DSCP markings |
| **Capacity management** | Forecast growth; avoid saturation | Baseline bandwidth trends; what-if modeling |
| **Fault detection & handling** | Rapid MTTR; maintain SLA | Ping/heartbeat, syslog traps, automated ticketing, redundant paths |

> Integrate monitoring feeds into a SIEM/SOAR platform for unified security + ops response (SecOps).

## Load Balancing
Distributes client requests across multiple back-end nodes to optimize availability, throughput, and fault tolerance.

| Scheduling Technique | How It Works |
|----------------------|--------------|
| **Round Robin** | Sequentially cycles through targets |
| **Least Connections / Latency** | Chooses node with fewest active sessions |
| **Weighted** | Assigns heavier load to beefier servers |
| **IP Hash / Affinity** | Same client → same server for state continuity |
| **Geo-locality** | Directs user to nearest data-center |

#### Virtual IP Addresses
A VIP is the public entry point exposed by the balancer. Behind it, multiple real servers exist. Advantages:

* Seamless **fail-over**—VIP reroutes to healthy nodes.  
* Enables **TLS offload** and HTTP/2 compression at the edge.  
* Facilitates **horizontal scaling**—add/remove nodes without DNS churn.

#### Active-Active vs Active-Passive
| Model | Normal State | Failure Handling | Pros | Cons |
|-------|--------------|------------------|------|------|
| **Active-Active** | All nodes service traffic | Remaining nodes absorb load | Maximizes utilization & throughput | Must size nodes for N-1 capacity; complex session sync |
| **Active-Passive** | Primary node(s) handle traffic; standby idle | Passive node promoted | Lower hardware burn; simpler state | Potential brief outage; under-utilized standby |

## Manage Email Security
Email remains the #1 initial attack vector. Security must address confidentiality, integrity, authenticity, and spam/abuse 📧.

### Email Security Goals
* **Confidentiality** – protect message content from eavesdropping.  
* **Integrity** – detect alteration during transit.  
* **Authentication & Non-repudiation** – verify sender identity, prevent denial.  
* **Delivery assurance** – confirm receipt; mitigate DoS (mail-bomb).  
* **Compliance/Retention** – meet legal hold, e-discovery, data-protection regs.

### Understand Email Security Issues
* SMTP, POP3, IMAP are plaintext by default ➜ sniffing.  
* **Spoofing & BEC**—easy to forge “From” header.  
* **Malware & phishing links** within attachments/HTML body.  
* **Spam** exhausts storage and attention; botnets exploit open relays.  
* **Mail-bomb / mail-storm** DoS through message floods.

### Email Security Solutions
| Control | Purpose | Notes for CISSP |
|---------|---------|-----------------|
| **S/MIME** | End-to-end encryption & signatures (X.509) | Requires PKI deployment; binds certs to email addresses |
| **OpenPGP / GnuPG** | User-controlled key mgmt, web-of-trust | Good for peer-to-peer; less enterprise manageability |
| **STARTTLS / SMTPS** | Opportunistic or implicit TLS for SMTP hop-to-hop | Protects in transit *between* MTAs, not at rest |
| **DKIM** | Domain-level signature in DNS to verify sender | Combats header spoofing |
| **SPF** | DNS TXT lists authorized outbound mail servers | Stops forged domain MAIL FROM |
| **DMARC** | Policy tying SPF & DKIM results; reporting | Reject/quarantine failures; visibility via RUA/RUF reports |
| **Gateway DLP & AV** | Strip malware, block sensitive data exfiltration | Sandboxing for zero-day payloads |
| **Spam filtering & reputation** | Reduce junk / phishing | RBLs (Spamhaus), Bayesian filters, challenge-response |
| **Attachment controls** | Block executables / macros | Allow-list mime types; cloud sandbox detonation |

> Blend **defense in depth**: TLS for transport, DKIM/SPF/DMARC for authenticity, S/MIME/PGP for content secrecy, and gateway filtering for hygiene.

## Virtual Private Network

A VPN creates a **logical, secure path** through an untrusted network, delivering confidentiality 🔒, integrity, and (with proper auth) access control between two hosts or networks.

### Tunneling
*Encapsulation* of one protocol inside another; the outer wrapper forms a “tunnel” the transit network simply forwards.  
- Inner packet stays intact; optional encryption shields its contents from inspection.  
- Adds header overhead ➜ larger frames & possible MTU/fragmentation tuning.  
- Security devices (IDS, DLP) **cannot inspect** payload until after de-encapsulation.

### How VPNs Work
1. **Handshake** – endpoints authenticate and negotiate crypto (e.g., IKE for IPSec, TLS for OpenVPN).  
2. **Key Exchange** – usually Diffie-Hellman/ECDHE plus certificates or pre-shared keys.  
3. **Data Channel** – encrypted traffic flows through the tunnel.  

| Mode | Encryption Scope | Typical Use | Key Point |
|------|------------------|-------------|-----------|
| **Transport** | Protects *payload only*; original IP header exposed | Host-to-host inside trusted network | Lightweight, but no source-IP privacy |
| **Tunnel** | Encrypts *entire* original packet; adds new outer header | Site-to-site, remote access over Internet | Hides internal addressing; slight overhead |

> Traffic is secure **only while inside** the tunnel. Plaintext resumes on either LAN unless additional controls (e.g., TLS inside VPN) are applied.

### Always-On
Client software automatically re-establishes the VPN whenever a network interface is up.  
*Benefits:* seamless protection on public Wi-Fi; prevents accidental data leakage outside tunnel.

### Split Tunnel vs Full Tunnel
| Attribute | Split Tunnel | Full Tunnel |
|-----------|--------------|-------------|
| Internet Traffic Path | Direct to ISP | Routed through VPN then out org firewall |
| LAN Protection | ❗ Client simultaneously exposed to Internet & corp network | ✔ Central security stack inspects all flows |
| Bandwidth Usage | Lower on VPN concentrator | Higher (all traffic traverses concentrator) |
| Common Use | SaaS access; low-risk workloads | Admin/privileged access; high compliance |

> CISSP exam frequently flags **split tunnels** as a security risk because they create an unfiltered bridge between the public Internet and the internal network.

### Common VPN Protocols
| Protocol | Ports | Crypto Provided | Notes / CISSP Tips |
|----------|-------|-----------------|--------------------|
| **PPTP** | TCP 1723 (+ GRE) | MPPE (weak) | Legacy only; vulnerable ⇨ avoid |
| **L2TP** (+IPSec) | UDP 1701 (+ ESP/AH) | Uses IPSec for AES | Works with RADIUS/802.1X; no native crypto |
| **IPSec** (AH/ESP) | IP 50, 51 (ESP, AH) | AES-GCM + HMAC | Industry standard; supports transport & tunnel |
| **OpenVPN (TLS)** | UDP/TCP 1194 (default) | TLS 1.3, AES-GCM | Flexible; certificates or PSK; NAT-friendly |
| **SSH Tunnels** | TCP 22 | ChaCha20/Poly1305, AES | Host-to-host “poor-man’s” VPN; limited scaling |
| **WireGuard** | UDP 51820 | ChaCha20-Poly1305 | Modern, minimalist, fast; kernel-mode driver |

> Remember: AH = integrity/auth only 🛡️, ESP = integrity + confidentiality.

## Switching and Virtual LANs

Modern Ethernet switches learn MAC↔port mappings to forward frames efficiently and support **VLAN** segmentation for security and performance.

### MAC Flooding Attack
An attacker blasts frames with bogus source MAC addresses until the switch’s CAM table overflows.  
*Result:* switch enters **fail-open flooding**, broadcasting frames to all ports—making eavesdropping possible.

**Mitigations**
- **Port Security / MAC limiting**—cap number of learned MACs per port.  
- 802.1X with dynamic VLAN assignment.  
- Rapid detection via NIDS looking for surges in unique MACs.

### MAC Cloning
Spoofing a legitimate device’s MAC to bypass filters or impersonate it (a form of identity theft at Layer 2).

**Threat Scenarios**
* Bypass “allowed-list” on WAPs or switches.  
* Hijack DHCP or ARP entries to receive traffic intended for victim.

| Defence | How It Helps |
|---------|--------------|
| **Sticky MAC + violation actions** | Locks first learned address to port; err-disable on change |
| **802.1X / certificate auth** | Ties port access to user/device credentials, not MAC |
| **Asset inventory & NMS alerting** | Detect duplicates or unauthorized MACs |

> For the exam, differentiate **MAC flooding** (cam-table exhaustion → switch acts as hub) from **MAC cloning** (spoof single address to impersonate).

## Network Address Translation
NAT hides internal addressing while enabling outbound Internet access—a **defense-in-depth staple** for IPv4 environments.

### Private IP Addresses
RFC 1918 reserves three non-routable blocks:

| Class | Range | Hosts | Typical Use |
|-------|-------|-------|-------------|
| A | 10.0.0.0 – 10.255.255.255 | 16 777 214 | Large enterprise, carrier core |
| B | 172.16.0.0 – 172.31.255.255 | 1 048 574 | Campus / division |
| C | 192.168.0.0 – 192.168.255.255 | 65 534 | Home/SOHO, lab |

Routers drop these addresses on the public Internet; translation is required for external reachability.

### Stateful NAT
* Maintains a **mapping table** (“state”) of inside-to-outside address/port pairs.  
* Only **responses** matching an existing entry are allowed back in → implicit one-way firewall.  
* Variants you must recognize for the exam:  

| Term | Meaning |
|------|---------|
| **PAT / NAPT / NPAT** | Port Address Translation—multiplex many private hosts over one public IP (uses unique source ports) |
| **SNAT** | Source NAT—generic umbrella for outbound translation |
| **DNAT / Static NAT / Port-forward** | Inbound pin-hole mapping of a public socket to an internal host |
| **NAT-T** | NAT Traversal; encapsulates IPSec in UDP/4500 to survive translation |

### Automatic Private IP Addressing
When DHCP fails, Windows autoconfigures **169.254.x.x/16** link-local addresses (RFC 3927).  
* Only single-segment connectivity 🔄; no Internet or routed access.  
* Diagnostic clue during exams: client with 169.254.* indicates DHCP outage or rogue attack on the service.

## Third-Party Connectivity
Any direct link between your network and an external entity introduces **shared risk**.

* **Governance Artifacts**  
  * **MOU/MOA** – documents intent and high-level responsibilities.  
  * **ISA** – technical & security controls for the interconnection (required for U.S. federal systems).  
* **Risk Management**  
  * Perform joint risk assessment and data-flow mapping.  
  * Principle of **least privilege**: expose only required services (extranet, API gateway, or segmented VLAN).  
  * Employ CASB, SD-WAN, or site-to-site VPN with strong crypto for cloud or partner links.  
* **Due Diligence**  
  * Verify third party’s patch cadence, incident response, and audit results.  
  * Include right-to-audit and termination clauses in contracts.

> CISSP tip: If confidentiality, integrity, or availability cannot be adequately assured via direct interconnect, use *indirect* methods (secure email, managed file transfer, or shared SaaS workspace).

## Switching Technologies
Switching defines how data moves across intermediary networks. Understand distinctions for both the exam and architecture decisions.

### Circuit Switching
* Establishes a **dedicated physical path** before data flows.  
* Predictable latency and bandwidth; ideal for constant-rate voice of yesteryear.  
* Inefficient for bursty traffic—resources idle when no data is sent.

### Packet Switching
* Breaks messages into packets, each routed independently.  
* Lines are shared ⇢ higher utilization, but variable delay and possible loss.  
* Dominant for modern data and VoIP.

#### Circuit vs Packet Switching (Exam Favourite)
| Characteristic | Circuit | Packet |
|----------------|---------|--------|
| Connection | Pre-allocated path | Dynamic hop-by-hop |
| Delay | Fixed | Variable (jitter) |
| Resource Use | Exclusive | Statistical multiplexing |
| Failure Impact | Call dropped | Packets reroute |
| Common Today | Niche (SCADA, T1) | Internet, MPLS, Ethernet |

### Virtual Circuits
Logical, software-defined “pipes” inside a packet-switched fabric.

| Type | Behavior | Analogy |
|------|----------|---------|
| **PVC** (Permanent) | Always available; pre-provisioned | Leased line over a packet core |
| **SVC** (Switched) | Set up on demand, torn down after idle | Phone call within packet network |

Technologies leveraging virtual circuits: Frame Relay, ATM, MPLS, many SD-WAN overlays.

## WAN Technologies
WANs extend connectivity across cities, countries, or the globe. Choose technology by distance, bandwidth, latency tolerance, and cost.

### Dedicated vs Nondedicated Links
| Attribute | Dedicated (Leased) | Nondedicated (On-Demand) |
|-----------|-------------------|--------------------------|
| Setup | Permanent point-to-point | Call/connection established per use |
| Availability | Always on | Dial/connect as needed |
| Example Services | T-carriers, E-carriers, Metro Ethernet, OC-x | Dial-up, DSL, LTE/5G, ISDN (legacy) |
| Security | Physically isolated, easier to secure | Must authenticate each session |
| Cost | High (flat monthly) | Pay-per-use or shared bandwidth |

#### Common WAN Offerings
| Technology | Medium | Typical Throughput | Notes for CISSP |
|------------|--------|--------------------|-----------------|
| **MPLS** | Fiber/copper | 10 Mbps – 10 Gbps | Label-switching core, supports QoS/CoS; often forms enterprise backbone |
| **Metro Ethernet** | Fiber | 10 Mbps – 100 Gbps | Carrier Ethernet MAN/WAN; VLAN and QinQ support |
| **SD-WAN** | Mixed (Internet, LTE, MPLS) | Policy-steered | Overlay tunnels with centralized orchestration; improves cost & resilience |
| **xDSL (ADSL/VDSL/SDSL)** | Copper pair | 1–300 Mbps | Distance-limited; still used for SMB/telework |
| **Cable DOCSIS** | Coax | 50 Mbps – 1 Gbps (shared) | Point-to-multipoint; encryption between modem ↔ CMTS |
| **Fiber PON (GPON, EPON)** | Fiber | 1–10 Gbps | Passive optical splitters reduce OPEX |
| **Satellite (GEO, LEO)** | Microwave | 25 Mbps+ (LEO latency < 50 ms) | VSAT dishes; essential for remote regions |
| **BPL** | Power line | < 30 Mbps | Niche; interference & regulation hurdles |

> **Resilience tip:** Procure dual providers on diverse physical routes to mitigate single-fault outages.

## Fiber-Optic Links
Optical transport delivers very high bandwidth and immunity to EMI, ideal for backbone and long-haul.

### SONET / SDH Hierarchy
| SONET OC-x | SDH STM-x | Payload Rate |
|------------|-----------|--------------|
| OC-1 | STM-0 | 51.84 Mbps |
| OC-3 | STM-1 | 155.52 Mbps |
| OC-12 | STM-4 | 622.08 Mbps |
| OC-48 | STM-16 | 2.49 Gbps |
| OC-192 | STM-64 | 9.95 Gbps |
| OC-768 | STM-256 | 39.81 Gbps |

* Uses synchronous TDM frames over single-mode fiber.  
* Supports ring and mesh topologies with automatic protection switching (≤ 50 ms fail-over).  
* SDH (ITU) and SONET (ANSI) interoperate via identical framing with different naming.

Security considerations: fiber is difficult to tap but not impossible—use physical protection and loss-of-light alarms; encrypt sensitive payloads at higher layers (MACsec, IPSec, TLS).

## Prevent or Mitigate Network Attacks
Communication channels face passive and active threats; layered controls are essential.

### Eavesdropping
**Goal:** covertly capture traffic.

| Vector | Typical Tools | Mitigations |
|--------|---------------|-------------|
| Copper tap, port span, Wi-Fi monitor | Protocol analyzers (Wireshark), RF sniffers | Strong link & end-to-end encryption (IPSec, TLS, SRTP) 🔐; switch port security; physical cable security |
| Fiber bending tap | Inline optical splitter, OTDR-stealth | Fiber conduit & alarmed enclosures; MACsec |
| Rogue access point | Evil twin, Karma attack | 802.1X/EAP-TLS, WPA3-Enterprise, WIPS |

User awareness + application whitelisting stop local sniffer install.

### Modification Attacks
Attacker intercepts, alters, then forwards traffic (on-path).

* **Threats:** packet injection, TCP hijack, bit-flipping, forged ARP/DNS replies.  
* **Controls:**  
  * Cryptographic integrity—HMAC, digital signatures, authenticated encryption (AES-GCM, ChaCha20-Poly1305).  
  * Sequence numbers & nonces to foil replay (TLS, IPSec ESP).  
  * ARP/DHCP snooping & dynamic ARP inspection on switches.  
  * DNSSEC to validate signed zone data.

## Summary
* **Protocol Security Mechanisms**
  * Harden the TCP/IP stack with authentication (PAP ➡️ EAP-TLS), port security (802.1X, sticky MAC), and QoS to preserve **availability**.  
* **Secure Voice Communications**
  * PSTN/PBX need physical protection; VoIP must add SRTP + TLS and guard against vishing & phreaking.  
* **Remote Access Security Management**
  * Combine strong MFA, encrypted tunnels (IPSec/SSL VPN), and clear policies for telework and admin access.  
* **Multimedia Collaboration**
  * Vet SaaS conferencing for end-to-end encryption, access controls, and logged recordings; secure IM with TLS, DLP, and retention rules.  
* **Monitoring & Management**
  * Achieve network observability via SNMPv3, NetFlow, and capacity/fault dashboards; shape traffic to uphold SLA.  
* **Load Balancing**
  * Distribute workloads with algorithms (round-robin, least-conn) using VIPs; design for ✨active-active (max throughput) vs. active-passive (steady availability).  
* **Email Security**
  * Baseline SMTP is plaintext—add STARTTLS or SMTPS for transport, SPF+DKIM+DMARC for authenticity, and S/MIME/PGP for end-to-end confidentiality 🔐.  
* **Virtual Private Networks**
  * Encrypt data over untrusted links; understand tunneling vs. transport modes, split vs. full tunnel, and major protocols (IPSec, L2TP/IPSec, OpenVPN, WireGuard).  
* **Switching & VLANs**
  * Segment traffic logically; defend against MAC flooding & cloning with port security and IDS; use VLAN tagging cautiously to avoid hopping exploits.  
* **NAT & Private Addressing**
  * PAT conserves IPv4 and masks internal topologies; recognize private (RFC 1918), APIPA (169.254/16), and loopback (127.0.0.1) ranges; NAT-T enables IPSec through translation.  
* **Third-Party Connectivity**
  * Formalize links with MOU → ISA, enforce least-privilege extranet or SD-WAN, and monitor shared-risk zones.  
* **Switching Technologies**
  * Circuit switching = dedicated path; packet switching = statistical multiplexing; virtual circuits (PVC/SVC) offer logical consistency over packet cores.  
* **WAN Technologies**
  * Options span MPLS, Metro-E, SD-WAN, satellite (VSAT/LEO), DSL, cable, fiber PON—select by bandwidth, latency, and cost.  
* **Fiber-Optic Backbones**
  * SONET/SDH deliver 50 Mbps–40 Gbps synchronous transport with fast fail-over; still encrypt sensitive payloads.  
* **Preventing Network Attacks**
  * Counter **eavesdropping** with strong encryption and physical security; block **modification/replay** via HMAC, sequence numbers, and signed protocols; monitor for DDoS, ARP/DNS poisoning, and spoofing.

> **Exam takeaway:** Apply the CIA triad to every communication layer—authentication + encryption (confidentiality), integrity checksums/signatures, and redundancy/QoS for availability—then document, monitor, and continuously improve.





