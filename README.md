# Azure Private Endpoint Security for Storage and SQL Workloads

> Implemented Azure Private Endpoints to secure Azure Storage and Azure SQL Database by eliminating public internet exposure, enforcing private-only connectivity, and routing traffic through the Microsoft backbone network.

---

## Project Overview

Azure PaaS services such as Storage Accounts and SQL Databases are publicly accessible by default through internet-routable endpoints. While firewall rules can limit access, traffic still traverses public endpoints.

This project demonstrates how Azure Private Endpoints can be used to establish private connectivity between Azure resources and PaaS services. By assigning private IP addresses from a Virtual Network (VNet), service traffic remains entirely within Microsoft's private network, significantly reducing the attack surface and improving security.

---

## Architecture Diagram

> Replace with your PNG architecture diagram after uploading it to the repository.

```text
                          Azure Virtual Network
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Subnet: Private Endpoint Subnet                            │
│                                                             │
│  ┌──────────────┐          ┌──────────────┐                 │
│  │ Private EP   │          │ Private EP   │                 │
│  │  Storage     │          │    SQL DB    │                 │
│  └──────┬───────┘          └──────┬───────┘                 │
│         │                         │                         │
│         ▼                         ▼                         │
│  Azure Storage             Azure SQL Database              │
│                                                             │
│  ┌──────────────────────────────────────┐                  │
│  │          Virtual Machine             │                  │
│  │                                      │                  │
│  │ • Private DNS Resolution             │                  │
│  │ • Access via Private IP              │                  │
│  └──────────────────────────────────────┘                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Public Network Access: Disabled
External Access: Blocked
Private Connectivity: Enabled
```

---

## Objectives

- Create Private Endpoints for Azure Storage and Azure SQL Database
- Connect Private Endpoints to a dedicated subnet
- Configure Private DNS Zones for automatic name resolution
- Disable public network access on Azure PaaS services
- Enforce private-only connectivity
- Restrict external access to Storage and SQL services
- Strengthen network isolation and service security

---

## Technologies Used

- Microsoft Azure
- Azure Virtual Network (VNet)
- Azure Private Endpoints
- Azure Private Link
- Azure Storage Account
- Azure SQL Database
- Azure Private DNS Zones
- Azure Virtual Machine
- Azure Networking
- Cloud Security

---

## Solution Components

### Azure Storage Account

Configured a Private Endpoint to provide secure access through a private IP address within the VNet.

### Azure SQL Database

Integrated Azure SQL Database with a Private Endpoint to eliminate public connectivity.

### Private DNS Zones

Implemented Azure Private DNS Zones to automatically resolve Storage and SQL service FQDNs to private IP addresses.

### Virtual Machine

Used a VNet-connected VM as the trusted workload source for accessing Storage and SQL services over private networking.

---

## Implementation Steps

### 1. Created a Virtual Network Environment

- Configured networking resources
- Established dedicated subnet infrastructure
- Prepared environment for Private Endpoint deployment

### 2. Deployed Azure Storage and SQL Services

- Created Azure Storage Account
- Created Azure SQL Database
- Verified service availability

### 3. Implemented Azure Private Endpoints

- Provisioned Private Endpoint for Storage Account
- Provisioned Private Endpoint for SQL Database
- Associated both endpoints with the designated subnet

### 4. Configured Private DNS Integration

- Created required Private DNS Zones
- Linked DNS Zones to the Virtual Network
- Enabled automatic private name resolution

### 5. Enforced Private-Only Access

- Disabled public network access on Storage Account
- Disabled public network access on Azure SQL Database
- Restricted service exposure to private network paths only

---

## Security Architecture

### Before Implementation

```text
Internet
   │
   ├── Storage Account (Public Endpoint)
   │
   └── SQL Database (Public Endpoint)
```

### After Implementation

```text
Internet
   │
   └── Access Blocked

VNet
   │
   ├── Private Endpoint → Storage Account
   │
   └── Private Endpoint → SQL Database
```

---

## Key Security Controls

| Security Control | Implementation |
|------------------|---------------|
| Private Networking | Azure Private Endpoints |
| Service Isolation | Dedicated Private IP Addresses |
| Name Resolution | Azure Private DNS Zones |
| Public Exposure Reduction | Public Access Disabled |
| Secure Connectivity | Microsoft Backbone Network |
| Network Segmentation | VNet-Based Access Control |

---

## Technical Outcomes

✅ Implemented Private Endpoints for Azure Storage and Azure SQL Database

✅ Integrated Private DNS Zones for private hostname resolution

✅ Disabled public network access on both PaaS services

✅ Eliminated direct internet exposure to critical resources

✅ Enforced private-only access through VNet-integrated private IPs

✅ Reduced attack surface through network isolation

✅ Routed all service communication through Microsoft's private backbone network

✅ Secured two Azure PaaS services using Private Link architecture

---

## Key Skills Demonstrated

- Azure Networking
- Azure Private Endpoints
- Azure Private Link
- Cloud Security Architecture
- Network Isolation
- Private DNS Configuration
- Azure Storage Security
- Azure SQL Security
- Infrastructure Security
- Access Control Design
- Secure Network Architecture
- Azure Platform Services

---

## Project Outcome

Successfully implemented a secure Azure networking architecture that restricts Azure Storage and Azure SQL Database access to private network paths only. By combining Private Endpoints, Private DNS Zones, and disabled public connectivity, the solution reduced exposure to internet-based threats while providing secure and scalable access to critical PaaS services.

---

## My Role

**Azure Private Endpoint Engineer (Self-Directed Project)**

- Designed and implemented the end-to-end Private Endpoint architecture
- Configured Private Endpoints for Azure Storage and Azure SQL Database
- Integrated Private DNS Zones with the Virtual Network
- Disabled public network access on PaaS resources
- Enforced private-only connectivity requirements
- Documented architecture, implementation steps, and security outcomes

---

## Repository Structure

```text
azure-private-endpoints-storage-sql-security/
│
├── README.md
├── architecture/
│   └── private-endpoint-architecture.png
│
├── screenshots/
│   ├── storage-private-endpoint.png
│   ├── sql-private-endpoint.png
│   ├── private-dns-zone.png
│   ├── public-access-disabled-storage.png
│   └── public-access-disabled-sql.png
│
└── documentation/
    └── implementation-notes.md
```
---
**Author:** Mubarak Mohamed  
**Role:** Azure Network Security Engineer (Self-Directed Project)
