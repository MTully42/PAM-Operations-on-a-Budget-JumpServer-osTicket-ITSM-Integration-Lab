# PAM-Operations-on-a-Budget-JumpServer-osTicket-ITSM-Integration-Lab

PAM Operations on a Budget: JumpServer & osTicket ITSM Integration Lab

🎯 Project Overview

This repository documents a functional home lab created to demonstrate core competencies required for a Senior II PAM Support Specialist, aligning directly with the provided job description. The lab utilizes free and open-source software (FOSS) to simulate a production-level Privileged Access Management (PAM) environment and its integration with an IT Service Management (ITSM) ticketing workflow.


💼 Demonstrated Core Competencies

This project provides verifiable experience in:

    PAM Implementation & Maintenance: Deployment and configuration of a robust PAM solution (JumpServer).

    User Provisioning: Integrating the PAM platform with Active Directory (AD).

    Session Management: Securing, monitoring, and auditing privileged sessions (mimicking CyberArk PSM).

    ITSM Workflow: Monitoring application queues, processing requests, and adhering to SLAs within a ticketing system (mimicking Ivanti Front Range).

    Documentation & Training: Creating end-user guides and troubleshooting scripts.

🛠️ Step 1: Lab Infrastructure Setup

This foundational step uses free hypervisors and evaluation software to build a realistic network environment.



Virtual Machines (VMs)

VM Name	Role	Purpose	OS (Free/Eval)
DC	Domain Controller	Hosts Active Directory (homelab.local) for centralized authentication.	Windows Server Evaluation
JS-Host	PAM Host	Hosts JumpServer (via Docker) to manage credentials.	Ubuntu/CentOS Server
OS-Host	ITSM Host	Hosts osTicket (LAMP/LEMP stack) for ticketing.	Ubuntu/CentOS Server
Target-01	Target Server	The asset whose local Administrator account is managed by PAM.	Windows Server Evaluation / Linux
Admin-WS	Workstation	Used to access JumpServer and osTicket web interfaces.	Windows 10/11

Setup Instructions

    Install a hypervisor (e.g., VMware Workstation Products or Oracle VirtualBox).

    Create and configure the DC VM as a Domain Controller for homelab.local.

    Install OS on all remaining VMs and join them to the homelab.local domain where applicable (Windows VMs).

🔒 Step 2: PAM Solution Setup (JumpServer)

JumpServer replaces CyberArk for this lab, demonstrating secure credential management and auditing.



2.1 Installation & AD Integration

    On the JS-Host VM, install Docker and deploy JumpServer using the official quick-start guides.

    Access the JumpServer Web UI (Lina) and configure LDAP integration to authenticate against the DC VM. (Competency: Implement application and manage user provisioning).

2.2 Onboard and Secure a Target Account

    Add Target-01 as an Asset in JumpServer, specifying its IP/hostname.

    Onboard the local Administrator account for Target-01 into JumpServer’s Asset Credentials Vault.

    Configure JumpServer to automatically rotate this password periodically. (Competency: Maintain applications; Ensure smooth operation).

2.3 Session Recording Demonstration

    Use the JumpServer Web UI to establish an RDP or SSH session to Target-01.

    After ending the session, navigate to the Audit Log within JumpServer to view and review the recorded session file. (Competency: Ensure secure access; Documentation on problem solutions).

🎫 Step 3: ITSM Workflow Setup (osTicket)

osTicket replaces Ivanti Front Range, simulating the critical Service Desk functions.


3.1 Installation & SLA Configuration

    On the OS-Host VM, install the necessary web stack (LAMP/LEMP) and deploy osTicket.

    In osTicket Admin settings, create a new SLA Plan named "PAM Critical Access" with a high-priority response time (e.g., 1 hour). (Competency: Ensure tickets are closed within established service levels).

3.2 Access Request Simulation

    Create a custom Help Topic called "PAM Privileged Account Checkout Request" with fields for Target Hostname and Business Justification.

    Workflow Simulation (Mimics Job Duties):

        User Action: Submit a test request via the osTicket portal.

        Agent Action (You): Monitor the queue, open the ticket, and assign the "PAM Critical Access" SLA. (Competency: Monitor application queues).

        Resolution Step: Add an Internal Note (Journal Entry) detailing the actions taken in JumpServer (e.g., "Account checked out and used to resolve issue. Password rotation confirmed via PAM platform."). (Competency: Document actions with real-time journal entries).

        Closing: Change the ticket status to Closed.

📚 Step 4: Documentation & Training Artifacts

These deliverables satisfy the documentation and training requirements of the role.

    Tool Configuration Document: A detailed guide on integrating JumpServer with the Active Directory on the DC VM. (Competency: Develop and maintain comprehensive documentation).

    End-User Training Guide: A one-page PDF or guide titled "How to Access Admin Systems via the JumpServer Portal." (Competency: Provide one-on-one training and guidance).

    Troubleshooting Script: A prepared script demonstrating how to assist a Help Desk member with a PAM access failure, checking both the osTicket log and the JumpServer session audit. (Competency: Offer over-the-phone/Webex assistance).

🔗 Project Resources & Technologies

The following software and resources were utilized in building this open-source PAM and ITSM competency lab.
Component	Tool / Platform	Link
PAM Solution (CyberArk Alternative)	JumpServer	https://www.jumpserver.org/
ITSM / Ticketing (Ivanti Alternative)	osTicket	https://osticket.com/download/
Hypervisor	VMware Workstation Pro / Player	VMware Workstation Products
Alternative Hypervisor	Oracle VirtualBox	https://www.virtualbox.org/wiki/Downloads
Operating System (DC/Target Servers)	Windows Server Evaluation	Microsoft Evaluation Center
Operating System (Host VMs)	Ubuntu Server / CentOS	https://ubuntu.com/download/server
