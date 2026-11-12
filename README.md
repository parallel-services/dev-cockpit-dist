# Dev Cockpit — binaires

Les versions publiées de **Dev Cockpit**, et de quoi savoir à quoi l'app ressemble. Le code source
et son historique vivent dans un dépôt privé ; ce dépôt-ci ne porte que les artefacts signés, leur
`latest.json`, la config distante et les captures ci-dessous.

C'est ce dépôt que l'app interroge pour ses mises à jour. Elle n'a donc besoin d'**aucun accès**
au dépôt de code.

## Les modules

Chacun s'allume ou s'éteint dans **Réglages › Modules** : ce qui est éteint quitte la barre, les
raccourcis et les notifications. La barre de gauche les range en quatre groupes — Flux, Qualité,
Pilotage, Automatisation — et trois vues vivent hors de la barre, ouvertes par la palette. Les
captures viennent du jeu de démonstration, pas d'un vrai compte.

## Flux

### Aujourd'hui
Ce qui t'attend dans les autres vues actives, en un coup d'œil : agents, sorties à trancher,
ménage, mentions, reviews, PR et cartes en cours. Chaque bloc se masque ou se déplace, et un bloc
masqué ne compte nulle part.

![Aujourd'hui](docs/screenshots/aujourdhui.png)

### Reviews
Tout ce qui attend ta review, avec le compteur de la barre de menus. L'en-tête dit d'abord combien,
puis depuis quand. Chaque ligne se lit en deux temps : le titre, puis son contexte — dépôt, auteur,
âge, raison, badges de risque (grosse PR, migration, fichiers sensibles). À droite, la CI et la
taille ; au survol ou à la sélection, les actions prennent leur place sans rien déplacer. j et k
circulent, Entrée ouvre, Espace ouvre le panneau Sujet.

Le champ de recherche comprend des jetons — `repo:app`, `ci:rouge`, `auteur:…`, `âge>2j` — avec
complétion ; un filtre actif s'affiche en puce supprimable. Ce qui bouge sans qu'on te l'ait demandé
devient un signal, rangé derrière son bouton.

![Reviews](docs/screenshots/reviews.png)

### Todo
Les cartes à prendre dans le sprint courant de tes boards, avec les workflows qui démarrent le
travail : Conductor, terminal, ou un départ en hotfix depuis une version de prod.

![Todo](docs/screenshots/todo.png)

### Triage
Les bugs remontés dans Notion et les erreurs Sentry, triés et transformés en cartes YouTrack.

![Triage](docs/screenshots/triage.png)

### Mes remontées
Les bugs que tu as remontés dans Notion, et ce qu'ils deviennent : ce qui attend ta réponse d'abord.

![Mes remontées](docs/screenshots/mes-remontees.png)

### Mon travail
Tes cartes en cours avec leur parcours, puis tes PR sans carte : branche, CI, reviews et conflits.

![Mon travail](docs/screenshots/mon-travail.png)

### Workspaces
Un worktree git par sujet, où Claude Code travaille : créer, suivre, relire le diff, commiter et
pousser. ⇧Entrée ouvre une session, ⌘⇧N crée un workspace.

![Workspaces](docs/screenshots/workspaces.png)

### Agents
Tes sessions Claude Code ; celles qui attendent une réponse passent devant.

![Agents](docs/screenshots/agents.png)

## Le panneau Sujet

Dans Reviews, Aujourd'hui, Mon travail, Todo et Workspaces, **Espace** ouvre un panneau à droite de
la liste. Il la pousse au lieu de la recouvrir, suit la sélection, et dit où en est le sujet de la
ligne : Carte → Branche → PR → CI → Review → Merge → Recette → Prod, l'étape en cours mise en
avant, une étape bloquée en rouge. Dessous, la progression des critères d'acceptation, les risques
détaillés, la CI et la taille.

Il **ne charge rien** : il ne montre que ce que la vue a déjà en mémoire. Une étape dont la donnée
n'est pas là est grisée d'un tiret plutôt que devinée. Tant qu'il est ouvert, un clic sur une ligne
la sélectionne au lieu de l'ouvrir ; Entrée et le bouton « Ouvrir » ouvrent toujours.

![Panneau Sujet](docs/screenshots/panneau-sujet.png)

## Deux densités

**Confortable** est la composition décrite ici : des lignes à deux temps, de l'air, un en-tête qui
porte le compteur. **Compacte** garde une ligne d'information par élément, pour qui en parcourt
beaucoup. Le bouton est dans la barre d'outils de Reviews et dans Réglages › Apparence ; changer
d'ambiance ne touche pas à la densité.

## Qualité

### CI & Sécurité
La santé de ce qui part en production : branche principale rouge, jobs instables et durées des
workflows d'un côté, alertes Dependabot, code scanning et secret scanning de l'autre, avec un
correctif guidé dans Conductor ou le terminal.

![CI & Sécurité](docs/screenshots/ci-securite.png)

### Déploiements
Les PR mergées, environnement par environnement : en recette, en prod ou pas encore déployées.

![Déploiements](docs/screenshots/deploiements.png)

### Migrations
Les PR ouvertes qui touchent une migration : qui doit la relire, depuis combien de jours ouvrés,
et le SQL qu'elle joue.

![Migrations](docs/screenshots/migrations.png)

### Release
Préparer une version : le tag suivant, le commit cible, les traductions en attente, les migrations
à relire et le changelog que les cartes ont écrit. **Aucune écriture** : la vue prépare, elle ne
crée pas la release et ne publie rien.

![Release](docs/screenshots/release.png)

## Pilotage

Un seul écran, trois onglets, à partir d'une seule copie locale de l'historique.

### Sprint
Le burndown du sprint et sa rétro. Les restes s'arrêtent au jour du jour : la safe zone continue
jusqu'au bout, les courbes de réalisé ne racontent que ce qui est connu.

![Sprint](docs/screenshots/pilotage-sprint.png)

### Équipe
Les KPI de fabrication : débit, durées et fluidité par sprint, par équipe et par période.

![Équipe](docs/screenshots/pilotage-equipe.png)

### Moi
Tes propres chiffres face à ceux de l'équipe, calculés sur ta machine.

![Moi](docs/screenshots/pilotage-moi.png)

## Automatisation

### À trancher
Les sorties des agents à trancher : accepter, rejeter ou reporter, brouillon de carte à l'appui.

![À trancher](docs/screenshots/a-trancher.png)

### Historique
Les enchaînements, actions, runs Factory et appels MCP passés, étape par étape : ce qui a été
écrit, ce qui a échoué, et où reprendre.

![Historique](docs/screenshots/historique.png)

## Hors de la barre

Trois vues que la palette (⌘K) ouvre, et qui se signalent d'elles-mêmes quand elles ont quelque
chose à dire.

### Ménage
Les branches fusionnées, worktrees, images et volumes à ranger, avec la place qu'ils reprennent.
Rien n'est supprimé sans aperçu ni confirmation. Il se rappelle à toi dans Aujourd'hui et par sa
notification hebdomadaire.

![Ménage](docs/screenshots/menage.png)

### Notes
La capture rapide : une note en deux secondes avec ⌘⇧Espace depuis n'importe où, triée ici et
convertie en carte quand elle le mérite.

![Notes](docs/screenshots/notes.png)

### Absence
Ce qu'il faut régler avant de partir : reviews à rendre, cartes en cours, passation à écrire. Les
notifications se taisent et les reviews ne te sont plus adressées jusqu'au retour.

![Absence](docs/screenshots/absence.png)

## Ce qui alimente le cockpit

### Les comptes
GitHub et YouTrack se connectent ici ; Notion et Sentry ont leur propre onglet. Les jetons vivent
dans le trousseau du système, jamais dans un fichier ; tout le réseau part du back Rust, et rien ne
sort sans passer par le masquage.

![Comptes](docs/screenshots/comptes.png)

### Les notifications
Ce qui te notifie, et quand : la section « Quand me déranger » met l'app en sourdine pendant tes
réunions et garde les reviews pour les créneaux que tu as choisis.

![Notifications](docs/screenshots/notifications.png)

## Composer son cockpit

Les modules s'activent un par un, avec leurs dépendances et des profils tout faits.

![Modules](docs/screenshots/modules.png)

## Choisir son ambiance

Une **ambiance** règle la peau de l'app : la matière des surfaces, la profondeur, la typographie et
le mouvement. Elle ne touche ni aux vues, ni à ce qu'elles montrent, ni à la densité des listes —
celle-ci reste là où tu l'as mise. Trois sont livrées, et le réglage fin des couleurs reste
dessous, en partant de celle que tu as choisie.

![Ambiances](docs/screenshots/ambiances.png)

### Précision
Le thème d'origine, et le défaut : monochrome froid, un seul accent bleu, surfaces opaques.

![Précision](docs/screenshots/ambiance-precision.png)

### Cockpit
Poste de pilotage sombre : accent teal, titres de section en mono, une lueur d'accent sur les
panneaux, et un halo sur la ligne sélectionnée, les pastilles de CI, le bouton principal et le bord
des dialogues.

![Cockpit](docs/screenshots/ambiance-cockpit.png)

### Verre
Panneaux translucides sur un fond en dégradés qui se voit autour d'eux et à travers eux, lignes de
liste en cartes espacées, panneaux décollés des bords, dialogues voilés de la couleur du fond. Sur
une webview qui ne sait pas flouter, les surfaces redeviennent opaques toutes seules.

![Verre](docs/screenshots/ambiance-verre.png)

Chaque ambiance a sa variante claire et sa variante sombre ; le mode (Système / Clair / Sombre)
décide laquelle s'affiche. Un thème est **refusé s'il ne se lit pas** : chaque paire texte/fond doit
tenir le contraste AA de 4,5:1 dans les deux variantes — pour les surfaces translucides, contre le
pire fond possible derrière elles — et le rouge et l'orange restent réservés à l'urgence réelle.
`prefers-reduced-motion` coupe toute animation, quelle que soit l'ambiance choisie.

Un thème s'exporte, s'importe et se partage par la configuration d'équipe. Une ambiance déjà
choisie suit ses évolutions : c'est sa version courante qui s'applique à chaque lancement.

## Visite guidée

Au premier lancement, un pas à pas éclaire les zones de l'app une à une : la barre des vues,
l'en-tête, le filtre d'équipe, la palette, les raccourcis et Réglages › Modules. Sa dernière étape
propose un **tour des modules**, qui passe sur chaque vue — les trois hors de la barre comprises —
puis sur chaque source. Les étapes d'un module éteint sont sautées : la visite ne parle jamais
d'une fonction que tu n'as pas. La palette (⌘K, « Visite guidée ») et Réglages › À propos
relancent le pas à pas.

![Visite guidée](docs/screenshots/visite-guidee.png)

## Installer

```bash
gh api repos/parallel-services/dev-cockpit-dist/contents/install.sh --jq .content | base64 --decode | bash
```

`--beta` pour le canal beta, `--version vX.Y.Z` pour une version précise, `--deb` sous Linux pour
le paquet plutôt que l'AppImage. Les versions suivantes arrivent dans l'app, toutes seules.

## Ce que porte une release

| Fichier | Pour |
|---|---|
| `Dev.Cockpit_<version>_universal.app.tar.gz` + `.sig` | macOS, c'est ce que l'updater installe |
| `Dev.Cockpit_<version>_universal.dmg` | macOS, première installation à la main |
| `Dev.Cockpit_<version>_amd64.AppImage` + `.sig` | Linux, mise à jour automatique |
| `Dev.Cockpit_<version>_amd64.deb` + `.sig` | Linux, paquet (root, mises à jour manuelles) |
| `latest.json` | le manifeste que l'app lit : version, notes, signature par plateforme |

Chaque artefact est signé (minisign). L'app vérifie la signature avec sa clé publique intégrée et
refuse toute mise à jour dont la signature ne correspond pas.

La release fixe `remote-config` porte la configuration distante signée, que les apps relisent
toutes les heures.
