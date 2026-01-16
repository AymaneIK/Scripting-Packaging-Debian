Contexte
Votre établissement déploie un nouveau parc de machines sous Linux (Ubuntu / Linux Mint)
destiné aux travaux pratiques.
Le service technique souhaite disposer d’un outil simple, automatisé et installable pour :
▪ Initialiser une machine,
▪ Gérer les utilisateurs et les droits,
▪ Collecter des informations système,
▪ Rechercher des fichiers et des traces,
▪ Surveiller les processus,
▪ Et produire des rapports exploitables.
Vous êtes chargés de concevoir, développer et livrer cet outil sous forme d’un package
Debian (.deb).
Objectif du projet
Développer un outil nommé SysAuditKit, installable via dpkg / apt, qui fournit un ensemble
de scripts shell permettant l’audit et la gestion basique d’un système Linux.
Technologies et notions autorisées
Vous devez obligatoirement utiliser les notions vues en cours :
▪ Commandes Linux de base : ls, cat, mkdir, stat, cp, mv
▪ Gestion des utilisateurs et privilèges : useradd, groupadd, chmod, chown, sudo
▪ Recherche: grep, find
▪ Scripting shell:
▪ variables
▪ conditions (if, case)
▪ boucles (for, while)
▪ Entrées / sorties :
▪ redirections >, >>
▪ here-document <<
▪ Gestion des processus:
• ps, pgrep, top, kill, nice, renice
▪ Packaging Debian:
• dpkg, apt-get
• structure .deb

Fonctionnalités attendues
▪ Commande principale
▪ Après installation, l’outil doit être exécutable depuis le terminal, par exemple :
▪ sysauditkit <commande>
Vous êtes libres de définir vos commandes, par exemple :
▪ init
▪ report
▪ search
▪ monitor
▪ help
Module INIT : Initialisation système
Ce module doit :
▪ Demander le Nom et le Prénom de l’étudiant,
▪ Générer un identifiant unique (ex : votre prenom.nom),
▪ Créer un utilisateur Linux basé sur cet identifiant,
▪ Créer un dossier de travail dédié,
▪ Attribuer des permissions cohérentes et justifiées,
▪ Tracer toutes les actions dans un fichier log.
Important :
Le Nom et le Prénom doivent être stockés dans un fichier de configuration.
Module REPORT : Rapport système
Générer un rapport texte contenant :
▪ Informations système (OS, kernel),
▪ Usage disque,
▪ Utilisateurs connectés,
▪ Processus actifs (top CPU/MEM),
▪ Date et heure.
▪ Le rapport doit :
• Utiliser > et >>,
• Inclure un entête généré avec un here-document <<,
• Être nommé dynamiquement avec votre identifiant (nom/prénom).
Module SEARCH : Recherche ciblée
Ce module doit être intégré à l’outil SysAuditKit.
▪ Le script doit être exécutable depuis la ligne de commande.
▪ Toutes les recherches doivent être non destructives (lecture seule).
▪ Les résultats doivent être enregistrés dans un fichier texte.
▪ Le script doit fonctionner avec des paramètres dynamiques (variables).

Tâche 1 : Recherche de fichiers (obligatoire)
Écrire un traitement permettant de rechercher des fichiers dans un répertoire donné selon au
moins deux critères parmi les suivants :
▪ type de fichier (fichier régulier)
▪ extension de fichier
▪ taille
▪ date de dernière modification
▪ Commande obligatoire : find
Exigences :
▪ Le chemin de recherche doit être stocké dans une variable,
▪ Les résultats doivent être affichés à l’écran,
▪ Les résultats doivent être redirigés vers un fichier de sortie.
Tâche 2 : Analyse du contenu des fichiers (obligatoire)
Mettre en place un traitement permettant d’analyser le contenu de fichiers texte afin de
détecter des mots-clés pertinents (ex : erreurs, échecs, alertes).
Commande obligatoire : grep
Exigences :
▪ Recherche récursive,
▪ Insensible à la casse,
▪ Affichage du numéro de ligne,
▪ Ajout des résultats dans le même fichier de sortie que la tâche 1.
Tâche 3: Combinaison find + grep (obligatoire)
▪ Concevoir une recherche combinée permettant :
• de sélectionner des fichiers via find,
• puis d’analyser leur contenu via grep.

Exigence clé :
Les deux commandes doivent être utilisées ensemble dans un même traitement.
Important :
Le choix de la méthode de combinaison est libre, mais devra être expliqué et justifié dans le
rapport du projet.
Tâche 4: Paramétrage dynamique (obligatoire)
Le script doit utiliser des variables shell pour définir :
▪ le répertoire de recherche,
▪ le ou les mots-clés à analyser,
▪ le fichier de sortie.
▪ Aucune valeur ne doit être codée en dur.

Tâche 5: Gestion des erreurs (obligatoire)
Le script doit gérer au minimum les situations suivantes :
▪ répertoire de recherche inexistant,
▪ droits insuffisants,
▪ aucun fichier trouvé,
▪ aucun résultat correspondant aux mots-clés.
▪ Dans chaque cas, un message clair doit être affiché et journalisé.
Module MONITOR – Processus
Permettre :
▪ L’affichage des processus d’un utilisateur donné,
▪ L’identification de processus gourmands,
▪ Une action contrôlée (kill, renice) avec confirmation.
Packaging Debian (obligatoire)
Votre projet doit produire un fichier :
▪ sysauditkit_<version>_all.deb
▪ Structure minimale attendue :

Vous devez démontrer :
▪ Installation : dpkg -i
▪ Vérification : dpkg -l
▪ Suppression : dpkg -r
Livrables
▪ Le fichier .deb
▪ Le dossier projet complet
▪ Un rapport PDF/Word (1–2 pages) expliquant :
▪ Votre architecture,
▪ Les permissions,
▪ Les commandes utilisées
▪ Captures d’écran ou sorties terminal montrant :
• Installation,
• Exécution des modules,
• Désinstallation
