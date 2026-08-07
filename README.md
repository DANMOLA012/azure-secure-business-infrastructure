# azure-secure-business-infrastructure
Designed and implemented a secure Microsoft Azure Windows Server environment with role-based access control, least privilege, NTFS permissions, security auditing and access validation for a small-business use case.

# Secure Azure Business Infrastructure

## Project Overview

This project involved designing and implementing a secure cloud-hosted Windows Server environment in Microsoft Azure for a small-business use case.

The business required a centralised environment where authorised users could access operational information while ensuring that sensitive resources such as Finance, HR, Inventory and Sales were restricted according to staff responsibilities.

I implemented individual user accounts, role-based security groups, NTFS permissions and Windows security auditing to provide controlled access and improve accountability.

The environment was then tested using different user accounts to verify that authorised access was permitted, unauthorised access was denied, and relevant file-access activity could be identified through Windows Security logs.

This project focuses on the infrastructure and security controls required to support secure business operations. It is not intended to function as a complete fraud-prevention or business transaction monitoring system.

****

## Project Scenario

TruGlamor is a small business operating in Lagos, Nigeria, with management requiring the ability to oversee business resources remotely.

The environment needed to support different responsibilities across the business while reducing unnecessary access to sensitive information.

Three primary business roles were considered:

- **Owner** – broader access to business resources and management information.
- **Manager** – operational access based on management responsibilities.
- **Bookkeeper** – access to financial and other resources required for bookkeeping responsibilities.

NOVIX was responsible for infrastructure administration and security configuration.

---

## Technologies Used

- Microsoft Azure
- Windows Server 2025 Datacenter
- Azure Virtual Machines
- Windows Local Users and Groups
- Role-Based Access Control (RBAC)
- NTFS Permissions
- Windows Security Auditing
- Windows Event Viewer
- Remote Desktop Protocol (RDP)


---

## Solution Architecture

The solution uses a Microsoft Azure-hosted Windows Server as the central environment for business resources.

Individual user accounts are assigned to security groups based on job responsibilities. NTFS permissions are then applied to business folders to control which roles can access sensitive information.

Windows security auditing provides an additional layer of accountability by recording selected security and file-access activity for investigation.

![Solution Architecture](architecture/truglamor-azure-architecture.png)

### Security Design Principles

The implementation was based on the following principles:

- **Individual accountability** – each user has a separate account rather than using shared credentials.
- **Least privilege** – users receive only the access required for their responsibilities.
- **Role-based access** – permissions are assigned through security groups rather than directly to individual users where possible.
- **Separation of responsibilities** – business roles have different levels of access to Finance, HR, Inventory, Sales and other resources.
- **Auditing** – security events and selected file-access activity are logged to support investigation.
- **Administrative separation** – NOVIX manages the infrastructure but is not assigned to normal TruGlamor business-role groups.


---

## Technical Implementation

### 1. Azure Infrastructure

I deployed a Windows Server 2025 Datacenter virtual machine in Microsoft Azure to provide the central environment for the project.

The server was configured as:

- **Hostname:** TG-LAGOS-SRV01
- **Cloud Platform:** Microsoft Azure
- **Operating System:** Windows Server 2025 Datacenter
- **Region:** Central US
- **Remote Administration:** Remote Desktop Protocol (RDP)

The Azure VM provided the underlying infrastructure for user management, access control, business file storage and security auditing.

### 2. User Accounts

Separate Windows accounts were created so that activity could be associated with individual users rather than relying on shared credentials.

The main accounts used during the implementation were:

| Account | Role |
|---|---|
| `tg.owner` | Business Owner |
| `tg.manager` | Branch Manager |
| `tg.bookkeeper` | Bookkeeper |
| `novix.admin` | Infrastructure Administration |

### 3. Security Groups

Instead of assigning permissions individually to every user, I created security groups representing the different responsibilities within the environment.

These included:

- `TG-Owners`
- `TG-Managers`
- `TG-Bookkeepers`
- `NOVIX-Admins`

Users were assigned to the appropriate group based on their role.

This approach makes permission management easier to maintain and allows additional users to be added to a role without redesigning the folder permissions.

### 4. Business Folder Structure

A central business workspace was created under:

`C:\Business`

The workspace was divided into separate areas for:

- Applications
- Finance
- HR
- Inventory
- Policies
- Reports
- Sales
- Shared

Separating the information into different folders allowed permissions to be applied according to business responsibility.

### 5. Role-Based Access Control

NTFS permissions were configured on the business folders to enforce least-privilege access.

For example:

- The **Owner** received broader access to business information.
- The **Bookkeeper** received access to financial resources required for the role.
- The **Manager** received access to operational resources while access to sensitive Finance information was restricted.
- **NOVIX administration** was separated from normal business-role group membership.

Permissions were assigned primarily through security groups rather than directly to individual user accounts.

This made the access-control model easier to understand, test and maintain.
