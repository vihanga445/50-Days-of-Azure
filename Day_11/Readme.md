# 50 Days of Azure - Day 11: Vertical Scaling (Resizing a VM)

## Task Overview
To handle increased workload demands on the Nautilus infrastructure, I dynamically scaled an existing virtual machine up to a tier with higher compute capabilities.

## Objective
Change the hardware profile of `xfusion-vm` from a `Standard_B1s` tier to a `Standard_B2s` tier in the `eastus` region, ensuring zero data loss and verifying its active operational status post-migration.

## Technical Details
* **Target VM:** `xfusion-vm`
* **Original Size:** `Standard_B1s` (1 vCPU, 1 GiB RAM)
* **Target Size:** `Standard_B2s` (2 vCPUs, 4 GiB RAM)
* **Final Power State:** Running

## Real-World Scenario
Imagine your application is running out of memory because users are uploading larger datasets. Instead of setting up a whole new secondary server from scratch (Horizontal Scaling), you simply upgrade the hardware specifications of your current machine. Azure handles the physical relocation of your virtual server to a host blade with more RAM and CPU capabilities behind the scenes.

## Lessons Learned
1. **Vertical Scaling Impact:** Resizing a VM causes a brief period of downtime because the system must undergo a cold reboot to change hardware profiles.
2. **Resource Preservation:** Modifying the VM size preserves the OS disk, attached data disks, and internal configurations, making it a low-effort upgrade option for temporary traffic surges.
3. **B-Series Flexibility:** B-series burstable VMs are highly cost-effective options for workloads that remain idle most of the time but need full CPU performance during spikes.

---
*Created as part of the 50 Days of Azure Challenge.*
