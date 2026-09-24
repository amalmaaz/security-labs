# Lab: Camphish — Webcam Phishing via Social Engineering

**Category:** Social Engineering / Phishing
**Tool source:** [link to original GitHub repo — do not re-upload the tool itself]
**Tested on:** My own device only
**Date:** 2026-09-24


## What It Does
Camphish generates a phishing link that, when opened, prompts the target's browser to request camera access — disguised as a legitimate-looking page. It's a demonstration of how social engineering combines with browser permission prompts to gain unauthorized access to a device's webcam.

## Objective
Understand how this class of attack works end-to-end so I can recognize, explain, and defend against it — not to deploy it against anyone.

## Setup (redacted)
1. Cloned the tool into an isolated test environment
2. Used a tunneling service (e.g. ngrok) to expose a local page — *[redact actual URLs/tokens]*
3. Opened the generated link on my own test device
4. Observed the permission prompt and resulting behavior

## Observations
- How the permission prompt was framed/presented
- What made the link/page look legitimate (or not)
- What data/access was actually captured in the test

## Defensive Takeaways
- Browsers sandbox camera/mic access per-origin — permission prompts are the last line of defense
- Red flags for end users: unexpected permission prompts, shortened/mismatched URLs, unsolicited links
- Recommended controls: browser permission auditing, awareness training, URL reputation checks, EDR alerting on new tunneling domains (e.g. `*.ngrok.io`)

## Screenshots
*(own device only, redact identifying info)*

## References
- [Original tool repo]
- [Relevant CEH module / MITRE ATT&CK technique if applicable]
