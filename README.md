# forge-master-prompt
html web page help you to structurat your prompt for coding, analysis and fix bugs

# Forge Master Prompt (FMP)

## Sommaire
- [À quoi sert cette application ?](#à-quoi-sert-cette-application-)
- [Ce que FMP n'est PAS](#ce-que-fmp-nest-pas)
- [Démarrage rapide](#démarrage-rapide)
- [Les 3 onglets de l'application](#les-3-onglets-de-lapplication)
- [Les deux modes : Développeur et Débutant](#les-deux-modes--développeur-et-débutant)
- [Le mode guidé 🧭](#le-mode-guidé-)
- [Les presets](#les-presets)
- [Détail de chaque section (mode Développeur)](#détail-de-chaque-section-mode-développeur)
- [Le panneau de résultat](#le-panneau-de-résultat)
- [Les vérifications automatiques](#les-vérifications-automatiques)
- [Gestion de plusieurs projets](#gestion-de-plusieurs-projets)
- [Historique](#historique)
- [Export / Import](#export--import)
- [Onglet "Analyser une version"](#onglet-analyser-une-version)
- [Onglet "Corriger des bugs"](#onglet-corriger-des-bugs)
- [Où sont stockées mes données ?](#où-sont-stockées-mes-données-)
- [Conseils pour profiter au maximum de l'outil](#conseils-pour-profiter-au-maximum-de-loutil)

---

## À quoi sert cette application ?

Forge Master Prompt est un **éditeur qui aide à rédiger un prompt complet et structuré**, destiné à être donné à une intelligence artificielle externe (ChatGPT, Claude, Gemini, etc.) pour qu'elle génère, analyse ou corrige un projet de logiciel.

Plutôt que de décrire son projet en quelques phrases improvisées à une IA — au risque d'oublier des informations essentielles (la plateforme cible, la base de données, le niveau de détail attendu, les contraintes techniques...) — FMP propose un formulaire structuré qui couvre systématiquement tous ces aspects, puis compile automatiquement tout cela en un **prompt maître** clair, complet et prêt à copier-coller.

L'outil va plus loin qu'une simple génération initiale : il propose aussi deux outils complémentaires pour **faire évoluer un projet dans la durée** (analyser une nouvelle version, corriger des bugs signalés), en gardant toujours le même niveau d'exigence dans la formulation des prompts.

## Ce que FMP n'est PAS

C'est un point essentiel à comprendre avant de commencer : **FMP n'est pas une intelligence artificielle**. L'application ne comprend pas votre projet, n'exécute aucun code, ne se connecte à aucun service en ligne et n'analyse rien par elle-même. C'est un formulaire intelligent qui transforme vos choix et votre texte en un prompt bien structuré — tout le travail de compréhension, de génération de code ou d'analyse est fait ensuite par l'IA externe à qui vous donnerez ce prompt.

Concrètement, cela veut dire :
- FMP fonctionne **entièrement hors ligne**, dans votre navigateur, sans aucune connexion internet requise pour l'utiliser.
- Les "vérifications automatiques" et "recommandations" que l'outil affiche sont basées sur des **règles fixes** (mots-clés, cases cochées), pas sur une compréhension réelle de votre texte.
- Vos données (projets sauvegardés, historique) restent **uniquement sur votre appareil**, dans votre navigateur.

## Démarrage rapide

1. Ouvrez le fichier HTML dans votre navigateur (aucune installation nécessaire).
2. Choisissez votre mode : **Développeur** (par défaut, formulaire complet) ou **Débutant** (questionnaire guidé) via l'interrupteur en haut à droite.
3. Remplissez les sections qui vous concernent (voir le détail plus bas) — au minimum le **type de projet** et une **description**.
4. Cliquez sur **Compiler** pour générer le prompt maître.
5. Copiez le résultat (bouton "Copier" ou "Copier et ouvrir l'IA") et collez-le dans l'IA de votre choix.

## Les 3 onglets de l'application

FMP est organisé en trois onglets, pensés pour accompagner un projet sur la durée, pas seulement au moment de sa création :

| Onglet | À quoi il sert |
|---|---|
| **🚀 Générer** | L'onglet principal : configurez votre projet et générez le prompt maître initial. |
| **🧭 Analyser une version** | Génère un prompt à donner à une IA pour qu'elle analyse une nouvelle version de votre projet (vérifier que des corrections demandées ont bien été appliquées, détecter des bugs). |
| **🩹 Corriger des bugs** | Génère un prompt à donner à une IA pour qu'elle corrige des bugs précis, à partir d'un rapport d'analyse, avec des garde-fous stricts pour ne rien casser. |

Ces trois onglets sont conçus pour s'enchaîner naturellement en cycle : **Générer** → donner le prompt à une IA externe → **Analyser** la version obtenue → coller le rapport dans **Corriger** → redonner le nouveau prompt à l'IA externe → et ainsi de suite à chaque itération de votre projet.

## Les deux modes : Développeur et Débutant

Un interrupteur en haut à droite de la page permet de basculer entre deux façons d'utiliser l'onglet "Générer" :

### Mode Développeur (par défaut)
Vous accédez à un formulaire complet en 9 sections (type, technologies, cible, base de données, déploiement, livraison, mode de génération, description, contraintes), avec **filtrage contextuel intelligent** : les choix incompatibles avec vos sélections précédentes sont automatiquement masqués (par exemple, si vous cochez "Application Web", certaines technologies mobiles disparaissent de la liste). Recommandé si vous savez déjà quelle stack technique vous voulez utiliser.

### Mode Débutant
Un questionnaire simplifié en une seule section : vous décrivez votre idée et vos objectifs en langage naturel, puis répondez à quelques questions simples (qui utilisera l'application, avez-vous besoin de stocker des données, sera-t-elle utilisée en ligne). FMP propose alors automatiquement une stack technique adaptée à vos réponses, sans que vous ayez à connaître les termes techniques. Recommandé si vous ne savez pas quelles technologies choisir.

**Dans les deux cas, le prompt généré est complet et immédiatement exploitable** — le mode Débutant ne produit pas un résultat "moins bon", il choisit juste les détails techniques à votre place.

## Le mode guidé 🧭

Un second interrupteur, situé sous le sélecteur de preset, active le **mode guidé** (activé par défaut). Il ne concerne que le mode Développeur.

Son objectif : réduire la charge visuelle du formulaire en n'affichant qu'une section à la fois. Concrètement :
- Seule la première section est ouverte au départ ; les suivantes sont repliées.
- Dès que vous faites un choix dans la section en cours, la suivante s'ouvre automatiquement et celle que vous venez de compléter se referme.
- Si vous utilisez un preset (voir plus bas), les sections concernées par ce preset s'enchaînent automatiquement, et le formulaire s'arrête sur la première section que le preset n'a pas remplie.

**Important : ce mode ne vous enferme jamais.** Vous pouvez à tout moment cliquer manuellement sur n'importe quelle section pour l'ouvrir — y compris une section plus loin dans le formulaire — sans que rien ne se bloque ou ne se réinitialise. C'est une aide visuelle, pas une contrainte. Si vous préférez avoir toutes les sections librement accessibles comme un formulaire classique, désactivez simplement cet interrupteur.

## Les presets

Le panneau "Préréglage" permet d'appliquer en un clic une configuration technique prête à l'emploi, plutôt que de cocher chaque case manuellement.

**Presets intégrés fournis** :
- API REST classique
- Application CRUD interne
- Jeu 2D (Canvas)
- Extension navigateur simple

**Comment ça marche** : sélectionnez un preset dans la liste (un aperçu de son contenu s'affiche automatiquement), puis cliquez sur "Appliquer". Si vous aviez déjà rempli des champs, une confirmation vous est demandée avant d'écraser vos choix — vous pouvez toujours annuler sans perte de données. Les sections concernées s'ouvrent automatiquement et les nouvelles cases cochées sont brièvement surlignées en vert pour que vous voyiez ce qui a changé.

**Presets personnalisés** : vous pouvez importer vos propres presets via un fichier `.json` (bouton "Importer des presets personnalisés"), et exporter les vôtres pour les partager avec quelqu'un d'autre. Ils apparaissent dans un groupe séparé de la liste déroulante. Si un fichier de preset contient des valeurs invalides ou obsolètes, elles sont ignorées silencieusement (l'outil vous indique combien de valeurs ont été ignorées) plutôt que de provoquer une erreur.

## Détail de chaque section (mode Développeur)

| # | Section | Rôle | Remarque |
|---|---|---|---|
| 1 | **Type de programme** *(requis)* | Nature du projet : application web, desktop, mobile, API/backend, jeu vidéo, extension navigateur, DevOps, etc. | Détermine le filtrage de toutes les sections suivantes. |
| — | **Spécialisation DevOps** *(optionnelle)* | N'apparaît que si "DevOps" est coché dans le type. Permet de préciser Docker, Kubernetes, CI/CD, etc. | Génère des règles techniques dédiées dans le prompt final. |
| 2 | **Langage / technologie** | Frameworks et langages à utiliser. | Liste filtrée selon le type choisi. |
| 3 | **Système cible** | Plateforme(s) visée(s) : Windows, macOS, Linux, Android, iOS, navigateur. | |
| 4 | **Base de données** *(optionnelle)* | PostgreSQL, MySQL, SQLite, MongoDB, Redis, etc. | Laissez vide si votre projet n'a pas besoin de stockage de données. |
| 5 | **Déploiement** *(optionnelle)* | Contexte de mise en production souhaité. | Laissez vide pour un usage purement local. |
| 6 | **Format de livraison** | Ce que l'IA doit produire : fichiers complets, README, instructions d'installation, tests, etc. | |
| 7 | **Mode de génération** | Deux réglages : l'ambition du projet (MVP, prototype, production...) et le niveau de détail souhaité dans la réponse de l'IA. | Ce sont deux menus déroulants avec une valeur par défaut déjà sélectionnée. |
| 8 | **Description** *(requis)* | Décrivez ici votre projet en langage libre : ce qu'il fait, ses fonctionnalités principales. | C'est le champ le plus important avec le type de programme. |
| 9 | **Contraintes** *(optionnelle)* | Toute exigence particulière : budget, licence, outils imposés, style de code, etc. | |

Un texte **"requis"** apparaît à côté des sections indispensables (Type et Description) pour vous rappeler qu'un prompt minimal a besoin d'au moins ces deux informations. Rien ne vous empêche cependant de compiler un prompt à tout moment, même incomplet.

## Le panneau de résultat

Situé à droite (ou en dessous sur mobile), il affiche le prompt maître une fois compilé, avec :
- **Compteur de mots/caractères**, avec une alerte si le prompt dépasse une taille raisonnable (au-delà, certaines IA pourraient tronquer ou avoir plus de mal à traiter l'ensemble).
- **Copier** : copie le texte dans le presse-papiers.
- **Télécharger .md** : enregistre le prompt dans un fichier Markdown sur votre disque.
- **Copier et ouvrir l'IA** : copie le texte et ouvre directement le site de l'IA sélectionnée dans le menu déroulant (ChatGPT, Claude, Gemini, Perplexity, Copilot, ou une URL personnalisée de votre choix).

## Les vérifications automatiques

Sous le panneau de résultat, un bloc "Vérifications automatiques" signale d'éventuelles incohérences ou points d'attention dans votre configuration (par exemple, un déploiement en ligne alors que vous avez indiqué vouloir un usage hors-ligne). Ce bloc scanne aussi votre texte libre (description, contraintes) à la recherche de mots-clés révélateurs (authentification, paiement, temps réel, multi-utilisateurs, etc.) pour vous suggérer de préciser ces points si nécessaire.

**Ce ne sont que des règles fixes**, pas une analyse intelligente de votre projet — le bloc le précise explicitement pour éviter toute confusion.

## Gestion de plusieurs projets

Le panneau "Projets" vous permet de nommer et sauvegarder votre configuration actuelle, pour la reprendre plus tard sans tout ressaisir :
- **Enregistrer** : sauvegarde la configuration actuelle sous un nom de votre choix.
- **Charger** : restaure un projet précédemment sauvegardé.
- **Dupliquer** : crée une copie d'un projet existant (utile pour partir d'une base commune et créer des variantes).
- **Supprimer** : efface un projet sauvegardé.

## Historique

Chaque fois que vous compilez un prompt, il est ajouté à un historique local (les 20 plus récents sont conservés). Vous pouvez le consulter et recharger un prompt précédent à tout moment via le menu déroulant dédié.

## Export / Import

Comme toutes vos données restent dans votre navigateur (voir plus bas), deux mécanismes permettent de les faire circuler :
- **Exporter/Importer mes projets (.json)** : sauvegarde l'ensemble de vos projets dans un fichier, à réimporter sur un autre appareil ou navigateur. Au moment de l'import, vous choisissez de fusionner avec vos projets existants ou de les remplacer entièrement.
- **Exporter/Importer des presets personnalisés (.json)** : permet de partager vos propres configurations types avec d'autres personnes, ou de récupérer les leurs.

## Onglet "Analyser une version"

Cet onglet génère un prompt à donner à une IA externe pour qu'elle **vérifie qu'une nouvelle version de votre projet respecte bien ce qui avait été demandé**, et qu'elle produise un rapport structuré et exploitable.

Renseignez :
- Le nom du projet, la version précédente et la version à analyser.
- Les modifications qui avaient été demandées (pré-rempli automatiquement si vous avez déjà utilisé l'onglet "Corriger des bugs" auparavant).
- D'éventuelles remarques ou points prioritaires à vérifier.

Une section optionnelle "Comparer deux fichiers" permet de charger la version précédente et la nouvelle version de votre projet : un résumé des différences est calculé directement dans votre navigateur (sans envoi en ligne) et peut être inséré automatiquement dans le champ des modifications demandées.

Le prompt généré impose à l'IA de confirmer quelle version elle analyse, de s'arrêter si aucun fichier n'est fourni, et de restituer son rapport dans **un tableau à 4 colonnes fixe** (priorité, titre, description du problème, comportement attendu) — ce format reste imposé pour toute la conversation qui suivra avec cette IA, même pour des questions de suivi informelles.

## Onglet "Corriger des bugs"

Cet onglet transforme un rapport de bugs (typiquement celui produit par l'onglet "Analyser une version") en un prompt de correction prêt à être donné à une IA, avec des garde-fous stricts pour qu'elle ne casse rien d'autre en corrigeant.

Collez le rapport reçu, indiquez la version concernée, et cochez les niveaux de priorité que vous souhaitez inclure (Haute/Moyenne/Basse/Optionnel) pour ne demander que les corrections qui vous intéressent. Le prompt généré rappelle explicitement à l'IA de ne modifier que ce qui est nécessaire et de ne jamais supprimer de fonctionnalité existante.

## Où sont stockées mes données ?

Toutes vos données (projets sauvegardés, historique, presets personnalisés) sont stockées **localement dans votre navigateur** (technologie `localStorage`), et ne sont jamais envoyées à un serveur — il n'y en a pas. Cela signifie :
- Vos données restent privées et ne quittent jamais votre appareil.
- Elles sont propres à un seul navigateur sur un seul appareil : si vous changez de navigateur ou d'ordinateur, utilisez l'export/import pour les récupérer.
- Vider le cache/les données de navigation de votre navigateur effacera ces informations — pensez à exporter régulièrement si vos projets vous sont précieux.

## Conseils pour profiter au maximum de l'outil

- **Remplissez toujours au minimum le type et la description** : ce sont les deux informations qui donnent le plus de contexte utile à l'IA qui recevra votre prompt.
- **Utilisez un preset comme point de départ** plutôt que de tout cocher à la main si votre projet correspond à un cas courant (API, CRUD, jeu, extension) — vous gagnerez du temps et pourrez ensuite ajuster les détails.
- **Laissez le mode guidé activé** si vous découvrez l'outil : il vous évite de vous sentir submergé par les 9 sections d'un coup. Désactivez-le une fois à l'aise si vous préférez naviguer librement.
- **Regardez le compteur de taille du prompt** avant de le copier : un prompt trop long peut perdre en efficacité selon l'IA utilisée.
- **Exportez vos projets régulièrement** si vous travaillez sur plusieurs appareils ou navigateurs, puisque rien n'est synchronisé automatiquement.
- **Utilisez le cycle complet des 3 onglets** pour un projet qui évolue dans le temps plutôt que de redécrire votre projet de zéro à chaque fois : Générer une fois, puis Analyser/Corriger à chaque itération suivante.
- **Ne prenez pas les "vérifications automatiques" pour une relecture experte** : elles sont utiles pour repérer des oublis évidents, mais elles ne remplacent pas votre propre jugement sur la cohérence de votre projet.
