# I. Récolte d'informations

 ## 🌞 Adresses IP de ta machine

 ### . affiche l'adresse IP que ta machine a sur sa carte réseau WiFi

```
PS C:\Users\willi> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.148
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```

   ### . affiche l'adresse IP que ta machine a sur sa carte réseau ethernet 

```
PS C:\Users\willi> ipconfig /all
Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
```

## 🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...

### . affiche l'adresse IP de la passerelle du réseau local

```
PS C:\Users\willi> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.148(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 26 septembre 2024 08:37:34
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 08:29:40
  🌞 Passerelle par défaut.   . . . . . . :10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 132433767
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-60-98-93-D4-93-90-3E-C1-1D
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
   ### . affiche l'adresse IP du serveur DNS que connaît ton PC 

   ```
   Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.148(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 26 septembre 2024 08:37:34
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 08:29:40
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 132433767
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-60-98-93-D4-93-90-3E-C1-1D
   🌞Serveurs DNS. . .  .. . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ```
   ### . affiche l'adresse IP du serveur DHCP que connaît ton PC 
   ```
   Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.148(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 26 septembre 2024 08:37:34
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 08:29:40
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   🌞Serveur DHCP . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . .      . . . . . . : 132433767
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-60-98-93-D4-93-90-3E-C1-1D
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ```
   ## 🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine

```
 C:\Users\willi> netsh advfirewall show 
     Paramètres Profil de domaine :
----------------------------------------------------------------------
État                                  Actif
Stratégie de pare-feu                 BlockInbound,AllowOutbound
LocalFirewallRules                    N/A (magasin d'objets de stratégie de groupe uniquement)
LocalConSecRules                      N/A (magasin d'objets de stratégie de groupe uniquement)
InboundUserNotification               Activer
RemoteManagement                      Désactiver
UnicastResponseToMulticast            Activer

Journalisation :
LogAllowedConnections                 Désactiver
LogDroppedConnections                 Désactiver
FileName                              %systemroot%\system32\LogFiles\Firewall\pfirewall.log
MaxFileSize                           4096
``` 
### . je veux aussi voir une commande pour lister les règles du pare-feu
``` 
je veux aussi voir une commande pour lister les règles du pare-feu
``` 
# II. Utiliser le réseau

## 🌞 Envoie un ping vers...

### . toi-même !
``` 
PS C:\Users\willi> ping 10.33.77.148

Envoi d’une requête 'Ping'  10.33.77.148 avec 32 octets de données :
Réponse de 10.33.77.148 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.148 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.148 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.148 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.77.148:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
### . vers l'adresse IP 127.0.0.1
```
C:\Users\willi> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
## 🌞 On continue avec ping 

### .ta passerelle 
``` 
PS C:\Users\willi> ping 10.33.79.254

Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
 ```
 ### . un(e) pote sur le réseau
 ```
 PS C:\Users\willi> ping 10.33.74.229

Envoi d’une requête 'Ping'  10.33.74.229 avec 32 octets de données :
Réponse de 10.33.74.229 : octets=32 temps=47 ms TTL=128
Réponse de 10.33.74.229 : octets=32 temps=16 ms TTL=128
Réponse de 10.33.74.229 : octets=32 temps=20 ms TTL=128
Réponse de 10.33.74.229 : octets=32 temps=10 ms TTL=128

Statistiques Ping pour 10.33.74.229:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 10ms, Maximum = 47ms, Moyenne = 23ms
```
### . un site internet

``` 
C:\Users\willi> ping google.com

Envoi d’une requête 'ping' sur google.com [142.250.178.142] avec 32 octets de données :
Réponse de 142.250.178.142 : octets=32 temps=16 ms TTL=117
Réponse de 142.250.178.142 : octets=32 temps=17 ms TTL=117
Réponse de 142.250.178.142 : octets=32 temps=17 ms TTL=117
Réponse de 142.250.178.142 : octets=32 temps=17 ms TTL=117

Statistiques Ping pour 142.250.178.142:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 16ms, Maximum = 17ms, Moyenne = 16ms
```

## 🌞 Faire une requête DNS à la main

```
 C:\Users\willi> nslookup 🌞 www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3120::7
          2a06:98c1:3121::7
          188.114.97.7
          188.114.96.7
``` 

```
 C:\Users\willi> nslookup 🌞 www.wikileaks.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  51.159.197.136
          80.81.248.21
Aliases:  www.wikileaks.org
```
```
 C:\Users\willi> nslookup 🌞 www.torproject.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2620:7:6002:0:466:39ff:fe7f:1826
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2a01:4f9:c010:19eb::1
          204.8.99.146
          116.202.120.165
          116.202.120.166
          95.216.163.36
          204.8.99.144
```

# III. Sniffer le réseau

### 🌞 J'attends dans le dépôt git de rendu un fichier ping.pcap
 Voire ping.pcap.pcapng

### 🌞 Livrez un deuxième fichier : dns.pcap
Voire dns.pcapng

# IV. Network scanning et adresses IP
### 🌞 Effectue un scan du réseau auquel tu es connecté

### 🌞 Changer d'adresse IP
```
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.149
   Masque de sous-réseau. . . . . . . . . : 255.0.0.0
   Passerelle par défaut. . . . . . . . . :
```



