---
name: inbox-to-knowledge
description: Workflow complet pour transformer les notes brutes de <INBOX> en connaissance structurée. Usage quand l'utilisateur demande de traiter l'inbox, transformer les notes brutes en connaissance, ou exécuter le workflow complet de structuration.

---

# Inbox to Knowledge

Transformer les notes brutes de `<INBOX>/` en connaissance structurée via une chaîne de skills.

## Flux

```
<INBOX>/ → <NOTES>/ → <CATEGORIES>/...
```

## Étapes (ordre obligatoire)

### 1) Trier la <INBOX>

**Skill :** `tri-inbox`

- Lire les notes de `<INBOX>/`
- Identifier le type (Projet / Concept / Note)
- Appliquer le template, propriétés, liens, hashtags
- Déplacer vers `<NOTES>/`

### 2) Créer les Concepts

**Skill :** `creer-concept`

- Repérer les idées clés dans les Notes
- Créer des fiches Concept
- Lier aux notes sources

### 3) Créer / Mettre à jour les Hubs

**Skill :** `creer-hub`

- Organiser les concepts par thématique
- Créer/mettre à jour les pages hub

## Chemins

| Dossier | Chemin |
|---------|--------|
| Entrée | `<VAULT_PATH>/<INBOX>/` |
| Traitement | `<VAULT_PATH>/<NOTES>/` |
| Sortie | `<VAULT_PATH>/<CATEGORIES>/` |

## Règles

- Exécuter les skills dans l'ordre
- Aucune suppression définitive
- Respecter les templates Obsidian
- Le playbook Obsidian fait autorité
