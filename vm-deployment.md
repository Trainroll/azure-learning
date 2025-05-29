# Lab - Create a Virtual Machine in Azure

## 📅 Date
May 26, 2025

## 🎯 Objective
To deploy a basic virtual machine (VM) in Microsoft Azure using the Azure Portal.

## 🔧 Tools & Requirements
- Azure Portal: https://portal.azure.com
- Azure Subscription free 
- Basic knowledge of VM concepts

## 📌 Steps

### 1. Log in to Azure
- Go to [Azure Portal](https://portal.azure.com)
- Sign in with your Azure account
- Active standbox from Microsofit learning (https://learn.microsoft.com/en-us/training/modules/intro-to-azure-virtual-machines/3-create-a-vm?source=learn)

  Use the Learning Subscription and Resource Group
  
### 2. Create the Virtual Machine from the portal 
- Search for "Virtual Machines"
- Click **+ Create > Azure virtual machine**
- Fill out the **Basics** tab:
  - Subscription: Concierge Subscription
  - Resource Group: `learn-fc5a5d11-ca18-4e7c-ac85-f26c41d49b70`
  - Virtual machine name: `MyLabVM`
  - Region: US (West US) 
  - Image: Ubuntu Server 24.04 LTS - x64 Gen2
  - Size: Standard_D2s_v3 - 2 vcpus, 8 GiB memory ($85.41/month)
  - Authentication type: Password
  - Username: `Learning2_3`
  - Password: YourSecuredevice1234!
    
### 3. Configure Inbound Port Rules
- Allow selected ports:
  - Check **SSH (22)**
  - Check **HTTPS (443)**

### 4. Click **Review + Create**
- Review your settings
- Click **Create**

### 6. Access the VM
- Once deployment is complete, go to the VM overview
- Copy the **public IP address**
- Use RDP
- IP 52.225.21.234
- Username : Learning2_3
- Password : YourSecuredevice1234!


** Method 2 **
    Using Poweshell CLI
    -# Set variables
RESOURCE_GROUP="myResourceGroup"
LOCATION="westUS"
VM_NAME="MylabVM"
IMAGE="Ubuntu2024"
ADMIN_USERNAME="Learning2_3"
ADMIN_PASSWORD="YourSecuredevice1234!"

# Create the virtual machine
az vm create \
  --resource-group $RESOURCE_GROUP \
  --name $VM_NAME \
  --image $IMAGE \
  --admin-username $ADMIN_USERNAME \
  --admin-password $ADMIN_PASSWORD \
  --authentication-type password \
  --size Standard_B1s \
  --output json

# Open port 22 for SSH
az vm open-port --port 22 --resource-group $RESOURCE_GROUP --name $VM_NAME

