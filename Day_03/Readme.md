```markdown
# 50 Days of Azure – Day 3: Creating a Linux VM Using Azure CLI

## Task Overview
Continuing the Nautilus DevOps migration journey, today’s focus was on provisioning compute resources entirely through the Azure CLI. Since the team does not have access to the Azure Portal, all operations were executed from the `azure-client` landing host.

The goal was to deploy a Linux Virtual Machine with specific compute, storage, and authentication requirements.

---

## Objective
Provision a Virtual Machine named **datacenter-vm** using Azure CLI with the following specifications:

- Image: Ubuntu 22.04 LTS (Ubuntu2204)
- Size: Standard_B2s
- Admin Username: azureuser
- Authentication: Auto-generated SSH keys
- OS Disk: 30GB, Standard_LRS
- State: VM must be running after creation

---

## Technical Details

| Component | Value |
|----------|--------|
| VM Name | datacenter-vm |
| Resource Group | kml_rg_main-9b82dd443c514286 |
| Region | eastus |
| Image | Ubuntu 22.04 LTS |
| Size | Standard_B2s |
| OS Disk | 30GB Standard_LRS |
| Authentication | SSH Key (auto-generated) |
| Public IP | Assigned automatically |

---

## Implementation Steps

### 1. Identify the Resource Group
The lab environment already contains a pre-created resource group. To fetch it:

```bash
az group list --query "[0].name" -o tsv
```

---

### 2. Create the Virtual Machine
This command provisions the VM exactly as required:

```bash
az vm create \
  --resource-group kml_rg_main-9b82dd443c514286 \
  --name datacenter-vm \
  --image Ubuntu2204 \
  --size Standard_B2s \
  --admin-username azureuser \
  --generate-ssh-keys \
  --storage-sku Standard_LRS \
  --os-disk-size-gb 30
```

Expected output includes:

- Public IP  
- Private IP  
- VM running state  
- SSH key generation path  

---

### 3. Verify VM Power State
Ensure the VM is running:

```bash
az vm get-instance-view \
  --resource-group kml_rg_main-9b82dd443c514286 \
  --name datacenter-vm \
  --query "instanceView.statuses[?starts_with(code, 'PowerState/')]" \
  -o table
```

Expected:

```
PowerState/running
```

---

### 4. (Optional) SSH into the VM

```bash
ssh -i ~/.ssh/id_rsa azureuser@<public-ip>
```

Example:

```bash
ssh -i ~/.ssh/id_rsa azureuser@104.211.60.102
```

---

## Troubleshooting & Logic

### Resource Group Discovery
Azure labs often include pre-created resource groups. Identifying the correct one ensures deployments succeed without conflicts.

### SSH Key Handling
Using `--generate-ssh-keys` is ideal for ephemeral lab environments where persistent key storage is not guaranteed.

### Disk & SKU Configuration
Explicitly specifying:

- `--os-disk-size-gb 30`
- `--storage-sku Standard_LRS`

ensures predictable performance and cost behavior.

### CLI-Only Deployment
Working without the Azure Portal reinforces understanding of:

- VM provisioning flow  
- Resource dependencies  
- Azure CLI syntax  

---

## Lessons Learned

### 1. CLI-Driven Deployments Are Precise
The CLI forces explicit configuration, improving clarity and reproducibility.

### 2. Resource Group Awareness Matters
Deploying into the wrong RG can break validation scripts in lab environments.

### 3. SSH Key Management in Labs
Auto-generated keys are perfect for temporary environments, but production should use centrally managed keys.

### 4. Storage SKU Selection
Choosing Standard_LRS is a cost-efficient option for general workloads that don’t require high IOPS.

---

## Summary
Today’s task reinforced the importance of mastering Azure CLI for real-world DevOps workflows. The VM was successfully deployed, configured, and validated entirely through command-line operations — a critical skill for automation-driven cloud environments.
```
