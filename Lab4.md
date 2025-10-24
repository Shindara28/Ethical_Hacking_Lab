# Scan Report
<img width="570" height="177" alt="pingkwasu" src="https://github.com/user-attachments/assets/671f8445-2aa4-4d6f-a62f-64d747f622ef" />
<img width="781" height="401" alt="nmapkwasu" src="https://github.com/user-attachments/assets/fafd5f33-60f3-4527-ab75-4d17a2c71111" />

Host: 208.109.188.35, portal.kwasu.edu.ng
Latency: ~309 ms, 0% packet loss

Open ports and services (summary)

22 SSH — OpenSSH 8.7

53 DNS — PowerDNS 4.9.5

80 HTTP — nginx

81 HTTP — Apache httpd

110 POP3, 143 IMAP — Dovecot

443 HTTPS — nginx

444 HTTPS — Apache on nonstandard port

465, 587 SMTP — Exim 4.98.2

993 IMAPS, 995 POP3S — secure mail ports reported open

3306 MySQL — open and unauthenticated

Most important risks
• Public MySQL on 3306. High risk of brute force or data theft.
• Mail services, Exim, and plaintext mail ports. Risk of open relay and credential leakage.
• Multiple web servers and exposed TLS on nonstandard ports. Could hide misconfigurations or weak certificates.
• Service version exposure makes targeted CVE attacks easier.

Top fixes, quick and simple

Firewall off port 3306 from the internet. Allow only internal admin IPs or VPN.

Enforce TLS and disable plaintext mail ports unless needed. Check Exim for open relay and patch it.

Harden SSH, prefer key only authentication, block root login, enable rate limiting.

Check TLS on 443 and 444, renew certificates, and disable weak ciphers.

Run an authorized vulnerability scan and fix any critical CVEs found.
