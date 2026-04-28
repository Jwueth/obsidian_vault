---
name: creer-concept
description: Transformation d'une ou plusieurs notes en une fiche concept structurée, claire et liée aux notes correspondantes. Usage lorsque l'utilisateur demande de créer un concept avec une ou plusieurs notes.

---

# Créer un Concept Obsidian

Transformer une ou plusieurs notes en une fiche **Concept** structurée et liée.

## Chemins

| Dossier | Chemin |
|---------|--------|
| Sources | `<VAULT_PATH>/<NOTES>/` |
| Sortie | `<VAULT_PATH>/<NOTES>/` |
| Template | `<VAULT_PATH>/<TEMPLATES>/Notes/<TEMPLATE_CONCEPT>` |

## Processus

### 1) Identifier le concept

Repérer dans les notes sources :
- Idée récurrente
- Principe important
- Notion centrale
- Modèle / framework

### 2) Créer la fiche avec le template `<TEMPLATE_CONCEPT>`

Structure obligatoire :
- Définition
- Pourquoi c'est important
- Comment l'utiliser
- Exemples
- Ressources
- Notes connexes

### 3) Renseigner les propriétés (frontmatter)

| Propriété | Règle | Valeur |
|-----------|-------|--------|
| `Tags:` | **Obligatoire** | Reprendre les hashtags présents en haut de la note |
| `Thématiques:` | **Obligatoire** | Métacatégorie(s) : <THEMATIQUE_1>, <THEMATIQUE_2>, <THEMATIQUE_3>, <THEMATIQUE_4>, <THEMATIQUE_5>, <THEMATIQUE_6>, <THEMATIQUE_7>, etc. |
| `Catégories:` | **Obligatoire** | **Double appartenance** : `<CONCEPTS>` + catégorie thématique (voir ci-dessous) |
| `Collection:` | Optionnel | Choisir parmi : liste
| `Statut:` | Obligatoire | `stable` / `draft` |
| `aliases:` | Optionnel | Synonymes du concept |

#### Double appartenance (<CONCEPTS> + catégorie thématique)

Les concepts utilisent **deux catégories** :
1. `[[<CATEGORIES>/<CONCEPTS>|<CONCEPTS>]]` — pour l'index des concepts
2. Catégorie thématique — pour le regroupement par sujet

| Catégorie thématique | Usage |
|---------------------|-------|


**Exemple** :
```yaml
Catégories:
  - "[[<CATEGORIES>/<CONCEPTS>|<CONCEPTS>]]"
  - "[[<CATEGORIES>/<CARRIERE>|<CARRIERE>]]"
```

### 4) Ajouter liens et hashtags

- Hashtags en haut : `#concept #<thematique> #<sujet>` — ces tags seront repris dans `Tags:`
- Liens `[[...]]` vers : notes sources, concepts proches, catégorie
- Créer les liens même si les notes n'existent pas encore

## Règles

- Ne pas supprimer les notes sources
- Ne pas modifier la structure du vault
- Ne pas créer de nouveaux templates
- 1 concept = 1 idée claire
- Ton clair et structuré
