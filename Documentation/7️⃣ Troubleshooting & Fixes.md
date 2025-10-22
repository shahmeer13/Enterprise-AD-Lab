**1. DNS Resolution Issue**
- Client unable to join domain (error: “Cannot contact domain”)
- Fixed by setting DC02 (10.0.0.1) as the DNS server on Windows 10

**2. Network Adapter Conflict**
- VirtualBox had two adapters (NAT + Internal Network)
- Disabled NAT and used only Internal Network for both DC02 and client

**3. Autoconfiguration IP (169.x.x.x)**
- Occurred when DHCP was unavailable
- Assigned static IPs manually in the 10.0.0.x range to ensure connectivity

**4. GPO Not Applying**
- Policies didn’t update on the client immediately
- Ran `gpupdate /force` and verified application using `gpresult /r`

**5. Domain Join Failure**
- Domain join failed due to DNS misconfiguration
- Corrected DNS settings and successfully joined `corp.local`
