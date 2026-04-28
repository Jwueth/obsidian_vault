---
name: creer-hub
description: Création ou mise à jour d'une note Hub (dossier catégorie) pour organiser une thématique ou un domaine. Usage lorsque l'utlisateur demande de créer un hub avec une note ou une liste de notes, de mettre à jour une catégorie ou d'analyser si une catégorie doit être créée.

---

# Créer un Hub Obsidian

Créer ou mettre à jour une note Hub pour organiser une thématique, catégorie ou domaine.

## Chemins

| Dossier | Chemin |
|---------|--------|
| Sources | `<VAULT_PATH>/<NOTES>/` |
| Sortie | `<VAULT_PATH>/<CATEGORIES>/` |
| Templates | `<VAULT_PATH>/<TEMPLATES>/bases/` |

## Catégories disponibles

| Catégorie | Usage |
|-----------|-------|


## Processus

### 1) Identifier le thème

Repérer : thématique récurrente, catégorie existante, domaine en croissance.

Exemples : ...

### 2) Créer la note Hub

Nom : `Hub – <Nom du thème>.md`

Structure :

```markdown
#hub #<categorie> #<theme>

# Hub – <Nom du thème>

## Vue d'ensemble
> Description courte du domaine

## Concepts clés
- [[Concept A]]

## Projets liés
- [[Projet X]]

## Guides & Méthodes
- [[Guide Y]]

## Ressources
- [[Ressource Z]]

## Notes connexes
- [[Note 1]]
```

### 3) Ajouter les liens

- Lier tous les éléments pertinents
- Wikilinks même si la note n'existe pas encore
- Relier le hub à la catégorie correspondante

## Règles

- Ne pas supprimer de notes
- Ne pas créer de nouvelles catégories
- Ne pas modifier la structure du vault
- 1 hub = 1 thème
