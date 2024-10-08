# TP2 : Hey yo tell a neighbor tell a friend

## 1. Quelques pings

### 🌞 Prouvez que votre configuration est effective

```
PS C:\Users\willi> Get-NetIPAddress -InterfaceAlias Ethernet


IPAddress         : fe80::ae57:56ef:302d:1e10%18
InterfaceIndex    : 18
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.1.1.3
InterfaceIndex    : 18
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore
```

### 🌞 Tester que votre LAN + votre adressage IP est fonctionnel
```

PS C:\Users\willi> ping 10.1.1.2

Envoi d’une requête 'Ping'  10.1.1.2 avec 32 octets de données :
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128
Réponse de 10.1.1.2 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.1.1.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

### 🌞 Capture de ping
Voir Ping-1

# II. Utilisation des ports

## 1. Animal numérique

### 🌞 Sur le PC serveur
``` 
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> ./nc.exe 10.1.1.2 8888
```
 ### 🌞Sur le PC serveur toujours
 ```
  TCP    10.1.1.3:39230         10.1.1.2:8888          ESTABLISHED
 [nc.exe]
 ```
 ### 🌞 Sur le PC client
 ``` 
 PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> .\nc 10.1.1.3 8888
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11>
```
### 🌞 Echangez-vous des messages
```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> ./nc.exe 10.1.1.2 8888
cc
ca va ?
salut
pas mal les bzez
````
### 🌞 Utilisez une commande qui permet de voir la connexion en cours
```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> netstat

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    10.33.77.148:38400     162.159.135.234:https  ESTABLISHED
  TCP    10.33.77.148:38572     par21s20-in-f3:http    ESTABLISHED
  TCP    10.33.77.148:38581     wf-in-f188:5228        ESTABLISHED
  TCP    10.33.77.148:38638     ec2-54-89-233-95:9339  ESTABLISHED
  TCP    10.33.77.148:38659     ae41dd3672a2e5b7b:https  ESTABLISHED
  TCP    10.33.77.148:38664     server-3-164-163-9:https  ESTABLISHED
  TCP    10.33.77.148:38916     ws-in-f188:5228        ESTABLISHED
```

### 🌞 Faites une capture Wireshark complète d'un échange
Voir Ping-e

### 🌞 Inversez les rôles

```
PS C:\Users\willi\Downloads\netcat-win32-1.11\netcat-1.11> .\nc -lvp 8888
listening on [any] 8888 ...
DNS fwd/rev mismatch: DESKTOP-N8AD10N != DESKTOP-N8AD10N.local
connect to [10.1.1.3] from DESKTOP-N8AD10N [10.1.1.2] 47408
salut man
ca va ?
```
Voir ping-3

# III. Analyse de vos applications usuelles

## 1. Serveur web
### 🌞 Utilisez Wireshark pour capturer du trafic HTTP
Voir http.pcapng

## 2. Autres services

### 🌞 Pour les 5 applications
```
Voicie la commande  netstat pour voir les connexions actives sur le système.

PS C:\Users\willi> netstat -a -b -n

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  RpcEptMapper
 [svchost.exe]
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:3926           0.0.0.0:0              LISTENING
  PolicyAgent
 [svchost.exe]
  TCP    0.0.0.0:5040           0.0.0.0:0              LISTENING
  CDPSvc
 [svchost.exe]
  TCP    0.0.0.0:7680           0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:27036          0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING
 [lsass.exe]
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:49668          0.0.0.0:0              LISTENING
  Schedule
 [svchost.exe]
  TCP    0.0.0.0:49669          0.0.0.0:0              LISTENING
  EventLog
 [svchost.exe]
  TCP    0.0.0.0:49676          0.0.0.0:0              LISTENING
 [spoolsv.exe]
  TCP    0.0.0.0:49678          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.77.148:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.77.148:54357     20.199.120.151:443     ESTABLISHED
  WpnService
 [svchost.exe]
  TCP    10.33.77.148:54472     66.102.1.188:5228      ESTABLISHED
 [opera.exe]
  TCP    10.33.77.148:54480     20.199.120.182:443     ESTABLISHED
 [OneDrive.exe]
  TCP    10.33.77.148:54497     162.159.134.234:443    ESTABLISHED
 [Discord.exe]
  TCP    10.33.77.148:54526     3.224.35.96:443        ESTABLISHED
 [EpicGamesLauncher.exe]
  TCP    10.33.77.148:54616     104.18.41.183:443      CLOSE_WAIT
 [RiotClientServices.exe]
  TCP    10.33.77.148:54622     104.18.41.183:443      CLOSE_WAIT
 [RiotClientServices.exe]
  TCP    10.33.77.148:54701     52.112.100.64:443      ESTABLISHED
 [ms-teams.exe]
  TCP    10.33.77.148:54721     185.25.182.20:443      ESTABLISHED
 [steam.exe]
  TCP    10.33.77.148:54820     52.123.159.129:443     ESTABLISHED
 [msedgewebview2.exe]
  TCP    10.33.77.148:54881     104.18.2.64:443        TIME_WAIT
  TCP    10.33.77.148:54893     3.165.113.92:443       CLOSE_WAIT
 [System]
  TCP    10.33.77.148:54921     52.222.169.107:443     CLOSE_WAIT
 [System]
  TCP    10.33.77.148:54923     18.245.199.26:443      CLOSE_WAIT
 [System]
  TCP    10.33.77.148:54928     104.18.2.64:443        TIME_WAIT
  TCP    10.33.77.148:54929     18.245.199.26:443      CLOSE_WAIT
 [System]
  TCP    10.33.77.148:54930     52.222.169.107:443     CLOSE_WAIT
 [System]
  TCP    10.33.77.148:55019     44.208.50.214:443      ESTABLISHED
 [System]
  TCP    10.33.77.148:55032     184.72.64.3:443        ESTABLISHED
 [System]
  TCP    10.33.77.148:55043     3.165.136.115:443      CLOSE_WAIT
 [EOSOverlayRenderer-Win64-Shipping.exe]
  TCP    10.33.77.148:55055     52.222.169.107:443     ESTABLISHED
 [System]
  TCP    10.33.77.148:55209     8.8.8.8:443            TIME_WAIT
  TCP    10.33.77.148:55240     20.166.109.4:443       TIME_WAIT
  TCP    10.33.77.148:55250     13.89.179.11:443       TIME_WAIT
  TCP    10.33.77.148:55254     204.79.197.222:443     TIME_WAIT
  TCP    10.33.77.148:55259     152.199.21.118:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55261     52.44.12.142:443       CLOSE_WAIT
 [EpicGamesLauncher.exe]
  TCP    10.33.77.148:55262     34.194.47.2:443        CLOSE_WAIT
 [EpicGamesLauncher.exe]
  TCP    10.33.77.148:55285     20.50.73.4:443         ESTABLISHED
 [msedgewebview2.exe]
  TCP    10.33.77.148:55299     2.18.40.144:443        ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55302     23.192.237.216:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55306     23.192.237.209:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55308     52.98.243.146:443      ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55310     13.107.6.158:443       ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55312     13.107.6.158:443       ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55321     40.126.32.138:443      ESTABLISHED
 [OneDrive.exe]
  TCP    10.33.77.148:55322     20.190.183.26:443      ESTABLISHED
 [OneDrive.exe]
  TCP    10.33.77.148:55325     20.199.58.43:443       ESTABLISHED
 [SystemSettings.exe]
  TCP    10.33.77.148:55330     13.107.6.254:443       ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55331     150.171.70.254:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55332     102.133.96.237:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55333     204.79.197.222:443     ESTABLISHED
 [SearchHost.exe]
  TCP    10.33.77.148:55337     51.105.71.137:443      ESTABLISHED
 [OneDrive.exe]
  TCP    127.0.0.1:6463         0.0.0.0:0              LISTENING
 [Discord.exe]
  TCP    127.0.0.1:9010         0.0.0.0:0              LISTENING
 [lghub_agent.exe]
  TCP    127.0.0.1:9010         127.0.0.1:54606        ESTABLISHED
 [lghub_agent.exe]
  TCP    127.0.0.1:9010         127.0.0.1:54608        ESTABLISHED
 [lghub_agent.exe]
  TCP    127.0.0.1:9010         127.0.0.1:54609        ESTABLISHED
 [lghub_agent.exe]
  TCP    127.0.0.1:9080         0.0.0.0:0              LISTENING
 [lghub_agent.exe]
  TCP    127.0.0.1:9100         0.0.0.0:0              LISTENING
 [lghub_updater.exe]
  TCP    127.0.0.1:9100         127.0.0.1:54631        ESTABLISHED
 [lghub_updater.exe]
  TCP    127.0.0.1:9180         0.0.0.0:0              LISTENING
 [lghub_updater.exe]
  TCP    127.0.0.1:27060        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:45654        0.0.0.0:0              LISTENING
 [lghub_agent.exe]
  TCP    127.0.0.1:49685        127.0.0.1:49686        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49686        127.0.0.1:49685        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49687        127.0.0.1:49688        ESTABLISHED
 [NVDisplay.Container.exe]
  TCP    127.0.0.1:49688        127.0.0.1:49687        ESTABLISHED
 [NVDisplay.Container.exe]
  TCP    127.0.0.1:49689        127.0.0.1:49690        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49690        127.0.0.1:49689        ESTABLISHED
 [WUDFHost.exe]
  TCP    127.0.0.1:49714        127.0.0.1:49715        ESTABLISHED
 [ipfsvc.exe]
  TCP    127.0.0.1:49715        127.0.0.1:49714        ESTABLISHED
 [ipfsvc.exe]
  TCP    127.0.0.1:49886        0.0.0.0:0              LISTENING
 [EABackgroundService.exe]
  TCP    127.0.0.1:54350        127.0.0.1:65001        ESTABLISHED
 [nvcontainer.exe]
  TCP    127.0.0.1:54364        0.0.0.0:0              LISTENING
 [NVIDIA Web Helper.exe]
  TCP    127.0.0.1:54364        127.0.0.1:54400        ESTABLISHED
 [NVIDIA Web Helper.exe]
  TCP    127.0.0.1:54364        127.0.0.1:55249        TIME_WAIT
  TCP    127.0.0.1:54364        127.0.0.1:55296        FIN_WAIT_2
 [NVIDIA Web Helper.exe]
  TCP    127.0.0.1:54364        127.0.0.1:55297        ESTABLISHED
 [NVIDIA Web Helper.exe]
  TCP    127.0.0.1:54400        127.0.0.1:54364        ESTABLISHED
 [NVIDIA Share.exe]
  TCP    127.0.0.1:54519        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:54519        127.0.0.1:54545        ESTABLISHED
 [steam.exe]
  TCP    127.0.0.1:54520        0.0.0.0:0              LISTENING
 [steam.exe]
  TCP    127.0.0.1:54520        127.0.0.1:54544        ESTABLISHED
 [steam.exe]
  TCP    127.0.0.1:54544        127.0.0.1:54520        ESTABLISHED
 [steamwebhelper.exe]
  TCP    127.0.0.1:54545        127.0.0.1:54519        ESTABLISHED
 [steamwebhelper.exe]
  TCP    127.0.0.1:54606        127.0.0.1:9010         ESTABLISHED
 [opera.exe]
  TCP    127.0.0.1:54608        127.0.0.1:9010         ESTABLISHED
 [opera.exe]
  TCP    127.0.0.1:54609        127.0.0.1:9010         ESTABLISHED
 [lghub_system_tray.exe]
  TCP    127.0.0.1:54631        127.0.0.1:9100         ESTABLISHED
 [lghub_agent.exe]
  TCP    127.0.0.1:54632        0.0.0.0:0              LISTENING
 [RiotClientServices.exe]
  TCP    127.0.0.1:55038        127.0.0.1:55039        ESTABLISHED
 [System]
  TCP    127.0.0.1:55039        127.0.0.1:55038        ESTABLISHED
 [System]
  TCP    127.0.0.1:55296        127.0.0.1:54364        CLOSE_WAIT
 [NVIDIA Share.exe]
  TCP    127.0.0.1:55297        127.0.0.1:54364        ESTABLISHED
 [NVIDIA Share.exe]
  TCP    127.0.0.1:55340        127.0.0.1:28194        SYN_SENT
 [lghub_agent.exe]
  TCP    127.0.0.1:65001        0.0.0.0:0              LISTENING
 [nvcontainer.exe]
  TCP    127.0.0.1:65001        127.0.0.1:54350        ESTABLISHED
 [nvcontainer.exe]
  TCP    192.168.56.1:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:135               [::]:0                 LISTENING
  RpcEptMapper
 [svchost.exe]
  TCP    [::]:445               [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:3926              [::]:0                 LISTENING
  PolicyAgent
 [svchost.exe]
  TCP    [::]:7680              [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49664             [::]:0                 LISTENING
 [lsass.exe]
  TCP    [::]:49665             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49668             [::]:0                 LISTENING
  Schedule
 [svchost.exe]
  TCP    [::]:49669             [::]:0                 LISTENING
  EventLog
 [svchost.exe]
  TCP    [::]:49676             [::]:0                 LISTENING
 [spoolsv.exe]
  TCP    [::]:49678             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::1]:42050            [::]:0                 LISTENING
 [Microsoft.SharePoint.exe]
  TCP    [::1]:49677            [::]:0                 LISTENING
 [jhi_service.exe]
  TCP    [::1]:49886            [::]:0                 LISTENING
 [EABackgroundService.exe]
  UDP    0.0.0.0:500            *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:4500           *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:5050           *:*
  CDPSvc
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
 [opera.exe]
  UDP    0.0.0.0:5353           *:*
 [opera.exe]
  UDP    0.0.0.0:5353           *:*
 [opera.exe]
  UDP    0.0.0.0:5353           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
 [opera.exe]
  UDP    0.0.0.0:5355           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:27036          *:*
 [steam.exe]
  UDP    0.0.0.0:50076          *:*
 [ms-teams.exe]
  UDP    0.0.0.0:52594          *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:54959          *:*
 [nvcontainer.exe]
  UDP    0.0.0.0:61823          *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:62751          *:*
 [ms-teams.exe]
  UDP    0.0.0.0:63516          47.245.143.98:22101
 [System]
  UDP    10.33.77.148:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.77.148:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.77.148:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    10.33.77.148:5353      *:*
 [nvcontainer.exe]
  UDP    10.33.77.148:50304     *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:1900         *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:10050        *:*
 [NVIDIA Web Helper.exe]
  UDP    127.0.0.1:10051        *:*
 [nvcontainer.exe]
  UDP    127.0.0.1:50305        *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:59829        *:*
 [nvcontainer.exe]
  UDP    127.0.0.1:64255        127.0.0.1:64255
  iphlpsvc
 [svchost.exe]
  UDP    192.168.56.1:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.56.1:5353      *:*
 [nvcontainer.exe]
  UDP    192.168.56.1:50303     *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::]:500               *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:4500              *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:5353              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:5353              *:*
 [opera.exe]
  UDP    [::]:5353              *:*
 [opera.exe]
  UDP    [::]:5355              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:50076             *:*
 [ms-teams.exe]
  UDP    [::]:52594             *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:54960             *:*
 [nvcontainer.exe]
  UDP    [::]:61823             *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:62751             *:*
 [ms-teams.exe]
  UDP    [::1]:1900             *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::1]:5353             *:*
 [nvcontainer.exe]
  UDP    [::1]:50302            *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::6d49:7bf0:ecb9:a74d%17]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::6d49:7bf0:ecb9:a74d%17]:50301  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::91c6:f33b:6281:b555%4]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::91c6:f33b:6281:b555%4]:50300  *:*
  SSDPSRV
 [svchost.exe]
  ````
  ### Voici les 5 app 
  ```
  [Discord.exe]
  TCP    10.33.77.148:54526
  [steam.exe]
  TCP    127.0.0.1:54519
  [NVIDIA Web Helper.exe]
  TCP    127.0.0.1:54364
  [opera.exe]
  UDP    0.0.0.0:5353
  [OneDrive.exe]
  TCP    10.33.77.148:55322
  ```
  