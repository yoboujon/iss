## 4 pilliers pour la virtualisation réseau
- Implementation de fonctions réseaux (**NF**) sous forme de logiciels
    - *ex: Proxy, Load Balancer*
- Deploiement des formats déployables, avec des packages
    - *ex: VM*
- Composition des **NF** (remplaçage de chaque brique dans la chaîne)
- Utilisation d'APIs pour la gestion + orchestration des **NF**

## Ce qui a été fait en cours de Cloud

- Les routeurs sont de type logiciel: *NF sous forme logicielle*
- Utilisation de containers ou machines virtuelles: *Deploiement des NF dans des formats déployables*
- ?
- Utilisation sous Openstack d'opérations de gestion, par la suite une API python pour modifier Openstack: *Automatisation via APIs de la gestion & Orchestration des NF*

## Standard et Principes de NFV

Standardisation: 
- ETSI GS NFV 002 
- ETSI GS NFV-MAN 001

une **NFV** permettra, de façon standardisée, de décrire et mettre en oeuvre des *"services"* (NS: Network Service) définis dans comme une succession de fonctions de réseau, ceci dans un environnement virtualisé. Notamment avec l'utilisation de serveurs isolés

### Modèle académique d'une NFV

NFV (Virtualisation des fonctions réseau) c'est un programme *(routeur, carte réseau virtuelle et une enveloppe)* qui extrait des fonctions réseaux et permet de contrôler ou manipuler les packets qui sont envoyés sur sa carte réseau. Elle possède souvent des primitives pour gérer des packets avec une API (libtcpdump, libwireshark...).

- **Utilisation de NFVd (NFV descriptors):** des fichiers de description avec le nom, vendeur, version, caractéristiques, événements du cycle de vie, opérations associées et réseau d'appartenance.
- **Utilisation de NFV dependency:** l'ordre dans lequel chaque server doit être lancé
- **Connection points:** ports, @MAC, @IP, VLAN ID

Une NFV possède un cycle de vie (démarrer, arrêter, supprimer).

**OSS/BSS**: Operationnal Support System/Business Support System, établie des services requis, des services d'exploitation de performances.

**NFVI**: NFV Infrastructure, ensemble des serveurs physiques et équipements réseaux mettant en oeuvre l'infrastructure de virtualisation.

**MANO**: management and network orchestration, possède un orchestrateur qui gère les cycles de vies (NFVO), un ou plusieurs manager de NFV (NFVM), un second orchestrateur qui gère l'infrastructure de virtualisation et de mettre en oeuvre les demandes de ressources des NFVM+NFVO, et enfin un REPO, descripteur de services réseaux et politique de gestion.

Open Source MANO est une implémentation développé par ETSI pour utiliser MANO. Cependant une solution plus légère nommée OpenBaton sera utilisé.

Il est possible de faire du chaînage de NFV par un graphe, avec des PNF (virtualisation des fonctions réseau Physique), KNF aussi pour une virtualisation sous Kubernetes. Ce chaînage permet d'avoir un point A vers un point B utilisant plusieurs infrastructures avec des Functions Réseaux (NF).

### Conclusion

NFV permet de d'utiliser des API pour permettre de faire des fonctions réseaux virtuelles, il est possible d'en chaîner plusieurs, ils dialoguent entre eux avec des NS. On peut les virtualiser dans des VM et des containers. Une VNF est une fonction qui peut être décomposée dans plusieurs VM, notamment avec VNFc *(container)*.

Quand on insère une VNF, on peut utiliser un SDN pour modifier les paquets et les rediriger vers les VNF.

### TP/TD

- mininet + containernet
- VIM sous VNF, pas MANO
- pas 1 seul Switch/ Ni 3000 Switch
- logique de gestion MAPE-K : Capteurs donne des données: **Observer, Analyser, Planifier, Executer** des Actions sont donnés à des Actionneurs.
- SDN change le traffic sortant de la gateway 1 vers le NFV

https://tiny.cc/Projet-SDCI
https://docs.google.com/presentation/d/1N_HovdFQlvxd32VUzZlEpD46pnBx_45RN4CnxDaeWEs/edit#slide=id.g2a3a7444ff_0_386

https://tiny.cc/Projet-SDCI-Infos
https://docs.google.com/document/d/1V1F-qK6Qz-YdlYJNXdcmtNZ6JqSJ76xdJ70pXGS9_G0/edit?tab=t.0

https://tiny.cc/CM-SDN
https://docs.google.com/presentation/d/1hbimXCK9TdbQ4chgJU-r6rcu3_CRtUJeNhCqhB_ifN4/edit#slide=id.g29b8b0e273_1_7

https://tiny.cc/TP-SDN
https://docs.google.com/document/d/12ASY9uIcCWtvEUPvqj_BjFp_2j-4_emWMXPPGrkEvw8/edit?tab=t.0

https://tiny.cc/CM-NFV
https://docs.google.com/presentation/d/1CRda7VK6MPpfG4TPHr9GR2pLNQkmv4A4p3Xq3L23wKc/edit#slide=id.g29b8b0e273_1_7

**Zone 1**: on créer beaucoup de device avec un Gateway a faible capture de paquets.

- **Action 1**: Déploiement 2ème GI et partage de traffic
- [x] **Action 2**: Déploiement Ordonnanceur: $Z_1$/$Z_2$/$Z_3$ -> $Ord$ -> $GI$
- **Action 3**: Déploiement Load Balancer: $Z_1$/$Z_2$/$Z_3$ -> $Load$ -> $GI/GI_2/GI_3$
- **Action 4**: Déploiement Rate Limiting (niveau 4)/Cache: $Z_1$ -> $GI$ et $Z_2$/$Z_3$ -> $VNF$ -> $GI$
- [ ] **Action 5 (full SDN)**: Rejet/Rate Limiting (niveau 7) au niveau du traffic $Z_2$/$Z_3$

**API Gateway**: `/ping`, `/health`

### Monitoring
- Monitoring avec temps de réponse app de la Gateway et l'état des ressources *(Middleware)*
- Monitoring app via un VNF proxy *(L7, deployement d'une VNF dans la gateway avant celle de monitoring)*
- [x] Monitoring L2/L3: Observer avec un SDN (Openflow) le counter des paquets entrants dans chaque port 

### Admin

1. Monitoring
2. Adaptation
3. Topologie
4. Mode auto.

### Work

Dockerfile, Scripts python