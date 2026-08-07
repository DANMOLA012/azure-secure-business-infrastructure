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
