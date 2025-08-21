# Digital Forensics of a Pcap File Using Wireshark

# Overview 
In this Network Forensics project I will be using wireshark to analyze a provided packet capture. My process will involve anayzing traffic to identify a suspicious host,  its communication to uncover an attack, and then tracing the evidence to prove the attack was successful. Ultimately, I will identify the compromised machine, its MAC address, and the high-privilege user account whose credentials were stolen, demonstrating the full scope of the incident.







# Wireshark Review 



1. What is the IP address of the infected Windows Client.
   
  Answer: 10.6.13.133

  By filtering for kerberos traffic I identified the source IP generating a high volume of AS-REQ traffic. 

<img width="1734" height="612" alt="Screenshot 2025-08-21 114112" src="https://github.com/user-attachments/assets/c3a03131-092c-4cba-983f-2aaec392987d" />


2. What is the MAC address of the infected Windows client?

   Answer: 24:77:03:91:57:61

    I'm able to use kerberos or others like dns to find the infected windows Client.

    More Specifically by Examining the ethernet header of a malicious packet from the infected IP

<img width="1510" height="475" alt="Screenshot 2025-08-21 122638" src="https://github.com/user-attachments/assets/1c3f36cf-470e-4415-b0b4-5188566345b0" />



3. What is the host name of the infected Windows client?

   Answer: DESKTOP-5AVE44C

   Applying the NBNS traffic filter from the infected IP to discover it's host name which is located in Queries. 

<img width="875" height="566" alt="Screenshot 2025-08-21 115631" src="https://github.com/user-attachments/assets/357c1df8-d76a-4dde-a4bf-34f2c7996da8" />


4. What is the user account name from the infected Windows client?

Answer: Adminstrator

So as we see below there is a TSG-REQ (ticket granting service request) packet. Which proves the previous brute force attack was susccesful. 

<img width="865" height="268" alt="Screenshot 2025-08-21 115217" src="https://github.com/user-attachments/assets/1819a7ef-067e-4a93-b4bf-744fd7425ab3" />

<img width="1138" height="472" alt="Screenshot 2025-08-21 120136" src="https://github.com/user-attachments/assets/d4a252c6-5c2f-4f30-91e1-ca91019646ef" />







# Conclusion
10.6.13.133 was compromised and was creating high AS-REQ traffic attempting to gain access to the "MASSFRICTION.COM" domain. I later find evidence of both a kerberos TGS-REG and an LDAP bind request which proves that they were successful with their brute-force spraying password attack. They were able to guess the "administrator" accounts password. They now have accesss to the account with highest privilage and have full control over the network. We also see proof of the attacker preforming reconnaissance and lateral movements. 

# Project Source
https://www.malware-traffic-analysis.net/2025/06/13/index.html

# Pcap File Link Address:
https://www.malware-traffic-analysis.net/2025/06/13/2025-06-13-traffic-analysis-exercise.pcap.zip
