# Pcap Malware File Analysis with Wireshark

# Pcap File Link Address:
https://www.malware-traffic-analysis.net/2025/06/13/2025-06-13-traffic-analysis-exercise.pcap.zip


# We will be answering these main questions:

What is the IP address of the infected Windows client?

What is the mac address of the infected Windows client?

What is the host name of the infected Windows client?

What is the user account name from the infected Windows client?



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
























































# Conclusion
The infected machine successfully brute-forced the password for the highly privileged administrator account and is now using that account's credentials to request access to other network resources (in this case, the cifs service on the domain controller). This is a severe compromise indicating lateral movement.

# Project Source
https://www.malware-traffic-analysis.net/2025/06/13/index.html
