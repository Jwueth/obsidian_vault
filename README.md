# Skills Obsidian pour Claude

> Une collection de skills pour utiliser Claude avec Obsidian pour la gestion des connaissances.

## Vue d'ensemble

Ce dépôt fournit un ensemble de skills qui permettent à Claude de travailler avec des vaults Obsidian. Les skills définissent comment Claude doit organiser, structurer et gérer vos notes.

## Démarrage rapide

1. Clonez ce dépôt
2. Copiez le dossier `.claude/skills/` dans votre vault Obsidian
3. Copiez le fichier `CLAUDE.md` à la racine de votre vault
4. Personnalisez les placeholders dans `CLAUDE.md` avec vos chemins de vault

## Prérequis

### Plugins requis

Les skills nécessitent les plugins communautaires suivants :

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
| [notebook-navigator](https://github.com/xRyul/notebook-navigator) | Navigation dans les notebooks |
| [obsidian-advanced-uri](https://github.com/Vinzent03/obsidian-advanced-uri) | URI avancées |

> **Note :** Les templates utilisent des formules [Templater](https://github.com/SilentVoid1/Templater). Assurez-vous que le plugin est installé et activé.

## Skills

### Skills principaux

| Skill | Description |
|-------|-------------|
| `tri-box` | Traiter l'inbox et déplacer les notes vers le dossier notes |
| `creer-concept` | Transformer une note en fiche concept |
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

## Utilisation

### Utilisation basique

Les skills sont automatiquement invoqués quand vous demandez à Claude d'effectuer des tâches spécifiques :

- **Traiter l'inbox** : "Traite mon inbox et organise les notes"
- **Créer un concept** : "Transforme cette note en concept"
- **Créer un hub** : "Crée un hub pour la catégorie 'Knowledge Management'"
- **Analyser le vault** : "Analyse mon vault et suggère de nouveaux concepts"

### Utilisation avancée

Vous pouvez aussi utiliser les skills directement :

```bash
# Traiter l'inbox
/tri-box

# Créer un concept
/creer-concept "Titre de la note"

# Créer un hub
/creer-hub "Nom de la catégorie"

# Analyser le vault
/scan-vault-infer
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

> **Note :** Les templates utilisent des formules [Templater](https://github.com/SilentVoid1/Templater) pour générer automatiquement des propriétés et du contenu.

## Philosophie

> Obsidian = mémoire
> Claude = amplificateur
> Les skills = la méthode

---

**Version :** v1.0.0  
**Dernière mise à jour :** 2026-04-28
