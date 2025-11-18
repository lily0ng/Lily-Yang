
## **Windows System & Hostname Commands**

### 1. Show System Information

```
Command - (code view)
root@lilyang - systeminfo

Output - (code view)
Host Name:                     LILYANG-PC
OS Name:                       Microsoft Windows 11 Pro
OS Version:                    10.0.22621 Build 22621
OS Manufacturer:               Microsoft Corporation
System Type:                   x64-based PC
...
```

### 2. Show Hostname

```
Command - (code view)
root@lilyang - hostname

Output - (code view)
LILYANG-PC
```

### 3. Change Computer Name

```
Command - (code view)
root@lilyang - Rename-Computer -NewName "NEWNAME"

Output - (code view)
# No output if successful, requires restart
```

### 4. Show Environment Variables

```
Command - (code view)
root@lilyang - set

Output - (code view)
ALLUSERSPROFILE=C:\ProgramData
APPDATA=C:\Users\LILYANG\AppData\Roaming
USERNAME=LILYANG
USERPROFILE=C:\Users\LILYANG
...
```

### 5. Display Windows Version

```
Command - (code view)
root@lilyang - ver

Output - (code view)
Microsoft Windows [Version 10.0.22621.1265]
```

### 6. Display OS Architecture

```
Command - (code view)
root@lilyang - wmic os get osarchitecture

Output - (code view)
OSArchitecture
64-bit
```

### 7. Display Boot Time

```
Command - (code view)
root@lilyang - systeminfo | find "Boot Time"

Output - (code view)
System Boot Time:               11/16/2025, 12:30:45 PM
```

### 8. Show Logged Users

```
Command - (code view)
root@lilyang - query user

Output - (code view)
 USERNAME              SESSIONNAME        ID  STATE   IDLE TIME  LOGON TIME
 LILYANG               console             1  Active      none   11/16/2025 12:20 PM
```

### 9. Show System Uptime

```
Command - (code view)
root@lilyang - net stats workstation

Output - (code view)
Statistics since 11/16/2025 12:00 PM
...
```

### 10. Shutdown System

```
Command - (code view)
root@lilyang - shutdown /s /t 0

Output - (code view)
# No output, system will shutdown immediately
```

### 11. Restart System

```
Command - (code view)
root@lilyang - shutdown /r /t 0

Output - (code view)
# No output, system will restart immediately
```

### 12. Log Off Current User

```
Command - (code view)
root@lilyang - shutdown /l

Output - (code view)
# No output, user will be logged off
```

### 13. Display OS Installation Date

```
Command - (code view)
root@lilyang - systeminfo | find "Install Date"

Output - (code view)
Original Install Date:          10/10/2025, 9:30:15 AM
```

### 14. Check Product Key Status

```
Command - (code view)
root@lilyang - slmgr /dli

Output - (code view)
Name: Windows(R) 11 Pro
Description: Windows(R) Operating System, RETAIL channel
Partial Product Key: XXXX-XXXX-XXXX-XXXX
License Status: Licensed
```

### 15. Display Detailed License Info

```
Command - (code view)
root@lilyang - slmgr /dlv

Output - (code view)
Name: Windows(R) 11 Pro
Description: Windows(R) Operating System, RETAIL channel
License Status: Licensed
Activation ID: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
...
```

### 16. Activate Windows

```
Command - (code view)
root@lilyang - slmgr /ato

Output - (code view)
# No output if activation is successful
```

### 17. Show BIOS Information

```
Command - (code view)
root@lilyang - wmic bios get serialnumber, smbiosbiosversion, manufacturer

Output - (code view)
Manufacturer  SMBIOSBIOSVersion  SerialNumber
Dell Inc.     1.25.0             ABC123456
```

### 18. Show CPU Info

```
Command - (code view)
root@lilyang - wmic cpu get name, numberofcores, numberoflogicalprocessors

Output - (code view)
Name                                NumberOfCores  NumberOfLogicalProcessors
Intel(R) Core(TM) i7-11700K CPU        8                   16
```

### 19. Show RAM Info

```
Command - (code view)
root@lilyang - wmic memorychip get capacity, speed, manufacturer

Output - (code view)
Capacity        Speed  Manufacturer
17179869184     3200   Corsair
17179869184     3200   Corsair
```

### 20. Display Disk Drives

```
Command - (code view)
root@lilyang - wmic diskdrive get model,size,interfaceType

Output - (code view)
Model                       Size          InterfaceType
Samsung SSD 970 EVO 1TB     1000204886016  NVMe
Seagate BarraCuda 2TB       2000398934016  SATA
```

### 21. Show System Locale

```
Command - (code view)
root@lilyang - systeminfo | find "System Locale"

Output - (code view)
System Locale:                 en-us;English (United States)
```

### 22. Display Timezone

```
Command - (code view)
root@lilyang - tzutil /g

Output - (code view)
UTC+06:30
```

### 23. Change Timezone

```
Command - (code view)
root@lilyang - tzutil /s "Myanmar Standard Time"

Output - (code view)
# No output if successful
```

### 24. Show Power Plan

```
Command - (code view)
root@lilyang - powercfg /l

Output - (code view)
Existing Power Schemes (* Active)
-----------------------------------
Power Saver                          GUID: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Balanced *                           GUID: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
High performance                      GUID: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

### 25. Set Power Plan

```
Command - (code view)
root@lilyang - powercfg /s XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX

Output - (code view)
# No output if successful
```

---
### **26. Show all users**

```
Command - (code view)
root@lilyang - net user

Output - (code view)
Administrator            DefaultAccount           Guest
User1                    User2                   ...
```

### **27. Create a new user**

```
Command - (code view)
root@lilyang - net user NewUser MyP@ssw0rd /add

Output - (code view)
The command completed successfully.
```

### **28. Delete a user**

```
Command - (code view)
root@lilyang - net user NewUser /delete

Output - (code view)
The command completed successfully.
```

### **29. Add user to administrators group**

```
Command - (code view)
root@lilyang - net localgroup administrators NewUser /add

Output - (code view)
The command completed successfully.
```

### **30. Remove user from administrators group**

```
Command - (code view)
root@lilyang - net localgroup administrators NewUser /delete

Output - (code view)
The command completed successfully.
```

### **31. Change user password**

```
Command - (code view)
root@lilyang - net user User1 NewP@ssw0rd

Output - (code view)
The command completed successfully.
```

### **32. Enable user account**

```
Command - (code view)
root@lilyang - net user User1 /active:yes

Output - (code view)
The command completed successfully.
```

### **33. Disable user account**

```
Command - (code view)
root@lilyang - net user User1 /active:no

Output - (code view)
The command completed successfully.
```

### **34. List local groups**

```
Command - (code view)
root@lilyang - net localgroup

Output - (code view)
Administrators
Backup Operators
Guests
Users
Remote Desktop Users
...
```

### **35. Create a new local group**

```
Command - (code view)
root@lilyang - net localgroup DevTeam /add

Output - (code view)
The command completed successfully.
```

### **36. Delete a local group**

```
Command - (code view)
root@lilyang - net localgroup DevTeam /delete

Output - (code view)
The command completed successfully.
```

### **37. Add user to local group**

```
Command - (code view)
root@lilyang - net localgroup DevTeam User1 /add

Output - (code view)
The command completed successfully.
```

### **38. Remove user from local group**

```
Command - (code view)
root@lilyang - net localgroup DevTeam User1 /delete

Output - (code view)
The command completed successfully.
```

### **39. Display user account info**

```
Command - (code view)
root@lilyang - net user User1

Output - (code view)
User name                    User1
Full Name                    
Comment                      
User's comment               
Country/region code           000 (System Default)
Account active                Yes
Account expires               Never
Password last set             11/16/2025 12:00 PM
Password expires              Never
Password changeable           11/16/2025 12:00 PM
Password required             Yes
User may change password      Yes
Workstations allowed          All
Logon script                  
User profile                 
Home directory                
Last logon                    11/16/2025 12:10 PM
```

### **40. Force user logoff**

```
Command - (code view)
root@lilyang - logoff 2

Output - (code view)
# No output, user with session ID 2 is logged off
```

### **41. Query user sessions**

```
Command - (code view)
root@lilyang - query user

Output - (code view)
 USERNAME              SESSIONNAME        ID  STATE   IDLE TIME  LOGON TIME
 LILYANG               console             1  Active      none   11/16/2025 12:20 PM
 Guest                 rdp-tcp#1           2  Disc        5+00:00  11/15/2025 10:00 AM
```

### **42. Unlock user account**

```
Command - (code view)
root@lilyang - net user User1 /active:yes

Output - (code view)
The command completed successfully.
```

### **43. Disable password expiration**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' set PasswordExpires=False

Output - (code view)
Method execution successful.
```

### **44. Enable password expiration**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' set PasswordExpires=True

Output - (code view)
Method execution successful.
```

### **45. Check group membership**

```
Command - (code view)
root@lilyang - net user User1 | find "Local Group Memberships"

Output - (code view)
Local Group Memberships      *Users
Global Group memberships     *None
```

### **46. Rename a user account**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' rename NewUserName

Output - (code view)
Method execution successful.
```

### **47. Enable hidden administrator account**

```
Command - (code view)
root@lilyang - net user Administrator /active:yes

Output - (code view)
The command completed successfully.
```

### **48. Disable administrator account**

```
Command - (code view)
root@lilyang - net user Administrator /active:no

Output - (code view)
The command completed successfully.
```

### **49. Set user description**

```
Command - (code view)
root@lilyang - net user User1 /comment:"IT Engineer"

Output - (code view)
The command completed successfully.
```

### **50. Get account expiration date**

```
Command - (code view)
root@lilyang - net user User1 | find "Account expires"

Output - (code view)
Account expires              Never
```

---
### **51. Show last logon of a user**

```
Command - (code view)
root@lilyang - net user User1 | find "Last logon"

Output - (code view)
Last logon                    11/16/2025 12:10 PM
```

### **52. Force password change at next logon**

```
Command - (code view)
root@lilyang - net user User1 /logonpasswordchg:yes

Output - (code view)
The command completed successfully.
```

### **53. Prevent user from changing password**

```
Command - (code view)
root@lilyang - net user User1 /passwordchg:no

Output - (code view)
The command completed successfully.
```

### **54. Display domain/workgroup info**

```
Command - (code view)
root@lilyang - systeminfo | find "Domain"

Output - (code view)
Domain:                        WORKGROUP
```

### **55. Add user to remote desktop users**

```
Command - (code view)
root@lilyang - net localgroup "Remote Desktop Users" User1 /add

Output - (code view)
The command completed successfully.
```

### **56. Remove user from remote desktop users**

```
Command - (code view)
root@lilyang - net localgroup "Remote Desktop Users" User1 /delete

Output - (code view)
The command completed successfully.
```

### **57. List all administrator accounts**

```
Command - (code view)
root@lilyang - net localgroup administrators

Output - (code view)
Alias name     administrators
Comment        Administrators have complete and unrestricted access to the computer/domain

Members
---------------------------------------
Administrator
User1
```

### **58. Show user SID**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' get name,sid

Output - (code view)
Name    SID
User1   S-1-5-21-1234567890-1234567890-1234567890-1001
```

### **59. Disable all local users except administrator**

```
Command - (code view)
root@lilyang - net user User1 /active:no
root@lilyang - net user User2 /active:no
...

Output - (code view)
The command completed successfully.
```

### **60. Enable all local users**

```
Command - (code view)
root@lilyang - net user User1 /active:yes
root@lilyang - net user User2 /active:yes
...

Output - (code view)
The command completed successfully.
```

### **61. Display local groups and members**

```
Command - (code view)
root@lilyang - net localgroup

Output - (code view)
Administrators
Backup Operators
Guests
Users
Remote Desktop Users
DevTeam
```

### **62. Display detailed local group info**

```
Command - (code view)
root@lilyang - net localgroup Administrators

Output - (code view)
Alias name     Administrators
Comment        Administrators have complete and unrestricted access to the computer/domain
Members
---------------------------------------
Administrator
User1
```

### **63. Create multiple users in batch**

```
Command - (code view)
root@lilyang - for %i in (UserA UserB UserC) do net user %i P@ssw0rd /add

Output - (code view)
The command completed successfully.
The command completed successfully.
The command completed successfully.
```

### **64. Add multiple users to group**

```
Command - (code view)
root@lilyang - for %i in (UserA UserB UserC) do net localgroup DevTeam %i /add

Output - (code view)
The command completed successfully.
The command completed successfully.
The command completed successfully.
```

### **65. Show locked accounts**

```
Command - (code view)
root@lilyang - net user | findstr /i "locked"

Output - (code view)
User3
User4
```

### **66. Unlock an account**

```
Command - (code view)
root@lilyang - net user User3 /active:yes

Output - (code view)
The command completed successfully.
```

### **67. Display last password set date**

```
Command - (code view)
root@lilyang - net user User1 | find "Password last set"

Output - (code view)
Password last set             11/16/2025 12:00 PM
```

### **68. Show password expiration date**

```
Command - (code view)
root@lilyang - net user User1 | find "Password expires"

Output - (code view)
Password expires              Never
```

### **69. Force immediate logoff of all users except admin**

```
Command - (code view)
root@lilyang - query user | findstr /v "Administrator" | for /f "tokens=3" %i in ('more') do logoff %i

Output - (code view)
# No output, users logged off
```

### **70. Check user privileges**

```
Command - (code view)
root@lilyang - whoami /priv

Output - (code view)
PRIVILEGE_NAME                DESCRIPTION                    STATE
SeIncreaseQuotaPrivilege      Adjust memory quotas for a process  Enabled
SeShutdownPrivilege           Shut down the system                Enabled
SeChangeNotifyPrivilege       Bypass traverse checking            Enabled
...
```

### **71. Add user to network configuration group**

```
Command - (code view)
root@lilyang - net localgroup "Network Configuration Operators" User1 /add

Output - (code view)
The command completed successfully.
```

### **72. Remove user from network configuration group**

```
Command - (code view)
root@lilyang - net localgroup "Network Configuration Operators" User1 /delete

Output - (code view)
The command completed successfully.
```

### **73. Display all user accounts with description**

```
Command - (code view)
root@lilyang - wmic useraccount get name, description

Output - (code view)
Name         Description
Administrator Built-in account for administering the computer/domain
User1        IT Engineer
User2        Sales Staff
Guest        
```

### **74. Set user account to never expire**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' set AccountExpires=Never

Output - (code view)
Method execution successful.
```

### **75. Set account expiration date**

```
Command - (code view)
root@lilyang - wmic useraccount where name='User1' set AccountExpires="20251231"

Output - (code view)
Method execution successful.
```

---
### **76. List files in a directory**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents

Output - (code view)
 Volume in drive C has no label.
 Directory of C:\Users\LILYANG\Documents

11/16/2025  12:00 PM    <DIR>          .
11/16/2025  12:00 PM    <DIR>          ..
11/16/2025  12:05 PM            1,024  file1.txt
11/16/2025  12:10 PM            2,048  file2.docx
...
```

### **77. Create a new folder**

```
Command - (code view)
root@lilyang - mkdir C:\Users\LILYANG\Documents\TestFolder

Output - (code view)
# No output if successful
```

### **78. Remove a folder**

```
Command - (code view)
root@lilyang - rmdir C:\Users\LILYANG\Documents\TestFolder

Output - (code view)
# No output if successful
```

### **79. Remove folder with contents**

```
Command - (code view)
root@lilyang - rmdir /s /q C:\Users\LILYANG\Documents\TestFolder

Output - (code view)
# No output if successful
```

### **80. Copy a file**

```
Command - (code view)
root@lilyang - copy C:\file.txt D:\Backup\file.txt

Output - (code view)
1 file(s) copied.
```

### **81. Move a file**

```
Command - (code view)
root@lilyang - move C:\file.txt D:\Backup\

Output - (code view)
1 file(s) moved.
```

### **82. Delete a file**

```
Command - (code view)
root@lilyang - del D:\Backup\file.txt

Output - (code view)
# No output if successful
```

### **83. Rename a file**

```
Command - (code view)
root@lilyang - ren C:\Users\LILYANG\Documents\file1.txt file1_old.txt

Output - (code view)
# No output if successful
```

### **84. Display file contents**

```
Command - (code view)
root@lilyang - type C:\Users\LILYANG\Documents\file1_old.txt

Output - (code view)
Hello World!
This is a sample file.
```

### **85. Show hidden files**

```
Command - (code view)
root@lilyang - dir /a:h C:\Users\LILYANG\Documents

Output - (code view)
 Volume in drive C has no label.
 Directory of C:\Users\LILYANG\Documents

11/16/2025  12:15 PM    <HIDDEN>      secret.txt
```

### **86. Show read-only files**

```
Command - (code view)
root@lilyang - dir /a:r C:\Users\LILYANG\Documents

Output - (code view)
 Volume in drive C has no label.
 Directory of C:\Users\LILYANG\Documents

11/16/2025  12:20 PM    <R>           readonly.txt
```

### **87. Change directory**

```
Command - (code view)
root@lilyang - cd C:\Users\LILYANG\Documents

Output - (code view)
C:\Users\LILYANG\Documents>
```

### **88. Go to parent directory**

```
Command - (code view)
root@lilyang - cd ..

Output - (code view)
C:\Users\LILYANG>
```

### **89. Display current directory**

```
Command - (code view)
root@lilyang - cd

Output - (code view)
C:\Users\LILYANG
```

### **90. Create multiple folders**

```
Command - (code view)
root@lilyang - mkdir C:\Folder1 C:\Folder2 C:\Folder3

Output - (code view)
# No output if successful
```

### **91. Copy all files from folder**

```
Command - (code view)
root@lilyang - xcopy C:\Source\* D:\Backup\ /s /i

Output - (code view)
C:\Source\file1.txt -> D:\Backup\file1.txt
C:\Source\file2.docx -> D:\Backup\file2.docx
...
```

### **92. Copy folder with contents**

```
Command - (code view)
root@lilyang - xcopy C:\Source D:\Backup /s /e /i

Output - (code view)
C:\Source\ -> D:\Backup\
```

### **93. Delete all files in folder**

```
Command - (code view)
root@lilyang - del /q C:\Users\LILYANG\Documents\*

Output - (code view)
# No output if successful
```

### **94. Delete all files and subfolders**

```
Command - (code view)
root@lilyang - rmdir /s /q C:\Users\LILYANG\Documents\TestFolder

Output - (code view)
# No output if successful
```

### **95. Check disk usage of folder**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents | find "File(s)"

Output - (code view)
               3 File(s)           7,296 bytes
```

### **96. Check free space on drive**

```
Command - (code view)
root@lilyang - dir C:\

Output - (code view)
 Volume in drive C has no label.
 Directory of C:\

3 File(s)  7,296 bytes
Free Space:  512,000,000,000 bytes
```

### **97. Compare two files**

```
Command - (code view)
root@lilyang - fc file1.txt file2.txt

Output - (code view)
Comparing files file1.txt and file2.txt
***** file1.txt
Hello World!
***** file2.txt
Hello World!!!
*****
```

### **98. Find text in files**

```
Command - (code view)
root@lilyang - find "Hello" C:\Users\LILYANG\Documents\file1.txt

Output - (code view)
---------- C:\Users\LILYANG\Documents\file1.txt
Hello World!
```

### **99. Search files in directory**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents\*.txt /s

Output - (code view)
C:\Users\LILYANG\Documents\file1.txt
C:\Users\LILYANG\Documents\file2.txt
...
```

### **100. Display file size**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents\file1.txt

Output - (code view)
 Volume in drive C has no label.
 Directory of C:\Users\LILYANG\Documents

11/16/2025  12:05 PM            1,024  file1.txt
```

---
### **101. Make a hidden folder**

```
Command - (code view)
root@lilyang - mkdir C:\Users\LILYANG\Documents\SecretFolder
root@lilyang - attrib +h C:\Users\LILYANG\Documents\SecretFolder

Output - (code view)
# No output if successful
```

### **102. Remove hidden attribute from folder**

```
Command - (code view)
root@lilyang - attrib -h C:\Users\LILYANG\Documents\SecretFolder

Output - (code view)
# No output if successful
```

### **103. Make a read-only file**

```
Command - (code view)
root@lilyang - attrib +r C:\Users\LILYANG\Documents\file1.txt

Output - (code view)
# No output if successful
```

### **104. Remove read-only attribute**

```
Command - (code view)
root@lilyang - attrib -r C:\Users\LILYANG\Documents\file1.txt

Output - (code view)
# No output if successful
```

### **105. Make a file system hidden + read-only**

```
Command - (code view)
root@lilyang - attrib +h +r C:\Users\LILYANG\Documents\file2.txt

Output - (code view)
# No output if successful
```

### **106. Display file attributes**

```
Command - (code view)
root@lilyang - attrib C:\Users\LILYANG\Documents\file2.txt

Output - (code view)
R  H  C:\Users\LILYANG\Documents\file2.txt
```

### **107. Create file using echo**

```
Command - (code view)
root@lilyang - echo Hello World > C:\Users\LILYANG\Documents\newfile.txt

Output - (code view)
# No output if successful
```

### **108. Append text to file**

```
Command - (code view)
root@lilyang - echo "Additional Line" >> C:\Users\LILYANG\Documents\newfile.txt

Output - (code view)
# No output if successful
```

### **109. Type file with paging**

```
Command - (code view)
root@lilyang - more C:\Users\LILYANG\Documents\newfile.txt

Output - (code view)
Hello World!
Additional Line
--More--
```

### **110. Copy multiple files with extension**

```
Command - (code view)
root@lilyang - copy C:\Users\LILYANG\Documents\*.txt D:\Backup\

Output - (code view)
3 file(s) copied.
```

### **111. Move multiple files with extension**

```
Command - (code view)
root@lilyang - move C:\Users\LILYANG\Documents\*.txt D:\Backup\

Output - (code view)
3 file(s) moved.
```

### **112. Display first 10 lines of a file**

```
Command - (code view)
root@lilyang - powershell -command "Get-Content C:\Users\LILYANG\Documents\file1.txt -TotalCount 10"

Output - (code view)
Line 1
Line 2
Line 3
...
Line 10
```

### **113. Display last 10 lines of a file**

```
Command - (code view)
root@lilyang - powershell -command "Get-Content C:\Users\LILYANG\Documents\file1.txt | Select-Object -Last 10"

Output - (code view)
Line 91
Line 92
...
Line 100
```

### **114. Search text in all files in folder**

```
Command - (code view)
root@lilyang - findstr /s /i "Hello" C:\Users\LILYANG\Documents\*.txt

Output - (code view)
C:\Users\LILYANG\Documents\file1.txt:Hello World!
C:\Users\LILYANG\Documents\newfile.txt:Hello World!
```

### **115. Create empty file**

```
Command - (code view)
root@lilyang - type nul > C:\Users\LILYANG\Documents\emptyfile.txt

Output - (code view)
# No output if successful
```

### **116. Copy folder structure only**

```
Command - (code view)
root@lilyang - xcopy C:\Source D:\Backup /t /e

Output - (code view)
C:\Source\
C:\Source\SubFolder1\
C:\Source\SubFolder2\
...
```

### **117. Display all drives**

```
Command - (code view)
root@lilyang - wmic logicaldisk get name, description, filesystem

Output - (code view)
Description       FileSystem   Name
Local Fixed Disk  NTFS         C:
Local Fixed Disk  NTFS         D:
CD-ROM Disc      CDFS         E:
```

### **118. Check file existence**

```
Command - (code view)
root@lilyang - if exist C:\Users\LILYANG\Documents\file1.txt echo File exists

Output - (code view)
File exists
```

### **119. Create folder with nested subfolders**

```
Command - (code view)
root@lilyang - mkdir C:\Users\LILYANG\Documents\Folder1\Sub1\Sub2

Output - (code view)
# No output if successful
```

### **120. Display folder tree**

```
Command - (code view)
root@lilyang - tree C:\Users\LILYANG\Documents

Output - (code view)
Folder PATH listing
Volume serial number is XXXX-XXXX
C:\USERS\LILYANG\DOCUMENTS
│   file1.txt
│   file2.docx
└───TestFolder
    │   testfile.txt
```

### **121. Delete folder if exists**

```
Command - (code view)
root@lilyang - if exist C:\Users\LILYANG\Documents\TestFolder rmdir /s /q C:\Users\LILYANG\Documents\TestFolder

Output - (code view)
# No output if successful
```

### **122. Check folder size**

```
Command - (code view)
root@lilyang - powershell -command "Get-ChildItem 'C:\Users\LILYANG\Documents' -Recurse | Measure-Object -Property Length -Sum"

Output - (code view)
Count    : 10
Average  :
Sum      : 123456
Maximum  :
Minimum  :
Property : Length
```

### **123. List files sorted by size**

```
Command - (code view)
root@lilyang - powershell -command "Get-ChildItem C:\Users\LILYANG\Documents | Sort-Object Length"

Output - (code view)
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----        11/16/2025 12:05 PM      1024 file1.txt
-a----        11/16/2025 12:10 PM      2048 file2.docx
...
```

### **124. List files with full path**

```
Command - (code view)
root@lilyang - dir /s /b C:\Users\LILYANG\Documents

Output - (code view)
C:\Users\LILYANG\Documents\file1.txt
C:\Users\LILYANG\Documents\file2.docx
C:\Users\LILYANG\Documents\TestFolder\testfile.txt
```

### **125. Copy folder to another drive**

```
Command - (code view)
root@lilyang - xcopy C:\Users\LILYANG\Documents D:\DocumentsBackup /s /e /i

Output - (code view)
C:\Users\LILYANG\Documents\file1.txt -> D:\DocumentsBackup\file1.txt
C:\Users\LILYANG\Documents\file2.docx -> D:\DocumentsBackup\file2.docx
...
```

---
### **126. Show IP configuration**

```
Command - (code view)
root@lilyang - ipconfig

Output - (code view)
Windows IP Configuration

Ethernet adapter Ethernet:
   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 192.168.1.100
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
```

### **127. Show detailed IP configuration**

```
Command - (code view)
root@lilyang - ipconfig /all

Output - (code view)
Windows IP Configuration

   Host Name . . . . . . . . . . . . : LILYANG-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   Ethernet adapter Ethernet:
      Connection-specific DNS Suffix  . :
      Description . . . . . . . . . . : Intel(R) Ethernet Connection
      Physical Address. . . . . . . . : 00-1A-2B-3C-4D-5E
      DHCP Enabled. . . . . . . . . . : Yes
      IPv4 Address. . . . . . . . . . : 192.168.1.100(Preferred)
      Subnet Mask . . . . . . . . . . : 255.255.255.0
      Default Gateway . . . . . . . . : 192.168.1.1
      DNS Servers . . . . . . . . . . : 8.8.8.8
```

### **128. Release IP address**

```
Command - (code view)
root@lilyang - ipconfig /release

Output - (code view)
Windows IP Configuration

Ethernet adapter Ethernet:
   Media State . . . . . . . . . . . : Media disconnected
```

### **129. Renew IP address**

```
Command - (code view)
root@lilyang - ipconfig /renew

Output - (code view)
Windows IP Configuration

Ethernet adapter Ethernet:
   IPv4 Address. . . . . . . . . . . : 192.168.1.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
```

### **130. Flush DNS cache**

```
Command - (code view)
root@lilyang - ipconfig /flushdns

Output - (code view)
Windows IP Configuration
Successfully flushed the DNS Resolver Cache.
```

### **131. Display DNS cache**

```
Command - (code view)
root@lilyang - ipconfig /displaydns

Output - (code view)
Windows IP Configuration

    www.google.com
    ----------------------------------------
    Record Name . . . . . : www.google.com
    Record Type . . . . . : 1
    Time To Live  . . . . : 299
    Data Length  . . . . . : 4
    Section  . . . . . . . : Answer
    A (Host) Record . . . . : 172.217.164.100
```

### **132. Ping a host**

```
Command - (code view)
root@lilyang - ping 8.8.8.8

Output - (code view)
Pinging 8.8.8.8 with 32 bytes of data:
Reply from 8.8.8.8: bytes=32 time=14ms TTL=117
Reply from 8.8.8.8: bytes=32 time=13ms TTL=117
...
Ping statistics for 8.8.8.8:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
```

### **133. Ping with continuous mode**

```
Command - (code view)
root@lilyang - ping 8.8.8.8 -t

Output - (code view)
Reply from 8.8.8.8: bytes=32 time=14ms TTL=117
Reply from 8.8.8.8: bytes=32 time=13ms TTL=117
# Ctrl+C to stop
```

### **134. Traceroute a host**

```
Command - (code view)
root@lilyang - tracert www.google.com

Output - (code view)
Tracing route to www.google.com [172.217.164.100]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  192.168.1.1
  2    10 ms     9 ms    10 ms  10.0.0.1
  3    14 ms    15 ms    13 ms  172.217.164.100
Trace complete.
```

### **135. Display routing table**

```
Command - (code view)
root@lilyang - route print

Output - (code view)
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
0.0.0.0                    0.0.0.0          192.168.1.1   192.168.1.100  25
127.0.0.0                  255.0.0.0        On-link       127.0.0.1      331
...
```

### **136. Display ARP cache**

```
Command - (code view)
root@lilyang - arp -a

Output - (code view)
Interface: 192.168.1.100 --- 0x3
  Internet Address      Physical Address      Type
  192.168.1.1           00-1A-2B-3C-4D-5E     dynamic
  192.168.1.101         00-1A-2B-3C-4D-5F     dynamic
```

### **137. Display active TCP connections**

```
Command - (code view)
root@lilyang - netstat

Output - (code view)
Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    192.168.1.100:50456    172.217.164.100:443   ESTABLISHED
  TCP    192.168.1.100:50457    172.217.164.101:443   TIME_WAIT
...
```

### **138. Display all TCP/UDP connections**

```
Command - (code view)
root@lilyang - netstat -an

Output - (code view)
Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    0.0.0.0:80             0.0.0.0:0              LISTENING
  UDP    0.0.0.0:123            *:*
...
```

### **139. Display listening ports**

```
Command - (code view)
root@lilyang - netstat -an | find "LISTEN"

Output - (code view)
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
...
```

### **140. Show network interfaces**

```
Command - (code view)
root@lilyang - netsh interface show interface

Output - (code view)
Admin State    State          Type             Interface Name
Enabled        Connected      Dedicated        Ethernet
Enabled        Disconnected   Dedicated        Wi-Fi
```

### **141. Enable network interface**

```
Command - (code view)
root@lilyang - netsh interface set interface "Wi-Fi" enabled

Output - (code view)
# No output if successful
```

### **142. Disable network interface**

```
Command - (code view)
root@lilyang - netsh interface set interface "Wi-Fi" disabled

Output - (code view)
# No output if successful
```

### **143. Show wireless networks**

```
Command - (code view)
root@lilyang - netsh wlan show networks

Output - (code view)
SSID 1 : HomeNetwork
    Network type            : Infrastructure
    Authentication          : WPA2-Personal
    Encryption              : CCMP
SSID 2 : GuestNetwork
...
```

### **144. Connect to Wi-Fi**

```
Command - (code view)
root@lilyang - netsh wlan connect name="HomeNetwork"

Output - (code view)
Connection request was completed successfully.
```

### **145. Disconnect from Wi-Fi**

```
Command - (code view)
root@lilyang - netsh wlan disconnect

Output - (code view)
Successfully disconnected from Wi-Fi network.
```

### **146. Display Wi-Fi profiles**

```
Command - (code view)
root@lilyang - netsh wlan show profiles

Output - (code view)
Profiles on interface Wi-Fi:

Group policy profiles (read only)
---------------------------------
<None>

User profiles
-------------
All User Profile     : HomeNetwork
All User Profile     : GuestNetwork
```

### **147. Show Wi-Fi profile key**

```
Command - (code view)
root@lilyang - netsh wlan show profile name="HomeNetwork" key=clear

Output - (code view)
Key Content            : MySecretPassword
```

### **148. Ping broadcast address**

```
Command - (code view)
root@lilyang - ping 192.168.1.255

Output - (code view)
Reply from 192.168.1.255: bytes=32 time<1ms TTL=128
...
```

### **149. Test route to host**

```
Command - (code view)
root@lilyang - pathping www.google.com

Output - (code view)
Tracing route to www.google.com [172.217.164.100]
over a maximum of 30 hops:
...
Calculating statistics for 250 seconds...
```

### **150. Display MAC address**

```
Command - (code view)
root@lilyang - getmac

Output - (code view)
Physical Address    Transport Name
00-1A-2B-3C-4D-5E  \Device\Tcpip_{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}
...
```

---
### **151. Display open ports by process**

```
Command - (code view)
root@lilyang - netstat -ano

Output - (code view)
Proto  Local Address          Foreign Address        State           PID
TCP    0.0.0.0:80             0.0.0.0:0              LISTENING       1234
TCP    192.168.1.100:50456    172.217.164.100:443    ESTABLISHED     5678
...
```

### **152. Kill process by PID**

```
Command - (code view)
root@lilyang - taskkill /PID 5678 /F

Output - (code view)
SUCCESS: The process with PID 5678 has been terminated.
```

### **153. Display network statistics**

```
Command - (code view)
root@lilyang - netstat -s

Output - (code view)
IPv4 Statistics
  Packets Received                 = 12345
  Received Header Errors           = 0
  Received Address Errors          = 0
  Datagrams Forwarded              = 0
  ...
```

### **154. Show current TCP connections by application**

```
Command - (code view)
root@lilyang - netstat -b

Output - (code view)
TCP    192.168.1.100:50456    172.217.164.100:443    ESTABLISHED   chrome.exe
TCP    192.168.1.100:50457    172.217.164.101:443    TIME_WAIT     outlook.exe
...
```

### **155. Display interface statistics**

```
Command - (code view)
root@lilyang - netstat -e

Output - (code view)
Interface Statistics

                           Received            Sent
Bytes                    12345678           8765432
Unicast packets           1234               4321
Non-unicast packets        12                 21
...
```

### **156. Display multicast group membership**

```
Command - (code view)
root@lilyang - netsh interface ip show joins

Output - (code view)
Interface 1: Ethernet
  Multicast Group: 224.0.0.251
Interface 2: Wi-Fi
  Multicast Group: 239.255.255.250
...
```

### **157. Display current IP routes**

```
Command - (code view)
root@lilyang - netsh interface ip show route

Output - (code view)
Publish  Type    Destination      Mask           Gateway
Yes      Static  0.0.0.0          0.0.0.0        192.168.1.1
Yes      Manual  192.168.1.0      255.255.255.0  On-link
...
```

### **158. Display network interface statistics**

```
Command - (code view)
root@lilyang - netsh interface ipv4 show interfaces

Output - (code view)
Idx     Met   MTU    State      Name
1       25    1500   Connected  Ethernet
2       50    1500   Disconnected Wi-Fi
...
```

### **159. Reset TCP/IP stack**

```
Command - (code view)
root@lilyang - netsh int ip reset

Output - (code view)
Resetting Interface, OK!
Resetting Neighbor, OK!
...
Restart the computer to complete reset.
```

### **160. Reset Winsock catalog**

```
Command - (code view)
root@lilyang - netsh winsock reset

Output - (code view)
Successfully reset the Winsock Catalog. You must restart the computer.
```

### **161. Display current gateway**

```
Command - (code view)
root@lilyang - ipconfig | find "Default Gateway"

Output - (code view)
Default Gateway . . . . . . . . . : 192.168.1.1
```

### **162. Ping local gateway**

```
Command - (code view)
root@lilyang - ping 192.168.1.1

Output - (code view)
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64
...
```

### **163. Test DNS resolution**

```
Command - (code view)
root@lilyang - nslookup www.google.com

Output - (code view)
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
Name:    www.google.com
Addresses:  172.217.164.100
```

### **164. Display interface IPs**

```
Command - (code view)
root@lilyang - netsh interface ipv4 show addresses

Output - (code view)
Configuration for interface "Ethernet"
    DHCP enabled: Yes
    IP Address: 192.168.1.100
    Subnet Prefix: 255.255.255.0
    Default Gateway: 192.168.1.1
...
```

### **165. Enable DHCP on interface**

```
Command - (code view)
root@lilyang - netsh interface ipv4 set address name="Ethernet" source=dhcp

Output - (code view)
OK.
```

### **166. Set static IP**

```
Command - (code view)
root@lilyang - netsh interface ipv4 set address name="Ethernet" static 192.168.1.150 255.255.255.0 192.168.1.1

Output - (code view)
OK.
```

### **167. Set DNS server**

```
Command - (code view)
root@lilyang - netsh interface ipv4 set dns name="Ethernet" static 8.8.8.8

Output - (code view)
OK.
```

### **168. Add secondary DNS**

```
Command - (code view)
root@lilyang - netsh interface ipv4 add dns name="Ethernet" 8.8.4.4 index=2

Output - (code view)
OK.
```

### **169. Display firewall status**

```
Command - (code view)
root@lilyang - netsh advfirewall show allprofiles

Output - (code view)
Domain Profile Settings:
    State                                 ON
Private Profile Settings:
    State                                 ON
Public Profile Settings:
    State                                 ON
```

### **170. Enable firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall set allprofiles state on

Output - (code view)
Ok.
```

### **171. Disable firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall set allprofiles state off

Output - (code view)
Ok.
```

### **172. Show firewall rules**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall show rule name=all

Output - (code view)
Rule Name: Remote Desktop
    Enabled: Yes
    Direction: Inbound
    Action: Allow
...
```

### **173. Allow application through firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall add rule name="MyApp" dir=in action=allow program="C:\Program Files\MyApp\app.exe"

Output - (code view)
Ok.
```

### **174. Block application through firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall add rule name="BlockApp" dir=in action=block program="C:\Program Files\BlockApp\app.exe"

Output - (code view)
Ok.
```

### **175. Reset firewall to default**

```
Command - (code view)
root@lilyang - netsh advfirewall reset

Output - (code view)
Ok.
```

---
### **176. Display running processes**

```
Command - (code view)
root@lilyang - tasklist

Output - (code view)
Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
explorer.exe                   3456 Console                    1    120,000 K
chrome.exe                     5678 Console                    1    300,000 K
svchost.exe                    1234 Services                   0     50,000 K
...
```

### **177. Kill process by name**

```
Command - (code view)
root@lilyang - taskkill /IM notepad.exe /F

Output - (code view)
SUCCESS: The process "notepad.exe" with PID 4321 has been terminated.
```

### **178. Display system information**

```
Command - (code view)
root@lilyang - systeminfo

Output - (code view)
Host Name:                 LILYANG-PC
OS Name:                   Microsoft Windows 11 Pro
OS Version:                10.0.22621 N/A Build 22621
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
...
```

### **179. Display Windows version**

```
Command - (code view)
root@lilyang - ver

Output - (code view)
Microsoft Windows [Version 10.0.22621.1105]
```

### **180. Display uptime**

```
Command - (code view)
root@lilyang - net stats workstation | find "Statistics since"

Output - (code view)
Statistics since 11/14/2025 7:05:32 AM
```

### **181. View system environment variables**

```
Command - (code view)
root@lilyang - set

Output - (code view)
ALLUSERSPROFILE=C:\ProgramData
APPDATA=C:\Users\LILYANG\AppData\Roaming
COMPUTERNAME=LILYANG-PC
PATH=C:\Windows\system32;C:\Windows;C:\Program Files\...
...
```

### **182. Add environment variable**

```
Command - (code view)
root@lilyang - setx MY_VAR "HelloWorld"

Output - (code view)
SUCCESS: Specified value was saved.
```

### **183. Delete environment variable**

```
Command - (code view)
root@lilyang - setx MY_VAR ""

Output - (code view)
SUCCESS: Specified value was deleted.
```

### **184. Display current user**

```
Command - (code view)
root@lilyang - whoami

Output - (code view)
lilyang\lilyang
```

### **185. Display all users**

```
Command - (code view)
root@lilyang - net user

Output - (code view)
User accounts for \\LILYANG-PC

-------------------------------------------------------------------------------
Administrator            Guest                   lilyang
The command completed successfully.
```

### **186. Add new user**

```
Command - (code view)
root@lilyang - net user NewUser MyPassword123 /add

Output - (code view)
The command completed successfully.
```

### **187. Delete user**

```
Command - (code view)
root@lilyang - net user NewUser /delete

Output - (code view)
The command completed successfully.
```

### **188. Display groups**

```
Command - (code view)
root@lilyang - net localgroup

Output - (code view)
Aliases for \\LILYANG-PC
---------------------------------------
*Administrators
*Users
*Guests
*Remote Desktop Users
...
The command completed successfully.
```

### **189. Add user to group**

```
Command - (code view)
root@lilyang - net localgroup Administrators lilyang /add

Output - (code view)
The command completed successfully.
```

### **190. Remove user from group**

```
Command - (code view)
root@lilyang - net localgroup Administrators lilyang /delete

Output - (code view)
The command completed successfully.
```

### **191. Display system uptime (alternative)**

```
Command - (code view)
root@lilyang - wmic os get lastbootuptime

Output - (code view)
LastBootUpTime
20251114070532.500000+330
```

### **192. Shutdown system**

```
Command - (code view)
root@lilyang - shutdown /s /t 60

Output - (code view)
# System will shutdown in 60 seconds
```

### **193. Restart system**

```
Command - (code view)
root@lilyang - shutdown /r /t 60

Output - (code view)
# System will restart in 60 seconds
```

### **194. Abort shutdown**

```
Command - (code view)
root@lilyang - shutdown /a

Output - (code view)
The scheduled shutdown has been cancelled.
```

### **195. Log off current user**

```
Command - (code view)
root@lilyang - shutdown /l

Output - (code view)
# User will be logged off immediately
```

### **196. Hibernate system**

```
Command - (code view)
root@lilyang - shutdown /h

Output - (code view)
# System will hibernate immediately
```

### **197. Lock system**

```
Command - (code view)
root@lilyang - rundll32.exe user32.dll,LockWorkStation

Output - (code view)
# System locked immediately
```

### **198. View scheduled tasks**

```
Command - (code view)
root@lilyang - schtasks /query

Output - (code view)
Folder: \
TaskName                          Next Run Time          Status
================================ ====================== ========
Adobe Acrobat Update Task          11/16/2025 12:30 PM   Ready
GoogleUpdateTaskMachineCore        11/16/2025 12:25 PM   Ready
...
```

### **199. Run scheduled task**

```
Command - (code view)
root@lilyang - schtasks /run /tn "Adobe Acrobat Update Task"

Output - (code view)
SUCCESS: Attempted to run the scheduled task "Adobe Acrobat Update Task".
```

### **200. Stop scheduled task**

```
Command - (code view)
root@lilyang - schtasks /end /tn "Adobe Acrobat Update Task"

Output - (code view)
SUCCESS: Attempted to stop the scheduled task "Adobe Acrobat Update Task".
```

---

### **201. Display system boot configuration**

```
Command - (code view)
root@lilyang - bcdedit

Output - (code view)
Windows Boot Manager
-------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
...
```

### **202. Enable/disable services**

```
Command - (code view)
root@lilyang - sc query wuauserv

Output - (code view)
SERVICE_NAME: wuauserv
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 4  RUNNING
        WIN32_EXIT_CODE    : 0  (0x0)
        ...
```

### **203. Stop a service**

```
Command - (code view)
root@lilyang - net stop wuauserv

Output - (code view)
The Windows Update service is stopping.
The Windows Update service was stopped successfully.
```

### **204. Start a service**

```
Command - (code view)
root@lilyang - net start wuauserv

Output - (code view)
The Windows Update service was started successfully.
```

### **205. Display installed software**

```
Command - (code view)
root@lilyang - wmic product get name,version

Output - (code view)
Name                                       Version
Microsoft Edge                             117.0.2045.60
Google Chrome                              118.0.5993.70
Python 3.12                                3.12.0
...
```

### **206. Install software via MSI**

```
Command - (code view)
root@lilyang - msiexec /i "C:\Install\Example.msi" /quiet

Output - (code view)
# No output if successful (quiet mode)
```

### **207. Uninstall software via MSI**

```
Command - (code view)
root@lilyang - msiexec /x "C:\Install\Example.msi" /quiet

Output - (code view)
# No output if successful (quiet mode)
```

### **208. Display disk partitions**

```
Command - (code view)
root@lilyang - diskpart

Output - (code view)
DISKPART> list disk

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online         476 GB    10 MB
  Disk 1    Online         931 GB    0 B
```

### **209. Select disk**

```
Command - (code view)
root@lilyang - select disk 0

Output - (code view)
Disk 0 is now the selected disk.
```

### **210. Display partitions on disk**

```
Command - (code view)
root@lilyang - list partition

Output - (code view)
Partition ###  Type              Size     Offset
-------------  ----------------  -------  -------
Partition 1    Primary           100 MB   1024 KB
Partition 2    Primary           475 GB   101 MB
```

### **211. Display volume information**

```
Command - (code view)
root@lilyang - diskpart
DISKPART> list volume

Output - (code view)
Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
----------  ---  ----------  -----  ----------  -------  ---------  ----
Volume 0     C   Windows     NTFS   Partition    475 GB  Healthy    Boot
Volume 1     D   Data        NTFS   Partition    931 GB  Healthy
```

### **212. Format a partition**

```
Command - (code view)
root@lilyang - format D: /FS:NTFS /Q /V:DataBackup

Output - (code view)
The type of the file system is NTFS.
The quick format has been completed.
```

### **213. Check disk for errors**

```
Command - (code view)
root@lilyang - chkdsk D: /f

Output - (code view)
The type of the file system is NTFS.
Volume label is Data.
Stage 1: Examining basic file system structure ...
Windows has scanned the file system and found no problems.
```

### **214. Display disk usage**

```
Command - (code view)
root@lilyang - wmic logicaldisk get name,size,freespace,description

Output - (code view)
Description       FreeSpace       Size          Name
Local Fixed Disk  1234567890      476123456789  C:
Local Fixed Disk  9876543210      931987654321  D:
```

### **215. Display CPU information**

```
Command - (code view)
root@lilyang - wmic cpu get name,numberofcores,maxclockspeed

Output - (code view)
Name                                        NumberOfCores  MaxClockSpeed
Intel(R) Core(TM) i7-12700H CPU @ 2.30GHz  12             4600
```

### **216. Display memory information**

```
Command - (code view)
root@lilyang - systeminfo | findstr /C:"Total Physical Memory"

Output - (code view)
Total Physical Memory:     32,768 MB
```

### **217. Display running services**

```
Command - (code view)
root@lilyang - services.msc

Output - (code view)
# Opens the GUI Services Manager
```

### **218. Export list of services**

```
Command - (code view)
root@lilyang - sc query type= service state= all > C:\services.txt

Output - (code view)
# All services exported to C:\services.txt
```

### **219. Display event logs**

```
Command - (code view)
root@lilyang - wevtutil qe System /c:5 /f:text

Output - (code view)
Event[0]:
  Log Name: System
  Source: Microsoft-Windows-Kernel-General
  Date: 2025-11-16T12:30:00.000
  Event ID: 1
  Message: The system time has changed to ...
...
```

### **220. Clear event log**

```
Command - (code view)
root@lilyang - wevtutil cl System

Output - (code view)
# System event log cleared
```

### **221. Enable Remote Desktop**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f

Output - (code view)
The operation completed successfully.
```

### **222. Disable Remote Desktop**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 1 /f

Output - (code view)
The operation completed successfully.
```

### **223. Enable RDP through firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall set rule group="remote desktop" new enable=yes

Output - (code view)
Ok.
```

### **224. Disable RDP through firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall set rule group="remote desktop" new enable=no

Output - (code view)
Ok.
```

### **225. Display system uptime via WMIC**

```
Command - (code view)
root@lilyang - wmic os get lastbootuptime /value

Output - (code view)
LastBootUpTime=20251114070532.500000+330
```

---
### **226. Display current password policy**

```
Command - (code view)
root@lilyang - net accounts

Output - (code view)
Force user logoff            : Never
Maximum password age          : 42 days
Minimum password age          : 1 days
Minimum password length       : 8
Password history length       : 24
Lockout threshold             : 0
Lockout duration              : 30 minutes
Lockout observation window    : 30 minutes
```

### **227. Set maximum password age**

```
Command - (code view)
root@lilyang - net accounts /maxpwage:60

Output - (code view)
The command completed successfully.
```

### **228. Set minimum password length**

```
Command - (code view)
root@lilyang - net accounts /minpwlen:12

Output - (code view)
The command completed successfully.
```

### **229. Set password history**

```
Command - (code view)
root@lilyang - net accounts /uniquepw:10

Output - (code view)
The command completed successfully.
```

### **230. Set lockout threshold**

```
Command - (code view)
root@lilyang - net accounts /lockoutthreshold:5

Output - (code view)
The command completed successfully.
```

### **231. Set lockout duration**

```
Command - (code view)
root@lilyang - net accounts /lockoutduration:15

Output - (code view)
The command completed successfully.
```

### **232. Set lockout observation window**

```
Command - (code view)
root@lilyang - net accounts /lockoutwindow:15

Output - (code view)
The command completed successfully.
```

### **233. Enable account**

```
Command - (code view)
root@lilyang - net user lilyang /active:yes

Output - (code view)
The command completed successfully.
```

### **234. Disable account**

```
Command - (code view)
root@lilyang - net user lilyang /active:no

Output - (code view)
The command completed successfully.
```

### **235. Force user to change password at next login**

```
Command - (code view)
root@lilyang - net user lilyang /logonpasswordchg:yes

Output - (code view)
The command completed successfully.
```

### **236. Remove password requirement**

```
Command - (code view)
root@lilyang - net user lilyang *

Output - (code view)
Type a password for the user: 
Retype the password to confirm: 
# Password removed if left blank
```

### **237. Display group membership**

```
Command - (code view)
root@lilyang - net user lilyang

Output - (code view)
User name                    lilyang
Full Name                    Lily Yang
Comment                      
User's comment               
Country/region code           000 (System Default)
Account active                Yes
Account expires               Never
Password last set             11/01/2025 08:15:00 AM
Password expires              01/01/2026 08:15:00 AM
Password changeable           11/01/2025 08:15:00 AM
Password required             Yes
User may change password      Yes
Workstations allowed          All
Logon script                  
User profile                  
Home directory                
Last logon                    11/16/2025 08:30:00 AM

Local Group Memberships       *Administrators       *Users
Global Group memberships      *None
```

### **238. Add user to group**

```
Command - (code view)
root@lilyang - net localgroup "Remote Desktop Users" lilyang /add

Output - (code view)
The command completed successfully.
```

### **239. Remove user from group**

```
Command - (code view)
root@lilyang - net localgroup "Remote Desktop Users" lilyang /delete

Output - (code view)
The command completed successfully.
```

### **240. Enable Windows Defender**

```
Command - (code view)
root@lilyang - sc start WinDefend

Output - (code view)
SERVICE_NAME: WinDefend
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 4  RUNNING
...
```

### **241. Disable Windows Defender**

```
Command - (code view)
root@lilyang - sc stop WinDefend

Output - (code view)
SERVICE_NAME: WinDefend
        STATE              : 1  STOPPED
...
```

### **242. Display Windows Defender status**

```
Command - (code view)
root@lilyang - Get-MpComputerStatus

Output - (code view)
AMServiceEnabled             : True
AntispywareEnabled           : True
AntivirusEnabled             : True
RealTimeProtectionEnabled    : True
```

### **243. Update Windows Defender definitions**

```
Command - (code view)
root@lilyang - MpCmdRun.exe -SignatureUpdate

Output - (code view)
Update started...
Definitions updated successfully.
```

### **244. Run quick scan with Windows Defender**

```
Command - (code view)
root@lilyang - MpCmdRun.exe -Scan -ScanType 1

Output - (code view)
Quick scan started...
Scan completed. No threats found.
```

### **245. Run full scan with Windows Defender**

```
Command - (code view)
root@lilyang - MpCmdRun.exe -Scan -ScanType 2

Output - (code view)
Full scan started...
Scan completed. No threats found.
```

### **246. Enable BitLocker**

```
Command - (code view)
root@lilyang - manage-bde -on C: -RecoveryPassword

Output - (code view)
BitLocker Drive Encryption: Configuration Tool version 10.0.22621
Volume C: will be encrypted.
Recovery Password: 123456-789012-345678-901234-567890-123456-789012-345678
Encryption in progress...
```

### **247. Suspend BitLocker**

```
Command - (code view)
root@lilyang - manage-bde -protectors -disable C:

Output - (code view)
BitLocker Drive Encryption: Configuration Tool version 10.0.22621
All protectors for C: have been suspended.
```

### **248. Resume BitLocker**

```
Command - (code view)
root@lilyang - manage-bde -protectors -enable C:

Output - (code view)
All protectors for C: have been enabled.
```

### **249. Lock BitLocker drive**

```
Command - (code view)
root@lilyang - manage-bde -lock C:

Output - (code view)
C: is now locked.
```

### **250. Unlock BitLocker drive**

```
Command - (code view)
root@lilyang - manage-bde -unlock C: -RecoveryPassword <RecoveryKey>

Output - (code view)
C: unlocked successfully.
```

---
### **251. Display audit policies**

```
Command - (code view)
root@lilyang - auditpol /get /category:*

Output - (code view)
System audit policy
Category/Subcategory                      Setting
Account Logon                              Success and Failure
Account Management                         Success and Failure
Logon/Logoff                               Success and Failure
Object Access                              No Auditing
Policy Change                              Success
Privilege Use                               No Auditing
...
```

### **252. Enable auditing for logon events**

```
Command - (code view)
root@lilyang - auditpol /set /subcategory:"Logon" /success:enable /failure:enable

Output - (code view)
The operation completed successfully.
```

### **253. Disable auditing for logon events**

```
Command - (code view)
root@lilyang - auditpol /set /subcategory:"Logon" /success:disable /failure:disable

Output - (code view)
The operation completed successfully.
```

### **254. View effective permissions on a folder**

```
Command - (code view)
root@lilyang - icacls "C:\Users\LILYANG\Documents"

Output - (code view)
C:\Users\LILYANG\Documents NT AUTHORITY\SYSTEM:(I)(F)
                                     BUILTIN\Administrators:(I)(F)
                                     LILYANG:(I)(F)
Successfully processed 1 files; Failed processing 0 files
```

### **255. Grant full control to a user**

```
Command - (code view)
root@lilyang - icacls "C:\TestFolder" /grant lilyang:F

Output - (code view)
processed file: C:\TestFolder
Successfully processed 1 files; Failed processing 0 files
```

### **256. Remove permissions from a user**

```
Command - (code view)
root@lilyang - icacls "C:\TestFolder" /remove lilyang

Output - (code view)
processed file: C:\TestFolder
Successfully processed 1 files; Failed processing 0 files
```

### **257. Take ownership of a file/folder**

```
Command - (code view)
root@lilyang - takeown /F "C:\TestFolder" /R /D Y

Output - (code view)
SUCCESS: The file (or folder): "C:\TestFolder" now owned by user "LILYANG-PC\lilyang".
```

### **258. Enable Windows Firewall auditing**

```
Command - (code view)
root@lilyang - auditpol /set /subcategory:"Filtering Platform Policy Change" /success:enable /failure:enable

Output - (code view)
The operation completed successfully.
```

### **259. Disable Windows Firewall auditing**

```
Command - (code view)
root@lilyang - auditpol /set /subcategory:"Filtering Platform Policy Change" /success:disable /failure:disable

Output - (code view)
The operation completed successfully.
```

### **260. Display user logon sessions**

```
Command - (code view)
root@lilyang - quser

Output - (code view)
USERNAME       SESSIONNAME   ID  STATE   IDLE TIME  LOGON TIME
lilyang        console       1   Active      none   11/16/2025 08:30 AM
Administrator  rdp-tcp#1     2   Disc        1+02:15 11/15/2025 07:20 PM
```

### **261. Force logoff a user**

```
Command - (code view)
root@lilyang - logoff 2

Output - (code view)
# User with session ID 2 logged off successfully
```

### **262. View account lockout status**

```
Command - (code view)
root@lilyang - net user lilyang /domain

Output - (code view)
Account active               Yes
Account expires              Never
Password last set            11/01/2025
Password expires             01/01/2026
Password changeable          11/01/2025
Password required            Yes
User may change password     Yes
Account locked out           No
```

### **263. Enable SmartScreen Filter**

```
Command - (code view)
root@lilyang - powershell Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer" -Name "SmartScreenEnabled" -Value "RequireAdmin"

Output - (code view)
# No output; property set successfully
```

### **264. Disable SmartScreen Filter**

```
Command - (code view)
root@lilyang - powershell Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer" -Name "SmartScreenEnabled" -Value "Off"

Output - (code view)
# No output; property set successfully
```

### **265. Enable UAC**

```
Command - (code view)
root@lilyang - reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v EnableLUA /t REG_DWORD /d 1 /f

Output - (code view)
The operation completed successfully.
```

### **266. Disable UAC**

```
Command - (code view)
root@lilyang - reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v EnableLUA /t REG_DWORD /d 0 /f

Output - (code view)
The operation completed successfully.
```

### **267. Enable Windows Hello**

```
Command - (code view)
root@lilyang - powershell Enable-WindowsOptionalFeature -Online -FeatureName "WindowsHelloFace"

Output - (code view)
Path          :
Online        : True
RestartNeeded : False
```

### **268. Disable Windows Hello**

```
Command - (code view)
root@lilyang - powershell Disable-WindowsOptionalFeature -Online -FeatureName "WindowsHelloFace"

Output - (code view)
Path          :
Online        : True
RestartNeeded : False
```

### **269. Enable BitLocker recovery key backup to AD**

```
Command - (code view)
root@lilyang - manage-bde -protectors -adbackup C:

Output - (code view)
All key protectors successfully backed up to Active Directory.
```

### **270. Enable Network Level Authentication for RDP**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 1 /f

Output - (code view)
The operation completed successfully.
```

### **271. Disable Network Level Authentication for RDP**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 0 /f

Output - (code view)
The operation completed successfully.
```

### **272. Enable Secure Boot**

```
Command - (code view)
root@lilyang - powershell Confirm-SecureBootUEFI

Output - (code view)
True
```

### **273. Disable Secure Boot (requires BIOS)**

```
Command - (code view)
root@lilyang - powershell Confirm-SecureBootUEFI

Output - (code view)
False
```

### **274. Display all local security policies**

```
Command - (code view)
root@lilyang - secedit /export /cfg C:\secpol.cfg

Output - (code view)
# Local security policy exported to C:\secpol.cfg
```

### **275. Apply security template**

```
Command - (code view)
root@lilyang - secedit /configure /db secedit.sdb /cfg C:\secpol.cfg /overwrite

Output - (code view)
Security configuration applied successfully.
```

---
### **276. Display files in directory**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents

Output - (code view)
 Volume in drive C has no label.
 Volume Serial Number is 1234-ABCD

 Directory of C:\Users\LILYANG\Documents

11/16/2025  08:30 AM    <DIR>          .
11/16/2025  08:30 AM    <DIR>          ..
11/15/2025  02:15 PM             1,024 report.docx
11/14/2025  11:45 AM               512 notes.txt
...
```

### **277. Display hidden files**

```
Command - (code view)
root@lilyang - dir C:\Users\LILYANG\Documents /A:H

Output - (code view)
 Volume in drive C has no label.
 Volume Serial Number is 1234-ABCD

 Directory of C:\Users\LILYANG\Documents

11/16/2025  08:30 AM    <DIR>          .hiddenfolder
11/14/2025  11:45 AM               256 .secret.txt
```

### **278. Copy file**

```
Command - (code view)
root@lilyang - copy C:\Users\LILYANG\Documents\notes.txt D:\Backup\

Output - (code view)
1 file(s) copied.
```

### **279. Move file**

```
Command - (code view)
root@lilyang - move C:\Users\LILYANG\Documents\report.docx D:\Backup\

Output - (code view)
        1 file(s) moved.
```

### **280. Delete file**

```
Command - (code view)
root@lilyang - del D:\Backup\notes.txt

Output - (code view)
        D:\Backup\notes.txt
```

### **281. Delete folder**

```
Command - (code view)
root@lilyang - rmdir /S /Q D:\Backup\OldFolder

Output - (code view)
# Folder D:\Backup\OldFolder deleted
```

### **282. Create folder**

```
Command - (code view)
root@lilyang - mkdir D:\Backup\NewFolder

Output - (code view)
# Folder D:\Backup\NewFolder created
```

### **283. Rename file**

```
Command - (code view)
root@lilyang - ren D:\Backup\NewFolder\notes.txt notes_backup.txt

Output - (code view)
# File renamed successfully
```

### **284. Display file attributes**

```
Command - (code view)
root@lilyang - attrib D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
A    D:\Backup\NewFolder\notes_backup.txt
```

### **285. Set file to read-only**

```
Command - (code view)
root@lilyang - attrib +R D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
# File is now read-only
```

### **286. Remove read-only attribute**

```
Command - (code view)
root@lilyang - attrib -R D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
# Read-only removed
```

### **287. Compress file using built-in compression**

```
Command - (code view)
root@lilyang - compact /c D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
D:\Backup\NewFolder\notes_backup.txt  50% compressed
```

### **288. Decompress file**

```
Command - (code view)
root@lilyang - compact /u D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
D:\Backup\NewFolder\notes_backup.txt  decompressed
```

### **289. Display disk space**

```
Command - (code view)
root@lilyang - dir C:\

Output - (code view)
 Volume in drive C has no label.
 Volume Serial Number is 1234-ABCD

 Directory of C:\

Free Space: 120,345,678,912 bytes
```

### **290. Map network drive**

```
Command - (code view)
root@lilyang - net use Z: \\Server01\SharedFolder

Output - (code view)
The command completed successfully.
```

### **291. Disconnect network drive**

```
Command - (code view)
root@lilyang - net use Z: /delete

Output - (code view)
Z: was deleted successfully.
```

### **292. Display open files on network share**

```
Command - (code view)
root@lilyang - net file

Output - (code view)
ID  Path                                User Name    # Locks
1   \\Server01\SharedFolder\report.docx lilyang      0
...
```

### **293. Close open file on network share**

```
Command - (code view)
root@lilyang - net file 1 /close

Output - (code view)
The command completed successfully.
```

### **294. Search for file**

```
Command - (code view)
root@lilyang - dir C:\ /s /b | findstr "notes.txt"

Output - (code view)
C:\Users\LILYANG\Documents\notes.txt
D:\Backup\NewFolder\notes_backup.txt
```

### **295. Display folder size**

```
Command - (code view)
root@lilyang - powershell -command "Get-ChildItem 'D:\Backup\NewFolder' -Recurse | Measure-Object -Property Length -Sum"

Output - (code view)
Count    : 2
Average  :
Sum      : 1536
Maximum  :
Minimum  :
Property : Length
```

### **296. Create symbolic link**

```
Command - (code view)
root@lilyang - mklink /D D:\Backup\LinkToDocs C:\Users\LILYANG\Documents

Output - (code view)
symbolic link created for D:\Backup\LinkToDocs <<===>> C:\Users\LILYANG\Documents
```

### **297. Create hard link**

```
Command - (code view)
root@lilyang - mklink /H D:\Backup\notes_hard.txt C:\Users\LILYANG\Documents\notes.txt

Output - (code view)
hard link created for D:\Backup\notes_hard.txt <<===>> C:\Users\LILYANG\Documents\notes.txt
```

### **298. Display mounted volumes**

```
Command - (code view)
root@lilyang - mountvol

Output - (code view)
\\?\Volume{12345678-ABCD-1234-ABCD-1234567890AB}\
    C:\
\\?\Volume{87654321-DCBA-4321-DCBA-0987654321DC}\
    D:\
```

### **299. Create VHD file**

```
Command - (code view)
root@lilyang - powershell New-VHD -Path D:\Backup\MyDisk.vhdx -SizeBytes 1GB -Dynamic

Output - (code view)
Path          : D:\Backup\MyDisk.vhdx
Size          : 1 GB
Dynamic       : True
```

### **300. Mount VHD**

```
Command - (code view)
root@lilyang - powershell Mount-VHD -Path D:\Backup\MyDisk.vhdx

Output - (code view)
# VHD mounted successfully
```

---
### **301. Dismount VHD**

```
Command - (code view)
root@lilyang - powershell Dismount-VHD -Path D:\Backup\MyDisk.vhdx

Output - (code view)
# VHD dismounted successfully
```

### **302. Initialize disk**

```
Command - (code view)
root@lilyang - diskpart
DISKPART> select disk 2
DISKPART> attributes disk clear readonly
DISKPART> online disk
DISKPART> convert gpt

Output - (code view)
DiskPart successfully converted the selected disk to GPT.
```

### **303. Create partition**

```
Command - (code view)
root@lilyang - diskpart
DISKPART> create partition primary size=50000

Output - (code view)
DiskPart succeeded in creating the specified partition.
```

### **304. Format partition**

```
Command - (code view)
root@lilyang - format fs=ntfs label=Data quick

Output - (code view)
The type of the file system is NTFS.
The quick format has been completed.
```

### **305. Assign drive letter**

```
Command - (code view)
root@lilyang - diskpart
DISKPART> assign letter=E

Output - (code view)
DiskPart successfully assigned the drive letter or mount point.
```

### **306. Display folder permissions recursively**

```
Command - (code view)
root@lilyang - icacls "D:\Backup\NewFolder" /T

Output - (code view)
D:\Backup\NewFolder NT AUTHORITY\SYSTEM:(OI)(CI)(F)
                      BUILTIN\Administrators:(OI)(CI)(F)
                      LILYANG:(OI)(CI)(F)
Successfully processed 3 files; Failed processing 0 files
```

### **307. Enable file sharing on folder**

```
Command - (code view)
root@lilyang - net share BackupFolder=D:\Backup\NewFolder /grant:lilyang,full

Output - (code view)
The command completed successfully.
```

### **308. Stop file sharing**

```
Command - (code view)
root@lilyang - net share BackupFolder /delete

Output - (code view)
BackupFolder was deleted successfully.
```

### **309. Display shared folders**

```
Command - (code view)
root@lilyang - net share

Output - (code view)
Share name   Resource                        Remark
-------------------------------------------------------------------------------
C$           C:\                             Default share
ADMIN$       C:\Windows                      Remote Admin
BackupFolder D:\Backup\NewFolder             Shared Folder
The command completed successfully.
```

### **310. Encrypt file using EFS**

```
Command - (code view)
root@lilyang - cipher /e D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
Encrypting file D:\Backup\NewFolder\notes_backup.txt
1 file(s) encrypted.
```

### **311. Decrypt file using EFS**

```
Command - (code view)
root@lilyang - cipher /d D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
Decrypting file D:\Backup\NewFolder\notes_backup.txt
1 file(s) decrypted.
```

### **312. Display encryption status**

```
Command - (code view)
root@lilyang - cipher D:\Backup\NewFolder\notes_backup.txt

Output - (code view)
Listing D:\Backup\NewFolder\notes_backup.txt
E - File is encrypted
```

### **313. Enable Offline Files**

```
Command - (code view)
root@lilyang - control /name Microsoft.OfflineFiles

Output - (code view)
# Opens Offline Files control panel to enable/disable caching
```

### **314. Sync Offline Files**

```
Command - (code view)
root@lilyang - csccmd /syncall

Output - (code view)
Synchronization complete.
```

### **315. Display disk health status**

```
Command - (code view)
root@lilyang - wmic diskdrive get status,model,size

Output - (code view)
Model                       Status  Size
Samsung SSD 970 EVO Plus     OK      500107862016
Seagate Backup Plus HDD      OK      1000204886016
```

### **316. Run CHKDSK with repair**

```
Command - (code view)
root@lilyang - chkdsk E: /f /r

Output - (code view)
The type of the file system is NTFS.
Stage 1: Examining basic file system structure ...
Windows has made corrections to the file system.
```

### **317. Display disk partitions**

```
Command - (code view)
root@lilyang - wmic partition get Name,DiskIndex,Size,Type

Output - (code view)
Name            DiskIndex  Size          Type
Disk #0, Part 1 0          104857600     Primary
Disk #0, Part 2 0          476879360000  Primary
```

### **318. Display logical disks**

```
Command - (code view)
root@lilyang - wmic logicaldisk get DeviceID,DriveType,FileSystem,Size,FreeSpace

Output - (code view)
DeviceID  DriveType  FileSystem  Size          FreeSpace
C:        3          NTFS        476879360000  120345678912
D:        3          NTFS        931500000000  450123456789
```

### **319. Convert FAT32 to NTFS**

```
Command - (code view)
root@lilyang - convert D: /fs:ntfs

Output - (code view)
The type of the file system is FAT32.
Volume converted to NTFS.
```

### **320. Display disk fragmentation**

```
Command - (code view)
root@lilyang - defrag D: /A

Output - (code view)
Windows Disk Defragmenter
Analysis report for volume D:
  Total fragmented space: 120 MB
  Largest free space: 350 MB
```

### **321. Defragment disk**

```
Command - (code view)
root@lilyang - defrag D: /U /V

Output - (code view)
Microsoft Drive Optimizer
Pass 1: Starting...
Pass complete.  Fragmentation reduced to 5%
```

### **322. Display disk quota**

```
Command - (code view)
root@lilyang - fsutil quota query D:

Output - (code view)
Volume : D:
Quota entries: 12
```

### **323. Set disk quota**

```
Command - (code view)
root@lilyang - fsutil quota modify D: /u lilyang 500MB 600MB

Output - (code view)
Quota set successfully.
```

### **324. Disable disk quota**

```
Command - (code view)
root@lilyang - fsutil quota disable D:

Output - (code view)
Quota management disabled on D:
```

### **325. Enable disk quota**

```
Command - (code view)
root@lilyang - fsutil quota enforce D:

Output - (code view)
Quota management enabled on D:
```

---
### **326. Display IP configuration**

```
Command - (code view)
root@lilyang - ipconfig /all

Output - (code view)
Windows IP Configuration

   Host Name . . . . . . . . . . . . : LILYANG-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Ethernet0:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) Ethernet Connection
   Physical Address. . . . . . . . . : 00-1A-2B-3C-4D-5E
   DHCP Enabled. . . . . . . . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.1.100(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 192.168.1.1
```

### **327. Release IP address**

```
Command - (code view)
root@lilyang - ipconfig /release

Output - (code view)
Windows IP Configuration

   Ethernet adapter Ethernet0:
      Connection-specific DNS Suffix  . :
      IPv4 Address. . . . . . . . . . . : 0.0.0.0
      Subnet Mask . . . . . . . . . . . : 0.0.0.0
      Default Gateway . . . . . . . . . : 0.0.0.0
```

### **328. Renew IP address**

```
Command - (code view)
root@lilyang - ipconfig /renew

Output - (code view)
Windows IP Configuration

   Ethernet adapter Ethernet0:
      IPv4 Address. . . . . . . . . . . : 192.168.1.100
      Subnet Mask . . . . . . . . . . . : 255.255.255.0
      Default Gateway . . . . . . . . . : 192.168.1.1
```

### **329. Display network routes**

```
Command - (code view)
root@lilyang - route print

Output - (code view)
===========================================================================
Interface List
 10...00 1a 2b 3c 4d 5e ......Intel(R) Ethernet Connection
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
0.0.0.0                    0.0.0.0          192.168.1.1  192.168.1.100 25
192.168.1.0                255.255.255.0    On-link      192.168.1.100 281
===========================================================================
```

### **330. Display active connections**

```
Command - (code view)
root@lilyang - netstat -an

Output - (code view)
Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    192.168.1.100:445      0.0.0.0:0              LISTENING
  UDP    0.0.0.0:137            *:*
```

### **331. Display routing table (IPv6)**

```
Command - (code view)
root@lilyang - netsh interface ipv6 show route

Output - (code view)
Publish  Type  Met  Prefix                  Idx  Gateway
Yes      U    256  ::/0                    12   fe80::1
Yes      U    256  fe80::/64               12   On-link
```

### **332. Display DNS cache**

```
Command - (code view)
root@lilyang - ipconfig /displaydns

Output - (code view)
Windows IP Configuration

    www.google.com
    ----------------------------------------
    Record Name . . . . . : www.google.com
    Record Type . . . . . : 1
    Time To Live  . . . . : 300
    Data Length  . . . . .: 4
    Section . . . . . . . : Answer
    A Record . . . . . . .: 172.217.3.164
```

### **333. Flush DNS cache**

```
Command - (code view)
root@lilyang - ipconfig /flushdns

Output - (code view)
Windows IP Configuration
Successfully flushed the DNS Resolver Cache.
```

### **334. Ping a host**

```
Command - (code view)
root@lilyang - ping 8.8.8.8

Output - (code view)
Pinging 8.8.8.8 with 32 bytes of data:
Reply from 8.8.8.8: bytes=32 time=14ms TTL=120
Reply from 8.8.8.8: bytes=32 time=13ms TTL=120
```

### **335. Trace route to host**

```
Command - (code view)
root@lilyang - tracert www.google.com

Output - (code view)
Tracing route to www.google.com [172.217.3.164]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  192.168.1.1
  2    13 ms    14 ms    12 ms  10.0.0.1
  3    15 ms    13 ms    14 ms  172.217.3.164
Trace complete.
```

### **336. Display open ports with listening status**

```
Command - (code view)
root@lilyang - netstat -an | find "LISTEN"

Output - (code view)
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
```

### **337. Display network interfaces**

```
Command - (code view)
root@lilyang - netsh interface show interface

Output - (code view)
Admin State    State          Type             Interface Name
Enabled        Connected      Dedicated        Ethernet0
Enabled        Disconnected   Dedicated        Wi-Fi
```

### **338. Enable network interface**

```
Command - (code view)
root@lilyang - netsh interface set interface "Ethernet0" admin=enabled

Output - (code view)
Ok.
```

### **339. Disable network interface**

```
Command - (code view)
root@lilyang - netsh interface set interface "Ethernet0" admin=disabled

Output - (code view)
Ok.
```

### **340. Display wireless networks**

```
Command - (code view)
root@lilyang - netsh wlan show networks

Output - (code view)
SSID 1 : HomeWiFi
    Network type            : Infrastructure
    Authentication          : WPA2-Personal
SSID 2 : OfficeWiFi
    Network type            : Infrastructure
    Authentication          : WPA2-Enterprise
```

### **341. Connect to Wi-Fi**

```
Command - (code view)
root@lilyang - netsh wlan connect name="HomeWiFi"

Output - (code view)
Connection request was completed successfully.
```

### **342. Disconnect Wi-Fi**

```
Command - (code view)
root@lilyang - netsh wlan disconnect

Output - (code view)
Successfully disconnected.
```

### **343. Display ARP table**

```
Command - (code view)
root@lilyang - arp -a

Output - (code view)
Interface: 192.168.1.100 --- 0x10
  Internet Address      Physical Address      Type
  192.168.1.1           00-1A-2B-3C-4D-5F   dynamic
  192.168.1.101         00-1A-2B-3C-4D-60   dynamic
```

### **344. Add static ARP entry**

```
Command - (code view)
root@lilyang - arp -s 192.168.1.200 00-1A-2B-3C-4D-70

Output - (code view)
# Static ARP entry added
```

### **345. Delete ARP entry**

```
Command - (code view)
root@lilyang - arp -d 192.168.1.200

Output - (code view)
# ARP entry deleted
```

### **346. Display network statistics**

```
Command - (code view)
root@lilyang - netstat -s

Output - (code view)
TCP Statistics for IPv4
  Packets Received              : 102345
  Packets Sent                  : 102300
  Segments Retransmitted        : 5
UDP Statistics for IPv4
  Datagrams Received            : 50000
  Datagrams Sent                : 50020
```

### **347. Enable Remote Desktop**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f

Output - (code view)
The operation completed successfully.
```

### **348. Disable Remote Desktop**

```
Command - (code view)
root@lilyang - reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 1 /f

Output - (code view)
The operation completed successfully.
```

### **349. Enable RDP firewall rule**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall set rule group="remote desktop" new enable=yes

Output - (code view)
Ok.
```

### **350. Disable RDP firewall rule**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall set rule group="remote desktop" new enable=no

Output - (code view)
Ok.
```

---

### **351. Display RDP listener status**

```
Command - (code view)
root@lilyang - qwinsta

Output - (code view)
 SESSIONNAME       USERNAME                 ID  STATE   TYPE        DEVICE
 console           lilyang                   1  Active  rdpwd
 rdp-tcp#0         Administrator             2  Listen  rdpwd
```

### **352. Display open RDP sessions**

```
Command - (code view)
root@lilyang - query session

Output - (code view)
 SESSIONNAME       USERNAME                 ID  STATE   TYPE
 console           lilyang                   1  Active
 rdp-tcp#0         Administrator             2  Listen
```

### **353. Log off RDP session**

```
Command - (code view)
root@lilyang - logoff 2

Output - (code view)
# User with session ID 2 logged off successfully
```

### **354. Enable ICMP (Ping) in Windows Firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall add rule name="Allow ICMPv4-In" protocol=icmpv4:8,any dir=in action=allow

Output - (code view)
Ok.
```

### **355. Disable ICMP (Ping) in Windows Firewall**

```
Command - (code view)
root@lilyang - netsh advfirewall firewall delete rule name="Allow ICMPv4-In"

Output - (code view)
Ok.
```

### **356. Test network connectivity**

```
Command - (code view)
root@lilyang - Test-Connection www.google.com -Count 4

Output - (code view)
Source        Destination     Replies
------        -----------     -------
LILYANG-PC    www.google.com  4/4 Successful
```

### **357. Display listening ports with process IDs**

```
Command - (code view)
root@lilyang - netstat -ano | find "LISTEN"

Output - (code view)
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       852
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING       4
```

### **358. Kill process by PID**

```
Command - (code view)
root@lilyang - taskkill /PID 852 /F

Output - (code view)
SUCCESS: The process with PID 852 has been terminated.
```

### **359. Display network adapter statistics**

```
Command - (code view)
root@lilyang - netstat -e

Output - (code view)
Interface Statistics

                   Received            Sent
Bytes               123456789       98765432
Unicast packets     123456          98765
Errors              0               0
Discarded           0               0
```

### **360. Display TCP connections with process names**

```
Command - (code view)
root@lilyang - netstat -b -n

Output - (code view)
TCP    192.168.1.100:50000  172.217.3.164:443  ESTABLISHED  chrome.exe
TCP    192.168.1.100:50001  172.217.3.164:443  ESTABLISHED  powershell.exe
```

### **361. Configure static IP**

```
Command - (code view)
root@lilyang - netsh interface ip set address name="Ethernet0" static 192.168.1.50 255.255.255.0 192.168.1.1

Output - (code view)
Ok.
```

### **362. Set DNS server**

```
Command - (code view)
root@lilyang - netsh interface ip set dns name="Ethernet0" static 8.8.8.8

Output - (code view)
Ok.
```

### **363. Set secondary DNS server**

```
Command - (code view)
root@lilyang - netsh interface ip add dns name="Ethernet0" 8.8.4.4 index=2

Output - (code view)
Ok.
```

### **364. Display network profiles**

```
Command - (code view)
root@lilyang - netsh wlan show profiles

Output - (code view)
Profiles on interface Wi-Fi:

Group policy profiles (read only)
---------------------------------
<None>

User profiles
-------------
    HomeWiFi
    OfficeWiFi
```

### **365. Export Wi-Fi profile**

```
Command - (code view)
root@lilyang - netsh wlan export profile name="HomeWiFi" folder="D:\Backup" key=clear

Output - (code view)
Profile HomeWiFi has been exported to D:\Backup\HomeWiFi.xml
```

### **366. Import Wi-Fi profile**

```
Command - (code view)
root@lilyang - netsh wlan add profile filename="D:\Backup\HomeWiFi.xml"

Output - (code view)
Profile HomeWiFi added on interface Wi-Fi.
```

### **367. Enable network adapter via PowerShell**

```
Command - (code view)
root@lilyang - Enable-NetAdapter -Name "Ethernet0"

Output - (code view)
Name                      InterfaceDescription       Status
----                      --------------------       ------
Ethernet0                 Intel(R) Ethernet          Up
```

### **368. Disable network adapter via PowerShell**

```
Command - (code view)
root@lilyang - Disable-NetAdapter -Name "Ethernet0"

Output - (code view)
Name                      InterfaceDescription       Status
----                      --------------------       ------
Ethernet0                 Intel(R) Ethernet          Disabled
```

### **369. Display network adapter MAC addresses**

```
Command - (code view)
root@lilyang - getmac /v /fo list

Output - (code view)
Connection Name: Ethernet0
Network Adapter: Intel(R) Ethernet Connection
Physical Address: 00-1A-2B-3C-4D-5E
Transport Name : \Device\Tcpip_{12345678-ABCD-1234-ABCD-1234567890AB}
```

### **370. Ping broadcast**

```
Command - (code view)
root@lilyang - ping 192.168.1.255 -t

Output - (code view)
Pinging 192.168.1.255 with 32 bytes of data:
Reply from 192.168.1.50: bytes=32 time<1ms TTL=128
Reply from 192.168.1.51: bytes=32 time<1ms TTL=128
```

### **371. Display active network shares**

```
Command - (code view)
root@lilyang - net view \\192.168.1.100

Output - (code view)
Shared resources at \\192.168.1.100

Share name   Type
-------------------
BackupFolder Disk
Public       Disk
```

### **372. Map network drive with credentials**

```
Command - (code view)
root@lilyang - net use Z: \\192.168.1.100\BackupFolder /user:LILYANG password123

Output - (code view)
The command completed successfully.
```

### **373. Test remote port connectivity**

```
Command - (code view)
root@lilyang - Test-NetConnection -ComputerName www.google.com -Port 443

Output - (code view)
ComputerName           : www.google.com
RemoteAddress          : 142.250.190.68
RemotePort             : 443
TcpTestSucceeded       : True
```

### **374. Enable remote management (WinRM)**

```
Command - (code view)
root@lilyang - winrm quickconfig

Output - (code view)
WinRM service started.
WinRM firewall exception enabled.
```

### **375. Disable remote management (WinRM)**

```
Command - (code view)
root@lilyang - winrm quickconfig -q

Output - (code view)
WinRM service stopped.
WinRM firewall exception disabled.
```

---
### **376. Display system information**

```
Command - (code view)
root@lilyang - systeminfo

Output - (code view)
Host Name:                 LILYANG-PC
OS Name:                   Microsoft Windows 11 Pro
OS Version:                10.0.22621 N/A Build 22621
System Manufacturer:       Dell Inc.
System Model:              XPS 15 9500
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 165 Stepping 2 GenuineIntel ~2600 Mhz
Total Physical Memory:     16,384 MB
Available Physical Memory: 9,812 MB
```

### **377. Display running processes**

```
Command - (code view)
root@lilyang - tasklist

Output - (code view)
Image Name                     PID Session Name   Session# Memory Usage
========================= ======== ============ ======== ============
explorer.exe                   1324 Console       1       120,000 K
chrome.exe                     2345 Console       1       350,000 K
powershell.exe                 3456 Console       1       50,000 K
```

### **378. Kill a process by name**

```
Command - (code view)
root@lilyang - taskkill /IM chrome.exe /F

Output - (code view)
SUCCESS: The process "chrome.exe" with PID 2345 has been terminated.
```

### **379. Display CPU usage**

```
Command - (code view)
root@lilyang - wmic cpu get loadpercentage

Output - (code view)
LoadPercentage
15
```

### **380. Display memory usage**

```
Command - (code view)
root@lilyang - wmic OS get FreePhysicalMemory,TotalVisibleMemorySize /Value

Output - (code view)
FreePhysicalMemory=9812345
TotalVisibleMemorySize=16384000
```

### **381. Display system uptime**

```
Command - (code view)
root@lilyang - net statistics workstation

Output - (code view)
Statistics since 11/16/2025 8:00:00 AM
```

### **382. Monitor real-time CPU & memory usage**

```
Command - (code view)
root@lilyang - perfmon /res

Output - (code view)
# Opens Resource Monitor showing CPU, memory, disk, and network usage in real-time
```

### **383. Display disk performance counters**

```
Command - (code view)
root@lilyang - typeperf "\LogicalDisk(_Total)\Disk Transfers/sec" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\LogicalDisk(_Total)\Disk Transfers/sec"
"11/16/2025 08:40:00.000","120.500"
"11/16/2025 08:40:05.000","115.750"
...
```

### **384. Display network adapter performance counters**

```
Command - (code view)
root@lilyang - typeperf "\Network Interface(*)\Bytes Total/sec" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\Network Interface(Intel[R] Ethernet)\Bytes Total/sec"
"11/16/2025 08:41:00.000","23456.0"
...
```

### **385. Display logged events (system)**

```
Command - (code view)
root@lilyang - wevtutil qe System /c:10 /f:text /rd:true

Output - (code view)
Event[0]:
  Log Name: System
  Source: Service Control Manager
  Event ID: 7036
  Task Category: None
  Level: Information
  Description: The Windows Update service entered the running state.
...
```

### **386. Display logged events (application)**

```
Command - (code view)
root@lilyang - wevtutil qe Application /c:10 /f:text /rd:true

Output - (code view)
Event[0]:
  Log Name: Application
  Source: Application Error
  Event ID: 1000
  Description: Faulting application name: chrome.exe, version: 116.0.5845.187, faulting module name: ntdll.dll
...
```

### **387. Display event logs with PowerShell**

```
Command - (code view)
root@lilyang - Get-EventLog -LogName System -Newest 5

Output - (code view)
   Index Time          EntryType   Source                 EventID Message
   ----- ----          ---------  ------                 ------- -------
   1543 11/16/2025 08:42 Information Service Control Manager 7036   The Windows Update service entered the running state.
...
```

### **388. Monitor real-time event logs**

```
Command - (code view)
root@lilyang - Get-EventLog -LogName System -Newest 1 -Wait

Output - (code view)
# Continuously displays new events as they occur
```

### **389. Display CPU performance counters**

```
Command - (code view)
root@lilyang - typeperf "\Processor(_Total)\% Processor Time" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\Processor(_Total)\% Processor Time"
"11/16/2025 08:43:00.000","12.5"
"11/16/2025 08:43:05.000","15.0"
...
```

### **390. Display memory performance counters**

```
Command - (code view)
root@lilyang - typeperf "\Memory\Available MBytes" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\Memory\Available MBytes"
"11/16/2025 08:44:00.000","9812"
"11/16/2025 08:44:05.000","9808"
...
```

### **391. Display page file usage**

```
Command - (code view)
root@lilyang - wmic pagefile list /format:list

Output - (code view)
AllocatedBaseSize=4096
CurrentUsage=1024
PeakUsage=1536
```

### **392. Display processes by memory usage**

```
Command - (code view)
root@lilyang - tasklist /FI "MEMUSAGE gt 50000"

Output - (code view)
Image Name                     PID Session Name   Session# Memory Usage
========================= ======== ============ ======== ============
chrome.exe                     2345 Console       1       350,000 K
explorer.exe                   1324 Console       1       120,000 K
```

### **393. Display processes by CPU usage**

```
Command - (code view)
root@lilyang - wmic path Win32_PerfFormattedData_PerfProc_Process get Name,PercentProcessorTime

Output - (code view)
Name              PercentProcessorTime
Idle              85
chrome.exe         8
powershell.exe     2
```

### **394. Start Performance Monitor**

```
Command - (code view)
root@lilyang - perfmon

Output - (code view)
# Opens Windows Performance Monitor GUI
```

### **395. Start Resource Monitor**

```
Command - (code view)
root@lilyang - resmon

Output - (code view)
# Opens Windows Resource Monitor GUI showing CPU, Memory, Disk, and Network usage
```

### **396. Monitor disk I/O in real-time**

```
Command - (code view)
root@lilyang - typeperf "\PhysicalDisk(_Total)\Disk Bytes/sec" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\PhysicalDisk(_Total)\Disk Bytes/sec"
"11/16/2025 08:45:00.000","23456"
...
```

### **397. Monitor network I/O in real-time**

```
Command - (code view)
root@lilyang - typeperf "\Network Interface(*)\Bytes Total/sec" -si 5 -sc 5

Output - (code view)
"(PDH-CSV 4.0)","\\LILYANG-PC\Network Interface(Intel[R] Ethernet)\Bytes Total/sec"
"11/16/2025 08:46:00.000","23456"
...
```

### **398. Display system uptime using PowerShell**

```
Command - (code view)
root@lilyang - (Get-CimInstance Win32_OperatingSystem).LastBootUpTime

Output - (code view)
11/16/2025 08:00:00 AM
```

### **399. Monitor real-time system performance (PowerShell)**

```
Command - (code view)
root@lilyang - Get-Counter -Counter "\Processor(_Total)\% Processor Time","\Memory\Available MBytes" -SampleInterval 5 -MaxSamples 5

Output - (code view)
Timestamp                CounterSamples
---------                --------------
11/16/2025 08:46:00      \\LILYANG-PC\Processor(_Total)\% Processor Time : 12.5
                         \\LILYANG-PC\Memory\Available MBytes           : 9812
...
```

### **400. Display top 5 memory-consuming processes**

```
Command - (code view)
root@lilyang - Get-Process | Sort-Object WorkingSet -Descending | Select-Object -First 5

Output - (code view)
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s) ProcessName
-------  ------    -----      ----- -----   ------ -----------
chrome     5000    350000     360000 1500     120.50 chrome
explorer   1500    120000     125000 800       25.10 explorer
powershell 300      50000      52000 200        5.20 powershell
```

---
