---
name: capitaliser-ressource
description: >
  Analyser une ressource enrichie pour créer ou enrichir des notes conceptuelles
  structurées. Propose des concepts à l'utilisateur, attend validation, puis exécute.
  Usage quand l'utilisateur demande de capitaliser une ressource, de créer des concepts
  depuis une ressource, ou de traiter le backlog de ressources enrichies.
---

# Capitaliser une Ressource en Connaissances

Analyser le contenu d'une ressource clipée pour identifier, créer ou enrichir des notes conceptuelles structurées. Processus supervisé : Claude propose, l'utilisateur valide, Claude exécute.

## Chemins

| Dossier | Chemin |
|---------|--------|
| Entrée | `<VAULT_PATH>/<INBOX>/ressources/` |
| Concepts | `<VAULT_PATH>/<NOTES>/` (les concepts sont dans <NOTES>/, pas dans <CATEGORIES>/) |
| Notes | `<VAULT_PATH>/<NOTES>/` |
| Sortie ressource | `<VAULT_PATH>/<RESOURCES>/` |
| Template concept | `<VAULT_PATH>/<TEMPLATES>/Notes/<TEMPLATE_CONCEPT>` |

## Distinction Concepts / Guides / Formations

Avant de créer un concept, vérifier que c'est bien un **concept** et pas un guide ou une formation :

| Type | Structure | Catégorie |
|------|-----------|-----------|
| **Concept** | Définition / Pourquoi / Comment / Exemples / Notes connexes | `<CONCEPTS>` + catégorie thématique |
| **Guide** | Protocole, méthode d'application, checklist | Catégorie thématique uniquement |
| **Formation** | Notes de cours, résumés pédagogiques | Catégorie thématique uniquement |
| **Note source** | Analyse détaillée, recherche | `<ANALYSES>` + catégorie thématique |

## Modes

### Mode batch (défaut)

`/capitaliser-ressource` — traite toutes les ressources dans `<INBOX>/ressources/` où `Enriched: true` et `Capitalised` est absent ou `false`. Traite une ressource à la fois avec validation entre chaque.

### Mode ciblé

`/capitaliser-ressource "Nom du fichier.md"` — traite un seul fichier, même sans `Enriched: true`.

## Processus

### Phase 1 — Analyse & proposition

Pour chaque ressource :

1. **Lire** le contenu + métadonnées de la ressource
2. **Scanner** les concepts existants dans `<NOTES>/` (chercher les notes avec `Catégories: Concepts`) et les notes dans `<NOTES>/`
3. **Proposer** un plan dans le terminal :

```
📄 "Titre de la ressource"

Concepts existants à enrichir :
  → [[Concept A]] — ajouter : description de ce qui serait ajouté
  → [[Concept B]] — ajouter : description de ce qui serait ajouté

Nouveaux concepts suggérés :
  → "Nouveau Concept" — définition courte du concept proposé

Aucune action ?
  → [skip] déplacer la ressource sans créer de notes

Valider ? (oui / ajuster / skip)
```

4. **Attendre** la réponse de l'utilisateur :
   - **oui** → exécuter le plan tel quel
   - **ajuster** → l'utilisateur modifie (retirer/ajouter des concepts), puis valider
   - **skip** → passer au rangement sans créer/modifier de notes
   - **quitter** → arrêter le batch, les ressources restantes ne sont pas traitées

### Phase 2 — Exécution

Pour chaque concept validé :

#### Nouveau concept

- Utiliser le skill `creer-concept` : créer la fiche concept en suivant le template `<TEMPLATE_CONCEPT>`
- Remplir les sections avec les apports de la ressource :
  - **Définition** : phrase claire extraite/synthétisée du contenu
  - **Pourquoi c'est important** : valeur, impact, cas d'usage
  - **Comment l'utiliser** : étapes pratiques si applicable
  - **Exemples** : exemples tirés de la ressource
  - **Ressources** : `[[Titre de la ressource]]` (wikilink)
- Renseigner le frontmatter : `Tags`, `Thématiques`, `Collection`, `Statut: draft`, `Catégories:` avec double appartenance (voir ci-dessous)

#### Double appartenance (Concepts + catégorie thématique)

Les concepts utilisent **deux catégories** :
1. `[[<CATEGORIES>/Concepts|Concepts]]` — pour l'index des concepts
2. Catégorie thématique — pour le regroupement par sujet

| Catégorie thématique | Usage |
|---------------------|-------|


**Exemple** :
```yaml
Catégories:
  - "[[<CATEGORIES>/Concepts|Concepts]]"
  - "[[<CATEGORIES>/Carrière|Carrière]]"
```

#### Concept existant — Append

Quand la note conceptuelle a peu de contenu ou que les apports sont distincts du contenu existant :

- Ajouter une section `## Apports de [[Titre de la ressource]]` en bas (avant `## Notes connexes` si présent)
- Rédiger les nouveaux insights de manière structurée
- Ajouter `[[Titre de la ressource]]` dans la section `## Ressources` si elle existe

#### Concept existant — Fusion

Quand la note est mature et qu'un simple append rendrait le contenu désorganisé :

- Réécrire les sections pertinentes en intégrant les nouveaux apports dans le texte existant
- Conserver le ton et la structure existants
- Ajouter `[[Titre de la ressource]]` dans `## Ressources`
- Signaler les modifications dans le terminal : `  ⟳ Fusion dans "Définition" et "Pourquoi c'est important"`

#### Liens bidirectionnels

- Dans le concept : ajouter `[[Titre de la ressource]]` dans `## Ressources`
- Dans la ressource : ajouter les wikilinks des concepts dans le body Markdown (section `## Concepts liés` ajoutée en bas si absente)

### Phase 3 — Rangement

1. Ajouter `Capitalised: true` dans le frontmatter de la ressource
2. Déplacer le fichier de `<INBOX>/ressources/` vers `<RESOURCES>/`
3. Afficher le résumé :

```
✓ "Titre de la ressource" → <RESOURCES>/
  Concepts enrichis : [[Concept A]], [[Concept B]]
  Concepts créés : [[Nouveau Concept]]
```

## Règles

- Toujours proposer avant d'exécuter — jamais de création/modification sans validation
- Utiliser le skill `creer-concept` pour les nouveaux concepts (respecter le template et la double appartenance)
- Vérifier que c'est bien un concept (pas un guide ou une formation) avant de créer
- Ne pas supprimer de fichier
- Ne pas modifier la structure du vault
- 1 concept = 1 idée claire (ne pas créer de concepts fourre-tout)
- En mode batch, traiter une ressource à la fois avec validation entre chaque
- L'utilisateur peut quitter à tout moment
