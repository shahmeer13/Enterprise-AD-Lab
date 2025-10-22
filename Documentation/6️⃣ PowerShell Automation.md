Automated administrative tasks using PowerShell:

```powershell
# Bulk User Creation
Import-Module ActiveDirectory
Import-Csv "C:\users.csv" | ForEach-Object {
    New-ADUser -Name $_.Name -SamAccountName $_.Username -UserPrincipalName "$($_.Username)@corp.local" `
    -Path $_.OU -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -Enabled $true
}

# Add Users to Departmental Groups
Add-ADGroupMember -Identity "Finance-SG" -Members FinanceUser1, FinanceUser2
Add-ADGroupMember -Identity "IT-SG" -Members ITUser1, ITUser2

# Force Group Policy Update
Invoke-GPUpdate -Computer "W10-Client" -Force

📁 Full script available in: PowerShell/ActiveDirectory_Automation.ps1


---

### 🧩 7️⃣ Troubleshooting & Fixes.md
```markdown
### Troubleshooting & Fixes

- Resolved “Cannot contact domain” issue by fixing DNS (client now points to DC02)
- Disabled secondary adapters in VirtualBox to isolate internal LAN
- Ensured Windows Firewall allowed inbound LDAP and RPC
- Used `ping`, `ipconfig /all`, and `nslookup` to verify connectivity
- Confirmed AD replication and GPO refresh worked after restarts


