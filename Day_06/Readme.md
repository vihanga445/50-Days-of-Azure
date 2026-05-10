# 50 Days of Azure - Day 6: Advanced Network Segmentation

## Task Overview
The Nautilus DevOps team is refining their cloud footprint by implementing structured networking. This task involved creating a primary Virtual Network (VNet) and a specific Subnet to host future workloads.

## Objective
Provision a VNet named `nautilus-vnet` in the `eastus` region with a `10.0.0.0/16` address space and a dedicated subnet named `nautilus-subnet`.

## Technical Details
* **VNet Name:** `nautilus-vnet`
* **Subnet Name:** `nautilus-subnet`
* **Region:** `eastus`
* **VNet Address Space:** `10.0.0.0/16` (65,536 total IPs)
* **Subnet Address Range:** `10.0.0.0/24` (256 total IPs)

## Real-World Scenario
Think of the VNet (`10.0.0.0/16`) as a large corporate campus. The Subnet (`10.0.0.0/24`) is a specific building on that campus. By dividing the network this way, the DevOps team can apply different security rules (Network Security Groups) to the "Building" (Subnet) without affecting the rest of the "Campus" (VNet).

## Lessons Learned
1. **Hierarchical Networking:** Learned how to nest a `/24` subnet inside a `/16` virtual network.
2. **Address Planning:** A `/16` space is vast, allowing the Nautilus team to create up to 256 different `/24` subnets in the future as the migration scales.
3. **Implicit Dependencies:** In Azure, you cannot create a subnet without a parent VNet, highlighting the "Container" relationship between these two resources.
