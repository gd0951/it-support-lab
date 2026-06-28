# IT Support Lab

Simulated IT support environment using **Active Directory**, **Jira Ticketing**, and **Azure Cloud Networking**.

---

## Scenario 1 – Sarah Jenkins (Account Disabled)
**Issue:** User unable to log in due to account being disabled.  
**Resolution:** Re-enabled the user account and verified login access.

**Evidence:**  
![Sarah Jenkins AD Enabled](screenshots/Sarah%20Jenkins%20AD%20account%20enabled.png)  
![Sarah Jenkins Jira](screenshots/Sarah%20Jenkins%20Jira%20Image%20.png)

---

## Scenario 2 – Daniel Carter (Password Reset)
**Issue:** User unable to log in due to password issues.  
**Investigation:** Accessed Active Directory, located the user account.  
**Resolution:** Performed password reset and confirmed access.

**Evidence:**  
![Daniel Carter AD](screenshots/Daniel%20Carter%20AD.png)  
![Password Reset](screenshots/Daniel%20Carter%20AD%20password%20reset.png)  
![Jira Ticket](screenshots/Daniel%20carter%20jira%20done.png)

---

## Scenario 3 – Emma Singh (Account Related)
**Evidence:**  
![Emma Singh AD](screenshots/Emma%20Singh%20AD%20.png)  
![Emma Singh Account Enabled](screenshots/Emma%20Singh%20account%20enabled.png)  
![Emma Singh Jira](screenshots/Emma%20ticket%20done.png)

---

## Scenario 4 – Azure VM Networking & ICMP Troubleshooting
**Objective:** Troubleshoot connectivity between two Azure VMs in different Virtual Networks using NSGs and Windows Firewall.

**Steps:**
- Created two Virtual Networks (`vm-1-vnet` and `vm-2-vnet`) and deployed VMs.
- Initial ping from VM-1 to VM-2 failed ("Destination host unreachable").
- Used `Test-NetConnection` in PowerShell to confirm port and ping issues.
- Identified blocking rules in Network Security Group and Windows Defender Firewall.
- Added Inbound NSG rule to allow ICMP traffic.
- Enabled ICMP echo requests in Windows Firewall.
- Retest showed successful ping.

**Evidence:**
![Virtual Networks](screenshots/Both%20vnets.png)  
![Ping Failure](screenshots/Ping-destination-host-unreachable.png)  
![PowerShell Test-NetConnection](screenshots/Powershell-test-netconnectionfailed.png)  
![Successful Ping](screenshots/ping-local-success-remote-unreachable.png)  
![Windows Firewall Settings](screenshots/vm2-windows-firewall-profiles-disabled.png)

**Key Learnings:**  
Azure NSGs block ICMP by default. Both cloud-level (NSG) and OS-level (Windows Firewall) configurations are required for connectivity. PowerShell tools like `Test-NetConnection` are valuable for diagnosing issues.

---

**Repository Purpose**  
This repository showcases practical IT support documentation, troubleshooting steps, and evidence collection using Active Directory, Jira, and Azure.
