# Comparing Passive vs Active Reconnaissance

| Passive Reconnaissance  | Active Reconnaissance |
|---|---|
| **Tool / Example command**: `whois example.com` | **Tool / Example commands**: `nmap -sS -Pn target` · `ping -c 4 target` |
| **What it does**: Queries public registries for domain/IP owner, registrar, name servers, creation/expiry dates, contact info. | **What it does**: Probes the target directly to discover live hosts, open ports, services, and measures latency (ping). |
| **Why use it (purpose)**: Gather background and ownership info without touching the target — useful for scoping and social-engineering leads. | **Why use it (purpose)**: Map the target’s live attack surface and get concrete technical details needed for testing or triage. |
| **Typical output**: Registrant data, DNS servers, IP blocks, timestamps — human-readable metadata. | **Typical output**: List of up hosts, open ports, service banners, RTT values, and possible OS/service fingerprints. |
| **Risk level**: **Low** — uses public sources and does not contact the target’s hosts. | **Risk level**: **High** — direct network traffic to the target can trigger alarms or be logged as hostile. |
| **Detection possibility**: **Minimal** — registries may log lookups but target network won’t see WHOIS queries. | **Detection possibility**: **High** — scanning/pinging creates observable traffic that IDS/IPS, firewalls, or SIEM will notice. |
| **Why the risk is low**: No packets are sent to the target’s systems — you remain stealthy and legally safer. | **Why the risk is high**: Probes (SYNs, ICMP, service requests) are noisy and easily detected; repeated scans look like attacks. |
| **When to use**: Early recon, scoping, and when stealth/legal safety matters. | **When to use**: When you need verified, technical information about live services — only with authorization. |
| **Precautions**: Respect WHOIS rate limits and privacy rules; corroborate data from multiple sources. | **Precautions**: Obtain written permission; use low-and-slow scan options, avoid aggressive flags on production systems. |



Passive reconnaissance is best used during the early stages of an assessment when you want to gather information about a target without being detected and
it relies on open sources and indirect data. Active reconnaissance, on the other hand, involves directly probing a system or network to discover live hosts and
vulnerabilities, which provides deeper insights but carries a higher risk of detection.
