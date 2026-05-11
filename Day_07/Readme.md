# 50 Days of Azure - Day 7: External Connectivity (Public IP)

## Task Overview
As part of the incremental migration, the Nautilus DevOps team required a method for external resources to access the cloud environment. I provisioned a static Public IP address to serve as a gateway for future services.

## Objective
Allocate a Static Public IP address named `datacenter-pip` to provide a consistent entry point from the internet to the Azure infrastructure.

## Technical Details
* **IP Name:** `datacenter-pip`
* **SKU:** Standard
* **Assignment:** Static
* **IP Version:** IPv4

## Real-World Scenario
Imagine you are setting up a storefront. The VNet is the inside of your shop, but the Public IP is the **Street Address** on the front door. Without this address, customers (users) can't find your business. By making it "Static," we ensure that the address never changes, so our customers always know where to go.

## Lessons Learned
1. **Static vs. Dynamic:** A Static IP remains assigned to the resource even when stopped, which is vital for DNS records and firewall allow-lists.
2. **SKU Selection:** Azure Standard SKUs offer better security by being "closed by default," meaning you must explicitly allow traffic via a Network Security Group (NSG).
3. **Decoupled Resources:** In Azure, an IP address is a standalone resource. It can be created now and attached to a Virtual Machine or Load Balancer later.

---
*Created as part of the 50 Days of Azure Challenge.*
