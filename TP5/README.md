# TP5 : Un ptit LAN à nousI. 
## Setup
### ☀️ Uniquement avec des commandes, prouvez-que :
client 1 
```
william@william-VirtualBox:~$ ip a
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:25:fe:57 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.11/24 brd 10.5.1.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe25:fe57/64 scope link
       valid_lft forever preferred_lft forever
```
client 2
```
Wlliam@william-VirtualBox:~$ ip a 
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:d1:ed:aa brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.12/24 brd 10.5.1.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fed1:edaa/64 scope link
       valid_lft forever preferred_lft forever
```
Routeur
```
[root@william ~]# ip a 
2: enpBs3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000 1ink/ether 08:00:27:c1:6c:cc brd ff:ff:ff:ff:ff:ff inet 18.5.1.254/24 brd 10.5.1.255 scope global nopref ixroute enp8s3 valid_lft forever preferred_lft forever inet6 fe88::a80:27ff:fec1:6ccc/64 scope link valid_lft forever preferred_lft forever
``` 
mon pc : 
```
Carte Ethernet Ethernet 3 :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::6a73:3bb3:9937:7615%58
   Adresse IPv4. . . . . . . . . . . . . .: 10.5.1.1
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . :
```
### ping du : 
ping client 1 avec client 2

``` 
william@william-VirtualBox:~$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=1.61 ms
64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=4.23 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=1.58 ms
64 bytes from 10.5.1.11: icmp_seq=4 ttl=64 time=2.01 ms
^C
--- 10.5.1.11 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 1.578/2.355/4.225/1.092 ms
```
ping client 2 avec client 1
```
william@william-VirtualBox:~$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=3.60 ms
64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=0.906 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=1.53 ms
^C
--- 10.5.1.11 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2018ms
rtt min/avg/max/mdev = 0.906/2.012/3.597/1.149 ms
```
ping client 2 vers mon pc 
```
william@william-VirtualBox:~$ ping 10.5.1.1
PING 10.5.1.1 (10.5.1.1) 56(84) bytes of data.
64 bytes from 10.5.1.1: icmp_seq=1 ttl=128 time=1.39 ms
64 bytes from 10.5.1.1: icmp_seq=2 ttl=128 time=1.11 ms
64 bytes from 10.5.1.1: icmp_seq=3 ttl=128 time=1.57 ms
64 bytes from 10.5.1.1: icmp_seq=4 ttl=128 time=2.35 ms
^C
--- 10.5.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3036ms
rtt min/avg/max/mdev = 1.112/1.605/2.351/0.460 ms
```



# II. Accès internet pour tous 
## 1. Accès internet routeur
### ☀️ Déjà, prouvez que le routeur a un accès internet
```
[william@william ~]# ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=46 time=37.5 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=46 time=36.0 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=46 time=33.3 ms
^C
--- ynov.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2028ms
rtt min/avg/max/mdev = 33.367/35.587/37.451/1.639 ms
```
## 2.Accès internet clients 
### ☀️ Prouvez que les clients ont un accés internet 
```
william@william-VirtualBox:~$ ping www.ynov.com
PING www.ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233: icmp_seq=1 ttl=51 time=16.6 ms
64 bytes from 104.26.10.233: icmp_seq=2 ttl=51 time=15.8 ms
64 bytes from 104.26.10.233: icmp_seq=3 ttl=51 time=17.1 ms
64 bytes from 104.26.10.233: icmp_seq=4 ttl=51 time=14.6 ms
64 bytes from 104.26.10.233: icmp_seq=5 ttl=51 time=16.2 ms
^C
--- www.ynov.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4092ms
rtt min/avg/max/mdev = 14.748/15.912/17.132/0.928 ms
```
### ☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau: 
sur le client 2 :
```
william@william-VirtualBox:~$ cat /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [10.5.1.12/24]
      gateway4: 10.5.1.254
      nameservers:
        addresses: { 1.1.1.1 }
``` 
# III.Serveur SSH
## ☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH

```
[william@william ~]# sudo ss -lnpt| grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=697,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=697,fd=4))
```
## ☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert
```
[william@william ~]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 22/tcp
  protocols:
  forward: yes
  masquerade: yes
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
[root@routeur matheo]#
```
# IV. Serveur DHCP
## 1. Le but
### ☀️ Installez et configurez un serveur DHCP sur la machine routeur.tp5.b1
```
[william@william ~]# dnf -y install dhcp-server
[william@william ~]# sudo nano dhcpd.conf
```
### Contenu du fichier "dhcpd.conf
```
# specify DNS server's hostname or IP address
option domain-name-servers  1.1.1.1;
# specify network address and subnetmask
subnet 10.5.1.0 netmask 255.255.255.0 {
    # specify the range of lease IP address
    range dynamic-bootp 10.5.1.137 10.5.1.237;
    # specify broadcast address
    option broadcast-address 10.5.1.255;
    # specify gateway
    option routers 10.5.1.254;
}
```
```
[william@william dhcp]# systemctl enable --now dhcpd
[william@william dhcp]# firewall-cmd --add-service=dhcp
[william@william dhcp]# firewall-cmd --runtime-to-permanent
```
### B. Test avec un nouveau client
