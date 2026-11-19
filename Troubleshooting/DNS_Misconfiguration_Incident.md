
# Incident 2 — Incorrect DNS Server Configuration

## Environment
- Client: AC-LAB-PC01 (Windows 11)
- Server: AC-LAB-DC01 (Windows Server 2025)
- Domain: corp.aclab.test
- Correct DNS Server: 192.168.50.10
- Incorrect DNS Server: 192.168.50.99

## Problem
A workstation using an incorrect DNS server could not resolve the company's domain controller hostname.

## Troubleshooting Process
1. Identified the correct DNS server as 192.168.50.10.
2. In the original controlled exercise, temporarily configured an incorrect DNS server and later restored the correct configuration.
3. Reproduced the failure using an explicit DNS query to 192.168.50.99.
4. Observed repeated DNS request timeouts.
5. Queried the correct server, 192.168.50.10, using Resolve-DnsName.
6. Confirmed successful resolution of AC-LAB-DC01.corp.aclab.test.
7. Verified that the client's DNS configuration currently points to 192.168.50.10.

## Root Cause
The simulated DNS misconfiguration directed name-resolution requests to an address that did not provide a DNS response.

## Resolution and Verification
The correct DNS server was restored during the original exercise.

In the final verification:
- Incorrect DNS server: Query timed out
- Correct DNS server: Query succeeded
- Returned IP address: 192.168.50.10
- Client DNS configuration: 192.168.50.10

The final tests used explicit DNS queries without changing the working DHCP configuration.

## Skills Demonstrated
- DNS troubleshooting
- PowerShell network diagnostics
- nslookup
- Resolve-DnsName
- DNS client configuration verification
- Incident documentation

## Evidence
- incident-02-dns-failure.png
- incident-02-dns-verified.png

## Final Status
Incorrect DNS configuration investigated; correct DNS resolution verified.
