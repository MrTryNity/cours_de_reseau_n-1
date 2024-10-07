**Prouvez que votre configuration est effective**

Get-NetIPAddress -InterfaceAlias ethernet


IPAddress         : fe80::9226:ac14:8677:ca47%4
InterfaceIndex    : 4
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     : Infinite ([TimeSpan]::MaxValue)
PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.1.1.2
InterfaceIndex    : 4
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     : Infinite ([TimeSpan]::MaxValue)
PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
SkipAsSource      : False
PolicyStore       : ActiveStore


**Tester que votre LAN + votre adressage IP est fonctionnel**

ping 10.1.1.1

Envoi d’une requête 'Ping'  10.1.1.1 avec 32 octets de données :
Réponse de 10.1.1.1 : octets=32 temps=1 ms TTL=128
Réponse de 10.1.1.1 : octets=32 temps=2 ms TTL=128
Réponse de 10.1.1.1 : octets=32 temps=2 ms TTL=128
Réponse de 10.1.1.1 : octets=32 temps=1 ms TTL=128

Statistiques Ping pour 10.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 2ms, Moyenne = 1ms

**Capture de ping**

PS C:\WINDOWS\system32> netstat -a -b -n | Select-String 9999

  TCP    0.0.0.0:9999           0.0.0.0:0              LISTENING

**Echangez-vous des messages**

PS C:\WINDOWS\system32> nc -lnvp 9999
listening on [any] 9999 ...
connect to [10.1.1.2] from (UNKNOWN) [10.1.1.1] 53539
salut
wsh
cidsvpfxdvùfd
vdbmd

**Utilisez une commande qui permet de voir la connexion en cours**

PS C:\WINDOWS\system32> netstat -a -b -n | Select-String 9999

  TCP    10.1.1.2:9999          10.1.1.1:53539         ESTABLISHED

**Inversez les rôles**

PS C:\WINDOWS\system32> nc 10.1.1.1 9999
salut
salut

PS C:\WINDOWS\system32> netstat -a -b -n | Select-String 9999

  TCP    10.1.1.2:13836         10.1.1.1:9999          ESTABLISHED

**Pour les 5 applications**