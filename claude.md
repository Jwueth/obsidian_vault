# Playbook Obsidian

> Ce fichier définit les règles, la structure et les conventions
> pour utiliser Claude avec **Obsidian**.
>
> Les actions concrètes sont gérées par des **skills** dans `<SKILLS_PATH>/`.

---

## 1) Chemins

| Élément | Chemin |
|---------|--------|
| Vault Obsidian | `<VAULT_PATH>` |
| Skills | `<SKILLS_PATH>/` |
| Ce playbook | `<CONFIG_PATH>/obsidian/CLAUDE.md` |

---

## 2) Structure du vault

```
<INBOX>/
  ressources/
<NOTES>/
<CATEGORIES>/
<RESOURCES>/
<TEMPLATES>/
Pièces jointes/
```

Cette structure doit être respectée.

---

## 3) Où va quoi

| Contenu | Dossier |
|---------|---------|
| Notes en vrac | `<INBOX>/` |
| Ressources clipées | `<INBOX>/ressources/` |
| Notes traitées | `<NOTES>/` |
| Indexes / Hubs | `<CATEGORIES>/` |
| Ressources (traitées) | `<RESOURCES>/` |
| Fichiers | Pièces jointes/ |

### Logique de rangement

- Toute note doit être traitée et déplacée vers `<NOTES>/`
- Toute note doit être liée à un hub via la propriété `Catégories:`
- `<CATEGORIES>/` contient les indexes qui pointent vers les notes

---

## 4) Templates à respecter

Claude doit utiliser les templates existants :

* `<TEMPLATES>/Notes/<TEMPLATE_PROJET>`
* `<TEMPLATES>/Notes/<TEMPLATE_STANDARD>`
* `<TEMPLATES>/Notes/<TEMPLATE_CONCEPT>`

Aucun nouveau template ne doit être créé sans validation.

---

## 5) Skills

Les **skills** définissent *comment* Claude doit agir. Ils sont invoqués automatiquement.

### Skills disponibles

| Skill | Description |
|-------|-------------|
| `tri-box` | Traiter `<INBOX>` et déplacer les notes vers `<NOTES>/` |
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

---

## 6) Règles

Claude doit :

* Respecter la structure du vault
* Utiliser les wikilinks `[[...]]` même si la note n'existe pas encore
* Ajouter des liens internes dès que possible
* Utiliser des hashtags au début des notes
* Écrire en Markdown propre
* Favoriser la lisibilité
* Éviter les doublons
* Ne jamais supprimer définitivement
* Ne jamais modifier la structure sans validation
* Ne jamais mélanger code et notes

---

## 7) Philosophie

> Obsidian = mémoire
> Claude = amplificateur
> Les skills = la méthode

---

**Version :** v6
**Dernière mise à jour :** 2026-04-28
