# IT Support Lab

Simulated IT support environment using **Active Directory**, **Jira Ticketing**, and **Azure Cloud Networking**.

---

## Scenario 1 – Sarah Jenkins (Account Disabled)
**Issue:** User unable to log in due to account being disabled.  
**Resolution:** Re-enabled the user account and verified access.  

**Evidence:**  
![Sarah Jenkins AD](screenshots/Sarah%20Jenkins%20AD%20account%20enabled.png)  
![Sarah Jenkins Jira](screenshots/Sarah%20Jenkins%20Jira%20Image%20.png)

---

## Scenario 2 – Daniel Carter (Password Reset)
**Issue:** User unable to log in due to password issues.  
**Investigation:** Accessed Active Directory, located account, identified password issue.  

**Evidence:**  
![Daniel Carter AD](screenshots/Daniel%20Carter%20AD.png)  
![Daniel Carter Password Reset](screenshots/Daniel%20Carter%20AD%20password%20reset.png)  
![Daniel Carter Jira](screenshots/Daniel%20carter%20jira%20done.png)

---

## Scenario 3 – Emma Singh (Account Related)

**Evidence:**

![Emma Singh AD](screenshots/Emma%20Singh%20AD.png)

![Emma Singh Account Enabled](screenshots/Emma%20Singh%20account%20enabled.png)

![Emma Singh Jira Ticket](screenshots/Emma%20ticket%20done.png) 
---

## Scenario 4 – Azure VM Networking & ICMP Troubleshooting
**Objective:** Troubleshoot connectivity between two Azure VMs in different Virtual Networks.

**Steps:**
- Created two Virtual Networks (`vm-1-vnet` and `vm-2-vnet`) and deployed VMs.
- Initial ping test failed (Destination host unreachable).
- Identified blocking rules in NSG and Windows Defender Firewall.
- Added Inbound NSG rule + enabled ICMP in Windows Firewall.
- Retest showed successful ping.

**Evidence:**
![Virtual Networks](screenshots/Both%20vnets.png)  
![VM Creation](screenshots/Create-new-vm2.png)  
![Ping Failure](screenshots/Ping-destination-host-unreachable.png)  
![Successful Local Ping](screenshots/ping-local-success-remote-unreachable.png)  
![Windows Firewall](screenshots/vm2-windows-firewall-profiles-disabled.png)  
![NSG / Firewall Rule](screenshots/VM2_windows_firewall_block_rule..png)  
![Successful Ping](screenshots/vm1-ping-local-ip-success.png)

**Key Learnings:** Azure NSGs block ICMP by default. Both cloud-level (NSG) and OS-level firewall rules must allow traffic.

---

**Repository Purpose**  
This repository showcases practical IT support documentation, troubleshooting steps, and evidence collection using Active Directory, Jira, and Azure.

---

