# Forensic

# ${{\color{purple}Windows}}\ $

### Command & Control - niveau 2 :

#### Trouver le nom de la machine :

``sudo /opt/volatility3/vol.py -h | grep env``

``sudo /opt/volatility3/vol.py -f /home/kali/Documents/forensic/ch2.dmp windows.envars``

### Command & Control - niveau 5 :

#### Trouver le mot de passe de l'utilisateur :

``Utiliser volatility version 2``

``sudo python2.7 vol.py -f /home/kali/Documents/forensic/ch2.dmp imageinfo``

![image](https://github.com/user-attachments/assets/8ed23987-4d04-4eef-8143-5c164717cb86)

``sudo python2.7 vol.py -f /home/kali/Documents/forensic/ch2.dmp --profile=Win7SP1x86 hashdump``

![image](https://github.com/user-attachments/assets/ddb146e4-b521-4696-bae9-1cd0c6f5ff77)

``john --format=NT --wordlist=/usr/share/wordlists/rockyou.txt passwords_hashed.txt``

![image](https://github.com/user-attachments/assets/a9f9f0ac-e7d8-4650-b28a-118121731b72)

