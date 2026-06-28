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
![Emma Singh AD](screenshots/Emma-Singh-AD..png)  
![Emma Singh Account Enabled](screenshots/Emma%20Singh%20account%20enabled.png)  
![Emma Singh Jira](screenshots/Emma%20ticket%20done.png)

---

## Scenario 4: Azure Cross-VNet Routing Failure & Security Hardening

### 📌 Objective
Troubleshoot an isolated multi-network topology in Microsoft Azure by identifying an IP address space overlap, re-architecting the Virtual Network layout, and adjusting Windows Defender Firewall security rules to safely handle ICMP diagnostics.

---

### 🛠️ Step-by-Step Engineering Walkthrough

#### 1. Topology Discovery & Blocker Analysis
The initial architecture consisted of two distinct networks within the same resource group environment: `vm-1-vnet` and `vm-2-vnet`. Attempting to log into VM-1 and establish communication with the target machine instantly failed, returning a "Destination host unreachable" error.

![01_initial_ping_failure](screenshots/Ping-destination-host-unreachable.png)

Upon pivoting to the Azure portal dashboard to link the two backbones using standard **Azure VNet Peering**, the platform threw an explicit red warning banner showing that both networks were provisioned using identical IP blocks (`10.0.0.0/16`), breaking standard cloud routing logic:

![02_vnet_peering_overlap_error](screenshots/vnet_peering_overlap_error.png)

#### 2. Environment Teardown & Reconstruction
To resolve the structural overlap, the misconfigured target infrastructure had to be decommissioned. `VM-2` was permanently deleted along with its virtual OS storage disk to clear out the bad topology footprint.

![03_delete_misconfigured_vm](screenshots/Delete-vm2.png)

A replacement VM instance was created. During the provisioning wizard's **Networking phase**, the machine was explicitly assigned directly onto `vm-1-vnet`'s infrastructure space instead of generating an isolated network loop.

![04_correct_vnet_provisioning](screenshots/Create-new-vm2.png)

#### 3. Guest Operating System Hardening
With both servers now attached to the same wire, the network path was established. Rather than insecurely disabling whole firewall profiles, the target server’s **Windows Defender Firewall with Advanced Security** suite was accessed via RDP. 

The specific inbound core rule **File and Printer Sharing (Echo Request - ICMPv4-In)** was enabled, showing the green checkmark verifying that secure inbound diagnostics are explicitly allowed.

![05_windows_firewall_rule_adjustment](screenshots/vm2-re-enable%20ICMP.png)

#### 4. Verification & Resolution Proof
A final diagnostic loop was sent across the established network bridge. The traffic cleared both the cloud infrastructure constraints and the guest OS endpoint controls flawlessly, achieving a stable continuous connection with sub-millisecond response times and 0% packet loss.

![06_successful_ping_reply](screenshots/vm1-ping-local-ip-success.png)

---

### 🧠 Key Learnings
* **IP Address Allocation:** Always plan network spacing and CIDR layouts beforehand to prevent resource conflicts and expensive teardowns.
* **Hierarchical Traffic Defense:** Traffic flow depends on a layered architecture. Connectivity must be cleanly green-lit at both the cloud fabric layer (VNets/Peering/NSGs) and the internal guest operating system tier (Windows Firewall).
