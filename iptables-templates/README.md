# Templates

The templates are collections of iptables rules that address specific security challenges or objectives. The templates are organized by categories, such as:

In here you can find ther following:

- block-malicious-user-agents.rules.v4: This template blocks incoming requests that have suspicious or malicious user-agent strings, such as bots, crawlers, scanners, etc.
- botnet-detection.rules.v4: This template detects and logs potential botnet activity on your server, such as command and control communication, distributed attacks, etc.
- brute-force-ssh.rules.v4: This template prevents brute force attacks on your SSH service by limiting the number of login attempts per minute from the same IP address.
- csrf-protection.rules.v4: This template protects your web applications from cross-site request forgery (CSRF) attacks by checking the referer header and dropping requests that do not match your domain name.
- directory-traversal-protection.rules.v4: This template protects your web applications from directory traversal attacks by dropping requests that contain malicious characters or patterns in the URL path.
- dns-amplification.rules.v4: This template protects your DNS server from being used for DNS amplification attacks by limiting the rate of DNS queries per source IP address and dropping requests that have a large response size.
- file-inclusion-attacks.rules.v4: This template protects your web applications from file inclusion attacks by dropping requests that contain malicious characters or patterns in the URL query string.
- hpkp.rules.v4: This template implements HTTP Public Key Pinning (HPKP) for your web server by adding a custom header that specifies the hashes of your SSL/TLS certificates.
- ip-reputation-lists.rules.v4: This template blocks incoming traffic from known malicious IP addresses using IP reputation lists, which are databases of IP addresses that have been reported as sources of spam, malware, phishing, or other malicious activities.
- malware-download-prevention.rules.v4: This template prevents malware download attempts by blocking requests that contain known malware signatures, suspicious file extensions, obfuscated or encoded payloads, abnormal HTTP response codes, etc.
- network-anomaly-detection.rules.v4: This template detects and logs network anomalies on your server, such as port scanning, SYN flooding, ICMP flooding, etc.
- port-scanning.rules.v4: This template prevents port scanning attempts by limiting the rate of TCP connections per source IP address and dropping packets that have suspicious TCP flags or options.
- rate-limiting.rules(Prevent DDoS).v4: This template prevents DDoS attacks by limiting the rate of incoming packets per source IP address or protocol and dropping packets that exceed the threshold.
- security-headers.rules.v4: This template adds security headers to your web server responses, such as Content-Security-Policy, X-XSS-Protection, X-Frame-Options, etc.
- shellshock-protection.rules.v4: This template protects your web server from Shellshock attacks by dropping requests that contain malicious characters or patterns in the HTTP headers.
- sql-injection.rules.v4: This template protects your web applications from SQL injection attacks by dropping requests that contain malicious characters or patterns in the URL query string or POST data.
- syn-flood.rules.v4: This template prevents SYN flood attacks by limiting the number of SYN packets per source IP address and dropping packets that have incomplete TCP handshakes.
- waf.rules.v4: This template integrates with ModSecurity WAF/IPS system, which is a popular open source web application firewall and intrusion prevention system that can protect web applications from various attacks, such as SQL injection, XSS, CSRF, etc.
- xss-protection.rules.v4: This template protects your web applications from cross-site scripting (XSS) attacks by dropping requests that contain malicious characters or patterns in the URL query string or POST data.
- xxe-protection.rules.v4: This template protects your web applications from XML external entity (XXE) attacks by dropping requests that contain malicious characters or patterns in the XML data.
- zero-day-exploit-protection.rules.v4: This template protects your server from zero-day exploit attacks by blocking requests that contain known exploit signatures, suspicious user-agent strings, anomalous HTTP request methods, malformed HTTP headers, etc.

The templates are available in the `iptables-templates` directory of this repository. Each template has a `.v4` extension, which indicates that it is compatible with iptables version 4. Each template also has a brief description and explanation of the rules.

## How to use the templates

To use the templates, you need to have iptables installed and configured on your server.
You can follow the guide for installation and configuration instructions.
You also need to have root privileges or sudo access to run iptables commands.

To apply a template, you can use the `iptables-restore` command to load the rules from a file.
For example, to apply the `block-malicious-user-agents.rules.v4` template, you can run:
```bash
sudo iptables-restore < templates/block-malicious-user-agents.rules.v4
```
This will overwrite your existing iptables rules with the ones from the template.

If you want to append the rules from the template to your existing rules, you can use the `-n` option:
```bash
sudo iptables-restore -n < templates/block-malicious-user-agents.rules.v4
```
This will add the rules from the template to the end of your existing chains.

If you want to insert the rules from the template to a specific position in your existing chains, you can use the `-I` option with a line number:
```bash
sudo iptables-restore -I 5 < templates/block-malicious-user-agents.rules.v4
```
This will insert the rules from the template after the fifth line of your existing chains.

To remove a template, you can use the `iptables-flush` command to delete all the rules from a chain or table.
For example, to remove the `block-malicious-user-agents.rules.v4` template, you can run:
```bash
sudo iptables-flush INPUT
```
This will delete all the rules from the INPUT chain.

If you want to delete all the rules from all the chains and tables, you can run:
```bash
sudo iptables-flush
```
This will reset your iptables configuration to the default state.

To save a template, you can use the `iptables-save` command to dump the rules to a file.
For example, to save the `block-malicious-user-agents.rules.v4` template, you can run:
```bash
sudo iptables-save > templates/block-malicious-user-agents.rules.v4
```
This will overwrite the file with the current iptables rules.

If you want to append the rules to an existing file, you can use the `>>` operator:
```bash
sudo iptables-save >> templates/block-malicious-user-agents.rules.v4
```
This will add the current iptables rules to the end of the file.

## Disclaimer

The templates provided in this repository are for educational and reference purposes only. They are not intended to be used as-is on production servers without proper testing and customization. The author is not responsible for any damage or loss caused by using these templates. Use them at your own risk.
