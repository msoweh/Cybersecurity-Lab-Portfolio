# Lab 7 – Core Network Services: DNS & DHCP Deployment

## Real-World Scenario

Marctech has expanded from a small office into a multi-department organization with more than 250 employees.

The IT department needs to replace manual network configuration with centralized network services to improve scalability, reduce administrative effort, and ensure workstations automatically receive the correct network configuration.

The Systems Administrator was tasked with deploying **Windows DHCP integrated with Active Directory and DNS** so newly deployed computers could automatically obtain IP addresses, locate Domain Controllers, authenticate users, and access organizational resources.

This lab focused on deploying and validating core network services that support the Marctech Identity and Access Management environment.

---

## Business Objective

The objective of this lab was to deploy and validate **Windows DHCP integrated with Active Directory and DNS**.

The implementation needed to:

* Install and authorize the DHCP Server role
* Create and configure a DHCP scope
* Configure DHCP Scope Options
* Create DHCP Reservations for business-critical devices
* Validate automatic IP address assignment
* Verify DNS resolution
* Verify Active Directory authentication
* Validate Domain Controller connectivity
* Document deployment and troubleshooting procedures

---

# Lab Environment

| Component         | Configuration                     |
| ----------------- | --------------------------------- |
| Domain Controller | DC01                              |
| Domain            | `marctech.local`                  |
| Server OS         | Windows Server 2025 Evaluation    |
| Client            | PC01                              |
| Client OS         | Windows 11 Pro                    |
| DHCP Scope        | `Marctech-Lab`                    |
| Network           | `192.168.50.0/24`                 |
| DHCP Range        | `192.168.50.100 – 192.168.50.150` |
| DNS Server        | DC01 – `192.168.1.12`             |
| Default Gateway   | `192.168.50.1`                    |
| Virtualization    | Oracle VirtualBox                 |

---

# Implementation

## Phase 1 – Network Verification

### Objective

Before deploying DHCP, the existing Active Directory and DNS infrastructure was verified to ensure the environment was functioning correctly.

### Tasks Performed

The following were verified:

* DNS configuration
* Domain Controller communication
* Domain authentication
* DNS name resolution
* Communication between DC01 and PC01
* Active Directory logon

### Validation

The environment successfully demonstrated:

```text
DNS Resolution
       ↓
Domain Controller Connectivity
       ↓
Active Directory Authentication
       ↓
Domain Logon
```

This established a functioning identity and DNS foundation before DHCP deployment.

---

## Phase 2 – DHCP Server Installation and Authorization

### Objective

Install and authorize the Windows DHCP Server role and integrate it with the existing Active Directory environment.

### Tasks Performed

The DHCP Server role was installed using Server Manager.

The required DHCP management tools were also installed.

DHCP Post-Installation Configuration was completed, including authorization of the DHCP server within Active Directory.

The DHCP service was then verified.

### Validation

The following were confirmed:

* DHCP Server role installed successfully
* DHCP Server authorized in Active Directory
* DHCP Server service running
* DHCP service configured for automatic startup

The resulting architecture was:

```text
Active Directory
       │
       ├── DNS
       │
       └── DHCP
             │
             ↓
           PC01
```

---

## Phase 3 – DHCP Scope Configuration

### Objective

Create a centralized DHCP scope for Marctech employee workstations.

### Scope Configuration

| Setting        | Configuration                            |
| -------------- | ---------------------------------------- |
| Scope Name     | `Marctech-Lab`                           |
| Description    | Corporate DHCP Scope for Marctech Office |
| Start IP       | `192.168.50.100`                         |
| End IP         | `192.168.50.150`                         |
| Subnet Mask    | `255.255.255.0`                          |
| Lease Duration | 8 Days                                   |

The configured address pool provides a controlled range of addresses that DHCP can automatically assign to client devices.

### DHCP Scope Options

The following DHCP options were configured:

| Option | Purpose                  | Configuration         |
| ------ | ------------------------ | --------------------- |
| 003    | Router / Default Gateway | `192.168.50.1`        |
| 006    | DNS Server               | `192.168.1.12 – DC01` |
| 015    | DNS Domain Name          | `marctech.local`      |

These options allow DHCP to provide clients with the network information required to communicate with the Marctech environment.

### Validation

The following were verified:

* DHCP scope created successfully
* DHCP scope activated
* Scope Options configured
* DHCP address pool available

---

## Phase 4 – DHCP Reservation

### Objective

Configure a DHCP Reservation for a business-critical device so that the device consistently receives the same IP address.

### Reservation Configuration

| Setting            | Configuration           |
| ------------------ | ----------------------- |
| Reservation Name   | `IT-Test-PC01`          |
| Reserved IP        | `192.168.50.110`        |
| Reservation Method | MAC Address Reservation |

The reservation associates the device's MAC address with a specific IP address.

### Why DHCP Reservations Matter

Reservations are useful for devices that benefit from predictable addressing while still being centrally managed through DHCP.

Examples include:

* Network printers
* File servers
* Security cameras
* Network scanners
* VoIP phones
* Infrastructure devices

Instead of manually configuring a static IP on the device, DHCP can consistently provide the designated address.

The process is:

```text
Device MAC Address
        ↓
DHCP Reservation
        ↓
Reserved IP Address
        ↓
Device receives same IP
```

### Validation

The reservation was verified by confirming:

* The reservation was visible under DHCP Reservations
* The reservation was associated with the device MAC address
* DHCP was configured to assign the reserved IP

---

## Phase 5 – DHCP Client Validation

### Objective

Validate that PC01 could obtain network configuration from DHCP and continue communicating with the Marctech Active Directory environment.

### Client Testing

The following commands were executed on PC01:

```cmd
ipconfig /release
ipconfig /renew
ipconfig /all
```

The resulting configuration was reviewed to verify:

* IP address assignment
* Default Gateway
* DNS Server
* DNS Domain

The client successfully received network configuration from the DHCP scope.

---

## DNS Resolution Validation

The following command was used:

```cmd
nslookup dc01.marctech.local
```

The command successfully returned the Domain Controller's IP address.

This confirmed that PC01 could resolve the Domain Controller using DNS.

The validation path was:

```text
PC01
  ↓
DNS Query
  ↓
DC01 DNS
  ↓
dc01.marctech.local
  ↓
Correct IP Address
```

---

## Active Directory Authentication Validation

The following command was used:

```cmd
echo %LOGONSERVER%
```

The command returned:

```text
\\DC01
```

This confirmed that the logged-on user was authenticating against the Marctech Domain Controller.

The combined validation demonstrated:

```text
DHCP
  ↓
IP Configuration
  ↓
DNS Resolution
  ↓
Domain Controller Discovery
  ↓
Active Directory Authentication
```

---

# Security Relevance

DHCP and DNS are not simply networking services. They are important supporting components of an enterprise identity infrastructure.

Active Directory environments rely heavily on DNS for locating domain services and Domain Controllers.

Incorrect DNS configuration can result in:

* Domain authentication failures
* Inability to locate Domain Controllers
* Group Policy processing problems
* Access to domain resources failing
* Problems joining computers to the domain

DHCP provides centralized control over client network configuration, reducing the risk of inconsistent manual configurations.

The lab demonstrated the relationship between:

```text
Network Configuration
        ↓
DNS
        ↓
Domain Controller Discovery
        ↓
Authentication
        ↓
Access to Organizational Resources
```

This reinforces an important cybersecurity concept:

> **Identity security depends on the underlying network infrastructure being correctly configured.**

---

# Troubleshooting

## Issue 1 – Domain Authentication Failure

### Problem

PC01 initially failed to authenticate to the Marctech domain.

### Cause

The client had incorrect DNS configuration after network changes.

### Resolution

The client's DNS configuration was updated to point to the Domain Controller.

DNS resolution was then verified using:

```cmd
nslookup dc01.marctech.local
```

After DNS was corrected, domain communication and authentication were successfully restored.

### Lesson Learned

In an Active Directory environment, DNS configuration is critical to Domain Controller discovery and domain authentication.

---

## Issue 2 – Intermittent Wi-Fi Connectivity

### Problem

Intermittent wireless connectivity prevented reliable communication between PC01 and DC01.

### Cause

A wireless adapter configuration issue affected network connectivity.

### Resolution

The wireless adapter configuration was corrected and network connectivity was restored.

Connectivity to DC01 was then validated.

### Lesson Learned

Network connectivity must be stable before troubleshooting higher-level services such as DNS, DHCP, and Active Directory authentication.

---

## Issue 3 – Shared Folder Access

### Problem

Access to shared folders was initially unsuccessful.

### Cause

NTFS permissions were not correctly configured for the user accessing the resource.

### Resolution

The following were reviewed:

* Active Directory security groups
* Share permissions
* NTFS permissions

The permissions were corrected and access was successfully validated using a domain user account.

### Lesson Learned

Network connectivity and authentication do not automatically grant access to resources.

Authorization is separately controlled through permissions and security groups.

---

# Production Rollout Considerations

A production DHCP deployment would follow a controlled implementation process:

1. Install DHCP Server
2. Authorize DHCP within Active Directory
3. Create DHCP Scope
4. Configure Scope Options
5. Configure DHCP Reservations
6. Activate DHCP Scope
7. Disable the legacy DHCP service only after validation
8. Renew client DHCP leases
9. Validate IP assignment
10. Verify Active Directory authentication
11. Monitor DHCP leases
12. Monitor DHCP logs

This staged approach reduces the risk of introducing conflicting DHCP services or disrupting existing client connectivity.

---

# Troubleshooting Methodology

The lab reinforced a layered troubleshooting approach.

When a domain client cannot authenticate or access resources, troubleshooting should proceed logically:

```text
1. Physical / Wireless Connectivity
             ↓
2. IP Configuration
             ↓
3. DHCP
             ↓
4. DNS Resolution
             ↓
5. Domain Controller Connectivity
             ↓
6. Authentication
             ↓
7. Authorization
             ↓
8. Resource Access
```

This prevents administrators from troubleshooting higher-level services before confirming that the underlying network services are functioning.

---

# Skills Demonstrated

* Windows Server Administration
* DHCP Server deployment
* DHCP authorization
* Active Directory integration
* DNS configuration
* DHCP Scope design
* DHCP Scope Options
* DHCP Reservations
* IP address management
* Network troubleshooting
* DNS troubleshooting
* Active Directory authentication
* Client configuration validation
* Network service documentation
* Enterprise network administration
* Access troubleshooting

---

# Lessons Learned

### DHCP Centralizes IP Management

DHCP eliminates the need to manually configure network settings on every workstation.

### Active Directory Depends on DNS

Correct DNS configuration is essential for Domain Controller discovery and Active Directory authentication.

### Scope Options Automate Client Configuration

DHCP Scope Options allow clients to automatically receive:

* IP addresses
* Default Gateway
* DNS Server
* DNS Domain

### Reservations Provide Predictable Addressing

DHCP Reservations allow administrators to provide consistent IP addresses to important devices while maintaining centralized DHCP management.

### Validation Reduces Deployment Risk

Testing DHCP, DNS, and Active Directory before production deployment reduces the risk of network outages and authentication failures.

---

# Evidence

# Evidence

The following screenshots provide implementation and validation evidence from the Marctech DHCP and Core Network Services lab environment.

## 1. DHCP Server Installation & Authorization

[View DHCP Server Installation & Authorization Evidence](./Screenshots/01-DHCP-Server-Authorization.png)

This screenshot shows the Windows DHCP Server role installed and authorized within the Marctech Active Directory environment.

The evidence demonstrates that DHCP was successfully integrated with the existing `marctech.local` domain infrastructure.

---

## 2. DHCP Scope Configuration

[View DHCP Scope Configuration Evidence](./Screenshots/02-DHCP-Scope-Configuration.png)

This screenshot shows the `Marctech-Lab` DHCP scope configured for the corporate network.

The scope was configured with:

```text
Network:       192.168.50.0/24
Start IP:      192.168.50.100
End IP:        192.168.50.150
Subnet Mask:   255.255.255.0
Lease Duration: 8 Days
```

This provides a centralized address pool for DHCP clients within the Marctech lab environment.

---

## 3. DHCP Scope Options

[View DHCP Scope Options Evidence](./Screenshots/03-DHCP-Scope-Options.png)

This screenshot provides evidence of the DHCP Scope Options configured for Marctech clients.

The configured options included:

* **003 – Default Gateway:** `192.168.50.1`
* **006 – DNS Server:** `192.168.1.12`
* **015 – DNS Domain Name:** `marctech.local`

These options allow DHCP clients to automatically receive the network configuration required to communicate with the Marctech environment and locate domain services.

---

## 4. DHCP Reservation for PC01

[View DHCP Reservation Evidence](./Screenshots/04-DHCP-PC01-Reservation.png)

This screenshot shows the DHCP reservation created for PC01.

The reservation associates the PC01 MAC address with the designated IP address:

```text
192.168.50.110
```

The reservation demonstrates how DHCP can provide predictable addressing for selected devices while maintaining centralized network management.

---

## 5. DHCP Client IP Assignment & Validation

[View DHCP Client Validation Evidence](./Screenshots/05-DHCP-Client-IP-Validation.png)

This screenshot shows PC01 receiving and validating its network configuration through DHCP.

The client configuration was verified using:

```cmd
ipconfig /all
```

The validation confirms that the workstation received the expected network configuration, including its IP address, default gateway, DNS server, and DNS domain.

The DHCP client configuration was successfully validated.

**Result: PASS**

---

## 6. DNS & Active Directory Authentication Validation

[View DNS & Active Directory Validation Evidence](./Screenshots/06-DNS-AD-Validation.png)

This screenshot provides final validation that the DHCP-configured workstation could communicate with the Marctech identity infrastructure.

DNS resolution was tested using:

```cmd
nslookup dc01.marctech.local
```

Active Directory authentication was validated using:

```cmd
echo %LOGONSERVER%
```

The validation demonstrated successful communication with:

```text
DC01
```

This confirms the complete network-services chain:

```text
DHCP
  ↓
IP Configuration
  ↓
DNS Resolution
  ↓
Domain Controller Discovery
  ↓
Active Directory Authentication
```

**Result: PASS**

---

# Evidence Summary

The six screenshots demonstrate the complete implementation and validation lifecycle of the Marctech DHCP deployment:

```text
DHCP Installation & Authorization
              ↓
       DHCP Scope Creation
              ↓
       Scope Options
              ↓
       PC01 Reservation
              ↓
     Client IP Assignment
              ↓
 DNS & Active Directory Validation
```

Together, the evidence demonstrates that DHCP was not only configured but also validated as part of the broader Marctech network and identity infrastructure.

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Passwords, credentials, MAC addresses, and other unnecessary sensitive information should be masked where appropriate before publication.


> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Passwords, credentials, and unnecessary sensitive information are not published.

---

# Key Takeaway

This lab demonstrated how **DHCP, DNS, and Active Directory work together to provide the network foundation required for enterprise identity services**.

The completed environment followed:

```text
DHCP
  ↓
Automatic IP Configuration
  ↓
DNS
  ↓
Domain Controller Discovery
  ↓
Active Directory
  ↓
Authentication
  ↓
Resource Access
```

The lab also demonstrated that network services and IAM are closely connected.

A user may have a valid Active Directory account, but successful authentication and access to organizational resources depend on the underlying network infrastructure being correctly configured.

The implementation therefore reinforced the relationship between:

```text
Network Services
       ↓
      DNS
       ↓
    Identity
       ↓
 Authentication
       ↓
 Authorization
       ↓
 Resource Access
```

This provides a foundation for more advanced enterprise infrastructure and IAM operations.
