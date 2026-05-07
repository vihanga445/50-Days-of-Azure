# 50 Days of Azure - Day 4: Building the Network Foundation (VNet)

## Task Overview
The Nautilus DevOps team is moving toward a segmented migration strategy. To support this, I provisioned the primary network infrastructure that will house future cloud resources.

## Objective
Create a Virtual Network (VNet) named `xfusion-vnet` in the `westus` region to establish a private, isolated network environment.

## Technical Details
* **VNet Name:** `xfusion-vnet`
* **Region:** `westus`
* **Address Space:** `10.0.0.0/16` (IPv4 CIDR)
* **Default Subnet:** `10.0.0.0/24`

## Real-World Scenario
Think of a VNet as the foundation and utility lines of a new office building. Before you move in the furniture (VMs) or hire the staff (Applications), you must define the boundaries of the property and ensure the internal communication lines (IP addresses) are mapped out.

## Lessons Learned
1. **Regional Strategy:** Choosing the right region (`westus`) is critical for reducing latency for users located on the West Coast and for complying with data residency requirements.
2. **CIDR Blocks:** Learned how CIDR notation defines the number of available IP addresses. A `/16` block provides 65,536 addresses, offering massive scalability for the Nautilus team.
3. **Isolation:** VNets provide a trust boundary. By default, resources in different VNets cannot communicate unless explicitly connected via Peering or VPNs.

---
*Created as part of the 50 Days of Azure Challenge.*
