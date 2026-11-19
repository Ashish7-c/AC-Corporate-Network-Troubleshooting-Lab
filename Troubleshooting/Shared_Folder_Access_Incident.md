
# Incident 4 — Shared Folder Access Troubleshooting

## Environment
- Server: AC-LAB-DC01
- Client: AC-LAB-PC01
- Domain: corp.aclab.test
- Employee: CORP\amsu.magar
- Protocol: SMB (TCP port 445)

## Reported Issue
An employee needs access to a restricted departmental shared folder.

## Investigation
1. Verified that TCP port 445 was reachable.
2. Confirmed the existing IT-Shared folder was accessible.
3. Inspected SMB share permissions and NTFS permissions.
4. Checked the employee's Active Directory security group membership.
5. Created a separate Restricted-Test share for the incident.
6. Configured administrator-only access initially.
7. Granted the employee Read permission at the share level.
8. Verified the employee could list the folder.
9. Attempted to create a file and received Access Denied.

## Root Cause
The initial test share was restricted to Administrators.
The employee required read access but did not require write access.

## Resolution
Granted the employee Read permission to the Restricted-Test share while preserving administrator Full access.

## Verification
- Shared-folder listing: Successful
- File creation: Access Denied (expected)
- Least-privilege access: Verified

## Skills Demonstrated
- SMB file sharing
- Windows share permissions
- NTFS permission inspection
- Active Directory security groups
- Access troubleshooting
- Least-privilege security

