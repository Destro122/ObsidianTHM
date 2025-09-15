Nmap permet de scanner le réseau pour différentes requêtes?.
Il y'a plusieurs moyens de spécifié les cibles :
 - - pour range d'ip (ex 192.168.0.1-10)
 - / pour range de subnet (192.168.0.1/24 -> 192.168.0.0-255)
 - Nom d'hote

## Scanner un réseau local / Host discovery 
nmap -sn ip 
lance un requete arp sur le réseau pour récuperer who is up
-sL permet de lister toutes les tentatives

# Port Scanning
### TCP
Deux possibilités : 
- connect avec -sT : Fait un threeway handshake complet 
- SYN avec -sS : est considéré comme plus discret
### UDP
-sU pour scanner les applications connecté en UDP

| Option     | Explanation                                                  |
|------------|--------------------------------------------------------------|
| `-sT`      | TCP connect scan – complete three-way handshake              |
| `-sS`      | TCP SYN – only first step of the three-way handshake         |
| `-sU`      | UDP scan                                                     |
| `-F`       | Fast mode – scans the 100 most common ports                  |
| `-p[range]`| Specifies a range of port numbers – `-p-` scans all the ports|
# Version Detection
| Option | Explanation                                          |
| ------ | ---------------------------------------------------- |
| `-O`   | OS detection                                         |
| `-sV`  | Service and version detection                        |
| `-A`   | OS detection, version detection, and other additions |
| `-Pn`  | Scan hosts that appear to be down                    |
# Timer
|Option|Explanation|
|---|---|
|`-T<0-5>`|Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)|
|`--min-parallelism <numprobes>` and `--max-parallelism <numprobes>`|Minimum and maximum number of parallel probes|
|`--min-rate <number>` and `--max-rate <number>`|Minimum and maximum rate (packets/second)|
|`--host-timeout`|Maximum amount of time to wait for a target host|
# output
|   |   |
|---|---|
|**_Real-time output_**||
|`-v`|Verbosity level – for example, `-vv` and `-v4`|
|`-d`|Debugging level – for example `-d` and `-d9`|
|**_Report_**||
|`-oN <filename>`|Normal output|
|`-oX <filename>`|XML output|
|`-oG <filename>`|`grep`-able output|
|`-oA <basename>`|Output in all major formats|