# Security Labs

Hands-on notes from ethical hacking and cybersecurity labs I practice on my own devices and lab environments (Kali Linux, DVWA), as part of my CEH and CCT certification prep.

> ⚠️ **Educational and defensive research only.** All techniques documented here were tested exclusively on my own devices and VMs in isolated environments. Nothing here is intended to target third parties. Sensitive values (tokens, IPs, real URLs) are redacted.

## About Me

Electronic engineer transitioning into cybersecurity and AI governance, currently doing a Diploma in Ethical Hacking and preparing for CEH and CCT. Certifications: Fortinet Getting Started in Cybersecurity 3.0, Fortinet Technical Introduction to Cybersecurity 3.0, and Securiti AI Security and Governance. Hands-on with Nmap, Metasploit, Wireshark, and Burp Suite. Targeting entry-level SOC / Cybersecurity Analyst roles.

## Labs Index

| Lab | Category | Status |
| --- | --- | --- |
| [Nmap scanning](Nmap) | Reconnaissance | ✅ Documented |
| [SQL injection on DVWA](dvwa/sql-injection) | Web Application Security | ✅ Documented |
| [Camphish](camphish/notes.md) | Social Engineering / Phishing Awareness | ✅ Documented |

## Detection and Defense

Each lab is paired with the defensive angle, the way a SOC analyst would see it:

| Lab | How it can be detected or prevented |
| --- | --- |
| Nmap scanning | Repeated connection attempts across many ports show up in firewall and IDS logs; limit exposed services and alert on scan patterns |
| SQL injection | Use parameterized queries, input validation, and least-privilege database accounts; a WAF and web server logs can flag injection patterns |
| Camphish | User awareness, checking links before opening them, browser camera permission prompts, and email/URL filtering |

## Structure

Each lab folder contains:

- `notes.md`: what the tool or technique does, setup steps, and what I learned
- `screenshots/`: evidence from my own test environment (optional)

## Why I Keep This

This repo is my running lab journal. It pairs offensive technique with the defensive and detection angle, which is how I want to think about security in practice, and it doubles as a portfolio for security analyst and governance roles.

---

## License / Disclaimer

Notes and write-ups are my own. Original tools referenced are linked to their respective repos and authors, not re-hosted here.
