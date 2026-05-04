# 50 Days of Azure - Day 1: Secure Access with SSH Keys

## Task Overview
The Nautilus DevOps team is migrating infrastructure to Azure. To ensure secure communication with future Linux Virtual Machines, the first step is to establish a secure authentication method using SSH key pairs.

## Objective
Create a standardized RSA SSH key pair named `devops-kp` within the Azure environment to replace password-based logins.

## Technical Details
*   **Service:** Azure SSH Keys
*   **Key Name:** `devops-kp`
*   **Encryption Type:** RSA 2048-bit
*   **Deployment Method:** Azure Portal

## Real-World Scenario
Imagine you are building a secure vault. Instead of using a combination code (password) that someone could overhear or guess, you install a high-tech biometric lock. The **Public Key** is the lock installed on the vault, and the **Private Key** is your unique fingerprint. Without that specific fingerprint, the vault stays locked.

## Lessons Learned
1. **One-Time Download:** The private key (`.pem` file) is only available for download at the moment of creation. If lost, it cannot be recovered from Azure.
2. **Security over Convenience:** SSH keys are significantly more resistant to brute-force attacks compared to traditional passwords.
3. **Naming Conventions:** Using consistent naming like `devops-kp` helps teams identify which keys belong to specific environments (Dev, Ops, Prod).

---
*Created as part of the 50 Days of Azure Challenge.*
