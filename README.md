# Antisèche du web 3

Ce document est destiné à celles et ceux qui s’intéressent au web 3 et sentent qu'ils manquent de fondations pour comprendre et trier la mode, l'arnaque de ce qui rend un vrai service.

Le but de ce document est de distiller le fonctionnement de la technologie en principes compréhensibles. Il est le fruit d'années d'explorations, d'experimentation et d'une proposition de services sur laquelle l'auteur pari qu'elle restera une fois la vague d'excitation passée.

Le document est volontairement simple, se focalise sur les usages les plus connus et à destination des utilisateurs de ces technologies.

## Blockchains, crypto, NFTs

### Chiffrement

Les mathématiques du chiffre (cryptographie en anglais) sont la fondation technologique dès qu'on évoque les crypto, blockchains, token, NFT etc...

C'est un domaine vaste, largement documenté, les algorithmes ont plusieurs dizaines d'années [^1]. Nous nous attachons ici aux principes de signature, de chiffrement et de condensats.

Chacun doit manipuler des paires de clefs asymétriques. Une clef est un ensemble de données unique. Les clefs ont une partie privée et une publique.

Les utilisateurs de crypto monnaies, NFT etc.. ont besoin d'un Wallet pour garder leurs biens. Ils sont donc responsable de garder leurs clefs privées dans un système utilisant lui-même le chiffrement pour rendre difficile de déchiffré la clef privée.

Cette clef privée sert à signer les transactions qui sont enregistrés sur les blockchains (registres) et c'est comme ca que l'on peut vérifier la possession d'un bien en le reliant à la clef publique. On perd cette clef on perd tout, il n'y a pas de tiers qui peut remédier à la perte. L'ensemble des biens, transactions etc.. utilisent les mêmes principes de chiffrement.

En détail Jeanne peut signer avec sa clef privée n'importe quelle donnée/fichier.
Le receveur de la transaction pourra vérifier avec la partie publique que la donnée signée n'a pas été modifiée et vient bien de Jeanne la propriétaire de la clef privé.
La donnée peut être publique ici.

On peut aussi chiffrer selon le même principe, c'est à dire rendre illisible pour un tier la donnée transmise.

On utilise aussi du chiffrement symétrique (la meme clef pour chiffrer/déchiffrer) car  
le chiffrement asymétrique est très gourmand en ressources.

Le hachage est une autre application du chiffrement.

La fonction de hachage prend une donnée digitale et crée un condensat unique cela permet de s'assurer facilement qu'une donnée n'a pas été modifiée lors d'un transfert. Le receveur peut recalculer le condensat et le comparer à celui de l'émetteur. Les condensats on des tailles fixes.

[^1]: Voir [Courbe d'Edwards tordue](https://fr.wikipedia.org/wiki/Courbe_d%27Edwards_tordue) remonte à 2008.

## Les blockchains ou LES TECHNOLOGIES DE REGISTRES DISTRIBUÉS (DLT)

Vous connaissez déjà les registres (ledger) ce sont les livres de comptes dans lesquels ont n'efface jamais rien. [Comptabilité à double entrée](https://fr.wikipedia.org/wiki/Comptabilit%C3%A9_en_partie_double) depuis 1494 et leur intérêt principal est de ne jamais effacer ou modifier les entrés précédentes.
Une blockchain est un ensemble de blocks constitués d'un groupe de transactions  chaque transaction étant signée par son propriétaire.
A chaque ajout de block le système calcul un hash (digest) de l'ensemble des
 blocks précédent plus le nouveau block.

Toute modification du registre passé invaliderait les condensats et sera rejeté, c'est ce qui rend le système immutable.

### Infrastructure

Un registre distribué (DLT) est hébergé sur un ensemble de nœuds (serveurs informatiques) qui ont tous une copie complete du registre, pour pouvoir calculer les condensats.
Les nœuds ont un protocole de synchronisation de l'état du registre et de l'accord pour l'ajout de blocks.

On peut donc définir des "objets digitaux" uniques, vérifiables enregistrés sur le registre immutable et leurs propriétaire. A chaque étape cela impliquera une transaction , une signature avec la clef privée et un enregistrement sur le registre pour la rendre vérifiable.

### Identité et registre privé

Certains consortiums d'entreprises ont développés des registres privés dont les noeuds et les utilisateurs pouvant écrire sont identifiés et autorisés. Au mieux le public peut vérifier l’existence d'un bien sur cette chaîne. Par exemple le certificat anti pollution d'un véhicule, la composition d'un produit etc..

Le nombre de nœuds, la gestion des permissions et le protocole de synchronisation sont souvent opaques et on  dépend de la confiance dans le consortium. Ces derniers ne sont pas toujours à la pointe de digital....

### Crypto monnaie.

On peut définir n'importe quel objet sur un registre et donc pourquoi pas une monnaie. C'est l'idée de bitcoin, expliquée dans le [whitepaper](https://bitcoin.org/bitcoin.pdf) initial. 
Une monnaie digitale permet de faire des échanges de valeurs sans repasser par le physique ou par des tiers (banques). Les monnaies sous appelées Token (pièces) et repose sur des DLT sans permissions souvent appelées blockchains.

Cette monnaie digitale permet d'avoir un protocole de synchronisation des noeuds d'un DLT qui récompense les nœuds pour leur travail. Il n'y a pas de permission pour ajouter un noeud au système ou pour utiliser le système. On est uniquement identifié par sa paire de clef, mais toutes les transactions sont publiques. On peut se créer une paire de clefs à tout moment.

### Sécurité: 51 %

L'intégrité du registre dépend du protocole de synchronization et de l'accord et vote entre les nœuds. Donc si nous controller plus de 51% des nœuds vous êtes propriétaire du registre et pouvez ajouter les transactions voir modifier. Il ne faut pas que ca arrive et donc on a besoin de beaucoup de noeuds indépendants et d'un nombre suffisant de détenteurs de monnaie. C'est à ce prix que l'on peut créer un système vraiment décentralisé.

On veut donc un système où le coût de possession des 51% est moins intéressant que les
récompenses du réseau pour les nœuds vertueux.

Les protocoles de synchronization sont auditable (c'est du code informatique) ce sont les "proof of work", "proof of stake" etc.. souvent liés au news sur la consommation électrique des "proof of work" qui sont des puzzles mathématiques complexes, mais qui sont en passe d'être remplacer par le "proof of stake", preuve d'enjeu beaucoup moins énergivore. C'est le cas Ethereum 2 qui est en phase de déploiement.
Anecdote le système bancaire consomme 2 fois plus que le bitcoin.

Les monnaies essayent d'être fongibles et divisibles, c'est à dire qu'un ether est identique à n'importe quel autre ether ou 2 demi ether. Essayent car toutes les transactions sont immutables dans le registre et donc on peut tracer à quoi à servi chaque token. Zcash par exemple essaye de palier à ca, les mouvement Zero Knowledge (ZK) cherche aussi à préserver la vie privée dans les blockchains.

Les NFT sont des jetons uniques, indivisibles et identifiables. (non fongibles). On les utilisera comme titre de propriété, d'accord etc.. Le milieu de l'art s'en ai emparé pour monétiser les creations digitales mais les principes s'applique à beaucoup de choses.

Les smart-contracts sont des programs informatiques qui tournent sur les blockchains directement (notamment Ethereum, Solana). Ils sont donc eux même immutables par rapport au passé. En gros on peut les modifier à date pour les transactions futures, mais le passé dans le registre ne change pas. Ce sont de programmes informatiques, donc vulnérables aux bugs, attaques, visible de tous. Leur sécurité peut passer par de la preuve d'execution formelle, mais c'est coûteux dès que le program est complexe.
Retenez qu'en terme de smart-contract la simplicité prime, donc le moins smart gagne.

## Arnaques, Ponzi etc

Pour ceux qui se souviennent du web initial on retrouve beaucoup des mêmes intentions de distribution, décentralisation etc...
Le web2 à vu l’avènement des GAFAs qui à coût de services gratuits sont devenues les détentrices de nos identités numériques sans remettre en cause la neutralité du web1.

C'est pourquoi l'identité liée à la possession d'une simple clef privée (32 octets) est si importante à maîtriser dans le web3.

Le web initial était aussi un far west avec beaucoup de profiteurs des crédules, ca ne l'a pas empêché de devenir prépondérant.

Journalistes en manque d'inspiration: vous pouvez reprendre les articles de 2000 et remplacer Internet par blockchain et crypto monnaies.
