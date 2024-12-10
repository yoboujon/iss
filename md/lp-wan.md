# LP Wan

## IPv6

Chaque paquet est composé de plusieurs fonctionnalitée directement intégré, chaque nouveau champ de donné peut être considéré comme une fonction. Il utilise énormement le multicast.

### Link-Local
Il est possible de créer une addresse IPv6 privée à partir de l'addresse MAC: cela s'appelle le **Link-local**. Elle commence toujours par `fe80::/10`, ensuite l'adresse MAC est convertie directement dans le reste de l'adresse IPv6. Soit le format suivant: `xx:xx:xx:xx:xx:xx:ff:fe` avec le dernier bit à 0 pour les adresses locales.

### Unique-local
A partir du format de plage `fc00::/7`, les adresses sont générées à partir d'un préfixe global unique dans un même réseau. Elles sont utilisables dans un réseau privé uniquement.

### Unique-global
Ces adresses sont routables dans internet, elles sont attribuées directement par les routeurs elles ont un format de `2000::/3`.

### Problèmes d'IPv6
- pas d'ARP
- pas de détection d'addresse double
- 40 octets d'entête: très gourmand
- MTU minimum de 1280 bytes (beaucoup pour un $\mu C$)

## 6LowPAN

Routage utilisant le Spanning Tree. Le but sera de compresser la taille du header, de faire une fragmentation efficace pour combattre le MTU minimum, permettre de découvrir les voisins. La possibilité de faire du *multi-hop layout*.

### Fonctionnement

Les premiers bits sont la compression de l'entête à quelques bits:
- `version` est supprimé
- `flow label` est optionnel
- `traffic class` est optionnel
- `payload length` supptimé car il est possible de le retrouver
- `next header` perd quelques bits
- `hop limit` est intact.
- Diminution des addresses dépend de comment il est fait
    - Local: On garde uniquement les bits différents de l'adresse MAC
    - Global: On garde uniquement le formattage qui n'est pas statique

Il existe par la suite un nouveau header nommé le "LOWPAN_IPHCHeader bitmap" qui précise quels headers sont compressés ou supprimés. Ce bitmap est uniquement réalisé par l'emetteur.

Très utile pour des noeuds entre elles, mais les next hop sont assez inefficaces.