# 50 Days of Azure - Day 9: Multi-NIC Virtual Machine Configuration

## Task Overview
As part of the Nautilus team's incremental migration, I configured advanced networking for a Linux node by attaching a secondary Network Interface (NIC) to an existing Virtual Machine.

## Objective
Attach the pre-existing `datacenter-nic` to `datacenter-vm` in the `eastus` region to support multi-homed networking capabilities.

## Technical Details
*   **VM Name:** `datacenter-vm`
*   **NIC Name:** `datacenter-nic`
*   **Region:** `eastus`
*   **Operation:** Hot-attach/Offline-attach of secondary network resource.

## Real-World Scenario
In high-security environments, you often want a "Management Lane" and a "Data Lane." By attaching a second NIC, you can have one interface dedicated to SSH access for the DevOps team (Management) and another interface dedicated to serving web traffic to the public (Data). This ensures that even if the public lane is flooded with traffic, the management lane stays open.

## Lessons Learned
1. **VM State Requirements:** Learned that attaching or detaching network interfaces often requires the VM to be in a "Stopped (Deallocated)" state to update the hardware configuration.
2. **Network Isolation:** Multi-NIC setups allow a single VM to communicate across different virtual networks or subnets simultaneously.
3. **Resource Independence:** Just like Disks and Public IPs, NICs are standalone resources in Azure that can be moved between compatible VMs if needed.

---
*Created as part of the 50 Days of Azure Challenge.*
