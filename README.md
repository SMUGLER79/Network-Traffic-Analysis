# Network-Traffic-Analysis

# Introduction

Several customers reported being unable to access the website `www.yummyrecipesforme.com`, receiving the error message "destination port unreachable." As a cybersecurity analyst, you were tasked with investigating the issue. Upon testing, you encountered the same error. Using the network analyzer tool, tcpdump, you discovered that DNS queries sent via UDP to the DNS server were met with ICMP "udp port 53 unreachable" errors, indicating a failure in DNS resolution. This report outlines the analysis of the problem and the affected network protocol.

# Scenario

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

![image](https://github.com/user-attachments/assets/4565e570-b511-4b8e-9f06-94a93e121baf)

# Workflow

1. Analyse the Network Protocol Analyzer Logs using tcpdump.
2. Provide a summary of the problem found in the tcpdump log.
3. Explain your analysis of the data and provide one solution to implement.

# Solution

To address the issue of UDP port 53 being unreachable, the first step is to check firewall rules to ensure that traffic on this port is not being blocked. Use tools like dig or nslookup to verify DNS functionality, and if the DNS server is unresponsive, restart the service to restore its operations. As a temporary measure, switch to public DNS servers like Google (8.8.8.8) or Cloudflare (1.1.1.1) to maintain access to services while troubleshooting. To investigate the root cause, analyze DNS and network logs for signs of attacks or misconfigurations, and use tcpdump to inspect DNS traffic on port 53. Additionally, audit firewall and system logs to identify any unauthorized changes. For long-term prevention, secure the DNS infrastructure by enabling DNSSEC and restricting recursive queries to trusted IPs. Monitor DNS traffic using tools like Suricata or Zeek to detect irregular activity, and restrict administrative access to DNS servers with multi-factor authentication (MFA). These steps will help restore functionality and safeguard against similar incidents in the future.

PFA the [`Cybersecurity incident report network traffic analysis.pdf`](https://github.com/SMUGLER79/Network-Traffic-Analysis/blob/main/Cybersecurity%20incident%20report%20network%20traffic%20analysis.pdf) for the complete network analysis.

# Conclusion

The investigation into the DNS access issue for www.yummyrecipesforme.com revealed that UDP port 53 is blocked, preventing the resolution of domain names and causing service disruptions. The most probable cause is a firewall or network security configuration blocking DNS traffic, possibly as a protective measure against DNS-based attacks. The network security team is actively investigating the root cause by analyzing the firewall settings and checking the DNS server for signs of malicious activity or downtime. Once the issue is identified, steps will be taken to restore DNS functionality and ensure continued access to critical services.
