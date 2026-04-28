---
name: tri-inbox
description: Restructure, trie, catégorise, lie les notes et les déplace dans le dossier notes. Usage quand l'utilisateur demande un tri, une analyse et une restructuration des notes du dossier /<INBOX>

---

# Tri de la <INBOX> Obsidian

Transformer les notes brutes de `<INBOX>/` en notes structurées, catégorisées et liées, puis les déplacer dans `<NOTES>/`.

## Chemins

| Dossier | Chemin |
|---------|--------|
| Entrée | `<VAULT_PATH>/<INBOX>/` |
| Sortie | `<VAULT_PATH>/<NOTES>/` |
| Templates | `<VAULT_PATH>/<TEMPLATES>/Notes/` |

## Processus par note

### 1) Identifier le type

| Type | Critères | Template |
|------|----------|----------|
| Projet | Travail en cours, mission | `<TEMPLATE_PROJET>` |
| Concept | Définition, principe, notion | `<TEMPLATE_CONCEPT>` |
| Note standard | Réflexion, info, apprentissage | `<TEMPLATE_STANDARD>` |

### 2) Renseigner les propriétés

#### Propriétés communes à toutes les notes

| Propriété | Règle | Valeurs |
|-----------|-------|---------|
| `Tags:` | **Obligatoire** | Reprendre les hashtags présents en haut de la note |
| `Thématiques:` | **Obligatoire** | Métacatégorie(s) du type : <THEMATIQUE_1>, <THEMATIQUE_2>, <THEMATIQUE_3>, <THEMATIQUE_4>, <THEMATIQUE_5>, <THEMATIQUE_6>, <THEMATIQUE_7>, etc. |
| `Collection:` | Optionnel | Choisir parmi : <COLLECTION_1> / <COLLECTION_2> / <COLLECTION_3> / <COLLECTION_4> / <COLLECTION_5> / <COLLECTION_6> — laisser vide si aucune ne correspond |
| `Catégories:` | Selon type | Wikilink vers la catégorie Obsidian |
| `Statut:` | Selon état | ex. `draft`, `done`, `in-progress` |

#### Propriétés spécifiques par type

| Type | Propriété | Valeur |
|------|-----------|--------|
| Projet | `Projet:` | `[[Nom du projet]]` |
| Concept | `Catégories:` | `[[<CATEGORIES>/<CONCEPTS>]]` |
| Note standard | `Catégories:` | `[[<CATEGORIES>/...]]` |

#### Règle Collection vs Catégories

- `Catégories` = index interne Obsidian (wikilink vers un hub du vault)
- `Collection` = appartenance à un projet externe (<COLLECTION_1>, etc.) — **ne pas confondre les deux**
- Une note peut avoir une `Catégorie` sans avoir de `Collection`

### 3) Restructurer

Chaque note doit contenir :
- Hashtags en haut : `#<thematique> #<categorie> #<sujet>` — ces tags seront repris dans la propriété `Tags:`
- Description brève
- Sections claires
- Liens internes `[[...]]` vers <CONCEPTS>, Projets, Catégories (même si inexistants)

### 4) Déplacer

`<INBOX>/` → `<NOTES>/`

## Règles

- Ne jamais supprimer de note
- Ne pas modifier la structure du vault
- Ne pas créer de nouveaux templates
- Respecter les templates existants
- 1 note = 1 idée principale
- Clarifier le titre si nécessaire
