# TP6 : Des bo services dans des bo LANs

## 2. Marche à suivre

### ☀️ Prouvez que...

.une machine du LAN1 peut joindre internet (ping un nom de domaine)
```
[root@localhost william]# ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=53 time=20.1 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=53 time=27.0 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=53 time=19.4 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=53 time=18.5 ms
^C
```

.une machine du LAN2 peut joindre internet (ping nom de domaine)
```
[root@dns william]# ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=53 time=19.4 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=53 time=19.3 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=53 time=18.8 ms
^C
--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 18.845/19.156/19.367/0.224 ms
```
.une machine du LAN1 peut joindre une machine du LAN2 (ping une adresse IP)
```
[root@localhost william]# ping 10.6.2.12
PING 10.6.2.12 (10.6.2.12) 56(84) bytes of data.
64 bytes from 10.6.2.12: icmp_seq=1 ttl=63 time=4.11 ms
64 bytes from 10.6.2.12: icmp_seq=2 ttl=63 time=3.34 ms
64 bytes from 10.6.2.12: icmp_seq=3 ttl=63 time=3.62 ms
^C
```
# II. LAN clients
Partie dédiée à la configuration du LAN1 : 10.6.1.0/24. Un réseau dans lequel des clients pourraient se connecter, accéder à internet, et plus tard accéder à nos services internes (un ptit site web de fou, ce sera partie III).

## 1. Serveur DHCP
## 2. Client

### ☀️ Prouvez que...

. le client a bien récupéré une adresse IP en DHCP
avec un ip a le mot-clé dynamic doit être écrit sur la ligne qui contient l'adresse IP
(y'a pas ce mot-clé quand tu définis une IP statique)


. vous avez bien 1.1.1.1 en DNS

commande dans le mémo pour consulter l'adresse IP du serveur DNS connu


.vous avez bien la bonne passerelle indiquée

idem, dans le mémo, pour afficher l'adresse de la passerelle actuellement configurée :)


. que ça ping un nom de domaine public sans problème magueule

# III. LAN serveurzzzz
## 1. Intro serveur Web
```
On appelle serveur Web une machine qui exécute un programme qu'on appelle un service Web.
Un service Web est un programme qui écoute sur un port, attend la connexion de clients.

Par convention, le port sur lequel écoute les services Web HTTP c'est 80/tcp.

Un client est supposé se connecter au port envoyer une requête HTTP, et le serveur renverra alors une page HTML qui correspond à la requête du client.

Comme nc aux premiers TPs, sauf que quand tu te connectes, et que t'envoies la bonne requête, bah le service Web répond automatiquement une page HTML.

On va utiliser un service Web qui s'appelle NGINX, réputé pour ses performances et sa stabilité !
```
## 2. Install this shiet
```
On est sur notre (futur) beau serveur Web web.tp6.b1.

On est pas en cours de Linux, ni en cours de dév Web, alors on va s'intéresser à la partie réseau uniquement, et limiter au maximum les interactions spécifiques à Linux.
➜ Installez et démarrez le service web NGINX

# installation du service NGINX
sudo dnf install -y nginx

# démarrage du service NGINX
sudo systemctl enable --now nginx


Devrait po y avoir d'erreurs, et ça tourne !

Le service web NGINX propose une page d'accueil (toute moche) par défaut. On aura même pas besoin d'écrire une vieille page HTML pour tester :D Il permet si on le configure d'héberger les sites Web de notre choix dans une utilisation réelle.
```
## 3. Analyse et test
### ☀️ Déterminer sur quel port écoute le serveur NGINX

```
[root@Web william]# sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=39662,fd=6),("nginx",pid=39661,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=39662,fd=7),("nginx",pid=39661,fd=7))
```
### ☀️ Ouvrir ce port dans le firewall

```
[root@Web william]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 80/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
  ```
### ☀️ Visitez le site web !
  ```
  william@willclient1:~$ curl http://10.6.2.11
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/

      html {
        height: 100%;
        width: 100%;
      }
```
# 2. Serveur DNS
## 4. Analyse du service
### ☀️ Déterminer sur quel(s) port(s) écoute le service BIND9.
```
[root@dns william]# sudo ss -lmpt | grep 53
LISTEN 0      10         10.6.2.12:domain      0.0.0.0:*    users:(("named",pid=11538,fd=25))
LISTEN 0      10         10.0.3.15:domain      0.0.0.0:*    users:(("named",pid=11538,fd=27))
LISTEN 0      4096       127.0.0.1:rndc        0.0.0.0:*    users:(("named",pid=11538,fd=30))
LISTEN 0      10         127.0.0.1:domain      0.0.0.0:*    users:(("named",pid=11538,fd=22))
LISTEN 0      4096           [::1]:rndc           [::]:*    users:(("named",pid=11538,fd=31))
LISTEN 0      10             [::1]:domain         [::]:*    users:(("named",pid=11538,fd=29))
```


### ☀️ Ouvrir ce(s) port(s) dans le firewall.
```
[root@dns william]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 53/tcp 53/udp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

# 5. Tests manuels
### ☀️ Effectuez des requêtes DNS manuellement depuis le serveur DNS lui-même dans un premier temps

```
[root@dns william]# dig web.tp6.b1 @10.6.2.12
;; ANSWER SECTION:
web.tp6.b1.             86400   IN    A10.6.2.11

[root@dns william]# dig dns.tp6.b1 @10.6.2.12
;; ANSWER SECTION:
dns.tp6.b1.             86400   IN      A       10.6.2.12

[root@dns william]# dig ynov.com @10.6.2.12
;; ANSWER SECTION:
ynov.com.               300     IN      A       104.26.10.233
ynov.com.               300     IN      A       172.67.74.226
ynov.com.               300     IN      A       104.26.11.233

[root@dns william]# dig -x 10.6.2.11 @10.6.2.12
;; ANSWER SECTION:
11.2.6.10.in-addr.arpa. 86400   IN      PTR     web.tp6.b1.

[root@dns william]# dig -x 10.6.2.12 @10.6.2.12 
;; ANSWER SECTION: 12.2.6.10.in-addr.arpa. 86400 IN PTR dns.tp6.b1.
```
### ☀️ Effectuez une requête DNS manuellement depuis client1.tp6.b1
```
william@willclient1:~$ nslookup web.tp.b1 ^C william@willclient1:~$ nslookup web.tp6.b1 Server: 127.0.0.53 Address: 127.0.0.53#53

Non-authoritative answer: Name: web.tp6.b1 Address: 10.6.2.11

```
### ☀️ Capturez une requête DNS et la réponse de votre serveur
```
Voir fichier dns.pcap 
```

# 3. Serveur DHCP
- récupérez une IP en DHCP sur ce nouveau client2.tp6.b1
```
william@client2:~$ ip a
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:93:ad:7e brd ff:ff:ff:ff:ff:ff
    inet 10.6.1.39/24 brd 10.6.1.255 scope global dynamic noprefixroute enp0s8
       valid_lft 42496sec preferred_lft 42496sec
    inet6 fe80::a00:27ff:fe93:ad7e/64 scope link
       valid_lft forever preferred_lft forever
```
 - vérifiez que vous avez bien 10.6.2.12 comme serveur DNS à contacter
```
william@client2:~$ resolvectl
Global
         Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
  resolv.conf mode: stub

Link 2 (enp0s8)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 10.6.2.12
       DNS Servers: 10.6.2.12
```
