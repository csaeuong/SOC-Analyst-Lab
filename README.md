# SOC-Analyst-Lab

## Objective

The SOC Analyst Lab project was designed to simulate a real-world Security Operations Center environment for analyzing and responding to cyber threats. The primary focus was on ingesting and reviewing log data within a Security Information and Event Management (SIEM) platform, generating test telemetry to replicate common attack techniques. This hands-on experience reinforced core SOC analyst skills such as log analysis, event correlation, and alert triage, while deepening understanding of adversary behavior and security operations workflows.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Log analysis (Windows Event Logs, Sysmon)
- SIEM query building and dashboard creation
- Event correlation and triage techniques
- MITRE ATT&CK mapping and Sigma rule interpretation
- Threat hunting across multiple data sources
- Incident investigation and response reporting

### Tools Used
[Bullet Points - Remove this afterwards]

- **Vultr** for hosting the SOC lab environment  
- **Elasticsearch, Logstash, Kibana** (ELK stack) for ingestion, querying, alerting, and dashboards  
- **Elastic Agents (Fleet / Beats)** for multi-source log collection  
- **Sysmon**, Windows Event Logs, and Linux syslog/auth logs for endpoint telemetry  
- **Kali Linux** for attack simulation  
- **Mythic C2** for post-exploitation command-and-control testing  
- **osTicket** for incident ticketing and workflow demonstration

## Steps

![30Day-SOC-Project-Diagram](https://github.com/user-attachments/assets/58095c69-6ebb-4fd1-a648-8f00877e1e4f)

Ref 1: Network Diagram - The diagram provides a visual overview of the virtual lab environment used in the SOC Analyst Lab. The architecture simulates a real-world Security Operations Center by integrating log-generating endpoints, a SIEM platform, a ticketing system,   and adversary infrastructure.
