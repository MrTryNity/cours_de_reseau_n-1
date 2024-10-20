**☀️ Uniquement avec des commandes, prouvez-que :**

Votre PC :
Adresse IPv4. . . . . . . . . . . . . .: 10.5.1.1

client1.tp5.b1 : 
inet 10.5.1.11/24 brd 10.5.1.255 scope global noprefixroute enp0s8

client2.tp5.b1 :
inet 10.5.1.12/24 brd 10.5.1.255 scope global noprefixroute enp0s8

routeur.tp5.b1 :
inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s8

**Votre PC :**
PS C:\Users\Mathis> ping 10.5.1.1

Envoi d’une requête 'Ping'  10.5.1.1 avec 32 octets de données :
Réponse de 10.5.1.1 : octets=32 temps<1ms TTL=128
Réponse de 10.5.1.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.5.1.1:
    Paquets : envoyés = 2, reçus = 2, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
Ctrl+C
PS C:\Users\Mathis> ping 10.5.1.11

Envoi d’une requête 'Ping'  10.5.1.11 avec 32 octets de données :
Réponse de 10.5.1.11 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.11 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 10.5.1.11:
    Paquets : envoyés = 2, reçus = 2, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
Ctrl+C
PS C:\Users\Mathis> ping 10.5.1.12

Envoi d’une requête 'Ping'  10.5.1.12 avec 32 octets de données :
Réponse de 10.5.1.12 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.12 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 10.5.1.12:
    Paquets : envoyés = 2, reçus = 2, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
Ctrl+C
PS C:\Users\Mathis> ping 10.5.1.254

Envoi d’une requête 'Ping'  10.5.1.254 avec 32 octets de données :
Réponse de 10.5.1.254 : octets=32 temps<1ms TTL=64
Réponse de 10.5.1.254 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 10.5.1.254:
    Paquets : envoyés = 2, reçus = 2, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms


__**1. Accès internet routeur**__

**☀️ Déjà, prouvez que le routeur a un accès internet**

[mrtrynity@vbox ~]$ ping www.ynov.com
PING www.ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=255 time=38.6 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=255 time=33.8 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=3 ttl=255 time=48.5 ms

**☀️ Activez le routage**
sudo firewall-cmd --add-masquerade --permanent
success
sudo firewall-cmd --reload
success

__**2. Accès internet clients**__

**☀️ Prouvez que les clients ont un accès internet**
client 1 
ping ynov.com
PING ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226: icmp_seq=1 ttl=254 time=15.6 ms
64 bytes from 172.67.74.226: icmp_seq=2 ttl=254 time=16.0 ms
64 bytes from 172.67.74.226: icmp_seq=3 ttl=254 time=18.2 ms
64 bytes from 172.67.74.226: icmp_seq=4 ttl=254 time=15.6 ms
^C
--- ynov.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 15.629/16.374/18.246/1.089 ms

client 2
ping ynov.com
PING ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233: icmp_seq=1 ttl=254 time=16.2 ms
64 bytes from 104.26.10.233: icmp_seq=2 ttl=254 time=18.6 ms
^C
--- ynov.com ping statistics ---
3 packets transmitted, 2 received, 33.3333% packet loss, time 2005ms
rtt min/avg/max/mdev = 16.187/17.379/18.571/1.192 ms

**☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau**
 
  [1/1]                                             /etc/netplan/01-netcfg.yaml                                                       network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s8:
      dhcp4: no
      addresses: [10.5.1.12/24]
      gateway4: 10.5.1.254
      nameservers:
        addresses: [1.1.1.1]

**__III. Serveur SSH__**

**☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH**

[mrtrynity@vbox ~]$ sudo ss -lnpt | grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=758,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=758,fd=4))

**☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert**

public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh

__**IV. Serveur DHCP**__




