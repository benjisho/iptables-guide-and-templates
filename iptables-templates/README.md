# IPTABLES Templates

![IPTABLES Logo](https://example.com/iptables-logo.png)

Welcome to the IPTABLES Templates repository. Here you'll find a collection of iptables rules templates designed to address various security challenges and objectives. These templates are organized by categories, making it easy to enhance the security of your server.

## Table of Contents

- [Overview](#overview)
- [Templates](#templates)
- [How to Use](#how-to-use)
- [Disclaimer](#disclaimer)

## Overview

Securing your server is crucial in today's digital landscape. This repository provides a set of carefully crafted iptables templates to help protect your server from various threats, such as botnet attacks, brute force attempts, and more. Each template is designed to address a specific security concern.

## Templates

Explore our collection of iptables templates:

- [**block-malicious-user-agents.rules.v4**](iptables-guide-and-templates/iptables-templates/block-malicious-user-agents.rules.v4): Block incoming requests with suspicious or malicious user-agent strings. This template is designed to filter out bots, crawlers, scanners, and other potentially harmful traffic.
- [**botnet-detection.rules.v4**](iptables-guide-and-templates/iptables-templates/botnet-detection.rules.v4): Detect and log potential botnet activity on your server. This template helps identify command and control communication and distributed attacks originating from botnets.
- [**brute-force-ssh.rules.v4**](iptables-guide-and-templates/iptables-templates/brute-force-ssh.rules.v4): Prevent brute force attacks on your SSH service by limiting the number of login attempts per minute from the same IP address.
- [**csrf-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/csrf-protection.rules.v4): Protect your web applications from cross-site request forgery (CSRF) attacks. This template verifies the referer header and drops requests that do not match your domain name.
- [**directory-traversal-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/directory-traversal-protection.rules.v4): Guard your web applications against directory traversal attacks by dropping requests that contain malicious characters or patterns in the URL path.
- [**dns-amplification.rules.v4**](iptables-guide-and-templates/iptables-templates/dns-amplification.rules.v4): Shield your DNS server from being used for DNS amplification attacks. This template limits the rate of DNS queries per source IP address and drops requests that have a large response size.
- [**file-inclusion-attacks.rules.v4**](iptables-guide-and-templates/iptables-templates/file-inclusion-attacks.rules.v4): Defend against file inclusion attacks on your web applications by dropping requests that contain malicious characters or patterns in the URL query string.
- [**hpkp.rules.v4**](iptables-guide-and-templates/iptables-templates/hpkp.rules.v4): Implement HTTP Public Key Pinning (HPKP) for enhanced web server security. This template adds a custom header that specifies the hashes of your SSL/TLS certificates.
- [**ip-reputation-lists.rules.v4**](iptables-guide-and-templates/iptables-templates/ip-reputation-lists.rules.v4): Block incoming traffic from known malicious IP addresses using IP reputation lists, which are databases of IP addresses that have been reported as sources of spam, malware, phishing, or other malicious activities.
- [**malware-download-prevention.rules.v4**](iptables-guide-and-templates/iptables-templates/malware-download-prevention.rules.v4): Prevent malware download attempts on your server by blocking requests that contain known malware signatures, suspicious file extensions, obfuscated or encoded payloads, abnormal HTTP response codes, and more.
- [**network-anomaly-detection.rules.v4**](iptables-guide-and-templates/iptables-templates/network-anomaly-detection.rules.v4): Detect and log network anomalies on your server, including port scanning, SYN flooding, ICMP flooding, and other unusual activity.
- [**port-scanning.rules.v4**](iptables-guide-and-templates/iptables-templates/port-scanning.rules.v4): Deter port scanning attempts on your server by limiting the rate of TCP connections per source IP address and dropping packets that have suspicious TCP flags or options.
- [**rate-limiting.rules(Prevent DDoS).v4**](iptables-guide-and-templates/iptables-templates/rate-limiting.rules(Prevent%20DDoS).v4): Prevent Distributed Denial of Service (DDoS) attacks by limiting the rate of incoming packets per source IP address or protocol and dropping packets that exceed the threshold.
- [**security-headers.rules.v4**](iptables-guide-and-templates/iptables-templates/security-headers.rules.v4): Add security headers to your web server responses, such as Content-Security-Policy, X-XSS-Protection, X-Frame-Options, and more, to enhance web application security.
- [**shellshock-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/shellshock-protection.rules.v4): Protect your web server from Shellshock attacks by dropping requests that contain malicious characters or patterns in the HTTP headers.
- [**sql-injection.rules.v4**](iptables-guide-and-templates/iptables-templates/sql-injection.rules.v4): Guard your web applications against SQL injection attacks by dropping requests that contain malicious characters or patterns in the URL query string or POST data.
- [**syn-flood.rules.v4**](iptables-guide-and-templates/iptables-templates/syn-flood.rules.v4): Prevent SYN flood attacks on your server by limiting the number of SYN packets per source IP address and dropping packets that have incomplete TCP handshakes.
- [**waf.rules.v4**](iptables-guide-and-templates/iptables-templates/waf.rules.v4): Integrate the ModSecurity WAF/IPS system, a popular open source web application firewall and intrusion prevention system, to protect your web applications from various attacks, such as SQL injection, XSS, CSRF, and more.
- [**xss-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/xss-protection.rules.v4): Protect your web applications from cross-site scripting (XSS) attacks by dropping requests that contain malicious characters or patterns in the URL query string or POST data.
- [**xxe-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/xxe-protection.rules.v4): Prevent XML external entity (XXE) attacks on your web applications by dropping requests that contain malicious characters or patterns in the XML data.
- [**zero-day-exploit-protection.rules.v4**](iptables-guide-and-templates/iptables-templates/zero-day-exploit-protection.rules.v4): Safeguard your server from zero-day exploit attacks by blocking requests that contain known exploit signatures, suspicious user-agent strings, anomalous HTTP request methods, malformed HTTP headers, and more.

You can find these templates in the `iptables-templates` directory of this repository. Each template comes with a brief description and explanations of the rules.

## How to Use

To use these templates, follow these steps:

1. Make sure you have iptables installed and configured on your server. Refer to the installation and configuration guide if needed.

2. Ensure you have root privileges or sudo access to run iptables commands.

3. To apply a template, use the `iptables-restore` command. For example, to apply the `block-malicious-user-agents.rules.v4` template, run:
   ```bash
   sudo iptables-restore < templates/block-malicious-user-agents.rules.v4
   ```

4. To append a template's rules to your existing configuration, use the -n option:
   ```bash
    sudo iptables-restore -n < templates/block-malicious-user-agents.rules.v4
    ```

5. To insert a template's rules at a specific position in your existing chains, use the -I option with a line number:
   ```bash
   sudo iptables-restore -I 5 < templates/block-malicious-user-agents.rules.v4
   ```

6. To remove a template, use the iptables-flush command. For example, to remove the block-malicious-user-agents.rules.v4 template, run:
   ```bash
   sudo iptables-flush INPUT
   ```

7. To save a template, use the iptables-save command. For example, to save the block-malicious-user-agents.rules.v4 template, run:
   ```bash
   sudo iptables-save > templates/block-malicious-user-agents.rules.v4
   ```
Please note that these templates are for educational and reference purposes. Test and customize them before using them on production servers.

## Disclaimer

These templates are provided for educational and reference purposes only. Use them at your own risk. The author of this repository is not responsible for any damage or loss caused by using these templates.

For questions or feedback, [contact me](https://linktr.ee/benjisho).

---
&copy; 2023 benjisho. All rights reserved.
