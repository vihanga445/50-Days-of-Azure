# 50 Days of Azure - Day 10: Mapping Public IPs to Network Interfaces

## Task Overview
To finalize external connectivity for the Nautilus migration project, I mapped an existing static Public IP address directly to the primary Network Interface Card (NIC) of a deployed Virtual Machine.

## Objective
Associate the pre-existing Public IP resource `datacenter-pip` to the NIC belonging to `datacenter-vm-pip` to expose the instance securely to external traffic.

## Technical Details
* **Target VM:** `datacenter-vm-pip`
* **Public IP Name:** `datacenter-pip`
* **Binding Target:** NIC IP Configuration (`ipconfig1`)
* **Status:** Successfully Associated

## Real-World Scenario
When you plug an internet cable into a physical server, the internet provider gives that network card a public route. In the cloud, we do this logically. By linking the `datacenter-pip` to the VM's network card rather than the VM itself, Azure allows us to easily detach this public identity and move it to a backup server if the main one ever crashes, preventing downtime.

## Lessons Learned
1. **Indirect Binding:** Learned that Azure architecture decouples public identities from compute hosts, routing all external traffic explicitly through Network Interfaces.
2. **IP Configuration Management:** Modifying `ipconfig1` configurations highlights how a single NIC can hold multiple IP profiles (both private internal IPs and public external IPs simultaneously).
3. **Dynamic Routing Updates:** Witnessed how Azure updates software-defined routing tables immediately upon saving network modifications without requiring an OS-level reboot.

---
*Created as part of the 50 Days of Azure Challenge.*
