---
name: monthly-audit
description: Audit mensuel du vault Obsidian pour maintenir un vault propre et structuré. Usage quand l'utilisateur demande un audit mensuel, une maintenance du vault, ou une revue globale de la structure des notes.

---

# Audit Mensuel du Vault

Maintenir un vault propre, structuré et évolutif via une chaîne de skills.

## Étapes (ordre obligatoire)

### 1) Scan intelligent

**Skill :** `scan-vault-infer`

- Identifier nouveaux Concepts
- Identifier Méthodes implicites
- Proposer Hubs pertinents

### 2) Formalisation

**Skill :** `creer-concept`

- Créer les Concepts validés
- Lier aux notes sources

### 3) Structuration

**Skill :** `creer-hub`

- Créer / mettre à jour les Hubs
- Organiser la navigation

### 4) Nettoyage léger (optionnel)

**Skill :** `refactor-vault` (si existant)

- Harmoniser titres
- Supprimer doublons
- Clarifier liens

## Chemins

| Dossier | Chemin |
|---------|--------|
| Notes | `<VAULT_PATH>/<NOTES>/` |
| Catégorie | `<VAULT_PATH>/<CATEGORIES>/` |
| Ressources | `<VAULT_PATH>/<RESOURCES>/` |

## Règles

- Commencer en mode Audit
- Valider avant Apply
- Aucun changement structurel sans accord
