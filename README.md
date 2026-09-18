PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS

Pentester Name
(Cybersecurity Professional)	ORES MWIJAGE OSCAR
Program/Batch	B083-Networkwalks
Date	17 August 2026
Modules completed	W2-PM1 (Multiple Kali Tools)
W2-PM5 (Zenmap Scanning)
Client/Target	1. Networkwalks (secured written permission already)
2. My own local LAN Network
Permission secured from client?	Yes
Phases covered	Phase 1: Footprinting & Reconnaissance Attacks with Multipe  Kali Tools
Phase 2: Footprinting & Reconnaissance with theHarvester
Phase 3: Network Scanning with Zenmap




1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.
 
2. Introduction
This report presents the Week 2 practical activities completed under the Cybersecurity & Ethical Hacking program. It combines three project modules: W2-PM1 (Footprinting & Reconnaissance with Multiple Kali Tools), W2-PM4 (Footprinting & Reconnaissance with theHarvester), and W2-PM5 (Network Scanning with Zenmap).
PM1 focuses on collecting publicly observable information about a web domain using WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon. PM4 focuses on passive reconnaissance using theHarvester to identify publicly available email addresses, subdomains, and related hosts from selected public sources. PM5 moves from public-domain reconnaissance to authorized local network discovery using Zenmap.
Together, the three modules demonstrate a basic security-assessment workflow: first understand what information is exposed, then identify technologies and infrastructure, and finally discover active devices within an authorized network.


3. Tools Used
The table below lists each tool used in this report and its purpose.
Tool	Purpose
Kali Linux & Windows	Operating systems used for reconnaissance activities
WHOIS	Find domain registration details (owner, dates, name servers).
whatweb	Fingerprint web technologies (server, CMS, plugins, IP).
nslookup	Resolve the domain name to its IP address using DNS.
curl -I	Read the HTTP response headers of the website.
wafw00f	Detect whether a Web Application Firewall protects the site.
dnsrecon	Enumerate all DNS records (NS, MX, SPF, TXT, SRV).
Zenmap (Nmap GUI)	Scan the local subnet to find live hosts, IPs and MAC addresses.
theHarvester	Collect publicly available emails, subdomains, hosts, and related information from supported sources.
Windows CMD	Local IP and MAC address identification

4. Activities Performed
4.1 Footprinting & Reconnaissance with Multiple Kali Tools
I performed the footprinting and reconnaissance activity against the assigned networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different category of publicly observable information about the domain and its web infrastructure.

First, I used WHOIS to obtain publicly available domain-registration information and identify the domain's name servers. 
 

I then used WhatWeb to fingerprint the website and identify technologies exposed by the web application, including the CMS, plugins and other technology indicators.

 

Using Nslookup, I resolved the domain name to the IP address returned by DNS. 

 

I also used Curl  -I option to inspect the HTTP response headers and identify technical information returned by the web server.

 
I used Wafw00f to check for indicators of a Web Application Firewall

 

DNSRecon to enumerate publicly available DNS information such as name servers, mail-related records and other DNS records.

 




4.2 Footprinting & Reconnaissance with theHarvester
I performed an additional footprinting and reconnaissance activity using theHarvester against the assigned microsoft.com domain. The purpose of this activity was to collect publicly available information from external sources, particularly email addresses, subdomains and hosts associated with the target domain.

The first search used Baidu as the selected source with a result limit of 1000. 

 






















The second search used all sources available to the installed version of theHarvester with a result limit of 50. 
 
 

This activity demonstrated the value of passive information gathering because publicly available information can reveal parts of an organization's external footprint without attempting to exploit the target. The results may vary depending on the available public sources, their current content, and any source-specific configuration or API requirements.


4.3 Network Scanning with Zenmap
I performed network discovery on my own authorized local network using Zenmap, the graphical interface for Nmap. The purpose was to identify the local network configuration, discover active hosts, record available IP and MAC address information, and visualize the network topology.
I first used the Windows ipconfig command to identify the computer's IPv4 address, subnet mask and local network information. 
 

I then used the resulting subnet in Zenmap and selected the Ping Scan profile to identify hosts that were responding on the authorized local network.

 

The discovered live hosts were recorded together with their IP addresses and, where available, their MAC addresses. 
 
After the scan, I opened Zenmap's Topology section, enabled the legend and generated the required topology output. The topology provides a visual representation of the hosts discovered during the network scan.
 








5. Risk Analysis / Impact
The observations below represent potential security implications of the information gathered during the practical activities. They are not confirmed vulnerabilities; confirmation would require additional authorized testing.

#	Risk / Finding	Evidence / Observation	Potential Impact	Risk Level
1	Web technology information exposed	WhatWeb identified WordPress and WP Download Manager	Attackers may use exposed technology/version information to identify software requiring further security review	● Medium
2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135	Provides information about the network location of the web service	● Low
3	HTTP technical information exposed	Curl returned HTTP response headers and exposed /wp-json/	May assist technology fingerprinting and further enumeration	● Low
4	WAF technology identifiable	Wafw00f identified ModSecurity (SpiderLabs)	Reveals information about the web application’s security architecture	● Low
5	DNS infrastructure information exposed	DNSRecon identified DNS, mail and service-related records	DNS information can help build a broader infrastructure profile	● Medium
6	Multiple live hosts visible on local network	Zenmap identified four live hosts in the example network	Unknown or unauthorized devices may potentially be present on a network	● Medium


10. Recommendations
	Review publicly exposed information about web technologies, domains and DNS infrastructure.
	Keep CMS platforms, plugins, frameworks and other software regularly updated.
	Review HTTP response headers and minimize unnecessary technical disclosure.
	Review DNS records periodically and remove obsolete or unnecessary records.
	Maintain and monitor the approved Web Application Firewall configuration where applicable.
	Review publicly discoverable email addresses and subdomains as part of information-exposure management.
	Perform periodic authorized internal network discovery to maintain visibility of connected devices.
	Investigate and document unexpected devices discovered during internal scans.
	Maintain current network topology and asset documentation.

11. Conclusion
During Week 2 of the Cybersecurity & Ethical Hacking program, I completed practical activities covering footprinting, reconnaissance and network scanning. W2-PM1 gave me practical experience using multiple Kali Linux tools to collect different categories of publicly observable information about a web domain.
W2-PM4 extended the reconnaissance process through theHarvester, showing how information from public sources can be collected and organized to understand an organization's external footprint. W2-PM5 then introduced network discovery with Zenmap, allowing me to identify active hosts on an authorized local network and generate a visual network topology.
The three activities showed that careful information gathering can provide significant insight into a digital environment before any exploitation is considered. They also reinforced the importance of documenting actual results, interpreting findings carefully, and performing reconnaissance and scanning only within an authorized scope.
12. Evidence Collected

      
  
 
   




-End-


👤 Author
ORES MWIJAGE OSCAR
Cybersecurity professional
LinkedIn: https://www.linkedin.com/in/waqaskarim/
________________________________________
📌 Project Information
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub


