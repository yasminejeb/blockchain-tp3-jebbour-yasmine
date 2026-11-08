# Vérification des diplômes universitaires au Maroc : base de données, registre permissionné ou blockchain publique ?

**Auteur :** Yasmine JEBBOUR (compte GitHub : @yasminejeb)
**Cours :** Master FinTech / Blockchain, TP3 (projet individuel)

## Question étudiée
Quelle technologie (base de données classique, registre permissionné ou blockchain publique) convient le mieux à la vérification des diplômes universitaires au Maroc ?

## Démarche
Comparaison des trois technologies selon plusieurs critères : coût, rapidité de vérification, résistance à la falsification, confidentialité, gouvernance et conformité à la protection des données personnelles. L'analyse complète est dans le fichier `analyse.md`.

## Résultat
L'analyse recommande une solution hybride : une base de données gérée par l'université, avec l'empreinte (hash) de chaque diplôme ancrée périodiquement sur une blockchain publique. Les données personnelles restent hors chaîne, ce qui facilite le respect de la loi marocaine 09-08, et l'employeur peut vérifier l'authenticité d'un diplôme en recalculant son empreinte. Un registre permissionné serait préférable si plusieurs universités et le ministère souhaitaient partager un système commun avec une gouvernance claire. Une blockchain publique seule n'est pas adaptée, car elle ne règle pas la confidentialité.
## Sources
Les sources complètes, avec la date de consultation, sont dans la section 7 de [`analyse.md`](analyse.md). Principales références :
- Blockcerts : https://blockcerts.org/guide
- OpenTimestamps (Peter Todd) : https://petertodd.org/2016/opentimestamps-announcement
- Hyperledger Fabric : https://hyperledger-fabric.readthedocs.io/
- Loi 09-08 : https://ires.ma/iip/?p=16722
- CNDP : https://www.cndp.ma
## Outils utilisés
GitHub Desktop et GitHub.com, RStudio, Markdown, assistant d'IA (aide à la structuration et à la relecture du plan).
