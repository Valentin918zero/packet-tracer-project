# packet-tracer-project
Présentation des différentes étapes

Dans cette section, je présente les principales étapes de la réalisation de ce projet réseau. Chaque partie est accompagnée de captures d'écran issues de Cisco Packet Tracer ainsi que d'une explication de la configuration effectuée et de son rôle dans le fonctionnement de l'infrastructure. Ces illustrations permettent de suivre le développement du projet et de vérifier le bon fonctionnement du réseau.

**Vue d'ensemble de l'infrastructure réseau**

Zone Bleue (192.168.1.0)

  Périphériques d'extrémité : 4 PC (compta_1, compta_2, compta_3, compta_4).

  Équipements réseau : 1 Commutateur (Switch0) et 1 Routeur (Router0).

Zone Rouge (133.33.0.0)

  Périphériques d'extrémité : 1 PC (technicien_1), 1 Serveur Web (Serveur_web), et 4 Laptops sans fil (Laptop0 à Laptop3).

  Équipements réseau : 1 Commutateur (Switch1), 1 Point d'accès Wi-Fi (AccessPoint0), et 1 Routeur (Router1).

Zone Verte (192.168.2.0)

  Périphériques d'extrémité : 1 PC (chef), 1 Serveur DNS (serveur DNS), et 1 Imprimante réseau (imprimente).

  Équipements réseau : 1 Commutateur (Switch2) et 1 Routeur (Router2).

Interconnexions WAN (Liaisons Série)

  1.0.0.0 : Liaison entre Zone Bleue (Router0) et Zone Rouge (Router1).

  2.0.0.0 : Liaison entre Zone Bleue (Router0) et Zone Verte (Router2).

  3.0.0.0 : Liaison entre Zone Rouge (Router1) et Zone Verte (Router2).


**Plan d'adressage IP**

La première étape a consisté à définir un plan d'adressage IP en attribuant un réseau distinct à chaque zone de l'infrastructure afin d'assurer une organisation claire et une séparation des différents réseaux locaux.

Zone bleue : 192.168.1.0
Zone rouge : 133.33.0.0
Zone verte : 192.168.2.0

Chaque machine appartenant à une zone reçoit ensuite une adresse IP correspondant au réseau auquel elle est connectée, ce qui permet aux équipements de communiquer correctement une fois le routage configuré.

Pour la zone bleue et la zone verte, j'ai choisi de configurer les adresses IP manuellement sur chaque machine, sans utiliser de serveur DHCP. Cette méthode permet de contrôler précisément les paramètres réseau attribués à chaque équipement.



**Configuration des équipements**

Après avoir configuré les adresses IP des différents postes, j'ai renseigné la passerelle par défaut (Default Gateway) de chaque machine.

Pour chaque zone, la passerelle correspond à l'adresse IP de l'interface du routeur connectée au réseau concerné :

Zone bleue : 192.168.1.254
Zone rouge : 133.33.0.254
Zone verte : 192.168.2.254

J'ai choisi d'utiliser l'adresse se terminant par .254 comme passerelle pour chaque réseau. Il s'agit d'une convention couramment utilisée pour la dernière adresse utilisable du sous-réseau car elle est souvent attribuée au routeur. Les équipements savent ainsi vers quelle adresse envoyer les paquets destinés à un autre réseau.

Dans la section RIP Routing, j'ai déclaré tous les réseaux directement connectés à chaque routeur. Cela comprend :

le réseau local (LAN) de la zone concernée ;
les réseaux des liaisons WAN reliant les routeurs entre eux.

J'ai configuré les interfaces Serial de chaque routeur en leur attribuant les adresses IP correspondant aux réseaux des liaisons WAN (par exemple 1.0.0.0, 2.0.0.0, etc.)

*DNS et DHCP*

De plus, j'ai mis en place un serveur DNS dans la zone verte. Son rôle est d'associer des noms de domaine à des adresses IP, permettant ainsi d'accéder aux services du réseau en utilisant leur nom plutôt que leur adresse IP.

Dans la zone rouge, j'ai créé un serveur DHCP permettant d'attribuer automatiquement des adresses IP aux appareils connectés au réseau. Cette configuration permet de montrer les différentes méthodes d'attribution d'adresses IP utilisées dans une infrastructure réseau : l'attribution manuelle (statique) dans certaines zones et l'attribution automatique grâce au DHCP.

**Test de connectivité**

Afin de vérifier le bon fonctionnement de l'infrastructure réseau, j'ai réalisé plusieurs tests de connectivité à l'aide de la commande ping.

Cette commande permet d'envoyer des paquets vers une autre machine afin de vérifier si celle-ci est joignable et si les paquets sont correctement reçus.

J'ai effectué des tests entre des ordinateurs appartenant à des zones différentes afin de vérifier que la communication entre les différents réseaux fonctionne correctement grâce à la configuration du routage.

Les résultats des tests sont disponilbes dans les screens intitulés "test connectivité"  où l'on constate que les paquets sont bien transmis et que les machines des différentes zones arrivent à communiquer entre elles.


**Conclusion**

Ce projet m'a apporté beaucoup de connaissances sur le fonctionnement d'un réseau et comment ils communiquent entre eux . Le réseau informatique occupe une place essentielle dans de nombreux domaines de l'IT, notamment dans la cybersécurité, l'administration système, le cloud computing, les télécommunications et le développement d'applications connectées, qui sont des domaine svers lesquels j'aimerai travailler.

Merci d'avoir lu jusqu'au bout et j'éspère que par ce projet j'ai pu montrer mes connaissances et les appliquer dans cette simulation. 










