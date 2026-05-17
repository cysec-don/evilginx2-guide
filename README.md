# A Student's Guide to Evilginx2

**A comprehensive and approachable guide to understanding man-in-the-middle phishing attacks, session hijacking, and how to defend against them.**

> **Author:** Cysec Don | cysecdon@gmail.com
> **Year:** 2026
> **Edition:** Enhanced Edition v3.0

---

## About This Guide

This book provides a detailed, student-friendly exploration of Evilginx2 — an Adversary-in-the-Middle (AiTM) phishing framework designed to bypass two-factor authentication. The guide uses simple analogies, humorous examples, and hands-on labs to make complex cybersecurity concepts accessible.

**DISCLAIMER:** This guide is intended strictly for educational purposes. The techniques described herein should only be used in authorized penetration testing scenarios with explicit written consent from the target organization. Unauthorized use of these techniques is illegal.

## Contents (14 Chapters)

| # | Chapter | Description |
|---|---------|-------------|
| 1 | What in the World is Evilginx2? | Introduction to AiTM phishing |
| 2 | The Magic Behind the Curtain | How Evilginx2 works: reverse proxy & MITM |
| 3 | Setting Up Your Lab | Safe, legal lab environment setup |
| 4 | Phishlets - The Recipe for Trouble | YAML configs for targeting services |
| 5 | Running Your First Simulation | Launching phishing campaigns |
| 6 | The Cookie Monster | Session hijacking explained |
| 7 | Bypassing 2FA - The Plot Twist | How 2FA gets defeated by AiTM |
| 8 | Defense - How to Not Get Evilginx'd | Multi-layered defense strategies |
| 9 | The Attacker's Playbook | Common tricks and techniques |
| 10 | Advanced Attacker Tricks | Domain squatting, email spoofing, redirect chains |
| 11 | Real-Life Attack Simulation | Full walkthrough with pitfalls |
| 12 | Pitfalls and Countermeasures | What can go wrong and how to avoid it |
| 13 | Emerging Defenses | Token Binding, CAE, Passkeys, and the future |
| 14 | Simulated Practice Lab | 5 intelligent hands-on lab exercises |

## Repository Structure

```
evilginx2-guide/
├── students_guide_to_evilginx2.pdf   # The complete book (PDF)
├── generate_guide.py                  # Python script to generate the body PDF
├── cover.html                         # Cover page (HTML with HUD theme)
├── cover_bg.png                       # AI-generated cover background
├── cover/
│   └── cover.pdf                      # Cover page (PDF)
└── README.md                          # This file
```

## Key Topics Covered

- **Reverse Proxy & MITM Mechanics** — How Evilginx2 sits between victim and real server
- **Phishlet Configuration** — YAML-based targeting configs for specific services
- **Session Cookie Theft** — Why stealing a cookie is worse than stealing a password
- **2FA Bypass** — SMS, push, and TOTP all fall to real-time proxy attacks
- **FIDO2/WebAuthn Defense** — The one authentication method that resists AiTM
- **Attacker Tricks** — Domain squatting, typo-squatting, email spoofing, redirect chains
- **Real-Life Simulation** — Step-by-step attack walkthrough with pitfalls highlighted
- **Hands-On Labs** — 5 progressive lab exercises from setup to full simulation

## How to Regenerate the PDF

### Prerequisites
```bash
pip install reportlab PyPDF2 playwright
playwright install chromium
```

### Generate Body PDF
```bash
python3 generate_guide.py
```

### Generate Cover PDF
```bash
# Uses Playwright to convert HTML to PDF
python3 -c "
from playwright.sync_api import sync_playwright
with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto('file://$(pwd)/cover.html', wait_until='networkidle')
    page.wait_for_timeout(3000)
    page.pdf(path='cover/cover.pdf', width='794px', height='1123px', print_background=True,
             margin={'top': '0', 'right': '0', 'bottom': '0', 'left': '0'})
    browser.close()
"
```

### Merge Cover + Body
```python
from PyPDF2 import PdfMerger
m = PdfMerger()
m.append('cover/cover.pdf')
m.append('body_evilginx2_v3.pdf')
m.write('students_guide_to_evilginx2.pdf')
m.close()
```

## License

This guide is provided for educational purposes only. All rights reserved by the author.

## Contact

**Cysec Don** — cysecdon@gmail.com
