# TP7 : On dit chiffrer pas crypter

## I. Setup
``` 
➜ Pour chaque machine

donnez une IP statique
pour l'accès internet

activer le routage sur le routeur
carte NAT sur le routeur
définir le routeur comme passerelle pour les autres
aussi, n'oubliez pas d'indiquer 1.1.1.1 en serveur DNS partout


nommez vos machines (configuration du hostname)
```

## II. Serveur Web

### 1. HTTP
### 🌞 Lister les ports en écoute sur la machine
```
[william@Web ~]$ sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1288,fd=6),("nginx",pid=1287,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1288,fd=7),("nginx",pid=1287,fd=7))
[william@Web ~]$
```
### 🌞 Ouvrir le port dans le firewall de la machine

```
[william@Web ~]$ sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 80/tcp 443/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```
## C. Tests client
### 🌞 Vérifier que ça a pris effet
```
william@william-VirtualBox:~$ ping sitedefou.tp7.b1
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=1.15 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=1.08 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=0.646 ms
^C
--- sitedefou.tp7.b1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2615ms
rtt min/avg/max/mdev = 0.646/0.957/1.149/0.222 ms
```
### 🌞 Vérifier que ça a pris effe
```
[william@client1 ~]$ curl http://sitedefou.tp7.b1
meow !
```
## D. Analyze 

### 🌞 Capture tcp_http.pcap
```
voire : tcp_http.pcap
```
### 🌞 Voir la connexion établie
```
william@client1:~$ ss -t -a
State  Recv-Q Send-Q         Local Address:Port          Peer Address:Port  
Process
ESTAB       0           0                         10.7.1.101:58478                    10.7.1.11:http
```
# 2. On rajoute un S 
## A. Config

### 🌞 Lister les ports en écoute sur la machine 
```
[william@Web ~]$ sudo ss -lnpt | grep 443
LISTEN 0      511        10.7.1.11:443       0.0.0.0:*    users:(("nginx",pid=6775,fd=6),("nginx",pid=6774,fd=6))
```

### 🌞 Gérer le firewall
```
[william@Web ~]$ sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 80/tcp 443/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

## B. Test test test analyyyze


### 🌞 Capture tcp_https.pcap
```
tcp_https.pcap
```

# III. Serveur VPN

## 1. Install et conf Wireguard
### 🌞 Prouvez que vous avez bien une nouvelle carte réseau wg0
```
[root@vpn william]# ip a
4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```
### 🌞 Déterminer sur quel port écoute Wireguard
```
[root@vpn william]# ss -lnpu | grep 51820
UNCONN 0      0            0.0.0.0:51820      0.0.0.0:*
UNCONN 0      0               [::]:51820         [::]:*
```
### 🌞 Ouvrez ce port dans le firewall
```
[root@vpn william]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s8 enp0s9
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 51820/udp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```
## 2. Ajout d'un client VPN

## 3. Proofs
### 🌞 Ping ping ping !
```
root@client1:/home/matheo# ping 10.7.200.1
PING 10.7.200.1 (10.7.200.1) 56(84) bytes of data.
64 bytes from 10.7.200.1: icmp_seq=1 ttl=64 time=0.598 ms
64 bytes from 10.7.200.1: icmp_seq=2 ttl=64 time=0.688 ms
64 bytes from 10.7.200.1: icmp_seq=3 ttl=64 time=1.72 ms
^C
--- 10.7.200.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2050ms
rtt min/avg/max/mdev = 0.624/0.951/1.606/0.489 ms
```
### 🌞 Capture ping1_vpn.pcap
```
william@client1:~$ sudo tcpdump -w ping1_vpn.pcap -i enp0s8
```
voir fichier "ping1_vpn.pcap"
### 🌞 Capture ping2_vpn.pcap
```
william@client1:~$ sudo tcpdump -w ping2_vpn.pcap -i enp0s8
```
voir fichier ping2_vpn.pcap
### 🌞 Prouvez que vous avez toujours un accès internet
```
root@client1:/home/william# ip route
default via 10.7.200.1 dev wg0
10.7.1.0/24 dev enp0s8 proto kernel scope link src 10.7.1.101 metric 100
10.7.200.0/24 dev wg0 proto kernel scope link src 10.7.200.11
```
```
root@client1:/home/william# ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233: icmp_seq=1 ttl=52 time=15.5 ms
64 bytes from 104.26.11.233: icmp_seq=2 ttl=52 time=16.6 ms
64 bytes from 104.26.11.233: icmp_seq=3 ttl=52 time=89.6 ms
^C
--- ynov.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 15.981/39.524/95.686/35.633 ms
```
## 4. Private service
### 🌞 Visitez le service Web à travers le VPN 
```
matheo@client1:~$ curl https://sitedefou.tp7.b1 -k
meow !
```
