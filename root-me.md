# Forensic

# ${{\color{purple}Windows}}\ $

### Command & Control - niveau 2 :

#### Trouver le nom de la machine

``sudo /opt/volatility3/vol.py -h | grep env``

``sudo /opt/volatility3/vol.py -f /home/kali/Documents/forensic/ch2.dmp windows.envars``



### Active Windows :

``nmap/gobuster/dnsrecon/nslookup/smbmap/enum4linux/smbclient/gpp-decrypt/impacket-GetADUsers/impacket-GetUserSPNs/impacket-psexec/john/runas/dir``

### Jerry Windows:

``nmap/dirb/seclists/hydra/HYDRA_PROXY_HTTP/msfvenom``

### Bastion Windows :

``nmap/smbclient/mnt/guestmount/impacket-secretsdump/mRemoteNG-Decrypt/ dir \a/impacket-psexec``

### Legacy Windows:

``nmap/nmap vuln/wget/msfvenom/ms08-067/zzz_exploit``
