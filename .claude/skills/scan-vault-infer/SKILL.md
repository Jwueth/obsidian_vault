---
name: scan-vault-infer
description: Analyse les notes Obsidian pour identifier de nouveaux concepts, méthodes et hubs potentiels. Utiliser quand l'utilisateur demande un audit du vault, d'identifier des patterns émergents, de trouver des idées répétées, des définitions implicites, des méthodes non formalisées, ou de proposer une meilleure structuration des notes.

---

# Scan & Inférence de Connaissance

Analyser les notes pour détecter des opportunités de structuration : **Concepts**, **Méthodes** et **Hubs** potentiels.

## Dossier cible

Par défaut : `<VAULT_PATH>/<NOTES>/`

L'utilisateur peut spécifier un autre dossier.

## Modes

### Mode Audit (défaut)

Proposer sans créer de fichiers :
- Concepts candidats
- Méthodes candidates
- Hubs possibles

### Mode Apply

Créer les fiches validées en utilisant les templates existants et les skills `creer-concept` / `creer-hub`.

## Critères d'analyse

### Concepts potentiels
- Définitions implicites
- Idées récurrentes
- Notions clés / principes généraux

### Méthodes potentielles
- Étapes répétées / checklists
- Procédures / process décrits

### Hubs potentiels
- Thématiques avec beaucoup de notes
- Sujets fragmentés
- Domaines en expansion

## Format de sortie (Audit)

### Concepts

| Champ | Description |
|-------|-------------|
| Titre proposé | Nom du concept |
| Catégorie | Classification |
| Résumé | Description courte |
| Notes sources | Liens vers les notes |
| Justification | Pourquoi c'est pertinent |

### Méthodes

| Champ | Description |
|-------|-------------|
| Nom proposé | Nom de la méthode |
| Objectif | But de la méthode |
| Résumé | Description courte |
| Notes sources | Liens vers les notes |
| Justification | Pourquoi formaliser |

### Hubs

| Champ | Description |
|-------|-------------|
| Nom du hub | Titre |
| Catégorie | Classification |
| Sous-thèmes | Thèmes regroupés |
| Notes sources | Liens vers les notes |

## Règles

- Ne pas supprimer de notes
- Ne pas modifier la structure existante
- Ne pas créer de nouveaux templates
- Respecter le playbook Obsidian (`<CONFIG_PATH>/obsidian/CLAUDE.md`)
- Citer les sources
- Proposer avant d'appliquer (sauf si mode Apply explicite)
