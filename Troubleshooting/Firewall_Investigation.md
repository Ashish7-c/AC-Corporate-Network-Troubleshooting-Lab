
# Incident 6 — Windows Firewall Troubleshooting

## Environment
- Server: AC-LAB-DC01
- Client: AC-LAB-PC01
- Domain: corp.aclab.test
- Server IP: 192.168.50.10
- Client IP: 192.168.50.100 (DHCP)
- Network: VirtualBox Internal Network (AC-LAB)

## Reported Issue
The domain controller could not ping the Windows 11 employee workstation.

## Investigation
1. Verified that Windows Firewall was enabled.
2. Confirmed the client network profile was DomainAuthenticated.
3. Tested ICMP connectivity from DC01 to PC01.
4. Observed 100% packet loss.
5. Inspected inbound ICMP Echo Request firewall rules.
6. Found that the existing ICMP Echo Request allow rules were disabled.
7. Created a custom inbound ICMPv4 rule restricted to 192.168.50.10.
8. Verified that the Domain Firewall remained enabled.
9. Retested ping connectivity from DC01 to PC01.

## Root Cause
The workstation had no enabled inbound allow rule permitting the domain controller's ICMPv4 Echo Requests.

## Resolution
Created a targeted firewall rule allowing inbound ICMPv4 Echo Requests from 192.168.50.10 on the Domain profile.

## Verification
- Before: 4 packets sent, 0 received, 100% loss
- After: 4 packets sent, 4 received, 0% loss
- Average response time: 1 ms
- Domain Firewall remained enabled

## Skills Demonstrated
- Windows Defender Firewall troubleshooting
- ICMP diagnostics
- Firewall rule configuration
- Network profile verification
- Least-privilege network access
- PowerShell administration
