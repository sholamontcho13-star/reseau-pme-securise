# Scénario : réseau d'Alpha Conseil

## Contexte
Alpha Conseil est un cabinet de conseil de 45 personnes réparti sur deux sites :
- **Siège** : 30 collaborateurs, les serveurs de l'entreprise et la salle d'accueil des visiteurs
- **Agence** : 15 collaborateurs

L'entreprise manipule des documents clients confidentiels. Elle veut un réseau
sécurisé, segmenté et capable de continuer à fonctionner en cas de panne d'un lien.

## Besoins métier
- Les collaborateurs accèdent aux serveurs internes et à Internet
- Les visiteurs disposent d'un accès Internet uniquement, sans aucun accès au réseau interne
- Le site web vitrine de l'entreprise est accessible depuis Internet
- Le siège et l'agence communiquent en permanence
- Les équipements sont administrés à distance de façon sécurisée

## Architecture prévue
**Siège**
- 1 routeur, 2 switchs
- VLAN 10 Utilisateurs, VLAN 20 Serveurs (fichiers, DHCP), VLAN 30 Invités,
  VLAN 40 DMZ (serveurs web et DNS), VLAN 99 Management

**Agence**
- 1 routeur, 1 switch
- VLAN 10 Utilisateurs, VLAN 30 Invités, VLAN 99 Management

**Interconnexion**
- Un lien principal et un lien de secours entre le siège et l'agence
- Un accès à Internet simulé

## Exigences de sécurité
- Segmentation par VLANs et filtrage par ACL
- Durcissement des équipements (SSH, mots de passe chiffrés, ports inutilisés coupés)
- Protection des accès physiques (port-security, DHCP snooping)
- Exposition minimale du serveur web (HTTP/HTTPS uniquement)

## Hors périmètre
Pare-feu dédié, SIEM, VPN. Ils pourront être ajoutés dans une évolution du projet.
