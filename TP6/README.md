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
