**Suricata Deployment Mode**



* Suricata IPS enabled on pfSense 2.8.1
* Mode: Inline IPS Mode (netmap)
* Interfaces protected:

&nbsp;    LAN (em1)

&nbsp;    OPT1 / DMZ (em2)

* Blocking Mode: Enabled (Drops malicious packets)



**Rule Sources Enabled**



* Emerging Threats Open (ET Open)



&nbsp;Malware

&nbsp;Port scan

&nbsp;Web attack

&nbsp;DNS anomaly

&nbsp;ICMP anomaly

&nbsp;Protocol decode rules



* Additional built-in rulesets included by pfSense:



&nbsp;Snort GPLv2 Community

&nbsp;Abuse.ch URL blocklists (default)

&nbsp;Feodo Tracker (botnet C2 indicators)



**Ruleset Update Status**



* &nbsp;Rules last updated successfully (ET Open)
* &nbsp;MD5 verification completed (integrity OK)
* &nbsp;Update mechanism: pfSense Package Manager → Suricata → Updates tab



Interface Bindings



* LAN / em1

&nbsp;Inline mode active

&nbsp;All ET Open rules loaded

&nbsp;Stream-depth inspection enabled

* OPT1 / em2 (DMZ)

&nbsp;Inline mode active

&nbsp;IPS blocking enabled

&nbsp;HTTP and TCP anomaly rules active



**Engine Settings**

* Pattern matcher: Hyperscan (default on pfSense if supported)
* Stream inspection: enabled
* HTTP parser: libhtp active
* IP defragmentation: enabled
* TCP reassembly: enabled
* Checksum validation: enabled
* Drop logs: /var/log/suricata/eve.json



**IPS Actions Observed**

* Suricata generated DROP and ALERT events for:

&nbsp;TCP SYN flood traffic

&nbsp;ICMP echo flood

&nbsp;UDP flood attempts

&nbsp;Nmap scans

&nbsp;HTTP Directory brute-force (DIRB)

&nbsp;Slowloris / slow HTTP tests

&nbsp;HTTP GET requests with SQL injection payloads



**Sample Suricata Alert Types (as seen in logs)**

* ET SCAN Nmap Scripting Engine User-Agent Detected
* ET SCAN Behavioral Unusual Port 80 SYN Flood
* ET POLICY Outbound ICMP Large Packet Fragmentation
* ET WEB\_SERVER Possible Directory Traversal Attempt
* ET WEB\_CLIENT SQL Injection Attempt Detected
* ET DOS Slowloris Attack Detected
* ET INFO HTTP 301 Redirect Detected (pfSense GUI)
* ET PROTOCOL Generic Protocol Command Decode
* ET DOS ICMP Flood Detected



**Suricata Log Evidence (eve.json)**

* Suricata recorded:

1. DROP: SYN flood packets blocked
2. DROP: ICMP flood packets blocked
3. ALERT: HTTP-based enumeration
4. ALERT: Directory brute-force
5. ALERT: TCP anomalies (FIN/XMAS scans)
6. DROP: Traffic from DMZ → LAN (due to IPS + firewall)
