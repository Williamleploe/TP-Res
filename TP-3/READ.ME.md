# TP3 : 32°13'34"N 95°03'27"W

## I. ARP basics

### ☀️ Avant de continuer...
.affichez l'adresse MAC de votre carte WiFi !

commande utilisé : PS C:\Users\willi> ipconfig /all
```
 Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
 ```
### ☀️ Affichez votre table ARP
```

PS C:\Users\willi> arp -a

Interface : 192.168.56.1 --- 0x4
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique

Interface : 10.33.77.148 --- 0x11
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.66.78           e4-b3-18-48-36-68     dynamique
  10.33.73.77           98-8d-46-c4-fa-e5     dynamique
  10.33.77.160          c8-94-02-f8-ab-97     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  ```
  ### ☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école


la passerelle, vous connaissez son adresse IP normalement (cf TP1 ;) )
si vous avez un accès internet, votre PC a forcément l'adresse MAC de la passerelle dans sa table ARP
### commande utilisé : PS C:\Users\willi> arp -a
```
 10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
 ```
 ### ☀️ Supprimez la ligne qui concerne la passerelle
```
 Voici la commande utilisé :
  PS C:\Users\willi> arp -d 10.33.79.254
``` 
### ☀️ Prouvez que vous avez supprimé la ligne dans la table ARP
```
PS C:\Users\willi> arp -a

Interface : 192.168.56.1 --- 0x4
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
```
### ☀️ Wireshark
[capture arp1.pcap](./arp1.pcapng)

## 1. Basics

### ☀️ Déterminer

pour la carte réseau impliquée dans le partage de connexion (carte WiFi ?)
son adresse IP au sein du réseau local formé par le partage de co
son adresse MAC


```
PS C:\Users\willi> ipconfig /all
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a01:cb1a:5f:b38:a05b:dfac:954b:7349(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a01:cb1a:5f:b38:147:19a2:fff4:a303(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.194.162(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 11:08:51
   Bail expirant. . . . . . . . . . . . . : mardi 8 octobre 2024 12:08:49
   Passerelle par défaut. . . . . . . . . : fe80::8c1b:32ff:fefd:e626%17
                                       192.168.194.45
   Serveur DHCP . . . . . . . . . . . . . : 192.168.194.45
   IAID DHCPv6 . . . . . . . . . . . : 132433767
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-60-98-93-D4-93-90-3E-C1-1D
   Serveurs DNS. . .  . . . . . . . . . . : 192.168.194.45
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   ```
### ☀️ DIY


changer d'adresse IP
vous pouvez le faire en interface graphique
faut procéder comme au TP1 :
vous respectez les informations que vous connaissez du réseau
remettez la même passerelle, le même masque, et le même serveur DNS
changez seulement votre adresse IP, ne changez que le dernier nombre
prouvez que vous avez bien changé d'IP
avec une commande !
```

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : E4-C7-67-81-D0-3F
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a01:cb1a:5f:b38:a05b:dfac:954b:7349(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a01:cb1a:5f:b38:147:19a2:fff4:a303(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::6d49:7bf0:ecb9:a74d%17(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.194.163(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . : fe80::8c1b:32ff:fefd:e626%17
                                       192.168.194.45
   IAID DHCPv6 . . . . . . . . . . . : 132433767
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-60-98-93-D4-93-90-3E-C1-1D
   Serveurs DNS. . .  . . . . . . . . . . : 192.168.194.45
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
### ☀️ Pingz !
````

PS C:\Users\willi> ping google.com

Envoi d’une requête 'ping' sur google.com [2a00:1450:4007:819::200e] avec 32 octets de données :
Réponse de 2a00:1450:4007:819::200e : temps=34 ms
Réponse de 2a00:1450:4007:819::200e : temps=34 ms
Réponse de 2a00:1450:4007:819::200e : temps=39 ms
Réponse de 2a00:1450:4007:819::200e : temps=52 ms

Statistiques Ping pour 2a00:1450:4007:819::200e:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 34ms, Maximum = 52ms, Moyenne = 39ms
````

## 2. ARP
### ☀️ Affichez votre table ARP !
```
PS C:\Users\willi> arp -a

Interface : 192.168.56.1 --- 0x4
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique

Interface : 192.168.180.182 --- 0x11
  Adresse Internet      Adresse physique      Type
  192.168.180.29        e2-b6-7a-88-24-14     dynamique
  192.168.180.91        f8-fe-5e-18-12-df     dynamique
  192.168.180.255       ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

```
### ☀️ Capture arp2.pcap

[capture arp2.pcpng](./arp2.pcapng)

## 3. Bonus : ARP poisoning 

### ⭐ Empoisonner la table ARP de l'un des membres de votre réseau

### ⭐ Mettre en place un MITM

