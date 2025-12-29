# Security Incident Report – Network Protocol Analysis

## Section 1: Identify the Network Protocol Involved in the Incident

The network protocol involved in this incident is the **Hypertext Transfer Protocol (HTTP)**.

The issue investigated involved users accessing the website **yummyrecipesforme.com**, which requires HTTP traffic to request and load web pages from a web server. When the cybersecurity analyst executed `tcpdump` and accessed the website, the captured network traffic showed HTTP being used to establish communication between the browser and the web server.

Additionally, the malicious executable file that users were prompted to download was delivered through HTTP traffic at the application layer of the TCP/IP model. After the file was executed, the browser initiated additional HTTP requests to a different website, indicating that HTTP was the primary protocol used throughout the incident.

---

## Section 2: Document the Incident

Several customers contacted the organization’s helpdesk reporting that when they visited **yummyrecipesforme.com**, they were prompted to download and run a file that claimed to provide access to free recipes. After executing the file, customers reported that their personal computers began running slowly. The website owner also reported being unable to access the administrative account for the website.

To investigate the incident, a cybersecurity analyst used a sandbox environment to safely access the website without affecting the organization’s production network. The analyst ran `tcpdump` to capture network traffic generated during the interaction with the website. While visiting the site, the analyst was prompted to download an executable file disguised as a browser update. The analyst accepted the download and executed the file.

After execution, the analyst observed that the browser was redirected from **yummyrecipesforme.com** to a different website, **greatrecipesforme.com**. Review of the tcpdump log showed that the browser initially requested DNS resolution for yummyrecipesforme.com, established a connection over HTTP, and then initiated a new DNS request for greatrecipesforme.com. Network traffic was subsequently redirected to the new IP address associated with the malicious site.

A senior cybersecurity analyst later reviewed the website source code and the downloaded executable file. The analysis confirmed that malicious JavaScript had been injected into the legitimate website to prompt users to download malware. Based on the website owner’s inability to access the administra
