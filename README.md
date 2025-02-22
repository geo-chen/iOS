# CVE-2022–22659 — iOS “VPN On Demand”

DGA-like outbound calls from iOS feature “VPN On Demand”

## Details
As part of Apple’s implementation of “VPN On Demand”, an iOS service called “nesessionmanager” performs DNS redirect tests. This test is performed in the function “NESMSession startDNSRedirectionDetection” and is implemented by generating a random domain address and initiating a DNS request to resolve it. Part of the random domain name generation code is shown here and the expected result of this process is a NXDOMAIN response:

![image](https://github.com/user-attachments/assets/9d6a4dc4-68db-4550-8e24-610f4c34f66b)

From the network logs of a single iOS device connected to wifi over a few hours, we see:

![image](https://github.com/user-attachments/assets/dad3bfd6-66f1-48c5-9f15-3009de7c962e)

## Attack Vector
<REDACTED>

## Impact
An attacker in a privileged network position may be able to leak sensitive user information.

## Timeline
- Reported to Apple Product Security in early 2020
- Assigned CVE in May 2022
