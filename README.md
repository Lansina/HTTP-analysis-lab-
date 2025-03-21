
# HTTP-analysis-lab

Analyzing HTTP Logs with Splunk:
In the modern cybersecurity landscape, security analysts must sift through massive amounts of logs to detect anomalies, investigate threats, and respond to incidents. During my recent lab, I used Splunk to analyze sample HTTP logs, extract meaningful insights, and build dashboards for efficient log navigation. This exercise replicated the kind of work done in a Security Operations Center (SOC) and demonstrated how important log analysis is in security.

# Understanding HTTP and Its Security Implications

 What is HTTP?
 
HTTP (Hypertext Transfer Protocol) is the foundation of web communication, allowing clients (like browsers) to request resources from servers. It operates over port 80 by default and is stateless, meaning each request is independent of the last. While modern web applications use HTTPS (HTTP Secure, using TLS encryption), many systems still rely on HTTP, leaving them vulnerable to attacks.

# Common HTTP-Based Attacks.

 Attackers frequently exploit weaknesses in HTTP to conduct malicious activities such as:

Brute Force Attacks – Automated login attempts to gain unauthorized access.
Directory Traversal – Accessing restricted files on a server.
SQL Injection (SQLi) – Injecting malicious SQL queries via web forms.
Cross-Site Scripting (XSS) – Injecting malicious scripts into web pages.
Command Injection – Running arbitrary commands on a vulnerable web server.
Since HTTP logs record all requests made to a web server, monitoring these logs is crucial for detecting and mitigating these attacks.

# Using Splunk for HTTP Log Analysis:

Setting Up the Search Queries:

In my lab, I used Splunk to ingest and analyze HTTP logs. A few key searches I conducted:

Top Source IPs Accessing the Server:

index=* OR index=_* sourcetype=httplogs | top limit=10 src_ip
This query lists the most frequent source IPs, helping identify potential attackers or suspicious traffic sources.

Top Destination IPs (Servers Being Accessed):

index=* OR index=_* sourcetype=httplogs | top limit=10 dst_ip
This query highlights which servers are being accessed the most. Unusual spikes could indicate DDoS attacks or unauthorized access attempts.

Investigating Suspicious Requests:

index=* sourcetype=httplogs status=404
Requests resulting in a 404 (Not Found) error can sometimes indicate reconnaissance activity, where attackers are probing for vulnerabilities.

Detecting Brute Force or Directory Traversal Attempts:

index=* sourcetype=httplogs uri="/admin" OR uri="/login" | stats count by src_ip
Many attackers attempt to brute force login pages or access sensitive directories. This search reveals potential brute-force attempts.



# Conclusion

This lab gave me hands-on experience in analyzing logs just like a SOC analyst would in a real-world environment. By using Splunk to detect anomalies, investigate logs, and visualize attack patterns, I gained a deeper appreciation for how critical log analysis is in cybersecurity.

If you’re looking to break into cybersecurity or improve your SOC skills, practicing with Splunk and HTTP logs is a great starting point!



![Screenshot 2024-12-29 205047](https://github.com/user-attachments/assets/dab4ef12-a051-48d8-8d6c-0b884a3ca4a3)
![Screenshot 2024-12-29 210504](https://github.com/user-attachments/assets/0c995bfc-6ac3-41a3-897e-bc114b97ae51)
![Screenshot 2024-12-29 210936](https://github.com/user-attachments/assets/df56b534-fbb4-45d9-a9e5-2c4ebc567c31)
![Screenshot 2024-12-29 211437](https://github.com/user-attachments/assets/3fe245b5-1d7c-443c-a4b0-92f283f29394)
![Screenshot 2024-12-29 211548](https://github.com/user-attachments/assets/26a6ccfb-6b25-484f-8a72-d4039431d226)
![Screenshot 2024-12-29 211834](https://github.com/user-attachments/assets/0cb51183-dfdc-469e-a070-689e8c1684a5)
