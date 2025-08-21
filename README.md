# Pcap Malware File Analysis with Wireshark

# Pcap File Link Address:
https://www.malware-traffic-analysis.net/2025/06/13/2025-06-13-traffic-analysis-exercise.pcap.zip


# We will be answering these main questions:

What is the IP address of the infected Windows client?

What is the mac address of the infected Windows client?

What is the host name of the infected Windows client?

What is the user account name from the infected Windows client?



1. What is the IP address of the infected Windows Client.
   
Answer:10.6.13.133
By filtering for kerberos traffic I identified the source IP generating a high volume of AS-REQ traffic. 
<img width="1734" height="612" alt="Screenshot 2025-08-21 114112" src="https://github.com/user-attachments/assets/c3a03131-092c-4cba-983f-2aaec392987d" />



























































# Conclusion
The infected machine successfully brute-forced the password for the highly privileged administrator account and is now using that account's credentials to request access to other network resources (in this case, the cifs service on the domain controller). This is a severe compromise indicating lateral movement.

# Project Source
https://www.malware-traffic-analysis.net/2025/06/13/index.html
