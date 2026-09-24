# Lab: Nmap — Network Reconnaissance & Port Scanning

**Category:** Reconnaissance
**Tool:** Nmap (Network Mapper)
**Tested on:** My own device / lab network only

## What It Does
Nmap is used to discover hosts on a network, identify open ports, detect running services and their versions, and fingerprint operating systems. It's one of the foundational tools for the reconnaissance phase of a penetration test.

## Objective
Get hands-on with core scan types to understand what information is exposed by a target, and how that maps to real-world attack surface assessment.

## Scans Practiced
<!-- fill in which ones you ran -->
- [ ] Ping scan (host discovery) — `nmap -sn <target>`
- [ ] Basic TCP scan — `nmap <target>`
- [ ] Service/version detection — `nmap -sV <target>`
- [ ] OS detection — `nmap -O <target>`
- [ ] Full port range — `nmap -p- <target>`
- [ ] Stealth/SYN scan — `nmap -sS <target>`

## Setup
1. Ran scans against my own device / local lab network (redact real IPs)
2. Compared results from different scan types (e.g. what -sV reveals vs a basic scan)

## Observations
- Which ports were open and what services were running
- What version/banner info was exposed
- How scan speed/stealth changed with different flags

## Defensive Takeaways
- Open ports should be minimized to only what's needed (attack surface reduction)
- Service banners can leak version info — useful for attackers fingerprinting known CVEs
- Firewalls/IDS can detect and log scan patterns (e.g. SYN scans); this is why network monitoring matters
- Regular internal scanning (as a defender) helps catch unintentionally exposed services

## References
- [Nmap official docs](https://nmap.org/book/man.html)
- Relevant CEH module: Reconnaissance / Scanning Networks
