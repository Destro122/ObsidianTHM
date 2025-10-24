Wireshark est un logiciel pour analysé le trafique d'un réseau.

Il est utilisé pour détecter et debugger les problèmes réseaux (congestion, load failure point), pour détecter les anomalies de sécurité (point d'accès non autorisé, usage anormaux des ports, trafic suspicieux) et investiguer et apprendre les détails des différents protocoles. (Code, payload)

## Colouring Packets
Wireshark permet de colorer les paquets afin d'avoir un apercu plus efficaces selon les protocoles ou selon ce que l'on recherche. Les options se trouves dans  **"View --> Coloring Rules"**.

## Traffic Sniffing
Blue Shark : capture le traffic

Il est possible de merge deux fichiers pcap. Ainsi que de voir les propriétés de ces mêmes fichiers dans l'onglet Statistics.

## Packets
Pour chaque packets il est possible de voir les détails. Pour chaque protocoles / chaque layer du model [[OSI]] on peut voir quelles bits du packet corresponds.

	Ctrl+G : Goto Packet avec le packet ID
	Ctrl+F : Find packet
		There are two crucial points in finding packets. The first is knowing the input type. This functionality accepts four types of inputs (Display filter, Hex, String and Regex). The second point is choosing the search field. You can conduct searches in the three panes (packet list, packet details, and packet bytes), and it is important to know the available information in each pane to find the event of interest.
	Ctrl+M : Mark le packet (afficjhé en noir)
	Ctrl+Alt+C : commenter le packet

## Expert 
![[Pasted image 20250727183608.png]]
## Packet Filtering

1. Right Click -> Apply as filter. Applique le filtre d'une trame sélectionnée sur le jeu de donnée
2. Right Click -> Conversation filter.  Filtre pour un certains protocole
3. 