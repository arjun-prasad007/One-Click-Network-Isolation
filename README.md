🛡️ SOAR Automation: One-Click Host Isolation with Wazuh & Tines
This repository showcases a fully automated Security Orchestration, Automation, and Response (SOAR) workflow designed to contain cyber threats in real-time. By integrating Wazuh (SIEM) and Tines (Automation Platform), I have implemented a mechanism to isolate compromised Windows endpoints with a single click from an email alert.
📋 Project Overview
When a high-severity alert (like a brute-force attack or malware execution) is detected by Wazuh, it triggers an automated workflow that sends an interactive email to the SOC analyst. The analyst can then choose to isolate the host immediately to prevent lateral movement.
Key Components:
Wazuh: Monitors endpoints and executes Active Response commands.
Tines: Orchestrates the workflow, handles webhooks, and manages analyst communication.
Active Response: Automatically creates Windows Firewall rules to block network traffic.
⚙️ How It Works (The Logic)
Detection: Wazuh identifies a threat and sends a JSON payload to a Tines Webhook.
Notification: Tines parses the data and sends an email with Isolate and Un-isolate links.
Action: Clicking "Isolate" sends a command back to the Wazuh API for the specific Agent ID.
Containment: The Wazuh agent on the Windows machine creates a firewall rule called Wazuh_Isolation, blocking all outbound/inbound traffic.
📸 Proof of Concept
1. Automation Workflow (Tines)
The logic built within Tines to handle alerts and branching triggers.
![](/assets/Tinesworkflow.png)
2. Analyst Interface (Email Alert)
The interactive email received by the analyst to make quick containment decisions.
![](/assets/Emailalet.png)
3. Verification (Proof of Isolation)
Evidence of a successful isolation where the Windows machine shows "General Failure" during network pings, confirming the firewall rule is active.
![](/assets/proofofisolation.png)
🛠️ Technical Skills Demonstrated
SIEM/XDR: Wazuh Rule configuration and Active Response.
SOAR: Workflow automation and API integration with Tines.
Endpoint Security: Windows Firewall management and network isolation.
Incident Response: Streamlining the "Containment" phase of the incident life cycle.
