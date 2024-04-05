1. scan with rustscan
2. have smb port 135,139 scan with smbmap and smbclient 
```bash
smbmap -H 10.10.207.211 -v  -q
smbclient -L //10.10.207.211/ -p 139
```

3. check for vuln with nmap:
```bash
nmap -sV --script=vuln -p 80,443,3128,135,139,8080,8118,8228,10011,49152,49154,49158,49153,49159  10.10.207.211
```

4. eternalblue 
https://www.rapid7.com/db/modules/exploit/windows/smb/ms17_010_eternalblue/
https://github.com/3ndG4me/AutoBlue-MS17-010

5. some info

- Security Accounts Manager (SAM) is a database file in the Microsoft Windows operating system (OS) that contains usernames and passwords. in C:\Windows\System32\config


