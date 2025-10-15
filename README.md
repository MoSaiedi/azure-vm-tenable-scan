Description: This project demonstrates a hands-on approach to building and testing a secure cloud environment using Microsoft Azure and Tenable vulnerability scanning tools. The primary objective of this lab is to understand the real-world process of deploying a cloud-hosted virtual machine (VM), configuring its accessibility, and assessing its security posture through authenticated local scans — all within a controlled and ethical testing environment.

Step 1: Created a Virtual Machine in Azure. I ensured this virtual machine had a public ip address. 
<img width="1405" height="515" alt="Screenshot 2025-10-14 at 7 33 46 PM" src="https://github.com/user-attachments/assets/dce72347-ea17-4f1e-a652-a05980e8a8c0" />

Step 2: I downloaded "Windows App" from the App store so I could RDP from my Mac to my Windows VM. Once I downloaded Windows App, I connected to my VM using the public IP address of the machine and the machine's credentials. 

<img width="1280" height="732" alt="image" src="https://github.com/user-attachments/assets/e70a4fd3-c08c-4a53-bb95-bfbe595fbeaa" />


Step 3: I logged into the virtual machine and removed fire wall settings on the machine. Typically you never want to do this to a machine, however because this is a lab machine that I would be taking down later I felt comfortable doing so. 

<img width="810" height="681" alt="image" src="https://github.com/user-attachments/assets/57694768-cfdb-4eb0-9091-658a754d1dbd" />
<img width="1045" height="782" alt="image" src="https://github.com/user-attachments/assets/cebb4345-8005-4263-9ef3-085ce042a114" />

Step 4: I logged into the Tenable console and started a Basic Network Scan. I provided Tenable with the public IP address of my machine. I ran scan on my machine without providing tenable my machine's credentials to similuate the kind of simple scan a curious hacker might deploy against a machine it doesn't have the credentials for. 

<img width="1280" height="643" alt="image" src="https://github.com/user-attachments/assets/b3968612-84ef-418d-aedc-3786acc6de6c" />

Step 5: Once the scan was complete I open up the scan and found that my machine had 6 medium and 1 low vulnerability discovered on it. 

<img width="1280" height="659" alt="image" src="https://github.com/user-attachments/assets/a7e7fc33-921c-4dab-a624-6e73a047b665" />

About the found vulnerabilities:

Medium Severity

SSL Medium Strength Cipher Suites (SWEET32): Uses weak 64-bit encryption (3DES); replace with modern TLS 1.2+ ciphers.

SSL Certificate Cannot Be Trusted: Certificate not from a trusted CA; use a valid, CA-signed certificate.

SSL Self-Signed Certificate: Self-issued certificate; replace with one signed by a recognized authority.

SMB Signing Not Required: SMB messages not validated; enable SMB signing to prevent tampering.

TLS 1.0 Protocol Detected: Outdated encryption protocol; disable and enforce TLS 1.2 or higher.

TLS 1.1 Deprecated Protocol: Deprecated version still active; disable and upgrade to TLS 1.2+.

Low Severity

ICMP Timestamp Disclosure: System responds to timestamp requests; disable to prevent minor reconnaissance.

Informational

Service & Port Detection (SMB, RDP, DCE, etc.): Identifies open services for network mapping; review and limit exposure.

OS and Host Info Disclosure: Reveals system details via SMB/NetBIOS; restrict information leaks and harden configurations.

SSL & Traceroute Information: Provides general certificate and routing data; minimal risk, used for network enumeration.

Step 6: What I've learned

Through this project, I gained hands-on experience in building, configuring, and assessing the security posture of a cloud-hosted system using Microsoft Azure and Tenable.
Creating a virtual machine with a public IP, remotely accessing it, and scanning it for vulnerabilities taught me how real-world systems can be exposed to common misconfigurations.

I learned:

How vulnerability scanners identify outdated protocols like TLS 1.0 and weak encryption ciphers (SWEET32).

The importance of valid SSL certificates for establishing trusted communication.

Why SMB signing and modern TLS versions are critical to protect against interception and tampering.

How even low-risk issues like ICMP timestamp disclosure can assist attackers during reconnaissance.

That informational findings (like open ports or service banners) still reveal valuable data that can be hardened or hidden.

Overall, this lab deepened my understanding of network security fundamentals, cloud hardening practices, and vulnerability management workflows — from detection to remediation.
