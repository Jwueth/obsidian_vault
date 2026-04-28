# Système KM Personnel pour Obsidian

> Un système complet de gestion des connaissances (KM) pour Obsidian, intégrant Claude comme amplificateur cognitif.

## Vue d'ensemble

Ce dépôt propose un **système KM personnel** pour Obsidian qui combine :

- **Structure de vault** organisationnelle (inbox, notes, catégories, ressources)
- **Skills Claude** pour automatiser les workflows de gestion des connaissances
- **Templates** pour standardiser la création de notes (concepts, projets, standards)
- **Templates de mise en page** pour les tableaux et colonnes (multi-column-markdown)
- **Thème custom** pinkdream avec snippets CSS
- **Configuration** complète et prête à l'emploi

## Démarrage rapide

1. Clonez ce dépôt
2. Copiez le dossier `.claude/skills/` dans votre vault Obsidian
3. Copiez le fichier `CLAUDE.md` à la racine de votre vault
4. Personnalisez les placeholders dans `CLAUDE.md` avec vos chemins de vault

## Plugins conseillés

Les plugins communautaires suivants sont recommandés pour une expérience optimale :

| Plugin | Usage |
|--------|-------|
| [templater-obsidian](https://github.com/SilentVoid1/Templater) | Formules dans les templates |
| [remotely-save](https://github.com/remotely-save/remotely-save) | Synchronisation du vault |
| [obsidian-local-rest-api](https://github.com/coddingtonbear/obsidian-local-rest-api) | API REST locale |
| [obsidian-importer](https://github.com/obsidianmd/obsidian-importer) | Import de données |
| [better-export-pdf](https://github.com/l1xnan/obsidian-better-export-pdf) | Export PDF amélioré |
| [multi-column-markdown](https://github.com/ckRobinson/multi-column-markdown) | Colonnes dans le Markdown |
| [obsidian-pandoc](https://github.com/OliverBalfour/obsidian-pandoc) | Export Pandoc |
| [obsidian-excalidraw-plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin) | Diagrammes Excalidraw |
| [notebook-navigator](https://github.com/johansan/notebook-navigator) | Navigation dans les notebooks |
| [obsidian-advanced-uri](https://github.com/Vinzent03/obsidian-advanced-uri) | URI avancées |

### Apparence

#### Thème custom pinkdream

Des snippets CSS personnalisés sont disponibles dans `.obsidian/snippets/` :

- `pinkdream.css` - Thème principal rose/pink
- `headers_pink.css` - Styles pour les titres
- `properties_pink.css` - Styles pour les propriétés

Pour activer le thème, allez dans **Paramètres → Apparence → CSS Snippets** et activez les snippets souhaités.

## Skills

### Skills principaux

| Skill | Description |
|-------|-------------|
| `tri-box` | Traiter l'inbox et déplacer les notes vers le dossier notes |
| `creer-concept` | Transformer une note en fiche Concept |
| `creer-hub` | Créer une note hub (index de catégorie) |
| `scan-vault-infer` | Analyser le vault pour identifier nouveaux concepts/hubs |
| `enrichir-ressource` | Enrichir les métadonnées d'une ressource clipée |
| `capitaliser-ressource` | Capitaliser une ressource en notes conceptuelles |
| `inbox-to-knowledge` | Workflow complet : inbox → notes → concepts → hubs |

### Skills techniques (plugin [Kepano](https://github.com/kepano/obsidian-skills))

| Skill | Usage |
|-------|-------|
| `obsidian-markdown` | Syntaxe Obsidian, wikilinks, callouts, propriétés |
| `obsidian-bases` | Fichiers `.base` (vues, filtres, formules) |
| `json-canvas` | Fichiers `.canvas` (nœuds, connexions) |

## Structure du vault

```
<INBOX>/
  ressources/
<NOTES>/
<CATEGORIES>/
<RESOURCES>/
<TEMPLATES>/
Pièces jointes/
```

## Configuration

### Chemins

Éditez `CLAUDE.md` pour configurer les chemins de votre vault :

| Élément | Chemin |
|---------|--------|
| Vault Obsidian | `<VAULT_PATH>` |
| Skills | `<SKILLS_PATH>/` |
| Ce playbook | `<CONFIG_PATH>/obsidian/CLAUDE.md` |

### Templates

Les skills utilisent les templates du dossier `<TEMPLATES>/Notes/` :

- `<TEMPLATE_PROJET>`
- `<TEMPLATE_STANDARD>`
- `<TEMPLATE_CONCEPT>`

### Templates de mise en page

Des templates de mise en page sont disponibles dans `<TEMPLATES>/mise en page/` :

#### Tableaux

- `Tab builder.md` - Créateur de tableaux personnalisés
- `Tableaux pré-remplis.md` - Tableaux pré-remplis
- `Tableaux pré-remplis v2.md` - Tableaux pré-remplis v2
- `weekly.md` - Tableau hebdomadaire

#### Colonnes

- `2 colonnes.md` - Mise en page 2 colonnes
- `2 colonnes comparaisons.md` - Comparaison en 2 colonnes
- `3 colonnes.md` - Mise en page 3 colonnes
- `Colonnes builder.md` - Créateur de colonnes personnalisées

## Architecture Cognitive Partagée (OpenClaw)

Le dossier `OpenClaw/` illustre une **architecture de collaboration humain-IA** basée sur la séparation lecture/écriture. Cette architecture nécessite une mise en place manuelle (Docker, Nextcloud, rsync) et n'est pas incluse dans ce dépôt.

### Principe

- **L'IA** accède au savoir humain en **lecture seule**
- **L'humain** garde une **observabilité totale** sur le travail de l'IA via un dossier miroir

### Structure

```
OpenClaw/
├── agent_output/    ← Production de l'IA (écriture)
├── context/         ← Contexte pour l'IA
├── human/           ← Instructions humaines (lecture pour l'IA)
└── mirror/          ← Miroir du workspace IA (observabilité)
```

### Avantages

- **Souveraineté** : Aucune donnée ne réside sur des clouds propriétaires
- **Séparation des rôles** : L'IA lit le savoir, l'humain valide la production
- **Auditabilité** : Chaque décision de l'IA est visible dans le graphe Obsidian
- **Collaboration sans conflit** : Zones read-only vs write évitent les corruptions

## Philosophie

> Obsidian = mémoire
> Claude = amplificateur
> Les skills = la méthode

---

**Version :** v1.0.0
**Dernière mise à jour :** 2026-04-28
