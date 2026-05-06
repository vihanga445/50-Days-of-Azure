# 50 Days of Azure - Day 2: Deploying a Linux Virtual Machine

## Task Overview
The Nautilus DevOps team is migrating infrastructure incrementally. I deployed a lightweight Ubuntu 24.04 LTS node to serve as a foundational environment for future service migrations.

## Objective
Deploy an Ubuntu 24.04 LTS Virtual Machine named `xfusion-vm` in the `eastus` region with specific disk and network configurations.

## Technical Details
*   **VM Name:** `xfusion-vm`
*   **Region:** `eastus`
*   **Image:** Ubuntu 24.04 LTS
*   **Size:** `Standard_B1s`
*   **Storage:** 30 GB Standard HDD
*   **Security:** NSG allowing Inbound Port 22 (SSH)
*   **Auth Method:** SSH Public Key (`devops-kp`)

## Troubleshooting & Logic
During deployment, I encountered a common Azure Portal hurdle: SSH Key visibility. In Azure, for a "Stored Key" to be selectable, it must reside in the same **Region** and **Resource Group** as the VM. To ensure a smooth deployment in this ephemeral lab environment, I utilized the **"Generate new key pair"** feature during the VM creation workflow, ensuring the key resource was perfectly scoped to the new VM.

## Lessons Learned
1. **Scope Alignment:** Cloud resources often have regional dependencies. A key created in one region may not be visible to a VM in another.
2. **Ephemeral Labs:** Resources are session-based. Always ensure your dependencies (keys, VNETs) are active in the current session.
3. **Storage Tiering:** Selecting `Standard HDD` over `Premium SSD` is a crucial cost-saving measure for development/test environments that don't require high IOPS.

---
