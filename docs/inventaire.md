Inventaire TP1



Paramètres généraux

Domaine : "pme.lan"

Réseau : "10.10.0.0/24"

Passerelle : "10.10.0.2" (VMware)



Machines

SRV-DC01 : 

&#x09;Windows Server 2025 ("10.10.0.10") 

&#x09;Rôles : AD DS, DNS, DHCP.



SRV-WEB01 : 

&#x09;Debian 13 ("10.10.0.20") 

&#x09;Rôles : Serveur Web (Nginx), joint au domaine, pare-feu UFW.



Utilisateurs Active Directory

a.martin : Administratrice Linux (Groupe "GG\_Admins\_Linux" -> accès sudo).

b.durand : Utilisateur standard (Groupe "GG\_Utilisateurs").

