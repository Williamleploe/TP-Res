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