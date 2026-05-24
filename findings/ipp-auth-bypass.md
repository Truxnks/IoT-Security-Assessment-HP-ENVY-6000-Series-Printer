# IPP Authentication Bypass

## Severity
Critical

## CVSS
8.2 High — AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:H/A:N

## Affected Service
TCP/631 — Internet Printing Protocol (IPP)

## Description
The HP ENVY 6000 printer implemented HTTP Digest authentication using an invalid all-zero nonce value.

Because the nonce was not properly generated or validated, arbitrary username/password combinations were accepted and resulted in authenticated sessions.

## Discovery Process
The issue was identified during manual HTTP authentication testing against the IPP service after enumeration revealed port 631 exposed on the network.

Testing confirmed:
- Multiple random credential pairs returned HTTP 200 OK
- Authenticated IPP sessions were established successfully
- Unauthorized print jobs could be submitted

## Security Impact
- Unauthorized printer access
- Authentication trust failure
- Unauthorized print submission
- Potential resource exhaustion
- Inability to trust authentication logs

## Mitigation
- Block TCP/631 externally
- Restrict IPP access to trusted hosts
- Apply latest firmware updates
- Segment printers onto isolated VLANs
