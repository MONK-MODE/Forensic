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


### Command & Control - niveau 3 :

#### Trouver le programme malveillant :

``python2.7 volatility/vol.py -f ch2.dmp --profile=Win7SP1x86 pstree``

#### Si l'on affiche la liste des processus sous forme d'arborescence parent-enfant, on remarque qu'un processus (PID 2772), fils de *explorer.exe*, a pour processus enfant un *cmd.exe* (PID 1616), ce qui est une situation inhabituelle.

![image](https://github.com/user-attachments/assets/bc84b917-656e-4e37-ab4a-f937a4137de0)

#### Pour trouver un malware en userspace, il faut faire le tour des clés de registre.

``
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnceEx
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServices
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
HKEY_CLASSES_ROOT\exefile\shell\open\command
``

``python2.7 volatility/vol.py -f ch2.dmp --profile=Win7SP1x86 printkey -K "Software\Microsoft\Windows\CurrentVersion\Run"``

![image](https://github.com/user-attachments/assets/8a4c1c68-5538-4835-b678-829163bf162a)

#### Il était également possible d'identifier le programme malveillant grâce au chemin affiché dans *cmdline*.

``python2.7 volatility/vol.py -f ch2.dmp --profile=Win7SP1x86 cmdline | grep App``

![image](https://github.com/user-attachments/assets/40697ce2-706c-4a89-bbb5-aacee5666e77)

