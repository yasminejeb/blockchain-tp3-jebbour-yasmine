# Analyse : quelle technologie pour la vérification des diplômes universitaires au Maroc ?

## 1. Introduction et problème
Lorsqu'un employeur reçoit un diplôme universitaire, il doit s'assurer qu'il est authentique. Aujourd'hui, cette vérification repose souvent sur un contact direct avec l'université, par courrier, par e-mail ou par téléphone, ce qui est lent et peu standardisé. Elle est aussi difficile pour les employeurs étrangers, qui ne connaissent pas toujours les établissements marocains.

Le problème est double. D'une part, les faux diplômes existent et sont difficiles à repérer sur un simple document papier ou PDF. D'autre part, la vérification dépend d'un seul acteur, l'établissement émetteur : si celui-ci ferme, perd ses archives ou ne répond pas, le diplôme ne peut plus être prouvé.

La blockchain est souvent présentée comme une solution à ce type de problème. Mais elle n'est pas toujours le meilleur outil : une base de données classique peut suffire dans certains cas, et un registre permissionné peut être plus adapté qu'une blockchain publique.

**Question étudiée :** quelle technologie (base de données classique, registre permissionné ou blockchain publique) convient le mieux à la vérification des diplômes universitaires au Maroc ?

## 2. Les acteurs et le besoin
### Les acteurs

- **L'étudiant** : il obtient le diplôme et veut pouvoir le prouver facilement, toute sa vie.
- **L'université** : elle délivre le diplôme et en est responsable.
- **L'employeur** : il veut vérifier rapidement qu'un diplôme est authentique.
- **Le ministère de l'Enseignement supérieur** : il peut superviser ou coordonner le système au niveau national.

### Ce que le système doit garantir

- **Authenticité** : un diplôme falsifié doit être détecté.
- **Rapidité** : la vérification doit prendre quelques secondes, pas plusieurs semaines.
- **Confidentialité** : les données personnelles de l'étudiant ne doivent pas être exposées publiquement.
- **Coût raisonnable** : pour les universités comme pour les employeurs.
- **Durabilité** : le diplôme doit rester vérifiable pendant 30 ans ou plus, même si l'université change ou disparaît.

## 3. Les trois solutions

### 3.1 Base de données classique
L'université (ou le ministère) enregistre les diplômes dans une base de données qu'elle contrôle. Pour vérifier un diplôme, l'employeur interroge un portail en ligne. La solution est rapide, peu coûteuse et simple à mettre en place. Son point faible est la confiance : l'administrateur peut modifier ou supprimer une ligne, et la base peut être piratée ou perdue. Le diplôme n'est vérifiable que tant que l'institution maintient son système.

### 3.2 Registre permissionné
Un registre permissionné est une blockchain dont seuls des membres autorisés peuvent écrire, par exemple plusieurs universités et le ministère. Hyperledger Fabric en est un exemple connu. Chaque diplôme est enregistré sur un registre partagé : aucun membre ne peut modifier seul l'historique, et la responsabilité est répartie. En revanche, il faut créer un consortium, financer l'infrastructure et gérer la gouvernance (qui entre, qui sort, qui décide). Les données restent accessibles aux seuls membres, ce qui protège mieux la confidentialité.

### 3.3 Blockchain publique
Sur une blockchain publique comme Bitcoin ou Ethereum, tout le monde peut lire les données et personne ne peut les modifier après coup. On ne publie jamais le diplôme lui-même, mais son **empreinte (hash)**, un code unique calculé à partir du document : si le document change d'un seul caractère, l'empreinte change. L'employeur recalcule l'empreinte du diplôme reçu et la compare à celle publiée. Des projets comme Blockcerts ou OpenTimestamps reposent sur ce principe. La falsification devient très difficile, et la preuve ne dépend plus de l'université. Les inconvénients sont les frais de transaction, la visibilité des données publiées et l'impossibilité de les effacer, ce qui pose problème avec la protection des données personnelles.
## 4. Tableau comparatif
| Critère | Base classique | Registre permissionné | Blockchain publique |
|---|---|---|---|
| Coût | Faible | Moyen | Variable (frais de transaction) |
| Rapidité de vérification | Très bonne | Bonne | Bonne (dépend du réseau) |
| Résistance à la falsification | Dépend de l'administrateur | Élevée | Très élevée |
| Confidentialité | Contrôlée | Contrôlée | Faible si on publie trop de données |
| Gouvernance | Centralisée | Partagée | Décentralisée |
| Protection des données personnelles | Facile à respecter | Plus complexe | Difficile (données non effaçables) |
| Maturité et facilité d'adoption | Très simple | Demande un consortium | Simple techniquement, mais peu connue des employeurs |

**Commentaires**

- **Coût** : la base classique est la moins chère. Le registre permissionné demande une infrastructure partagée. La blockchain publique coûte peu par empreinte, mais les frais varient.
- **Falsification** : dans une base classique, un administrateur malhonnête ou un pirate peut modifier les données. Le registre et la blockchain rendent cela beaucoup plus difficile.
- **Confidentialité** : sur une blockchain publique, ce qui est publié reste visible pour toujours, d'où l'intérêt de ne publier que l'empreinte.
- **Gouvernance** : plus on décentralise, moins on dépend d'un seul acteur, mais plus la coordination est complexe.
- **Données personnelles** : la loi marocaine 09-08, supervisée par la CNDP, protège les données personnelles. Le droit de rectification ou d'effacement est difficile à concilier avec une donnée inscrite de façon permanente.
## 5. Recommandation
Je recommande une solution **hybride** : une base de données gérée par l'université, avec l'**empreinte de chaque diplôme ancrée périodiquement sur une blockchain publique**.

- Les données personnelles restent dans la base de l'université, hors blockchain, ce qui facilite le respect de la loi 09-08.
- Seule l'empreinte est publiée, ce qui ne révèle aucune information sur l'étudiant.
- L'employeur peut vérifier l'authenticité sans dépendre de la bonne volonté de l'université, en recalculant l'empreinte.
- Le coût reste faible, car on ancre des lots d'empreintes et non chaque diplôme séparément.

Un registre permissionné serait préférable si plusieurs universités et le ministère voulaient partager un système commun avec une gouvernance claire. Une blockchain publique seule n'est pas adaptée, car elle ne résout pas la question de la confidentialité.
## 6. Limites
- **Coût et compétences** : la mise en place demande un budget et des équipes formées.
- **Adoption** : il faut que les universités et les employeurs acceptent de changer leurs pratiques.
- **Cadre juridique** : la valeur légale d'une preuve par empreinte doit être reconnue.
- **Erreurs** : si un diplôme est enregistré par erreur, on ne peut pas effacer l'empreinte, mais seulement publier une correction ou une révocation.
- **Limite de cette analyse** : elle repose sur des sources publiques et sur un raisonnement théorique, sans test réel ni données chiffrées sur le Maroc.
## 7. Sources
- Blockcerts, « Introduction » (standard ouvert pour émettre et vérifier des certificats sur blockchain), https://blockcerts.org/guide, consulté le 8 novembre 2026.
- Blockcerts, « About Blockcerts » (origine : MIT Media Lab et Learning Machine, aujourd'hui géré par Hyland), https://www.blockcerts.org/about, consulté le 8 novembre 2026.
- Peter Todd, « OpenTimestamps: Scalable, Trust-Minimized, Distributed Timestamping with Bitcoin » (annonce du projet, regroupement de nombreux horodatages dans une seule transaction Bitcoin), https://petertodd.org/2016/opentimestamps-announcement, consulté le 8 novembre 2026.
- Hyperledger Fabric, « What is Hyperledger Fabric? » (différence entre blockchain permissionnée et sans permission), https://hyperledger-fabric.readthedocs.io/en/latest/_sources/whatis.md.txt, consulté le 8 novembre 2026.
- Hyperledger Fabric, documentation officielle, https://hyperledger-fabric.readthedocs.io/, consulté le 8 novembre 2026.
- Dahir n° 1-09-15 du 18 février 2009 portant promulgation de la loi n° 09-08 relative à la protection des personnes physiques à l'égard du traitement des données à caractère personnel, https://ires.ma/iip/?p=16722, consulté le 8 novembre 2026.
- CNDP (Commission nationale de contrôle de la protection des données à caractère personnel), site officiel, https://www.cndp.ma, consulté le 8 novembre 2026.