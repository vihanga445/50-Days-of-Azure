# 50 Days of Azure - Day 8: Managing Persistent Storage

## Task Overview
As part of the Nautilus team's incremental migration, I managed storage scalability by attaching a pre-existing managed data disk to an active Linux Virtual Machine.

## Objective
Attach a managed disk named `xfusion-disk` to the `xfusion-vm` virtual machine in the `westus` region to expand available storage capacity.

## Technical Details
*   **VM Name:** `xfusion-vm`
*   **Disk Name:** `xfusion-disk`
*   **Disk Type:** Data Disk
*   **LUN Assignment:** 0 (Default)
*   **Region:** `westus`

## Real-World Scenario
In a production environment, you never want to store your data (like a database or a large dataset for machine learning) on the same drive as the Operating System. By using a separate Data Disk, you can delete or rebuild the VM without losing your actual data. It’s like keeping your files on a USB drive instead of just on your laptop's desktop.

## Lessons Learned
1. **Separation of Concerns:** Keeping data disks separate from OS disks enhances data portability and security.
2. **Regional Constraints:** For a disk to be attached to a VM, both resources MUST reside in the same Azure region (`westus`).
3. **LUN (Logical Unit Number):** Azure uses LUNs to identify different data disks attached to the same VM, allowing for multiple storage expansions on a single node.

---
*Created as part of the 50 Days of Azure Challenge.*
