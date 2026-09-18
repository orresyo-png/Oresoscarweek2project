# 🔐 Penetration Testing Report | Footprinting & Network Scanning

<p align="center">

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Penetration%20Testing-red?style=for-the-badge)
![Week 02](https://img.shields.io/badge/Week-02-blue?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/Kali%20Linux-Reconnaissance-black?style=for-the-badge&logo=kalilinux)
![Zenmap](https://img.shields.io/badge/Zenmap-Nmap-green?style=for-the-badge)

</p>

---

## 📌 Project Information

| Field | Details |
|---|---|
| **Project** | Penetration Testing Report |
| **Focus** | Footprinting & Network Scanning Phases |
| **Program** | Cybersecurity Program at Networkwalks |
| **Week** | 02 |
| **Pentester** | ORES MWIJAGE OSCAR |
| **Program / Batch** | B083-Networkwalks |
| **Date** | 17 August 2026 |
| **Modules Completed** | W2-PM1 — Multiple Kali Tools, W2-PM4 theHarvester; W2-PM5 — Zenmap Scanning |
| **Client / Target** | Networkwalks — secured written permission |
| **Additional Target** | My own local LAN Network |
| **Permission Secured** | Yes |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery |
| **Phase 3–5** | In Progress |

---

# ⚠️ 1. Liability Disclaimer

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself.

All these materials are for education and research purpose only. Do not use anything from here to break the law.

The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility.

Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

---

# 📖 2. Introduction

This report covers footprinting the `networkwalks.com` domain using multiple Kali Linux tools (**W2-PM1**) and scanning my own local network with Zenmap (**W2-PM5**).

One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network.

It is the Week 2 part of my ongoing internship program at Networkwalks.

All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning).

Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

---

# 🛠️ 3. Tools Used

| Tool | Purpose |
|---|---|
| **Kali Linux & Windows** | Operating systems used for reconnaissance activities |
| **WHOIS** | Find domain registration details (owner, dates, name servers). |
| **WhatWeb** | Fingerprint web technologies (server, CMS, plugins, IP). |
| **Nslookup** | Resolve the domain name to its IP address using DNS. |
| **Curl -I** | Read the HTTP response headers of the website. |
| **Wafw00f** | Detect whether a Web Application Firewall protects the site. |
| **DNSRecon** | Enumerate DNS records (NS, MX, SPF, TXT, SRV). |
| **Zenmap (Nmap GUI)** | Scan the local subnet to find live hosts, IPs and MAC addresses. |
| **Windows CMD** | Local IP and MAC address identification. |

---

# 🔎 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed reconnaissance against the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon**.

Each tool was used to collect a different type of information about the target.

### WHOIS

First, I used WHOIS to obtain publicly available domain registration information and identify the domain's name servers. The results provided information about the domain registration and hosting infrastructure.

```bash
whois networkwalks.com
```
## WHOIS evidence
![](PM1.JPG)

### WhatWeb

I then used WhatWeb to identify technologies used by the website. The results identified **WordPress 7.1** and **WP Download Manager 3.3.58**, along with other information exposed by the website.

```bash
whatweb networkwalks.com
```

![WhatWeb evidence](PM12.JPG)

### Nslookup

Using Nslookup, I resolved the domain name to its IP address. The provided result identified:

```text
192.232.216.135
```

```bash
nslookup networkwalks.com
```

![Nslookup evidence](PM13.JPG)

### Curl

I used Curl with the `-I` option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint `/wp-json/`.

```bash
curl -I https://networkwalks.com
```

![Curl evidence](PM14.JPG)

### Wafw00f

Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified **ModSecurity (SpiderLabs)**.

```bash
wafw00f networkwalks.com
```

![Wafw00f evidence](PM15.JPG)

### DNSRecon

Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.

```bash
dnsrecon -d networkwalks.com
```

![DNSRecon evidence](PM16.JPG)

---
## 4.2 Footprinting & Reconnaissance with theHarvester
I performed an additional footprinting and reconnaissance activity using theHarvester against the assigned microsoft.com domain. The purpose of this activity was to collect publicly available information from external sources, particularly email addresses, subdomains and hosts associated with the target domain.

The first search used Baidu as the selected source with a result limit of 1000. 
![](PM42.JPG)
 

The second search used all sources available to the installed version of theHarvester with a result limit of 50. 
 
 ![](33333333333.JPG)

This activity demonstrated the value of passive information gathering because publicly available information can reveal parts of an organization's external footprint without attempting to exploit the target. The results may vary depending on the available public sources, their current content, and any source-specific configuration or API requirements.


## 4.3 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network.

The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.


After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical.

> **Note:** The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.

### Windows IP Configuration

```cmd
ipconfig
```

### Zenmap Ping Scan

![Zenmap scan evidence](PM53.JPG)

### Zenmap Network Topology

![Zenmap topology evidence](PM52.JPG)

---

# ⚠️ 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---:|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager | Attackers may use exposed technology/version information to identify software requiring further security review | **Medium** |
| 2 | Server IP address identifiable | Nslookup resolved the domain to `192.232.216.135` | Provides information about the network location of the web service | **Low** |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration | **Low** |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application's security architecture | **Low** |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service-related records | DNS information can help build a broader infrastructure profile | **Medium** |
| 6 | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network | Unknown or unauthorized devices may potentially be present on a network | **Medium** |

### Risk Level Key

- 🔴 Critical
- 🟠 Medium
- 🟢 Low

> The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

---

# 🛡️ 6. Recommendations

### 1. Review publicly exposed technology information

Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.

### 2. Keep software updated

CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.

### 3. Review HTTP headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Review DNS records regularly

DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

### 5. Properly configure and monitor the WAF

Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.

### 6. Perform regular internal network discovery

Organizations should periodically scan their own networks to identify active devices.

### 7. Investigate unknown devices

Any unexpected device discovered during network scanning should be investigated and verified.

### 8. Maintain network documentation

Network topology and device information should be documented and updated regularly.

### 9. Perform security testing with authorization

Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

---

# 🎯 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering **footprinting, reconnaissance and network scanning**.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.

In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

---

# 📸 8. Evidences Collected


![](22222222222222222.JPG)

![](PM1.JPG)

![](PM12.JPG)

![](PM13.JPG)

![](PM14.JPG)

![](PM15.JPG)

![](PM16.JPG)

![](PM41.JPG)

![](PM42.JPG)

![](PM43.JPG)

![](PM51.JPG)

![](PM52.JPG)

![](PM53.JPG)

![](33333333333.JPG)

# 👤 Author

**ORES MWIJAGE OSCAR**

Cybersecurity Professional — B083

**Program:** Cybersecurity Program at Networkwalks  
**Week:** 02  
**Repository:** GitHub

---

<p align="center">

**🔐 Cybersecurity • Ethical Hacking • Network Security**

</p>
