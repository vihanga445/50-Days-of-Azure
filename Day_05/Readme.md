# 50 Days of Azure - Day 5: Targeted Network Segmentation

## Task Overview
The Nautilus DevOps team is continuing their incremental migration. This task involved setting up a specific network environment to host isolated services within the `eastus` region.

## Objective
Provision a Virtual Network (VNet) named `xfusion-vnet` with a specific CIDR block (`192.168.0.0/24`) to define a dedicated IP address space.

## Technical Details
*   **VNet Name:** `xfusion-vnet`
*   **Region:** `eastus`
*   **Address Space:** `192.168.0.0/24`
*   **Total Available IPs:** 251 (256 total minus 5 Azure-reserved addresses)

## Real-World Scenario
A `/24` network is similar to a small office floor. It provides enough room for about 250 devices. By using the `192.168.x.x` range (a common private IP standard), we are creating a network that feels familiar to on-premises engineers while maintaining full cloud scalability.

## Lessons Learned
1. **CIDR Precision:** Choosing `/24` instead of a larger `/16` range prevents "IP waste" if the team only plans to host a small cluster of servers in this specific segment.
2. **Azure Reserved IPs:** In any VNet subnet, Azure reserves 5 IP addresses (first four and the last one) for networking overhead (DHCP, DNS, Gateway).
3. **Regional Isolation:** Resources within this `eastus` VNet are logically isolated from other regions, requiring VNet Peering if communication with `westus` resources is needed later.

---
*Created as part of the 50 Days of Azure Challenge.*
