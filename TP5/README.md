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

ping client1 avec client 2

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

# II. Accès internet pour tous 
## 1. Accès internet routeur
### ☀️ Déjà, prouvez que le routeur a un accès internet




