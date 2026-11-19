# Incident 5 — DHCP Troubleshooting Investigation

## Environment
- Server: AC-LAB-DC01 (Windows Server 2025)
- Client: AC-LAB-PC01 (Windows 11)
- Domain: corp.aclab.test
- Network: 192.168.50.0/24
- DHCP Server: 192.168.50.10

## Reported Issue
A Windows 11 employee workstation could not obtain a valid IP address automatically.

## Investigation and Configuration
1. Checked whether the DHCP Server role was installed.
2. Installed the Windows DHCP Server role and management tools.
3. Verified the DHCP Server service was running.
4. Authorized DHCP Server in Active Directory.
5. Created and activated the AC-LAB-Office DHCP scope.
6. Configured the DHCP range from 192.168.50.100 to 192.168.50.150.
7. Configured DNS server 192.168.50.10 and domain corp.aclab.test.
8. Enabled DHCP on the Windows 11 workstation.
9. Observed an initial APIPA address of 169.254.221.56.
10. Renewed the DHCP lease using ipconfig /renew.
11. Verified network connectivity and DNS resolution.

## Findings
- Initial automatic IP assignment did not succeed.
- Windows assigned a temporary APIPA address.
- A subsequent DHCP renewal successfully obtained 192.168.50.100.
- The DHCP server was identified as 192.168.50.10.
- Network connectivity tests showed 0% packet loss.
- Domain controller hostname resolution succeeded.

## Resolution
Successfully obtained a valid DHCP lease after renewing the Windows 11 network adapter's address.

The exact cause of the initial unsuccessful lease attempt was not conclusively identified.

## Skills Practiced
- Windows Server DHCP administration
- Active Directory DHCP authorization
- DHCP scope configuration
- APIPA troubleshooting
- PowerShell network diagnostics
- IP address renewal
- DNS and connectivity verification

## Final Status
DHCP address assignment and network connectivity verified successfully.