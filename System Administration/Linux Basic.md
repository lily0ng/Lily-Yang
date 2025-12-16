# **1. File & Directory Commands**

### **1. List files**

**Command**

```bash
root@lilyang:~# ls
```


**Output**

```bash
Desktop  Downloads  Pictures  Documents  file.txt  script.sh
```




### **2. Long listing**

```bash
root@lilyang:~# ls -l
```

```bash
-rw-r--r-- 1 root root   20 Nov 10  file.txt
drwxr-xr-x 2 root root 4096 Nov 10  Documents
```

### **3. Show hidden files**

```bash
root@lilyang:~# ls -a
```

```bash
.  ..  .bashrc  Documents  file.txt
```

### **4. List with human-readable sizes**

```bash
root@lilyang:~# ls -lh
```

---

### **5. Change directory**

```bash
root@lilyang:~# cd /etc
```

### **6. Go back**

```bash
root@lilyang:~# cd -
```

### **7. Go to home**

```bash
root@lilyang:~# cd ~
```

---

### **8. Print working directory**

```bash
root@lilyang:~# pwd
```

```bash
/root
```

---

### **9. Create file**

```bash
root@lilyang:~# touch test.txt
```

### **10. Create multiple files**

```bash
root@lilyang:~# touch a.txt b.txt c.txt
```

---

### **11. Create directory**

```bash
root@lilyang:~# mkdir projects
```

### **12. Create nested directories**

```bash
root@lilyang:~# mkdir -p dev/python/scripts
```

---

### **13. Remove file**

```bash
root@lilyang:~# rm file.txt
```

### **14. Remove directory**

```bash
root@lilyang:~# rmdir testdir
```

### **15. Remove directory with files**

```bash
root@lilyang:~# rm -rf foldername
```

---

### **16. Copy file**

```bash
root@lilyang:~# cp file.txt /tmp/
```

### **17. Copy directory**

```bash
root@lilyang:~# cp -r dir1 dir2
```

### **18. Move file**

```bash
root@lilyang:~# mv file.txt /root/Documents/
```

### **19. Rename file**

```bash
root@lilyang:~# mv oldname.txt newname.txt
```

---

### **20. View file contents**

```bash
root@lilyang:~# cat file.txt
```

### **21. Paginated view**

```bash
root@lilyang:~# less file.txt
```

### **22. Head (first 10 lines)**

```bash
root@lilyang:~# head file.txt
```

### **23. Tail (last 10 lines)**

```bash
root@lilyang:~# tail file.txt
```

### **24. Tail follow log**

```bash
root@lilyang:~# tail -f /var/log/syslog
```

---

# **2. File Permissions & Ownership**

### **25. Show permissions**

```bash
root@lilyang:~# ls -l file.txt
```

### **26. Change file permission**

```bash
root@lilyang:~# chmod 755 script.sh
```

### **27. Add execute permission**

```bash
root@lilyang:~# chmod +x script.sh
```

### **28. Change owner**

```bash
root@lilyang:~# chown user:user file.txt
```

### **29. Change owner recursively**

```bash
root@lilyang:~# chown -R www-data:www-data /var/www/
```

### **30. Change group**

```bash
root@lilyang:~# chgrp developers file.txt
```

---

# **3. Search Commands**

### **31. Search files by name**

```bash
root@lilyang:~# find / -name "file.txt"
```

### **32. Search by type (dir)**

```bash
root@lilyang:~# find . -type d -name "backup"
```

### **33. Search by size**

```bash
root@lilyang:~# find / -size +100M
```

---

### **34. Grep search in file**

```bash
root@lilyang:~# grep "error" logfile.txt
```

### **35. Recursive grep**

```bash
root@lilyang:~# grep -r "password" /etc/
```

### **36. Case-insensitive grep**

```bash
root@lilyang:~# grep -i "server" config.txt
```

---

# **4. Networking Commands**

### **37. Show IP**

```bash
root@lilyang:~# ip addr
```

### **38. Show network interfaces**

```bash
root@lilyang:~# ifconfig
```

### **39. Show routing table**

```bash
root@lilyang:~# ip route
```

### **40. Ping host**

```bash
root@lilyang:~# ping google.com
```

### **41. Check DNS**

```bash
root@lilyang:~# nslookup google.com
```

### **42. DNS query**

```bash
root@lilyang:~# dig google.com
```

### **43. Show open ports**

```bash
root@lilyang:~# netstat -tulnp
```

### **44. Show active connections**

```bash
root@lilyang:~# ss -tulnp
```

### **45. Test HTTP connection**

```bash
root@lilyang:~# curl -I https://1cloudtechnology.com
```

---

# **5. User & Group Management (Ubuntu/Debian/RHEL)**

### **46. Add user**

```bash
root@lilyang:~# adduser lily
```

### **47. Add user (RHEL)**

```bash
root@lilyang:~# useradd lily
```

### **48. Delete user**

```bash
root@lilyang:~# userdel lily
```

### **49. Add group**

```bash
root@lilyang:~# groupadd devops
```

### **50. Add user to group**

```bash
root@lilyang:~# usermod -aG devops lily
```

### **51. Change password**

```bash
root@lilyang:~# passwd lily
```

---

# **6. Package Management**

## **Ubuntu / Debian (APT)**

### **52. Update package list**

```bash
root@lilyang:~# apt update
```

### **53. Upgrade packages**

```bash
root@lilyang:~# apt upgrade -y
```

### **54. Install package**

```bash
root@lilyang:~# apt install nginx -y
```

### **55. Remove package**

```bash
root@lilyang:~# apt remove nginx -y
```

### **56. Purge package + config**

```bash
root@lilyang:~# apt purge nginx -y
```

### **57. Search packages**

```bash
root@lilyang:~# apt search docker
```

---

## **RedHat / CentOS / Rocky (YUM / DNF)**

### **58. Install package**

```bash
root@server ~# dnf install httpd -y
```

### **59. Update system**

```bash
root@server ~# dnf update -y
```

### **60. Remove package**

```bash
root@server ~# dnf remove httpd -y
```

---

# **7. System Information**

### **61. OS version**

```bash
root@lilyang:~# cat /etc/os-release
```

### **62. Kernel version**

```bash
root@lilyang:~# uname -r
```

### **63. All system info**

```bash
root@lilyang:~# uname -a
```

### **64. CPU info**

```bash
root@lilyang:~# lscpu
```

### **65. Memory info**

```bash
root@lilyang:~# free -h
```

### **66. Disk usage**

```bash
root@lilyang:~# df -h
```

### **67. Disk partition**

```bash
root@lilyang:~# lsblk
```

### **68. Processes**

```bash
root@lilyang:~# ps aux
```

### **69. Top processes**

```bash
root@lilyang:~# top
```

### **70. Modern system monitor**

```bash
root@lilyang:~# htop
```

---

# **8. Systemd Service Management**

### **71. Start service**

```bash
root@lilyang:~# systemctl start nginx
```

### **72. Stop service**

```bash
root@lilyang:~# systemctl stop nginx
```

### **73. Restart service**

```bash
root@lilyang:~# systemctl restart nginx
```

### **74. Enable at boot**

```bash
root@lilyang:~# systemctl enable nginx
```

### **75. Disable at boot**

```bash
root@lilyang:~# systemctl disable nginx
```

### **76. Check service status**

```bash
root@lilyang:~# systemctl status nginx
```

---

# **9. Archive & Compress**

### **77. Tar create**

```bash
root@lilyang:~# tar -cvf backup.tar folder/
```

### **78. Tar extract**

```bash
root@lilyang:~# tar -xvf backup.tar
```

### **79. Tar gzip**

```bash
root@lilyang:~# tar -czvf backup.tar.gz folder/
```

### **80. Tar unzip**

```bash
root@lilyang:~# tar -xzvf backup.tar.gz
```

### **81. Zip**

```bash
root@lilyang:~# zip file.zip file.txt
```

### **82. Unzip**

```bash
root@lilyang:~# unzip file.zip
```

---

# **10. Disk & Filesystem**

### **83. Mount device**

```bash
root@lilyang:~# mount /dev/sdb1 /mnt
```

### **84. Unmount**

```bash
root@lilyang:~# umount /mnt
```

### **85. Check filesystem**

```bash
root@lilyang:~# fsck /dev/sda1
```

### **86. Format drive**

```bash
root@lilyang:~# mkfs.ext4 /dev/sdb1
```

---

# **11. Logs**

### **87. View syslog**

```bash
root@lilyang:~# cat /var/log/syslog
```

### **88. View auth log**

```bash
root@lilyang:~# cat /var/log/auth.log
```

### **89. Journal logs**

```bash
root@lilyang:~# journalctl -xe
```

---

# **12. SSH & SCP**

### **90. SSH login**

```bash
root@lilyang:~# ssh user@server-ip
```

### **91. Copy file to remote**

```bash
root@lilyang:~# scp file.txt user@server:/tmp/
```

### **92. Copy directory to remote**

```bash
root@lilyang:~# scp -r folder user@server:/tmp/
```

---

# **13. Process Management**

### **93. Kill process**

```bash
root@lilyang:~# kill 1234
```

### **94. Kill by name**

```bash
root@lilyang:~# killall nginx
```

### **95. Background process**

```bash
root@lilyang:~# command &
```

### **96. Bring to foreground**

```bash
root@lilyang:~# fg
```

### **97. List jobs**

```bash
root@lilyang:~# jobs
```

---

# **14. Text Manipulation**

### **98. Count lines**

```bash
root@lilyang:~# wc -l file.txt
```

### **99. Sort file**

```bash
root@lilyang:~# sort file.txt
```

### **100. Remove duplicate lines**

```bash
root@lilyang:~# uniq file.txt
```

---

# **15. Download Tools**

### **101. wget**

```bash
root@lilyang:~# wget https://example.com/file.zip
```

### **102. curl download**

```bash
root@lilyang:~# curl -O https://example.com/file.zip
```

---

# **16. Firewall**

### **Ubuntu (UFW)**

### **103. Enable**

```bash
root@lilyang:~# ufw enable
```

### **104. Allow port**

```bash
root@lilyang:~# ufw allow 22
```

### **105. Deny port**

```bash
root@lilyang:~# ufw deny 80
```

---

### **RHEL (FirewallD)**

### **106. Allow port**

```bash
root@server:~# firewall-cmd --add-port=80/tcp --permanent
```

### **107. Reload**

```bash
root@server:~# firewall-cmd --reload
```

---

# **17. Crontab**

### **108. Edit cron**

```bash
root@lilyang:~# crontab -e
```

### **109. List cron**

```bash
root@lilyang:~# crontab -l
```

---

# **18. Environment**

### **110. Show env variables**

```bash
root@lilyang:~# env
```

### **111. Export variable**

```bash
root@lilyang:~# export NAME=LILY
```

---

# **19. Shell**

### **112. Show history**

```bash
root@lilyang:~# history
```

### **113. Clear screen**

```bash
root@lilyang:~# clear
```

---

# **20. Hardware**

### **114. USB devices**

```bash
root@lilyang:~# lsusb
```

### **115. PCI devices**

```bash
root@lilyang:~# lspci
```

---

# **21. Special Useful Commands**

### **116. Locate file (fast)**

```bash
root@lilyang:~# locate nginx.conf
```

### **117. Generate SSH key**

```bash
root@lilyang:~# ssh-keygen
```

### **118. View ARP table**

```bash
root@lilyang:~# arp -a
```

### **119. Host lookup**

```bash
root@lilyang:~# host google.com
```

### **120. Reboot**

```bash
root@lilyang:~# reboot
```

---

✔ Ubuntu + RHEL mixed  

---

#  **121. Check Disk Usage by Directory (du)**

```
root@lilyang:~# du -sh /var/log
```

```
120M    /var/log
```

---

#  **122. Show Disk Usage of All Directories**

```
root@lilyang:~# du -h --max-depth=1 /
```

```
4.0K    /media
2.1G    /usr
600M    /var
```

---

#  **123. Show Inode Usage**

```
root@lilyang:~# df -i
```

```
Filesystem      Inodes   IUsed  IFree  IUse% Mounted on
/dev/sda1      6553600  120345 6433255  2%   /
```

---

#  **124. Display Memory Info**

```
root@lilyang:~# free -m
```

```
              total   used   free
Mem:           7920   1930   5990
```

---

#  **125. Show CPU Hardware Info**

```
root@lilyang:~# lscpu
```

```
Architecture: x86_64
CPU(s):       8
Vendor ID:    GenuineIntel
```

---

#  **126. Show Block Devices**

```
root@lilyang:~# lsblk
```

```
sda      100G
 ├─sda1   96G /
 └─sda2    4G swap
```

---

#  **127. Show All Mounted Filesystems**

```
root@lilyang:~# mount | grep sda
```

```
/dev/sda1 on / type ext4 (rw,relatime)
```

---

#  **128. Show Kernel Messages**

```
root@lilyang:~# dmesg | tail
```

```
eth0: Link is Up 1000 Mbps
```

---

#  **129. Show System Boot Time**

```
root@lilyang:~# who -b
```

```
system boot  2025-11-16 10:21
```

---

#  **130. Show System Uptime**

```
root@lilyang:~# uptime
```

```
10:21:04 up  1:32,  load average: 0.30, 0.22, 0.18
```

---

#  **131. View CPU Temperature (if supported)**

```
root@lilyang:~# sensors
```

```
CPU Temp: +52.0°C
```

---

#  **132. List All Active Systemd Services**

```
root@lilyang:~# systemctl list-units --type=service
```

```
ssh.service         active running
cron.service        active running
```

---

#  **133. Check If a Service is Running**

```
root@lilyang:~# systemctl status ssh
```

```
Active: active (running)
```

---

#  **134. Start a Service**

```
root@lilyang:~# systemctl start ssh
```

```
(no output)
```

---

#  **135. Stop a Service**

```
root@lilyang:~# systemctl stop ssh
```

```
(no output)
```

---

#  **136. Enable Service at Boot**

```
root@lilyang:~# systemctl enable ssh
```

```
Created symlink ...
```

---

#  **137. Disable a Service**

```
root@lilyang:~# systemctl disable ssh
```

```
Removed /etc/systemd/system/multi-user.target.wants/ssh.service
```

---

#  **138. Check Open Ports**

```
root@lilyang:~# ss -tulnp
```

```
LISTEN 0 128 0.0.0.0:22
```

---

#  **139. Network Interface Information**

```
root@lilyang:~# ip a
```

```
eth0: state UP, mtu 1500
```

---

#  **140. Get Routing Table**

```
root@lilyang:~# ip route
```

```
default via 192.168.1.1 dev eth0
```

---

#  **141. Check DNS Resolution**

```
root@lilyang:~# dig google.com +short
```

```
142.250.68.238
```

---

#  **142. Ping Test**

```
root@lilyang:~# ping -c 3 8.8.8.8
```

```
3 packets transmitted, 3 received, 0% loss
```

---

#  **143. Traceroute**

```
root@lilyang:~# traceroute google.com
```

```
1 192.168.1.1
2 10.0.0.1
```

---

#  **144. Download File with wget**

```
root@lilyang:~# wget https://example.com/file.zip
```

```
Saving to: ‘file.zip’
```

---

#  **145. Download File with curl**

```
root@lilyang:~# curl -O https://example.com/file.zip
```

```
 100% |██████████████|
```

---

#  **146. HTTP GET Request**

```
root@lilyang:~# curl https://example.com
```

```
<html>...</html>
```

---

#  **147. Show TCP Connections**

```
root@lilyang:~# netstat -ant
```

```
ESTABLISHED  443 → 192.168.1.20
```

---

#  **148. Show ARP Table**

```
root@lilyang:~# arp -a
```

```
192.168.1.1 at 00:11:22:33:44:55
```

---

#  **149. Clear DNS Cache (systemd-resolve)**

```
root@lilyang:~# systemd-resolve --flush-caches
```

```
(no output)
```

---

#  **150. Create New User**

```
root@lilyang:~# adduser testuser
```

```
Adding user `testuser` ...
```

---

#  **151. Delete User**

```
root@lilyang:~# deluser testuser
```

```
Removing user `testuser` ...
```

---

#  **152. Create Group**

```
root@lilyang:~# groupadd admins
```

```
(no output)
```

---

#  **153. Add User to Group**

```
root@lilyang:~# usermod -aG admins testuser
```

```
(no output)
```

---

#  **154. Show User Info**

```
root@lilyang:~# id testuser
```

```
uid=1001 gid=1001 groups=1001,1002(admins)
```

---

#  **155. Show All Users**

```
root@lilyang:~# cat /etc/passwd
```

```
root:x:0:0:root:/root:/bin/bash
```

---

#  **156. Change User Password**

```
root@lilyang:~# passwd testuser
```

```
New password:
```

---

#  **157. List Permissions**

```
root@lilyang:~# ls -l /etc
```

```
-rw-r--r-- 1 root root hosts
```

---

#  **158. Change Permissions**

```
root@lilyang:~# chmod 755 script.sh
```

```
(no output)
```

---

#  **159. Change Ownership**

```
root@lilyang:~# chown root:admins file.txt
```

```
(no output)
```

---

#  **160. Find Files by Name**

```
root@lilyang:~# find / -name "*.log"
```

```
/var/log/syslog
```

---

#  **161. Find Files by Size**

```
root@lilyang:~# find / -size +100M
```

```
/var/lib/docker/overlay2/...
```

---

#  **162. Find Files Modified Recently**

```
root@lilyang:~# find / -mtime -1
```

```
/home/user/.bash_history
```

---

#  **163. Search Text in Files**

```
root@lilyang:~# grep -R "error" /var/log
```

```
error found in sshd.log
```

---

#  **164. Count Lines in File**

```
root@lilyang:~# wc -l /var/log/syslog
```

```
1245 /var/log/syslog
```

---

#  **165. Compare Two Files**

```
root@lilyang:~# diff file1.txt file2.txt
```

```
1c1
< hello
---
> hello world
```

---

#  **166. Combine Two Files**

```
root@lilyang:~# cat file1.txt file2.txt >> merged.txt
```

```
(no output)
```

---

#  **167. Sort File**

```
root@lilyang:~# sort names.txt
```

```
Aung
Kyaw
Zaw
```

---

#  **168. Remove Duplicate Lines**

```
root@lilyang:~# sort names.txt | uniq
```

```
Aung
Kyaw
Zaw
```

---

#  **169. Replace Text with sed**

```
root@lilyang:~# sed -i 's/nginx/apache/g' config.txt
```

```
(no output)
```

---

#  **170. Print First 20 Lines**

```
root@lilyang:~# head -20 file.txt
```

```
...
```

---

#  **171. Print Last 20 Lines**

```
root@lilyang:~# tail -20 file.txt
```

```
...
```

---

#  **172. Follow Log File in Real Time**

```
root@lilyang:~# tail -f /var/log/auth.log
```

```
Accepted password for root
```

---

#  **173. Create Symbolic Link**

```
root@lilyang:~# ln -s /var/log loglink
```

```
(no output)
```

---

#  **174. Create Hard Link**

```
root@lilyang:~# ln file1.txt file1_hard.txt
```

```
(no output)
```

---

#  **175. Copy Directory Recursively**

```
root@lilyang:~# cp -r dir1 dir2
```

```
(no output)
```

---

#  **176. Move File**

```
root@lilyang:~# mv file1.txt /tmp/
```

```
(no output)
```

---

#  **177. Delete Directory**

```
root@lilyang:~# rm -rf /tmp/test
```

```
(no output)
```

---

#  **178. View Kernel Parameters**

```
root@lilyang:~# sysctl -a
```

```
kernel.threads-max = 125674
```

---

#  **179. Modify Kernel Parameter (Temporary)**

```
root@lilyang:~# sysctl -w net.ipv4.ip_forward=1
```

```
net.ipv4.ip_forward = 1
```

---

#  **180. Modify Kernel Parameter (Permanent)**

```
root@lilyang:~# echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf
```

```
(no output)
```

---

#  **181. Check SELinux Mode (RHEL)**

```
[root@server ~]# getenforce
```

```
Enforcing
```

---

#  **182. Disable SELinux (Temporary)**

```
[root@server ~]# setenforce 0
```

```
Permissive
```

---

#  **183. Show Firewall Rules (RHEL)**

```
[root@server ~]# firewall-cmd --list-all
```

```
services: ssh dhcpv6-client
```

---

# **184. Add Firewall Rule**

```
[root@server ~]# firewall-cmd --add-service=http --permanent
```

```
success
```

---

#  **185. Reload Firewall**

```
[root@server ~]# firewall-cmd --reload
```

```
success
```

---

#  **186. Show iptables Rules**

```
root@lilyang:~# iptables -L
```

```
ACCEPT all -- anywhere anywhere
```

---

#  **187. Add iptables Rule**

```
root@lilyang:~# iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

```
(no output)
```

---

#  **188. Save iptables**

```
root@lilyang:~# iptables-save > /etc/iptables.rules
```

```
(no output)
```

---

#  **189. Check Open Files**

```
root@lilyang:~# lsof | head
```

```
systemd  PID 1
```

---

#  **190. Check Which Process Uses a Port**

```
root@lilyang:~# lsof -i :22
```

```
sshd  PID 590
```

---

#  **191. Kill Process by PID**

```
root@lilyang:~# kill 1234
```

```
(no output)
```

---

#  **192. Kill by Name**

```
root@lilyang:~# pkill nginx
```

```
(no output)
```

---

#  **193. Show Environment Variables**

```
root@lilyang:~# printenv
```

```
PATH=/usr/local/sbin:/usr/sbin:/usr/bin
```

---

#  **194. Set Environment Variable**

```
root@lilyang:~# export APP=test
```

```
(no output)
```

---

#  **195. View Bash History**

```
root@lilyang:~# history | tail
```

```
  993 ls
```

---

#  **196. Clear Bash History**

```
root@lilyang:~# history -c
```

```
(no output)
```

---

#  **197. Create a Cron Job**

```
root@lilyang:~# crontab -e
```

```
(no output)
```

---

#  **198. List Cron Jobs**

```
root@lilyang:~# crontab -l
```

```
0 2 * * * /usr/bin/backup.sh
```

---

#  **199. List All Scheduled Cron Jobs**

```
root@lilyang:~# ls /etc/cron.*
```

```
cron.daily  cron.weekly
```

---

#  **200. Create System Backup with tar**

```
root@lilyang:~# tar -czvf backup.tar.gz /etc
```

```
adding: etc/ssh/ ...
```

---

#  **201. Extract tar Archive**

```
root@lilyang:~# tar -xzvf backup.tar.gz
```

```
etc/ssh/sshd_config
```

---

#  **202. Zip Directory**

```
root@lilyang:~# zip -r logs.zip /var/log
```

```
adding: syslog
```

---

#  **203. Unzip File**

```
root@lilyang:~# unzip logs.zip
```

```
inflating: syslog
```

---

#  **204. Check Running Processes**

```
root@lilyang:~# top
```

```
PID USER PR NI VIRT RES %CPU %MEM TIME+
```

---

#  **205. Use htop (better top)**

```
root@lilyang:~# htop
```

```
(colored interactive view)
```

---

#  **206. Check System Journal Logs**

```
root@lilyang:~# journalctl -xe
```

```
sshd[2045]: Failed password
```

---

#  **207. View Boot Logs**

```
root@lilyang:~# journalctl -b
```

```
system boot log...
```

---

#  **208. Show Disk Health (SMART)**

```
root@lilyang:~# smartctl -a /dev/sda
```

```
SMART overall-health self-assessment test result: PASSED
```

---

#  **209. Test Disk Read Speed**

```
root@lilyang:~# hdparm -Tt /dev/sda
```

```
Timing buffered disk reads: 500 MB/s
```

---

#  **210. Benchmark with dd**

```
root@lilyang:~# dd if=/dev/zero of=test.img bs=1G count=1 oflag=direct
```

```
1073741824 bytes copied, 1.5 s, 715 MB/s
```

---

#  **211. Show PCI Hardware**

```
root@lilyang:~# lspci
```

```
00:1f.2 SATA controller: Intel Corporation
```

---

#  **212. Show USB Devices**

```
root@lilyang:~# lsusb
```

```
Bus 001 Device 003: SanDisk USB
```

---

#  **213. Kernel Info**

```
root@lilyang:~# uname -r
```

```
5.15.0-90-generic
```

---

#  **214. System Info Summary**

```
root@lilyang:~# neofetch
```

```
OS: Ubuntu 22.04 LTS
```

---

#  **215. Get System Release Info**

```
root@lilyang:~# cat /etc/os-release
```

```
NAME="Ubuntu"
```

---

#  **216. RHEL Version**

```
[root@server ~]# cat /etc/redhat-release
```

```
Red Hat Enterprise Linux 9.3
```

---

#  **217. Install Package (Ubuntu)**

```
root@lilyang:~# apt install htop -y
```

```
Setting up htop ...
```

---

#  **218. Update System (Ubuntu)**

```
root@lilyang:~# apt update && apt upgrade -y
```

```
Get:1 ...
```

---

#  **219. Install Package (RHEL)**

```
[root@server ~]# yum install htop -y
```

```
Installed: htop.x86_64
```

---

#  **220. Update System (RHEL)**

```
[root@server ~]# yum update -y
```

```
Updated: kernel ...
```

---

#  **221. Search Packages (Ubuntu)**

```
root@lilyang:~# apt search nginx
```

```
nginx/jammy ...
```

---

#  **222. Search Packages (RHEL)**

```
[root@server ~]# yum search nginx
```

```
nginx.x86_64 : High performance web server
```

---

#  **223. Remove Package**

```
root@lilyang:~# apt remove htop -y
```

```
Removing htop ...
```

---

#  **224. Clean APT Cache**

```
root@lilyang:~# apt autoclean
```

```
(no output)
```

---

#  **225. Show All Installed Packages**

```
root@lilyang:~# dpkg -l
```

```
ii  nginx 1.18.0-0ubuntu1
```

---

#  **226. Show RHEL RPM Packages**

```
[root@server ~]# rpm -qa | head
```

```
bash-5.1.8
```

---

#  **227. Install .deb Package**

```
root@lilyang:~# dpkg -i app.deb
```

```
Selecting previously unselected package
```

---

#  **228. Fix Broken Packages**

```
root@lilyang:~# apt --fix-broken install
```

```
Fixing dependencies ...
```

---

#  **229. Create New Bash Script**

```
root@lilyang:~# nano script.sh
```

```
(no output)
```

---

#  **230. Make Script Executable**

```
root@lilyang:~# chmod +x script.sh
```

```
(no output)
```

---

#  **231. Run Script**

```
root@lilyang:~# ./script.sh
```

```
Hello World
```

---

#  **232. Create Alias**

```
root@lilyang:~# echo "alias ll='ls -la'" >> ~/.bashrc
```

```
(no output)
```

---

#  **233. Reload Bash Config**

```
root@lilyang:~# source ~/.bashrc
```

```
(no output)
```

---

#  **234. Print Calendar**

```
root@lilyang:~# cal
```

```
   November 2025
Su Mo Tu We Th Fr Sa
```

---

#  **235. Time & Date**

```
root@lilyang:~# date
```

```
Sun Nov 16 12:22:40 MMT 2025
```

---

#  **236. Set Timezone**

```
root@lilyang:~# timedatectl set-timezone Asia/Yangon
```

```
(no output)
```

---

#  **237. Check Timezone**

```
root@lilyang:~# timedatectl
```

```
Time zone: Asia/Yangon (MMT)
```

---

#  **238. Sync Time (NTP)**

```
root@lilyang:~# timedatectl set-ntp true
```

```
(no output)
```

---

#  **239. Show Hostname**

```
root@lilyang:~# hostname
```

```
lilyang
```

---

#  **240. Change Hostname**

```
root@lilyang:~# hostnamectl set-hostname server01
```

```
(no output)
```

# **241. Check running processes (ps aux)**

```
root@lilyang:~# ps aux
```

```
root       1  0.0  0.1 168532  8484 ?     Ss   10:11   0:02 /sbin/init
root     723  0.1  0.3 276540 15432 ?     Ss   10:12   0:00 /usr/lib/systemd/systemd-journald
```

---

# **242. Show process tree**

```
root@lilyang:~# pstree
```

```
systemd─┬─NetworkManager─┬─dhclient
        ├─sshd───sshd───bash
        └─udisksd
```

---

# **243. Top (interactive process viewer)**

```
root@lilyang:~# top
```

```
PID USER   PR  NI  VIRT   RES  SHR S %CPU %MEM TIME+ COMMAND
723 root   20   0 276540 15432 8420 S  0.7  0.2 0:02 systemd-journal
```

---

# **244. htop — better process viewer**

```
root@server ~]# htop
```

```
CPU[|||||     ]  Mem[|||       ]  Tasks: 145
  PID USER  PRI  NI  VIRT   RES  S  CPU%  MEM%  Command
  723 root   20   0 276540 15432 S   1.0   0.2   systemd-journal
```

---

# **245. Kill a process**

```
root@lilyang:~# kill 1234
```

```
(no output)
```

---

# **246. Force kill**

```
root@lilyang:~# kill -9 1234
```

```
(no output)
```

---

# **247. Kill process by name**

```
root@lilyang:~# pkill nginx
```

```
(no output)
```

---

# **248. Kill all users' processes**

```
root@server ~]# pkill -u bob
```

```
(no output)
```

---

# **249. Check memory usage**

```
root@lilyang:~# free -h
```

```
               total        used        free
Mem:            7.6G        2.1G        4.9G
Swap:             0B          0B          0B
```

---

# **250. Check CPU info**

```
root@lilyang:~# lscpu
```

```
Model name: Intel(R) Xeon(R) CPU
CPU(s):    4
```

---

# **251. Check Linux kernel**

```
root@server ~]# uname -r
```

```
6.8.0-31-generic
```

---

# **252. Check system info**

```
root@lilyang:~# uname -a
```

```
Linux lilyang 6.8.0-31-generic x86_64 GNU/Linux
```

---

# **253. Show system boot logs**

```
root@lilyang:~# dmesg | head
```

```
[    0.000000] Linux version 6.8.0-31-generic ...
```

---

# **254. Journalctl — show logs**

```
root@server ~]# journalctl -xe
```

```
systemd[1]: Starting SSH Daemon...
sshd[715]: Server listening on 0.0.0.0 port 22.
```

---

# **255. Show logs for specific service**

```
root@lilyang:~# journalctl -u ssh
```

```
Started OpenSSH Daemon.
Accepted publickey for root from 192.168.1.10
```

---

# **256. Live logs (tail -f)**

```
root@lilyang:~# tail -f /var/log/syslog
```

```
Nov 16 10:12:01 CRON[843]: root CMD (/usr/lib/rotate)
```

---

# **257. Check disk partitions**

```
root@lilyang:~# lsblk
```

```
sda   8:0   0   80G  disk
├─sda1 8:1  0   80G part /
```

---

# **258. Human readable disk usage**

```
root@lilyang:~# df -h
```

```
Filesystem  Size  Used Avail Use%
/dev/sda1    80G   21G   57G  27%
```

---

# **259. Directory size**

```
root@server ~]# du -sh /var
```

```
2.1G    /var
```

---

# **260. Largest directories**

```
root@lilyang:~# du -ah / | sort -hr | head
```

```
2.1G /var
700M /usr
```

---

# **261. See mounted drives**

```
root@lilyang:~# mount | grep sda
```

```
/dev/sda1 on / type ext4 (rw,relatime)
```

---

# **262. Check filesystem type**

```
root@lilyang:~# df -T
```

```
/dev/sda1 ext4
```

---

# **263. Show block devices with UUID**

```
root@lilyang:~# blkid
```

```
/dev/sda1: UUID="01a3-ef91" TYPE="ext4"
```

---

# **264. Systemd — list services**

```
root@server ~]# systemctl list-units --type=service
```

```
sshd.service   loaded active running ...
cron.service   loaded active running ...
```

---

# **265. Start service**

```
root@server ~]# systemctl start nginx
```

```
(no output)
```

---

# **266. Stop service**

```
root@server ~]# systemctl stop nginx
```

```
(no output)
```

---

# **267. Restart service**

```
root@lilyang:~# systemctl restart apache2
```

```
(no output)
```

---

# **268. Service status**

```
root@lilyang:~# systemctl status ssh
```

```
Active: active (running)
```

---

# **269. Enable service at boot**

```
root@server ~]# systemctl enable firewalld
```

```
Created symlink /etc/systemd/system/multi-user.target.wants/firewalld.service
```

---

# **270. Disable service**

```
root@server ~]# systemctl disable firewalld
```

```
Removed symlink /etc/systemd/system/multi-user.target.wants/firewalld.service
```

---

# **271. Show failed services**

```
root@lilyang:~# systemctl --failed
```

```
0 loaded units listed.
```

---

# **272. Show power management**

```
root@lilyang:~# systemctl suspend
```

```
(no output)
```

---

# **273. Shutdown**

```
root@server ~]# shutdown -h now
```

```
Shutdown scheduled.
```

---

# **274. Reboot**

```
root@server ~]# reboot
```

```
Connection closing.
```

---

# **275. Check TCP connections**

```
root@lilyang:~# ss -tulpn
```

```
tcp  LISTEN  0 128 0.0.0.0:22  users:(("sshd",pid=723))
```

---

# **276. Netstat equivalent**

```
root@server ~]# netstat -anp | grep 22
```

```
tcp  0  0 0.0.0.0:22  0.0.0.0:*  LISTEN  723/sshd
```

---

# **277. Show ARP table**

```
root@lilyang:~# arp -a
```

```
192.168.1.1   dc:a6:32:8b:21  eth0
```

---

# **278. Show hostname**

```
root@lilyang:~# hostname
```

```
lilyang
```

---

# **279. Change hostname**

```
root@server ~]# hostnamectl set-hostname myserver
```

```
(no output)
```

---

# **280. Show network interfaces**

```
root@lilyang:~# ip a
```

```
eth0: 192.168.1.20/24
lo: 127.0.0.1/8
```

---

# **281. Bring interface down**

```
root@server ~]# ip link set eth0 down
```

```
(no output)
```

---

# **282. Bring interface up**

```
root@server ~]# ip link set eth0 up
```

```
(no output)
```

---

# **283. Add IP**

```
root@lilyang:~# ip addr add 192.168.1.50/24 dev eth0
```

```
(no output)
```

---

# **284. Delete IP**

```
root@lilyang:~# ip addr del 192.168.1.50/24 dev eth0
```

```
(no output)
```

---

# **285. Show routing table**

```
root@server ~]# ip route
```

```
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel
```

---

# **286. Add route**

```
root@lilyang:~# ip route add 10.0.0.0/24 via 192.168.1.1
```

```
(no output)
```

---

# **287. Delete route**

```
root@lilyang:~# ip route del 10.0.0.0/24
```

```
(no output)
```

---

# **288. Test port**

```
root@server ~]# nc -zv 192.168.1.50 22
```

```
Connection to 192.168.1.50 22 port [tcp/ssh] succeeded!
```

---

# **289. Scan ports**

```
root@lilyang:~# nmap 192.168.1.1
```

```
22/tcp open ssh
80/tcp open http
```

---

# **290. Check firewall (ufw)**

```
root@lilyang:~# ufw status
```

```
Status: inactive
```

---

# **291. Allow SSH**

```
root@lilyang:~# ufw allow 22
```

```
Rule added
```

---

# **292. Enable firewall**

```
root@lilyang:~# ufw enable
```

```
Firewall is active
```

---

# **293. RHEL firewall (firewalld)**

```
root@server ~]# firewall-cmd --list-all
```

```
services: ssh dhcpv6-client
```

---

# **294. Add firewall rule RHEL**

```
root@server ~]# firewall-cmd --permanent --add-service=http
```

```
success
```

---

# **295. Reload RHEL firewall**

```
root@server ~]# firewall-cmd --reload
```

```
success
```

---

# **296. Check SELinux status**

```
root@server ~]# sestatus
```

```
SELinux status: enabled
Mode: enforcing
```

---

# **297. Disable SELinux (temp)**

```
root@server ~]# setenforce 0
```

```
Permissive
```

---

# **298. SELinux Boolean list**

```
root@server ~]# getsebool -a | head
```

```
httpd_can_network_connect --> off
```

---

# **299. Check last logins**

```
root@lilyang:~# last
```

```
root pts/0 192.168.1.10 Sun 10:12
```

---

# **300. Check failed logins**

```
root@lilyang:~# faillog -u root
```

```
root  0 failures
```

---
# **301. List disks (lsblk)**

```
root@lilyang:~# lsblk
```

```
sda      8:0  0  100G disk
├─sda1   8:1  0   80G part /
└─sda2   8:2  0   20G part /home
```

---

# **302. Partition disk with fdisk**

```
root@lilyang:~# fdisk /dev/sdb
```

```
Command (m for help): n
```

---

# **303. Show partition table**

```
root@lilyang:~# fdisk -l /dev/sdb
```

```
Device     Boot Start   End Sectors Size Type
/dev/sdb1       2048 2097151 2095104 1G Linux
```

---

# **304. Create filesystem (ext4)**

```
root@lilyang:~# mkfs.ext4 /dev/sdb1
```

```
Creating filesystem with 131072 4k blocks
```

---

# **305. Mount partition**

```
root@lilyang:~# mount /dev/sdb1 /mnt
```

```
(no output)
```

---

# **306. Check mounted disks**

```
root@lilyang:~# df -h
```

```
/dev/sdb1   1.0G  4.0K  950M  1% /mnt
```

---

# **307. Add to fstab (persistent mount)**

```
root@lilyang:~# echo "/dev/sdb1 /mnt ext4 defaults 0 0" >> /etc/fstab
```

```
(no output)
```

---

# **308. Create swap**

```
root@lilyang:~# fallocate -l 2G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
```

```
Swap: 2G enabled
```

---

# **309. Check swap**

```
root@lilyang:~# swapon -s
```

```
Filename Type Size Used Priority
/swapfile file 2097148 0 -2
```

---

# **310. Show disk usage**

```
root@lilyang:~# du -sh /home
```

```
2.5G    /home
```

---

# **311. Show inode usage**

```
root@lilyang:~# df -i
```

```
Filesystem    Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1    6553600 120345 6433255   2% /
```

---

# **312. Create LVM physical volume**

```
root@lilyang:~# pvcreate /dev/sdc
```

```
Physical volume "/dev/sdc" successfully created
```

---

# **313. Create LVM volume group**

```
root@lilyang:~# vgcreate vgdata /dev/sdc
```

```
Volume group "vgdata" successfully created
```

---

# **314. Create logical volume**

```
root@lilyang:~# lvcreate -L 10G -n lvdata vgdata
```

```
Logical volume "lvdata" created
```

---

# **315. Make filesystem on LV**

```
root@lilyang:~# mkfs.ext4 /dev/vgdata/lvdata
```

```
Creating filesystem with 2621440 4k blocks
```

---

# **316. Mount logical volume**

```
root@lilyang:~# mount /dev/vgdata/lvdata /mnt/data
```

```
(no output)
```

---

# **317. Create RAID 1**

```
root@lilyang:~# mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdd /dev/sde
```

```
mdadm: array /dev/md0 started
```

---

# **318. Check RAID status**

```
root@lilyang:~# cat /proc/mdstat
```

```
md0 : active raid1 sdd[0] sde[1]
```

---

# **319. SSH login**

```
root@lilyang:~# ssh user@192.168.1.10
```

```
user@192.168.1.10's password:
Welcome to Ubuntu 22.04 LTS
```

---

# **320. Copy file with scp**

```
root@lilyang:~# scp file.txt user@192.168.1.10:/home/user/
```

```
file.txt          100%  1.2MB   1.1MB/s 00:01
```

---

# **321. Copy directory with scp**

```
root@lilyang:~# scp -r /var/log user@192.168.1.10:/home/user/logs
```

```
(no output)
```

---

# **322. SFTP login**

```
root@lilyang:~# sftp user@192.168.1.10
```

```
sftp> 
```

---

# **323. Upload file with SFTP**

```
sftp> put file.txt
```

```
Uploading file.txt to /home/user/file.txt
```

---

# **324. Download file with SFTP**

```
sftp> get file.txt
```

```
Fetching /home/user/file.txt
```

---

# **325. Git clone repository**

```
root@lilyang:~# git clone https://github.com/example/repo.git
```

```
Cloning into 'repo'...
```

---

# **326. Git status**

```
root@lilyang:~# git status
```

```
On branch main
nothing to commit, working tree clean
```

---

# **327. Git add file**

```
root@lilyang:~# git add file.txt
```

```
(no output)
```

---

# **328. Git commit**

```
root@lilyang:~# git commit -m "Add new file"
```

```
[main 123abc] Add new file
```

---

# **329. Git push**

```
root@lilyang:~# git push origin main
```

```
Counting objects: 3, done.
```

---

# **330. Git pull**

```
root@lilyang:~# git pull
```

```
Already up to date.
```

---

# **331. Create archive (tar.gz)**

```
root@lilyang:~# tar -czvf backup.tar.gz /etc
```

```
adding: etc/ssh/sshd_config
```

---

# **332. Extract archive**

```
root@lilyang:~# tar -xzvf backup.tar.gz
```

```
etc/ssh/sshd_config
```

---

# **333. Zip directory**

```
root@lilyang:~# zip -r logs.zip /var/log
```

```
adding: syslog
```

---

# **334. Unzip file**

```
root@lilyang:~# unzip logs.zip
```

```
inflating: syslog
```

---

# **335. Docker install (Ubuntu)**

```
root@lilyang:~# apt install docker.io -y
```

```
Setting up docker.io
```

---

# **336. Docker install (RHEL)**

```
root@server ~]# yum install docker -y
```

```
Installed: docker.x86_64
```

---

# **337. Start Docker**

```
root@lilyang:~# systemctl start docker
```

```
(no output)
```

---

# **338. Enable Docker at boot**

```
root@lilyang:~# systemctl enable docker
```

```
Created symlink
```

---

# **339. Docker version**

```
root@lilyang:~# docker --version
```

```
Docker version 24.0.2
```

---

# **340. List Docker images**

```
root@lilyang:~# docker images
```

```
REPOSITORY TAG IMAGE ID SIZE
ubuntu latest abc123 72MB
```

---

# **341. Pull Docker image**

```
root@lilyang:~# docker pull ubuntu:latest
```

```
latest: Pulling from library/ubuntu
```

---

# **342. Run Docker container**

```
root@lilyang:~# docker run -it ubuntu /bin/bash
```

```
root@container-id:/#
```

---

# **343. List running containers**

```
root@lilyang:~# docker ps
```

```
CONTAINER ID  IMAGE   STATUS   PORTS   NAMES
```

---

# **344. Stop Docker container**

```
root@lilyang:~# docker stop container_id
```

```
(container stopped)
```

---

# **345. Remove Docker container**

```
root@lilyang:~# docker rm container_id
```

```
(container removed)
```

---

# **346. Remove Docker image**

```
root@lilyang:~# docker rmi ubuntu
```

```
Deleted: sha256:abc123
```

---

# **347. Monitor CPU usage**

```
root@lilyang:~# mpstat
```

```
CPU   %usr %sys %idle
0     3.2  1.1  95.7
```

---

# **348. Monitor disk IO**

```
root@lilyang:~# iostat
```

```
Device tps  kB_read/s kB_wrtn/s
sda    5    100       200
```

---

# **349. Check memory usage**

```
root@lilyang:~# vmstat
```

```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
r  b   swpd free buff cache si so bi bo in cs us sy id wa st
1  0      0 4992  123  456   0  0  1  2  10 20  3  1 95  1  0
```

---

# **350. Monitor network usage**

```
root@lilyang:~# iftop
```

```
(Interactive bandwidth monitor)
```

---

# **351. Check open files**

```
root@lilyang:~# lsof
```

```
COMMAND PID USER  FD  TYPE DEVICE SIZE/OFF NODE NAME
sshd    723 root  3u  IPv4  12345 0t0    TCP *:22 (LISTEN)
```

---

# **352. Check file permissions**

```
root@lilyang:~# ls -l /etc/ssh
```

```
-rw-r--r-- 1 root root ssh_config
```

---

# **353. Change file permission**

```
root@lilyang:~# chmod 600 /etc/ssh/ssh_config
```

```
(no output)
```

---

# **354. Change file owner**

```
root@lilyang:~# chown root:root /etc/ssh/ssh_config
```

```
(no output)
```

---

# **355. Find files by name**

```
root@lilyang:~# find / -name "*.log"
```

```
/var/log/syslog
```

---

# **356. Find files by size**

```
root@lilyang:~# find / -size +100M
```

```
/var/lib/docker/overlay2/...
```

---

# **357. Search text in files**

```
root@lilyang:~# grep -R "error" /var/log
```

```
error found in sshd.log
```

---

# **358. Monitor system load**

```
root@lilyang:~# uptime
```

```
10:21:04 up  2:45,  load average: 0.30, 0.22, 0.18
```

---

# **359. Check last boot time**

```
root@lilyang:~# who -b
```

```
system boot  2025-11-16 10:21
```

---

# **360. System hardware summary**

```
root@lilyang:~# lshw -short
```

```
H/W path      Device     Class      Description
/0            sda        disk       100GB ATA Disk
/0/1          sda1       volume     80GB Partition
```

# **361. Trace network route**

```
root@lilyang:~# traceroute google.com
```

```
1  192.168.1.1  1.123 ms
2  10.10.10.1   5.234 ms
3  142.250.72.206  12.345 ms
```

---

# **362. Ping host**

```
root@lilyang:~# ping -c 4 8.8.8.8
```

```
4 packets transmitted, 4 received, 0% packet loss
```

---

# **363. Check DNS**

```
root@lilyang:~# dig google.com
```

```
;; ANSWER SECTION:
google.com.  299 IN A 142.250.72.206
```

---

# **364. Lookup domain**

```
root@lilyang:~# nslookup google.com
```

```
Name: google.com
Address: 142.250.72.206
```

---

# **365. Open port scan**

```
root@lilyang:~# nmap -p 1-65535 192.168.1.10
```

```
22/tcp open ssh
80/tcp open http
443/tcp open https
```

---

# **366. Monitor real-time logs**

```
root@lilyang:~# multitail /var/log/syslog
```

```
(Interactive syslog monitoring)
```

---

# **367. Monitor processes by name**

```
root@lilyang:~# pgrep -l apache2
```

```
723 apache2
724 apache2
```

---

# **368. Network interface statistics**

```
root@lilyang:~# ifconfig eth0
```

```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>
inet 192.168.1.20  netmask 255.255.255.0
```

---

# **369. Show route (netstat)**

```
root@lilyang:~# netstat -rn
```

```
Kernel IP routing table
Destination  Gateway  Genmask  Flags  Iface
0.0.0.0      192.168.1.1 0.0.0.0 UG eth0
```

---

# **370. TCP dump capture**

```
root@lilyang:~# tcpdump -i eth0 -c 10
```

```
10 packets captured
```

---

# **371. Firewall check**

```
root@lilyang:~# iptables -L
```

```
Chain INPUT (policy ACCEPT)
Chain FORWARD (policy ACCEPT)
Chain OUTPUT (policy ACCEPT)
```

---

# **372. Add firewall rule (iptables)**

```
root@lilyang:~# iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
```

```
(no output)
```

---

# **373. Delete firewall rule**

```
root@lilyang:~# iptables -D INPUT -p tcp --dport 8080 -j ACCEPT
```

```
(no output)
```

---

# **374. Fail2Ban status**

```
root@lilyang:~# fail2ban-client status
```

```
Status
|- Number of jail: 2
```

---

# **375. User management — add user**

```
root@lilyang:~# adduser alice
```

```
Adding user 'alice' ...
```

---

# **376. User management — delete user**

```
root@lilyang:~# userdel -r alice
```

```
(no output)
```

---

# **377. Group management — add group**

```
root@lilyang:~# groupadd devops
```

```
(no output)
```

---

# **378. Add user to group**

```
root@lilyang:~# usermod -aG devops bob
```

```
(no output)
```

---

# **379. Check groups**

```
root@lilyang:~# groups bob
```

```
bob : bob devops
```

---

# **380. Check sudo privileges**

```
root@lilyang:~# sudo -l
```

```
User bob may run the following commands:
(ALL : ALL) ALL
```

---

# **381. Monitor disk changes**

```
root@lilyang:~# inotifywait -m /var/log
```

```
/var/log/ MODIFY syslog
```

---

# **382. Monitor file changes**

```
root@lilyang:~# watch -n 2 ls -l /var/log
```

```
(every 2 seconds refresh)
```

---

# **383. Backup directory (rsync)**

```
root@lilyang:~# rsync -av /var/www /backup/www
```

```
sent 10M bytes  received 2M bytes
```

---

# **384. Backup remote (rsync over SSH)**

```
root@lilyang:~# rsync -avz /var/www user@192.168.1.10:/backup
```

```
sent 10M bytes  received 2M bytes
```

---

# **385. Compress with gzip**

```
root@lilyang:~# gzip file.txt
```

```
(file.txt.gz created)
```

---

# **386. Decompress gzip**

```
root@lilyang:~# gunzip file.txt.gz
```

```
(file.txt restored)
```

---

# **387. Compress with bzip2**

```
root@lilyang:~# bzip2 file.txt
```

```
(file.txt.bz2 created)
```

---

# **388. Decompress bzip2**

```
root@lilyang:~# bunzip2 file.txt.bz2
```

```
(file.txt restored)
```

---

# **389. Compress with xz**

```
root@lilyang:~# xz file.txt
```

```
(file.txt.xz created)
```

---

# **390. Decompress xz**

```
root@lilyang:~# unxz file.txt.xz
```

```
(file.txt restored)
```

---

# **391. Check crontab**

```
root@lilyang:~# crontab -l
```

```
* * * * * /usr/bin/backup.sh
```

---

# **392. Edit crontab**

```
root@lilyang:~# crontab -e
```

```
(edit file)
```

---

# **393. List installed packages (Ubuntu)**

```
root@lilyang:~# dpkg -l | head
```

```
ii  bash 5.1-2ubuntu1 amd64
```

---

# **394. List installed packages (RHEL)**

```
root@server ~]# rpm -qa | head
```

```
bash-5.1-3.el9
```

---

# **395. Install package (Ubuntu)**

```
root@lilyang:~# apt install htop -y
```

```
Setting up htop
```

---

# **396. Install package (RHEL)**

```
root@server ~]# yum install htop -y
```

```
Installed: htop.x86_64
```

---

# **397. Remove package (Ubuntu)**

```
root@lilyang:~# apt remove htop -y
```

```
Removing htop
```

---

# **398. Remove package (RHEL)**

```
root@server ~]# yum remove htop -y
```

```
Removed: htop
```

---

# **399. Update system (Ubuntu)**

```
root@lilyang:~# apt update && apt upgrade -y
```

```
All packages are up to date
```

---

# **400. Update system (RHEL)**

```
root@server ~]# yum update -y
```

```
Updated: 10 packages
```

---

# **401. System info summary**

```
root@lilyang:~# neofetch
```

```
OS: Ubuntu 22.04 LTS
Kernel: 6.8.0-31-generic
CPU: Intel Xeon
Memory: 2.1G/7.6G
```

---

# **402. Display environment variables**

```
root@lilyang:~# printenv
```

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOME=/root
```

---

# **403. Export environment variable**

```
root@lilyang:~# export MY_VAR="hello"
```

```
(no output)
```

---

# **404. Show process limits**

```
root@lilyang:~# ulimit -a
```

```
core file size          (blocks, -c) 0
max user processes              (-u) 63399
```

---

# **405. Change process limits**

```
root@lilyang:~# ulimit -n 65535
```

```
(no output)
```

---

# **406. Check mounted devices (lsblk + mount)**

```
root@lilyang:~# lsblk -f
```

```
NAME FSTYPE LABEL UUID MOUNTPOINT
sda1 ext4 root  01a3-ef91 /
```

---

# **407. Check SMART status**

```
root@lilyang:~# smartctl -a /dev/sda
```

```
SMART overall-health self-assessment test passed
```

---

# **408. Check system uptime**

```
root@lilyang:~# uptime
```

```
10:45:23 up 3:05, 2 users, load average: 0.21,0.25,0.19
```

---

# **409. Monitor IO in real-time**

```
root@lilyang:~# iotop
```

```
(Interactive IO monitor)
```

---

# **410. Check CPU temperature**

```
root@lilyang:~# sensors
```

```
Core 0: +42.0°C
```

---

# **411. Disk check**

```
root@lilyang:~# fsck /dev/sda1
```

```
fsck from util-linux 2.37.2
```

---

# **412. Check open ports**

```
root@lilyang:~# lsof -i -P -n | grep LISTEN
```

```
sshd   723 root 3u IPv4  0t0 TCP *:22 (LISTEN)
```

---

# **413. Find large files**

```
root@lilyang:~# find / -type f -size +500M
```

```
/var/lib/mysql/ibdata1
```

---

# **414. Find recently modified files**

```
root@lilyang:~# find /var/log -mtime -1
```

```
/var/log/syslog
```

---

# **415. Show login history**

```
root@lilyang:~# lastlog
```

```
Username         Port  From  Latest
root             pts/0 192.168.1.10 Mon Nov 16 10:12
```

---

# **416. List active TCP sockets**

```
root@lilyang:~# ss -s
```

```
Total: 10 (estab 3, closed 2, orphaned 0, timewait 2)
```

---

# **417. Check established connections**

```
root@lilyang:~# netstat -ant | grep ESTABLISHED
```

```
tcp 0 0 192.168.1.20:22 192.168.1.10:52344 ESTABLISHED
```

---

# **418. Show disk I/O scheduler**

```
root@lilyang:~# cat /sys/block/sda/queue/scheduler
```

```
[mq-deadline] noop cfq
```

---

# **419. Change I/O scheduler**

```
root@lilyang:~# echo noop > /sys/block/sda/queue/scheduler
```

```
(no output)
```

---

# **420. Check mounted NFS shares**

```
root@lilyang:~# showmount -e 192.168.1.50
```

```
Export list for 192.168.1.50:
/mnt/data *
```

---

# **421. Mount NFS share**

```
root@lilyang:~# mount -t nfs 192.168.1.50:/mnt/data /mnt/nfs
```

```
(no output)
```

---

# **422. Unmount NFS**

```
root@lilyang:~# umount /mnt/nfs
```

```
(no output)
```

---

# **423. Check open files per process**

```
root@lilyang:~# lsof -p 723
```

```
COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME
sshd    723 root 3u IPv4 0t0 TCP *:22 (LISTEN)
```

---

# **424. Show listening UDP ports**

```
root@lilyang:~# ss -u -l
```

```
Netid  State  Recv-Q Send-Q Local Address:Port
udp    UNCONN 0      0       0.0.0.0:68
```

---

# **425. Disable IPv6**

```
root@lilyang:~# sysctl -w net.ipv6.conf.all.disable_ipv6=1
```

```
net.ipv6.conf.all.disable_ipv6 = 1
```

---

# **426. Enable IPv6**

```
root@lilyang:~# sysctl -w net.ipv6.conf.all.disable_ipv6=0
```

```
net.ipv6.conf.all.disable_ipv6 = 0
```

---

# **427. Show system boot time**

```
root@lilyang:~# who -b
```

```
system boot  2025-11-16 10:21
```

---

# **428. Set timezone**

```
root@lilyang:~# timedatectl set-timezone Asia/Yangon
```

```
(no output)
```

---

# **429. Show timezone**

```
root@lilyang:~# timedatectl
```

```
Time zone: Asia/Yangon (MMT, +0630)
```

---

# **430. Systemctl isolate runlevel**

```
root@lilyang:~# systemctl isolate multi-user.target
```

```
(no output)
```

---

# **431. Show systemctl list jobs**

```
root@lilyang:~# systemctl list-jobs
```

```
(no jobs running)
```

---

# **432. Show listening UNIX sockets**

```
root@lilyang:~# ss -x -l
```

```
Netid State  Path
u_str LISTEN /run/systemd/private
```

---

# **433. Disk benchmark (dd)**

```
root@lilyang:~# dd if=/dev/zero of=/tmp/test.img bs=1G count=1 oflag=direct
```

```
1+0 records in
1+0 records out
```

---

# **434. Monitor network bandwidth**

```
root@lilyang:~# nload
```

```
(Interactive real-time bandwidth)
```

---

# **435. List kernel modules**

```
root@lilyang:~# lsmod
```

```
Module                  Size  Used by
nf_conntrack           16384  1
```

---

# **436. Load kernel module**

```
root@lilyang:~# modprobe nf_conntrack
```

```
(no output)
```

---

# **437. Unload kernel module**

```
root@lilyang:~# modprobe -r nf_conntrack
```

```
(no output)
```

---

# **438. Check running timers**

```
root@lilyang:~# systemctl list-timers
```

```
NEXT                         LEFT  LAST  PASSED  UNIT
Thu 2025-11-16 11:00:00      20min  Wed 2025-11-15 11:00:00  cron.timer
```

---

# **439. Disk usage by directory**

```
root@lilyang:~# du -h --max-depth=1 /
```

```
1.2G /var
700M /usr
```

---

# **440. Watch command**

```
root@lilyang:~# watch -n 2 df -h
```

```
(refreshes every 2 sec)
```

---

