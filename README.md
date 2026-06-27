# Enterprise Windows Administration Lab (Azure)

## Overview

This project demonstrates the deployment and administration of a Windows Server 2022 Domain Controller in Microsoft Azure. The lab simulates an enterprise Active Directory environment by configuring Active Directory Domain Services (AD DS), DNS, DHCP, Organizational Units (OUs), Security Groups, and Group Policy Objects (GPOs).

The objective was to gain hands-on experience with Windows Server administration, identity management, and enterprise security policies commonly used by system administrators and cybersecurity professionals.

---

## Technologies Used

- Microsoft Azure
- Windows Server 2022 Datacenter
- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server
- Group Policy Management
- Active Directory Users and Computers (ADUC)

---

## Lab Architecture

The environment consists of a single Windows Server 2022 Azure Virtual Machine configured as the Domain Controller for the `corp.local` domain.

![Azure VM](images/vm.png)

---

# 1. Azure Virtual Machine Deployment

A Windows Server 2022 virtual machine was deployed in Microsoft Azure to host the enterprise environment.

**Configuration**

- Windows Server 2022 Datacenter
- Azure Virtual Machine
- East US Region
- Domain Controller
- Private IP: 10.0.0.4

![VM Deployment](images/vm.png)

---

# 2. Active Directory Domain Services

The Active Directory Domain Services role was installed and the server was promoted to a Domain Controller.

The new Active Directory forest:

```
corp.local
```

was created to centrally manage users, computers, and security policies.

### Installed Server Roles

- Active Directory Domain Services
- DNS Server
- DHCP Server

![Server Roles](images/server_roles.png)

---

# 3. Domain Creation

After promoting the server, the new Active Directory domain was successfully created.

![Domain](images/domain.png)

---

# 4. DNS Configuration

Active Directory automatically configured an integrated DNS zone.

The Forward Lookup Zone contains:

- corp.local
- Host (A) records
- Name Server (NS)
- Start of Authority (SOA)

allowing computers to locate domain resources by name instead of IP addresses.

![DNS Manager](images/dns.png)

---

# 5. Organizational Units (OUs)

To organize users by department, multiple Organizational Units were created.

```
IT
HR
Finance
Sales
Servers
Workstations
Groups
```

![Organizational Units](images/organizational_units.png)

---

## IT Department

![IT OU](images/IT_organizational_unit.png)

---

## HR Department

![HR OU](images/HR_organizational_unit.png)

---

## Finance Department

![Finance OU](images/Finance_organizational_unit.png)

---

## Sales Department

![Sales OU](images/Sales_organziational_unit.png)

---

# 6. User Management

Users were created inside their appropriate Organizational Units.

Example users include:

| Department | Users |
|------------|----------------|
| IT | Marie Leopold-Hooke |
| HR | Sarah Williams, John Brown |
| Finance | Michael Lee, Emily Davis |
| Sales | David Garcia, Olivia Martinez |

---

# 7. Security Groups

Department-specific security groups were created to simplify permission management.

```
IT_Admins
HR_Users
Finance_Users
Sales_Users
```

![Security Groups](images/groups_organizational_units.png)

---

# 8. Group Membership

Users were assigned to the correct department security groups.

Example:

- Marie Leopold-Hooke
    - Domain Users
    - IT_Admins

![Adding Users to Groups](images/adding_users_to_groups.png)

---

# 9. Group Policy Objects (GPO)

A custom Group Policy Object named **Corporate Password Policy** was created and linked to the domain.

The policy enforces stronger authentication requirements across all domain users.

![GPO](images/Password_GPO.png)

---

## Password Policy

Configured settings include:

- Password Complexity Enabled
- Minimum Password Length: 12 characters
- Maximum Password Age: 90 days
- Password History: 10 passwords remembered

![Password Settings](images/password_settings.png)

---

## Account Lockout Policy

Additional security was implemented through account lockout settings.

Configuration:

- Lockout Threshold: 5 failed attempts
- Lockout Duration: 15 minutes
- Counter Reset: 15 minutes

![Account Lockout](images/account_lockout_policy.png)

---

## GPO Verification

The Group Policy Object was successfully linked to the domain and configured to apply to authenticated users.

![Verify GPO](images/verify_GPO.png)

---

# Skills Demonstrated

- Windows Server Administration
- Microsoft Azure
- Active Directory
- Domain Controller Deployment
- DNS Administration
- DHCP Configuration
- Organizational Unit Design
- User & Group Management
- Group Policy Management
- Identity and Access Management (IAM)
- Enterprise Windows Administration

---

# Key Takeaways

This lab provided practical experience deploying and administering a Windows Server environment in Azure. It demonstrates foundational enterprise administration skills including Active Directory deployment, DNS configuration, user lifecycle management, security group implementation, and Group Policy enforcement.

These are core technologies used by Windows System Administrators, Identity Engineers, and Blue Team cybersecurity professionals.
