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


**1. Accès internet routeur**

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


