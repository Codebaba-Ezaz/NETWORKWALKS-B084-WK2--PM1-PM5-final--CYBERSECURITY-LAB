# Networkwalks Cybersecurity Lab — Week 2

**Batch:** B084  
**Coverage:** PM 1–PM 5  
**Platform:** Kali Linux  
**Focus:** Open-source intelligence (OSINT), DNS and web reconnaissance, information gathering, and host discovery.

## Overview

Week 2 focused on gathering publicly available information about domains and understanding how reconnaissance tools reveal a website's technical footprint. The activities also introduced visual relationship mapping, subdomain/email discovery, and basic host discovery with Zenmap.

> **Authorization:** The screenshots show work against `networkwalks.com`, `microsoft.com`, and the lab host `10.0.2.15`. Perform reconnaissance and scanning only on systems you own or have explicit permission to assess.

## Activities

### PM 1 — Domain and website reconnaissance

Tools and commands shown in the lab:

| Tool | Example | Purpose |
|---|---|---|
| WHOIS | `whois networkwalks.com` | Review domain registration and registrar information |
| WhatWeb | `whatweb networkwalks.com` | Identify visible web technologies and server details |
| nslookup | `nslookup networkwalks.com` | Query DNS and resolve the domain to an IP address |
| cURL | `curl -I https://networkwalks.com` | Inspect HTTP response headers |
| WAFW00F | `wafw00f networkwalks.com` | Check for indications of a web application firewall |
| DNSRecon | `dnsrecon -d networkwalks.com` | Gather DNS-related records and enumeration results |

**Observations from the screenshots:**
- WHOIS returned registrar, domain dates, and domain-status information.
- DNS lookup resolved `networkwalks.com` to `192.232.216.135`.
- WhatWeb identified visible technologies including Apache, Bootstrap, jQuery, and WordPress.
- The cURL request returned an HTTP `200 OK` response and displayed response headers.
- WAFW00F was run; the captured screen shows its banner but does not establish a confirmed WAF detection.
- DNSRecon displayed DNS enumeration output, including SOA, NS, and MX-related information.

### PM 3 — Reconnaissance relationship graph

A graph visualization was saved as `PM 3/New Graph (1).png`.

The image presents a central entity connected to multiple related nodes. It documents the use of a visual graph to explore and communicate relationships discovered during reconnaissance. The screenshot does not make every node label readable, so individual entities are not transcribed here.

### PM 4 — TheHarvester

**Target shown:** `microsoft.com`

TheHarvester was used to collect publicly discoverable information associated with the target domain.

**Observations from the screenshots:**
- The captured run reports one email address found.
- Multiple hostnames/subdomains are listed in the output.
- A second run shows API-key/source configuration messages and unsuccessful source requests; these are tool/source limitations, not proof that the target has no additional public information.

### PM 5 — Zenmap / Nmap host discovery

**Lab target shown:** `10.0.2.15`  
**Profile:** Ping scan  
**Command shown:** `nmap -sn 10.0.2.15`

**Result shown:** The target host was reported as up. The scan output reports one IP address and one host up, with a runtime of approximately 0.50 seconds.

The topology screenshot shows the lab machine (`localhost`) connected to `10.0.2.15`.

## Key Learning Outcomes

- Understand the purpose of WHOIS and DNS lookups in domain reconnaissance.
- Inspect HTTP response headers and identify visible web technologies.
- Recognize the role and limitations of WAF detection tools.
- Use DNSRecon and TheHarvester to collect publicly available domain information.
- Interpret a reconnaissance relationship graph.
- Perform a basic ping/host-discovery scan in an authorized lab using Zenmap/Nmap.

## Evidence

Screenshots are organized by activity:

- `PM 1/` — WHOIS, WhatWeb, nslookup, cURL, WAFW00F, and DNSRecon
- `PM 3/` — reconnaissance relationship graph
- `PM 4/` — TheHarvester output
- `PM 5/` — Zenmap ping scan and topology view

## Notes

Results reflect the captured lab session and can change over time as DNS records, hosting infrastructure, and website technologies change. Tool output should be validated and interpreted in context rather than treated as a complete security assessment.
