# Network traffic monitoring and attack detection in Wireshark

## Objective

The Network Traffic monitoring project aimed to perform network traffic monitoring and analysis using Wireshark. This project had the focus of filtering and analysing network packets to identify potential security threats such as brute force attempts and unauthorised access attemps, such as attempts to log into the FTP server. This hands on experience was to develop practical skills in traffic inspection, threat detection, digital forensics and simulate real-world network security monitoring tasks

### Skills Learned

- Advanced understanding of packet analysis.
- Proficiency in traffic filtering and pattern recognition.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network forensics - to investigate and document network based security incidents.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Powershell for network commands and generating hashfiles to perform OSINT.
- VirusTotal to gain more knowledge about files through searching their hash value.
- Abuseipdb to find out more information about a specific IP such as country and city of origin.

## Steps
- Two screenshots of HackTheBox Sherlock questions regarding the specific PCAP file that showcased network traffic regarding a brute force attack.
![Screenshot 2025-03-28 204249](https://github.com/user-attachments/assets/a707bfcf-b485-4ac6-9e40-734ce5251b50)
![Screenshot 2025-03-28 204238](https://github.com/user-attachments/assets/f9e68881-8e7a-4fce-a10f-ac806ae13a6a)
- This screenshot shows the conversations that are contained in this specific PCAP file sorted by the amount of bytes from highest to lowest. This information shows that the highest number of bytes that were sent were from the source IP address of 15.206.185.207 > the destination IP address of 172.31.45.144. This provides key information regarding which IP addresses to filter by and gain more information.
![Screenshot 2025-03-28 203717](https://github.com/user-attachments/assets/df32ab1a-1a02-42e0-bd64-e0803d84c3d4)
- Screenshot shows a filter of ip.addr == 15.206.185.207 in Wireshark to show all network traffic that contained the specific IP addres (either source or destination). Upon further analysis, I saw the FTP protocol being used and specific requests to access certain users which provided context and showed me that more information can be obtained if i filter for all FTP traffic
![Screenshot 2025-03-28 203832](https://github.com/user-attachments/assets/82b5efe7-5771-4b48-bfff-2be084ab6491)
- Screenshot shows the following of a TCP stream that tried to access the FTP server under the USER admin and the PASSWORD alonzo.spire!rocks - and showed the outcome of the login attempt - failed
![Screenshot 2025-03-28 203858](https://github.com/user-attachments/assets/1e10d1eb-fa2d-4be8-8516-cbfd01b9797d)
- Screenshot shows filtering of specific IP mentioned previously and filter for only FTP traffic. Can see the request to log into the FTP server and the response generated from the server which stated that the login was successful
![Screenshot 2025-03-28 204034](https://github.com/user-attachments/assets/ee96f80c-04be-437a-95d0-898a03243970)
- Screenshot shows the following of the TCP stream from the successful login - able to see the correct USER forlea-ftp and the correct PASSWORD ftprocks69$
![Screenshot 2025-03-28 204051](https://github.com/user-attachments/assets/ec3f94ec-7fbc-4600-81a2-c4a765e21904)
- Screenshot shows OSINT of the source IP that was used to login to the FTP server to gain information such as the country and city of origin
![Screenshot 2025-03-28 204144](https://github.com/user-attachments/assets/bf6bcca6-4953-49f0-913c-b166cde074cc)
- Screenshot shows critical information of the actions that were performed by the IP that successfully logged into the FTP server. Requests / commands such as RETR (used to request a file that can be transferred from the server to the client's local system) on specific files - Maintenance-notice.pdf and s3_buckets.txt.
![Screenshot 2025-03-28 204414](https://github.com/user-attachments/assets/f7cf5daf-d60a-407b-acd9-40708a21e74b)
- Screenshot shows powershell commands ran after exporting the specific files mentioned before to gain the hash values of each file to run in VirusTotal to gain more knowledge about each file.
![Screenshot 2025-03-28 204657](https://github.com/user-attachments/assets/932efe21-fd46-4fa5-bf4d-f8ee711e9a4c)
- The next two screenshots show the content of each file that was requested by the attacker's IP address. The PDF file contains important information such as the temporary password for the
 backup SSH server - **B@ckup2024** and the .txt file containing information such as important domain names and email addresses to contact for security clearances.
![Screenshot 2025-03-28 204818](https://github.com/user-attachments/assets/ea85f259-3374-4547-b15b-d4faca3d48c6)
![Screenshot 2025-03-28 204848](https://github.com/user-attachments/assets/ed5dd072-e889-40d9-88ad-9fb8a2eda39b)









