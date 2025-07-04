<h1>Home Lab & Live Attack Map</h1>

<h2>Introduction</h2>

In today’s rapidly evolving digital landscape, organizations face an ever-growing threat from cyberattacks that are increasingly sophisticated, persistent, and global in scale. Real-time visibility into these threats is essential for proactive defense and effective incident response. With this cybersecurity project I have leveraged Microsoft Azure and Microsoft Sentinel to design and implement a live attack map—a dynamic visualization tool that displays cyber threats and malicious activity as they occur across the globe.

Using the scalability and flexibility of Microsoft Azure, combined with the advanced threat detection and SIEM (Security Information and Event Management) capabilities of Microsoft Sentinel, this project integrates real-time telemetry, log analytics, threat intelligence, and geolocation data. The result is an interactive dashboard that not only illustrates ongoing attacks but also enhances situational awareness for security teams, enabling faster and more informed decision-making.

The objective of this project is to demonstrate how cloud-native tools can be harnessed to provide immediate insights into the cyber threat landscape, helping organizations shift from reactive to proactive cybersecurity strategies.


<h2>Creating the Resource Group, NSG and Virtual Machine</h2>

To set up the environment for my cybersecurity project, I started by creating a Resource Group in Microsoft Azure, which served as a logical container to manage all the related infrastructure components.

I then created a Network Security Group (NSG), which came with default firewall rules to allow basic connectivity. To support my project requirements, I reviewed these default rules to allow specific types of traffic necessary for accessing and interacting with my Virtual Machine (VM).

![Firewall Rules before removing RDP](https://github.com/user-attachments/assets/f4a3364b-4e7a-40c4-8e39-151c35f1e095)


As we can see from the image above, The remote desktop protocol rule is active. I needed to remove this so I could render my Virtual Machine vulnerable to live attacks and so I could personally test that the VM was active and accessible.

<h2>Creating the Honeypot & Custom Firewall rule</h2>

Here I removed the RDP rule and created a custom firewall rule that allowed all incoming traffic and made sure all ports were open to entice attackers into our honeypot 

![Custom firwall rule added](https://github.com/user-attachments/assets/71488421-4557-4b0e-986f-c79935f4239a)

<h2>Testing the VM using Windows Powershell</h2>


Once the configuration was complete, I obtained the VM IP Address and tested connectivity to the VM using Windows Powershell and the 'ping command to confirm that the NSG rules were functioning as intended—permitting authorized access while maintaining a secure baseline. This configuration laid the foundation for live threat monitoring and visualization using Microsoft Sentinel.

![Ping VM from Powershell](https://github.com/user-attachments/assets/343753dc-a00a-45c0-be65-d295a7d35d8a)

<h2>Log Analytics and Threat Watchlist Summary</h2>
As part of enhancing threat detection and visibility in my cybersecurity project, I began by creating a Log Analytics Workspace in Microsoft Azure. This workspace acts as a central hub for collecting, storing, and querying log data from various connected resources.

To track known threat actors, I compiled a custom watchlist containing details of suspected attacker IP addresses and relevant metadata. This watchlist was then imported into Microsoft Sentinel, which integrates with the Log Analytics Workspace to provide advanced threat hunting and alerting capabilities.

Once the watchlist was in place, I used Kusto Query Language (KQL) to cross-reference the list of attackers with log data collected in the workspace. This allowed me to efficiently identify any matches between the watchlist and incoming traffic or activity logs—surfacing potential threats in real time.

This setup enabled a powerful, scalable method for identifying known attackers and laid the foundation for automated detection rules and visual dashboards within my live attack map.

![using KQL to find logs](https://github.com/user-attachments/assets/d1cee703-06a0-452d-ac5a-4ba3550c6763)

<h2>Live Attack Map Workbook Summary</h2>

To visualize threat activity in real time, I created a custom Workbook within Microsoft Sentinel, which served as the front-end for my Live Attack Map.

Using data collected from my Log Analytics Workspace—including logs enriched with geolocation and threat intelligence—I built dynamic visual components inside the Workbook. These included a geospatial map to display the location and source of attacks.

I used Kusto Query Language (KQL) to query log data and correlate it with my imported watchlist of attackers. The results were then fed into interactive visuals within the Workbook, enabling live tracking of attacker IPs across global regions.

This Workbook not only made threat patterns immediately visible but also provided a central place for continuous monitoring, analysis, and response—bringing the Live Attack Map to life directly within the Sentinel dashboard.

![Attack Map](https://github.com/user-attachments/assets/d90c74df-da8c-40ea-bffd-a22932e896fb)


<h2>Conclusion & Takeaways</h2>

This project gave me valuable hands-on experience with Microsoft Azure and Microsoft Sentinel, allowing me to build a fully functional Live Attack Map that visualizes real-time threats. Through this process, I learned how to deploy and secure cloud-based infrastructure, manage firewall rules using Network Security Groups, and leverage Sentinel’s powerful tools like Log Analytics, Watchlists, and Workbooks.

Working with Kusto Query Language (KQL) helped me understand how to query and analyze large volumes of security data efficiently. Creating a custom Workbook taught me how to translate raw log data into meaningful, actionable visual insights—an essential skill for any SOC (Security Operations Center) analyst or cybersecurity professional.

In a real-world cybersecurity role, the skills developed through this project would be directly applicable to threat detection, incident response, and security monitoring. The ability to build dashboards, correlate data with known threat indicators, and respond to suspicious activity in real time is critical for protecting organizations from evolving cyber threats. This project also highlighted the importance of automation, visibility, and proactive defense strategies in modern cloud security environments.



