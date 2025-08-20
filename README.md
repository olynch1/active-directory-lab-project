# active-directory-lab-project
This lab demonstrates how I successfully promoted a Windows Server 2016 VM to a Domain Controller using PowerShell and manually resolved common issues during setup.
## 🛠️ Lab Environment
- **Host OS:** Windows 10
- **Guest VM:** Windows Server 2016 (via VirtualBox)
- **Tools Used:** 
  - PowerShell
  - Server Manager
  - `Install-ADDSForest`
  - `dsacls`

---

## ✅ Key Achievements

### 1. Installed ADDS Role:
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
2. Promoted Server to Domain Controller:
powershell
Copy code
Import-Module ADDSDeployment

Install-ADDSForest `
  -DomainName "lab.local" `
  -InstallDns:$true `
  -SafeModeAdministratorPassword (ConvertTo-SecureString "YourPasswordHere" -AsPlainText -Force)
3. Resolved:

InstallDNS not recognized error

Verified required PowerShell module was loaded with:

Import-Module ADDSDeployment

4. Verified AD Domain Tree in Server Manager
🔐 Bonus: Used dsacls to Explore AD Permissions
dsacls "CN=Users,DC=lab,DC=local"

Example: Granting Create User rights
dsacls "OU=TestOU,DC=lab,DC=local" /G "LAB\OssirisLynch:CA;user"

📸 Screenshots

Screenshots of:

Windows Update success

PowerShell command errors and fixes

Final successful DC promotion

You can upload these in the screenshots/ folder or link from the repo.

🔄 Future Labs

Add secondary Domain Controller

Setup DNS replication

Join client machine to domain

GPO enforcement and testing

🧠 Lessons Learned

Always load the ADDS module before using Install-ADDSForest

Use PowerShell for precision and automation

Read error messages closely — they’re clues, not roadblocks

📇 Author

Ossiris Lynch – Inspector, IT Student, Cybersecurity Trainee
📍 Las Vegas, Nevada
🎓 UNLV Cyber Security Program
