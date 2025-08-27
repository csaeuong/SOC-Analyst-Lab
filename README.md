# SOC-Analyst-Lab

## Objective

The SOC Analyst Lab project was designed to simulate a real-world Security Operations Center environment for analyzing and responding to cyber threats. The primary focus was on ingesting and reviewing log data within a Security Information and Event Management (SIEM) platform, generating test telemetry to replicate common attack techniques. This hands-on experience reinforced core SOC analyst skills such as log analysis, event correlation, and alert triage, while deepening understanding of adversary behavior and security operations workflows.

### Skills Learned

- Log analysis (Windows Event Logs, Sysmon)
- SIEM query building and dashboard creation
- Event correlation and triage techniques
- Threat hunting across multiple data sources
- Incident investigation and response reporting

### Tools Used

- **Vultr** for hosting the SOC lab environment  
- **Elasticsearch, Logstash, Kibana** (ELK stack) for ingestion, querying, alerting, and dashboards  
- **Elastic Agents (Fleet / Beats)** for multi-source log collection  
- **Sysmon**, Windows Event Logs, and Linux syslog/auth logs for endpoint telemetry  
- **Kali Linux** for attack simulation  
- **Mythic C2** for post-exploitation command-and-control testing  
- **osTicket** for incident ticketing and workflow demonstration

## Steps

![30Day-SOC-Project-Diagram (1) (1)](https://github.com/user-attachments/assets/489cf17e-e3cf-4b87-84ee-50ed7a2784e3)

Ref 1: Network Diagram - The diagram provides a visual overview of the virtual lab environment used in the SOC Analyst Lab. The architecture simulates a real-world Security Operations Center by integrating log-generating endpoints, a SIEM platform, a ticketing system, and adversary infrastructure.

***

<img width="1920" height="1036" alt="Created the ELK server" src="https://github.com/user-attachments/assets/1ec7ca7d-5bef-41a4-a0cd-9a323660f9fd" />
Ref 2: ELK Server - Deployed an Ubuntu server on **Vultr**, fully updated it, and installed the ELK Stack to serve as the central SIEM.  

***

<img width="1919" height="1034" alt="Set Firewall" src="https://github.com/user-attachments/assets/88a3468f-0e18-4541-ad95-04a95db4f176" />
Ref 3: Firewall - Configured strict firewall rules to harden the server and only allow necessary services.  


***

<img width="1920" height="1034" alt="Started elasticsearch service" src="https://github.com/user-attachments/assets/91f38fd5-e349-4cf1-acb9-cffc167cefc6" />
Ref 4: Elastic Search - Installed and started the Elasticsearch service for log ingestion.  

***

<img width="1920" height="1038" alt="Installed Kibana" src="https://github.com/user-attachments/assets/df4332f2-7a3f-41bf-9dc8-d19fbaf23906" />
Ref 5: Kibana - Installed Kibana to provide dashboards, data visualizations, and SOC analyst workflows.  

***

<img width="1920" height="1041" alt="Deploy windows machine" src="https://github.com/user-attachments/assets/01e43abe-2248-4edd-801a-bca7eb9e1604" />
Ref 6: Windows Machine - Deployed a Windows endpoint, intentionally exposed to the internet to generate and capture attack logs.

***

<img width="1920" height="1036" alt="Installed agent on Windows" src="https://github.com/user-attachments/assets/00a19880-0e8e-4a01-ad84-d518831aac3d" />
Ref 7: Agent - Installed Elastic Agent via Fleet on the Windows machine to forward telemetry to the SIEM. 

***

<img width="1829" height="1015" alt="Installed sysmon" src="https://github.com/user-attachments/assets/ff1c81b8-ed56-459f-b8f3-e25db485e90b" />
Ref 8: Sysmon - Deployed Sysmon to collect detailed Windows event data for advanced detection and correlation.

***

<img width="1919" height="1040" alt="Set up log intergration" src="https://github.com/user-attachments/assets/07db765d-b2df-427c-8288-2008fa44fdf9" />
Ref 9: Intergrations - Configured Elastic integrations to monitor the Windows machine in real time. 

***

<img width="1920" height="1037" alt="Set up firewall to allow port 9200" src="https://github.com/user-attachments/assets/c438ad1a-50ce-41e4-91e5-3615346258b8" />
Ref 10: Port 9200 - Troubleshot an issue where agents appeared healthy but weren’t sending logs. Root cause: port **9200** was blocked by the firewall. After opening the port, data ingestion worked correctly.  

***

<img width="1920" height="1039" alt="Setup a SSH server in the cloud to observe hacking attempts" src="https://github.com/user-attachments/assets/a5e8a270-6338-4ebb-8ea4-6ffe7b547923" />
Ref 11: SSH Server - Deployed a Linux SSH server in the cloud to attract brute force attacks.

***

<img width="1920" height="1030" alt="Installed elastic agent on ssh server" src="https://github.com/user-attachments/assets/b71331dd-3f84-4c95-9f3f-973b640c14ae" />
Ref 12: Elastic agent SSH - Installed Elastic Agent on the SSH server for log forwarding. 

***

<img width="1918" height="949" alt="Created a rule to see SSH brute force failed attempts" src="https://github.com/user-attachments/assets/551fd5da-1278-4ee2-a800-ff2014983752" />
Ref 13: SSH Rules: Created a detection rule to flag repeated failed SSH logins.

***

<img width="1917" height="950" alt="Created a rule to see RDP Burte Force attempt on administrator" src="https://github.com/user-attachments/assets/d603915e-e28a-489e-bf6d-d6e871b4edc6" />
Ref 14: RDP Rules: Built a detection rule for RDP brute force attempts targeting the Administrator account.  

***

<img width="1915" height="955" alt="Created a few dashboards to show both failed and successfull authentications for SSH and RDP" src="https://github.com/user-attachments/assets/271fe6e9-bffa-46fd-9b5f-b853da46844b" />
Ref 15: Dashboards - Designed Kibana dashboards to visualize failed/successful SSH and RDP authentications, including geographic mapping of attack sources.

***

<img width="1914" height="932" alt="Install and Mythic and used it to download a file" src="https://github.com/user-attachments/assets/8fceb86d-4901-4b2f-8ddb-40a8de4f7179" />
Ref 16: Mythic C2 - Installed **Mythic C2**, which turned out to be one of the bigger challenges in the lab. At first, the server would not display the Mythic dashboard at all, just a blank error page. I spent several days troubleshooting, checking ports, certificates, firewall rules, and even redeploying a new virtual machine on **Vultr** to confirm it wasn’t the Mythic install itself. That worked, which told me the issue was local to my own setup.  

***

After more digging, I discovered the root cause: my VPN had a web filter running in the background, even when the VPN was “disabled.” Once I turned off that filter, Mythic worked perfectly. From there I installed the **Apollo agent** on the Windows machine and used it to simulate attacker activity by downloading a honeytoken file. 

***

<img width="1849" height="1048" alt="installed osTicket and created a ticketing system" src="https://github.com/user-attachments/assets/c3d2322b-1f4d-4561-8cfa-da1048908c09" />
Ref 17: osTicket - Set up osTicket as a SOC ticketing system to simulate analyst workflows.  

***

<img width="1795" height="973" alt="Fully functional ticketing system" src="https://github.com/user-attachments/assets/054d31f2-d3cd-4109-90c9-a669413991da" />
Ref 18: osTicket Troubleshooting -  Resolved an issue with the login screen by switching browsers and using incognito mode.

***

<img width="1914" height="939" alt="Set up the ticketing system and ran test" src="https://github.com/user-attachments/assets/e9fcb650-6db6-439c-8dba-9cc05c45b1ff" />
Ref 19: Ticket Automation -Configured automation so alerts from Elasticsearch automatically generated tickets in osTicket.  

***

<img width="1915" height="945" alt="Set up elastic EDR" src="https://github.com/user-attachments/assets/e15ca072-768e-44a3-8a12-376d60252d67" />
Ref 20: Elastic EDR - Enabled Elastic EDR capabilities. Successfully detected the Mythic C2 Apollo agent on the Windows endpoint and blocked its activity.  
