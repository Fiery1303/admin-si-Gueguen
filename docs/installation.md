Fiche d'installation - TP1



1\. SRV-DC01 (Windows Server 2025)

IP fixe : "10.10.0.10/24", passerelle "10.10.0.2".

AD DS \& DNS : Domaine "pme.lan" promu via PowerShell".

DHCP : Étendue "10.10.0.100" à "10.10.0.200".

Annuaire : OU "PME" (Utilisateurs, Groupes, Serveurs) créée via script "New-StructureAD.ps1".



2\. SRV-WEB01 (Debian 13)

Réseau : IP fixe "10.10.0.20/24" configurée dans "/etc/network/interfaces".

DNS \& NTP : DNS pointé vers "10.10.0.10", NTP synchronisé sur "srv-dc01.pme.lan".



Jonction AD : Paquets "realmd", "sssd", "adcli", "krb5-user" installés.

Commande : "sudo realm join -U Administrator --computer-ou="OU=Serveurs,OU=PME,DC=pme,DC=lan" pme.lan".



Droits Sudo : Configuré dans "/etc/sudoers.d/admins-linux" pour "%gg\_admins\_linux@pme.lan".



SSH : Clé "ed25519" déployée + durcissement ("PermitRootLogin no", "PubkeyAuthentication yes").



Web \& Pare-feu : Nginx installé, UFW activé avec autorisations "OpenSSH" et "Nginx HTTP".



3\. Problèmes rencontrés \& Solutions

Échec "realm join" : Utilisation de "-U Administrator" au lieu de "-U Administrateur" car le système Windows Server était en anglais.

