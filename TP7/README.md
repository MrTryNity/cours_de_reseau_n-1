**Lister les ports en écoute sur la machine**
[root@web ~]# sudo ss -lnpt | grep nginx
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=11700,fd=6),("nginx",pid=11699,fd=6),("nginx",pid=11698,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=11700,fd=7),("nginx",pid=11699,fd=7),("nginx",pid=11698,fd=7))


 **Vérifier que ça a pris effet**
mathis@client1:~$ ping sitedefou.tp7.b1
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=0.423 ms