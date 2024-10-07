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

PS C:\Users\willi> netstat -an

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:3926           0.0.0.0:0              LISTENING
  TCP    0.0.0.0:5040           0.0.0.0:0              LISTENING
  TCP    0.0.0.0:27036          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49668          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49669          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49676          0.0.0.0:0              LISTENING
  TCP    0.0.0.0:49678          0.0.0.0:0              LISTENING
  TCP    127.0.0.1:9010         0.0.0.0:0              LISTENING
  TCP    127.0.0.1:9010         127.0.0.1:53245        ESTABLISHED
  TCP    127.0.0.1:9010         127.0.0.1:53250        ESTABLISHED
  TCP    127.0.0.1:9010         127.0.0.1:53269        ESTABLISHED
  TCP    127.0.0.1:9080         0.0.0.0:0              LISTENING
  TCP    127.0.0.1:9100         0.0.0.0:0              LISTENING
  TCP    127.0.0.1:9100         127.0.0.1:53261        ESTABLISHED
  TCP    127.0.0.1:9180         0.0.0.0:0              LISTENING
  TCP    127.0.0.1:27060        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:45654        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:49685        127.0.0.1:49686        ESTABLISHED
  TCP    127.0.0.1:49686        127.0.0.1:49685        ESTABLISHED
  TCP    127.0.0.1:49687        127.0.0.1:49688        ESTABLISHED
  TCP    127.0.0.1:49688        127.0.0.1:49687        ESTABLISHED
  TCP    127.0.0.1:49689        127.0.0.1:49690        ESTABLISHED
  TCP    127.0.0.1:49690        127.0.0.1:49689        ESTABLISHED
  TCP    127.0.0.1:49714        127.0.0.1:49715        ESTABLISHED
  TCP    127.0.0.1:49715        127.0.0.1:49714        ESTABLISHED
  TCP    127.0.0.1:49886        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:53236        127.0.0.1:65001        ESTABLISHED
  TCP    127.0.0.1:53245        127.0.0.1:9010         ESTABLISHED
  TCP    127.0.0.1:53250        127.0.0.1:9010         ESTABLISHED
  TCP    127.0.0.1:53261        127.0.0.1:9100         ESTABLISHED
  TCP    127.0.0.1:53269        127.0.0.1:9010         ESTABLISHED
  TCP    127.0.0.1:53300        127.0.0.1:57654        ESTABLISHED
  TCP    127.0.0.1:53751        127.0.0.1:28194        SYN_SENT
  TCP    127.0.0.1:57654        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:57654        127.0.0.1:53300        ESTABLISHED
  TCP    127.0.0.1:57771        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:57771        127.0.0.1:57790        ESTABLISHED
  TCP    127.0.0.1:57773        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:57773        127.0.0.1:57789        ESTABLISHED
  TCP    127.0.0.1:57789        127.0.0.1:57773        ESTABLISHED
  TCP    127.0.0.1:57790        127.0.0.1:57771        ESTABLISHED
  TCP    127.0.0.1:57846        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:65001        0.0.0.0:0              LISTENING
  TCP    127.0.0.1:65001        127.0.0.1:53236        ESTABLISHED
  TCP    192.168.1.26:139       0.0.0.0:0              LISTENING
  TCP    192.168.1.26:53237     52.112.100.64:443      ESTABLISHED
  TCP    192.168.1.26:53291     192.168.1.16:60369     TIME_WAIT
  TCP    192.168.1.26:53305     140.82.112.25:443      ESTABLISHED
  TCP    192.168.1.26:53307     52.123.159.129:443     ESTABLISHED
  TCP    192.168.1.26:53324     155.133.248.43:27018   ESTABLISHED
  TCP    192.168.1.26:53337     34.226.132.151:443     ESTABLISHED
  TCP    192.168.1.26:53451     162.159.130.234:443    TIME_WAIT
  TCP    192.168.1.26:53661     104.208.16.95:443      TIME_WAIT
  TCP    192.168.1.26:53662     20.189.173.4:443       TIME_WAIT
  TCP    192.168.1.26:53684     204.79.197.222:443     ESTABLISHED
  TCP    192.168.1.26:53691     2.22.57.122:443        ESTABLISHED
  TCP    192.168.1.26:53724     54.225.130.14:443      ESTABLISHED
  TCP    192.168.1.26:53726     152.199.19.160:443     ESTABLISHED
  TCP    192.168.1.26:53727     104.85.38.96:443       ESTABLISHED
  TCP    192.168.1.26:53729     52.201.28.61:443       ESTABLISHED
  TCP    192.168.1.26:53735     23.15.179.49:80        TIME_WAIT
  TCP    192.168.1.26:53736     23.15.179.49:80        TIME_WAIT
  TCP    192.168.1.26:53739     23.1.254.216:443       TIME_WAIT
  TCP    192.168.1.26:53744     20.189.173.11:443      ESTABLISHED
  TCP    192.168.1.26:57836     104.18.41.183:443      CLOSE_WAIT
  TCP    192.168.1.26:57839     104.18.41.183:443      CLOSE_WAIT
  TCP    192.168.1.26:59777     4.231.141.208:443      ESTABLISHED
  TCP    192.168.56.1:139       0.0.0.0:0              LISTENING
  TCP    [::]:135               [::]:0                 LISTENING
  TCP    [::]:445               [::]:0                 LISTENING
  TCP    [::]:3926              [::]:0                 LISTENING
  TCP    [::]:49664             [::]:0                 LISTENING
  TCP    [::]:49665             [::]:0                 LISTENING
  TCP    [::]:49668             [::]:0                 LISTENING
  TCP    [::]:49669             [::]:0                 LISTENING
  TCP    [::]:49676             [::]:0                 LISTENING
  TCP    [::]:49678             [::]:0                 LISTENING
  TCP    [::1]:42050            [::]:0                 LISTENING
  TCP    [::1]:49677            [::]:0                 LISTENING
  TCP    [::1]:49886            [::]:0                 LISTENING
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53241  [2603:1020:805:3::401]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53262  [2603:1020:805:3::401]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53302  [2a00:1450:400c:c1d::bc]:5228  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53351  [2603:1020:805:3::401]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53649  [2603:1027:1:108::80]:443  TIME_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53681  [2620:1ec:46::254]:443  CLOSE_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53682  [2620:1ec:bdf::42]:443  CLOSE_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53683  [2620:1ec:46::254]:443  CLOSE_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53694  [2620:1ec:bdf::254]:443  CLOSE_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53699  [2a02:26f0:2b00:14::216:e14a]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53700  [2a02:26f0:2b00:14::216:e14e]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53704  [2a01:111:202c::254]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53705  [2603:1000:0:2::26]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53714  [2001:4c28:1:430:82:145:216:15]:443  CLOSE_WAIT
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53715  [2606:4700:90:0:f22e:fbec:5bed:a9b9]:443  ESTABLISHED
  TCP    [2a01:cb19:cfc:1d00:5446:83b9:4625:8a09]:53721  [2001:4c28:1:430:82:145:216:15]:443  ESTABLISHED
  UDP    0.0.0.0:500            *:*
  UDP    0.0.0.0:4500           *:*
  UDP    0.0.0.0:5050           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5355           *:*
  UDP    0.0.0.0:27036          *:*
  UDP    0.0.0.0:49455          *:*
  UDP    0.0.0.0:50084          *:*
  UDP    0.0.0.0:50350          *:*
  UDP    0.0.0.0:51600          *:*
  UDP    0.0.0.0:54959          *:*
  UDP    0.0.0.0:57760          *:*
  UDP    127.0.0.1:1900         *:*
  UDP    127.0.0.1:10040        *:*
  UDP    127.0.0.1:59070        *:*
  UDP    127.0.0.1:61946        *:*
  UDP    127.0.0.1:64255        127.0.0.1:64255
  UDP    192.168.1.26:137       *:*
  UDP    192.168.1.26:138       *:*
  UDP    192.168.1.26:1900      *:*
  UDP    192.168.1.26:5353      *:*
  UDP    192.168.1.26:59069     *:*
  UDP    192.168.56.1:137       *:*
  UDP    192.168.56.1:138       *:*
  UDP    192.168.56.1:1900      *:*
  UDP    192.168.56.1:5353      *:*
  UDP    192.168.56.1:59068     *:*
  UDP    [::]:500               *:*
  UDP    [::]:4500              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5355              *:*
  UDP    [::]:49455             *:*
  UDP    [::]:50084             *:*
  UDP    [::]:50350             *:*
  UDP    [::]:51600             *:*
  UDP    [::]:54960             *:*
  UDP    [::]:57760             *:*
  UDP    [::1]:1900             *:*
  UDP    [::1]:5353             *:*
  UDP    [::1]:59067            *:*
  UDP    [fe80::6d49:7bf0:ecb9:a74d%17]:1900  *:*
  UDP    [fe80::6d49:7bf0:ecb9:a74d%17]:59066  *:*
  UDP    [fe80::91c6:f33b:6281:b555%4]:1900  *:*
  UDP    [fe80::91c6:f33b:6281:b555%4]:59065  *:*
  ````
  