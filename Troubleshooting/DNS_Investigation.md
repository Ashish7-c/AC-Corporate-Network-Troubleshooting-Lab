
# DNS Troubleshooting Investigation

## Environment
- Windows Server: AC-LAB-DC01
- Windows 11 Client: AC-LAB-PC01
- Domain: corp.aclab.test
- DNS Server IP: 192.168.50.10
- Client IP: 192.168.50.20
- Network: VirtualBox Internal Network (AC-LAB)

## Reported Issue
The Windows 11 client could reach the domain controller using its IP address, but DNS queries sometimes timed out.

## Diagnostic Steps
1. Verified IP connectivity using ping.
2. Checked that the DNS Server service was running.
3. Verified the DNS zone and A records.
4. Tested DNS over UDP and TCP.
5. Verified TCP port 53 connectivity.
6. Inspected Windows Firewall DNS rules.
7. Confirmed the DNS process was listening on UDP port 53.
8. Checked DNS server statistics.
9. Used Resolve-DnsName to test client name resolution.

## Findings
- IP connectivity worked with 0% packet loss.
- TCP DNS queries succeeded.
- UDP DNS queries initially experienced timeouts.
- DNS Server service and A records were present.
- Windows Firewall had an enabled UDP port 53 allow rule.
- Five consecutive client DNS lookups succeeded.

## Conclusion
DNS name resolution was successful during the final tests. The earlier intermittent timeouts were not conclusively explained, and no configuration change was made.

## Skills Practiced
- Network troubleshooting
- Windows DNS Server administration
- PowerShell diagnostics
- TCP vs. UDP investigation
- Windows Firewall inspection
- Technical documentation
