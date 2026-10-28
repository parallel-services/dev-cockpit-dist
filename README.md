# Dev Cockpit — binaires

Les versions publiées de **Dev Cockpit**, et de quoi savoir à quoi l'app ressemble. Le code source
et son historique vivent dans un dépôt privé ; ce dépôt-ci ne porte que les artefacts signés, leur
`latest.json`, la config distante et les captures ci-dessous.

C'est ce dépôt que l'app interroge pour ses mises à jour. Elle n'a donc besoin d'**aucun accès**
au dépôt de code.

## Les modules

Chacun s'allume ou s'éteint dans **Réglages › Modules** : ce qui est éteint quitte la barre, les
raccourcis et les notifications. La barre de gauche les range en quatre groupes — Flux, Qualité,
Pilotage, Automatisation. Les captures viennent du jeu de démonstration, pas d'un vrai compte.

## Flux

### Aujourd'hui
Ce qui t'attend dans les autres vues actives, en un coup d'œil.

![Aujourd'hui](docs/screenshots/aujourdhui.png)

### Reviews
Tout ce qui attend ta review, avec le compteur de la barre de menus. j et k circulent, Entrée ouvre.

![Reviews](docs/screenshots/reviews.png)

### Todo
Les cartes à prendre dans le sprint courant de tes boards.

![Todo](docs/screenshots/todo.png)

### Triage
Les bugs remontés dans Notion, triés et transformés en cartes YouTrack.

![Triage](docs/screenshots/triage.png)

### Mes remontées
Les bugs que tu as remontés dans Notion, et ce qu'ils deviennent.

![Mes remontées](docs/screenshots/mes-remontees.png)

### Mon travail
Tes cartes en cours avec leur parcours, puis tes PR sans carte : branche, CI, reviews et conflits.

![Mon travail](docs/screenshots/mon-travail.png)

### Agents
Tes sessions Claude Code ; celles qui attendent une réponse passent devant.

![Agents](docs/screenshots/agents.png)

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

## Composer son cockpit

Les modules s'activent un par un, avec leurs dépendances et des profils tout faits.

![Modules](docs/screenshots/modules.png)

## Visite guidée

Au premier lancement, un pas à pas éclaire les zones de l'app une à une. Il se relance depuis la
palette (⌘K) ou l'aide (?).

![Visite guidée](docs/screenshots/visite-guidee.png)

## Installer

```bash
gh api repos/jeremie-vasco/dev-cockpit-dist/contents/install.sh --jq .content | base64 --decode | bash
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
