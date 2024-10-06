**Adresses IP de ta machine :**

    affiche l'adresse IP que ta machine a sur sa carte réseau WiFi

           Adresse IPv4. . . . . . . . . . . . . .: 192.168.1.111

    affiche l'adresse IP que ta machine a sur sa carte réseau ethernet

           Adresse IPv4. . . . . . . . . . . . . .: 192.168.1.19

 **Si t'as un accès internet normal, d'autres infos sont forcément dispos...**

 Adresse IP de la passerelle du réseau local :

        Pour la carte Ethernet : 192.168.1.1
        Pour la carte Wi-Fi : 192.168.1.1

    Adresse IP du serveur DNS :

        Pour la carte Ethernet : 192.168.1.1
        Pour la carte Wi-Fi : 192.168.1.1

    Adresse IP du serveur DHCP :

        Pour la carte Ethernet : 192.168.1.1
        Pour la carte Wi-Fi : 192.168.1.1


**BONUS : Détermine s'il y a un pare-feu actif sur ta machine**

    pare-feu actif
    netsh advfirewall firewall show rule name=all

**Envoie un ping vers...**

    toi-même !

     ping 192.168.1.19

      Envoi d’une requête 'Ping'  192.168.1.19 avec 32 octets de données :
      Défaillance générale.
      Défaillance générale.
      Défaillance générale.
      Défaillance générale.

        Statistiques Ping pour 192.168.1.19:
            Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),

             normal windows bloque les pings
    
    vers l'adresse IP 127.0.0.1

    ping 127.0.0.1

    Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
    Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

    Statistiques Ping pour 127.0.0.1:
       Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
        Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

**On continue avec ping. Envoie un ping vers...**

    ta passerelle

**ping 192.168.1.1**

Envoi d’une requête 'Ping'  192.168.1.1 avec 32 octets de données :
Réponse de 192.168.1.1 : octets=32 temps<1ms TTL=64
Réponse de 192.168.1.1 : octets=32 temps<1ms TTL=64
Réponse de 192.168.1.1 : octets=32 temps<1ms TTL=64
Réponse de 192.168.1.1 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 192.168.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

**un(e) pote sur le réseau**

    J'ai pas de pote nis d'autre ordi chez moi

**un site internet**

ping www.thinkerview.com

Envoi d’une requête 'ping' sur www.thinkerview.com [2a06:98c1:3121::6] avec 32 octets de données :
Réponse de 2a06:98c1:3121::6 : temps=14 ms
Réponse de 2a06:98c1:3121::6 : temps=14 ms
Réponse de 2a06:98c1:3121::6 : temps=14 ms
Réponse de 2a06:98c1:3121::6 : temps=14 ms

Statistiques Ping pour 2a06:98c1:3121::6:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 14ms, Maximum = 14ms, Moyenne = 14ms

**Faire une requête DNS à la main**

**www.thinkerview.com**

nslookup www.thinkerview.com
Serveur :   ALG7
Address:  192.168.1.1

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3120::6
          2a06:98c1:3121::6
          188.114.96.6
          188.114.97.6

**www.wikileaks.org**

nslookup www.wikileaks.org
Serveur :   ALG7
Address:  192.168.1.1

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  80.81.248.21
          51.159.197.136
Aliases:  www.wikileaks.org

**www.torproject.org**

nslookup www.torproject.org
Serveur :   ALG7
Address:  192.168.1.1

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f9:c010:19eb::1
          2620:7:6002:0:466:39ff:fe7f:1826
          116.202.120.166
          204.8.99.144
          204.8.99.146
          116.202.120.165
          95.216.163.36

**Effectue un scan du réseau auquel tu es connecté**

nmap -sn -PR 192.168.1.0/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-10-06 20:57 Paris, Madrid (heure dÆÚtÚ)
Nmap scan report for ALG7 (192.168.1.1)
Host is up (0.00096s latency).
MAC Address: B0:B3:69:94:13:2E (Shenzhen Sdmc Technology)
Nmap scan report for DESKTOP-2SKU1PL (192.168.1.19)
Host is up.
Nmap scan report for DESKTOP-2SKU1PL (192.168.1.111)
Host is up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.16 seconds

**Changer d'adresse IP**

InterfaceAlias      : Wi-Fi
InterfaceAddress    : 192.168.1.20
PrefixLength        : 24
IPAddress           : 192.168.1.20
DefaultGateway      : 192.168.1.1
