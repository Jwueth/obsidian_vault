---
name: enrichir-ressource
description: >
  Enrichir les métadonnées d'une ressource clipée via Obsidian Web Clipper.
  Complète la description, les thématiques, les tags et la langue si manquants.
  Usage quand l'utilisateur demande d'enrichir une ressource ou en batch sur
  <INBOX>/ressources/.
---

# Enrichir une Ressource Clipée

Compléter automatiquement les métadonnées manquantes d'une ressource capturée via Obsidian Web Clipper.

## Chemins

| Dossier | Chemin |
|---------|--------|
| Entrée / Sortie | `<VAULT_PATH>/<INBOX>/ressources/` |

## Modes

### Mode batch (défaut)

`/enrichir-ressource` — traite tous les fichiers `.md` dans `<INBOX>/ressources/` où `Enriched` est absent ou `false`.

### Mode ciblé

`/enrichir-ressource "Nom du fichier.md"` — traite un seul fichier, même s'il est déjà enrichi.

## Processus

### 1) Lire le fichier

Lire le contenu Markdown et le frontmatter YAML de la ressource.

### 2) Compléter les champs manquants

Pour chaque champ vide ou absent, inférer la valeur depuis le contenu clipé :

| Champ | Règle |
|-------|-------|
| `Description` | Résumé de 2-3 phrases du contenu. Clair, factuel, informatif. |
| `Thematiques` | Inférer depuis le contenu. Valeurs existantes en DB : <THEMATIQUE_6>, <THEMATIQUE_2>, <THEMATIQUE_8>, <THEMATIQUE_1>, <THEMATIQUE_9>, <THEMATIQUE_3>, <THEMATIQUE_4>, <THEMATIQUE_10>, <THEMATIQUE_11>, <THEMATIQUE_12>, <THEMATIQUE_13>, etc. Proposer de nouvelles thématiques si aucune ne correspond. |
| `Tags` | Extraire 3-6 mots-clés spécifiques au contenu (pas les mêmes que Thematiques). |
| `Language` | Détecter la langue du contenu (fr, en, de, it). |
| `Type` | Vérifier la cohérence. Un podcast classé "article" → corriger en "podcast". Valeurs : article, video, podcast, book, tool, course, research-paper, tweet, wiki-guide, image, presentation, automation, recipe, citation, code-snippet, chatgpt-conversation. |
| `Level` | Inférer si évident (beginner, intermediate, advanced). Laisser vide si incertain. |
| `Collection` | Proposer si le contenu correspond clairement. Valeurs : <COLLECTION_6>, <COLLECTION_3>, <COLLECTION_2>, <COLLECTION_4>, <COLLECTION_1>, <COLLECTION_5>. Laisser vide si aucune ne correspond. |

### 3) Règles de non-écrasement

- Ne **jamais** modifier un champ déjà rempli par l'utilisateur
- Exception : incohérence flagrante (ex: `Type: article` pour un contenu qui est clairement un podcast)
- En cas d'incohérence, signaler le changement dans le terminal

### 4) Écrire les modifications

- Mettre à jour le frontmatter YAML du fichier `.md`
- Ajouter `Enriched: true` dans le frontmatter
- Ne pas modifier le contenu Markdown (body) du fichier

### 5) Rapport terminal

Pour chaque fichier traité, afficher :
```
✓ "Titre de la ressource"
  Description: ajoutée (2 phrases)
  Thematiques: <THEMATIQUE_6>, <THEMATIQUE_1>
  Tags: obsidian, pkm, workflow
  Language: fr (détecté)
```

## Règles

- Ne pas déplacer le fichier
- Ne pas modifier le contenu (body Markdown)
- Ne pas créer de nouveaux fichiers
- Ne pas supprimer de fichier
- Le fichier reste dans `<INBOX>/ressources/` après enrichissement
