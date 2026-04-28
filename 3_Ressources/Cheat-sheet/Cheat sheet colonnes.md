---
Date: 2025-11-25
aliases:
Catégories:
  - "[[<CATEGORIES>/<GUIDE>|<GUIDE>]]"
Tags:
  - colonnes
---
--- 
# Pandoc Multi-Column Cheat Sheet - Obsidian

## Syntaxe de base

### Région simple (2 colonnes par défaut)

```markdown
::: columns

Contenu colonne 1

::: columnbreak
:::

Contenu colonne 2

:::
```

---

## Avec attributs et ID

### Structure complète

```markdown
::::: {.columns id=MonID propriété=valeur}

Contenu colonne 1

::: columnbreak
:::

Contenu colonne 2

:::::
```

⚠️ **L'ID est OBLIGATOIRE** pour que ça fonctionne !

---

## Nombre de colonnes

### Avec mots anglais (jusqu'à 10)

```markdown
::: twocolumns
Contenu sur 2 colonnes
:::

::: three-columns
Contenu sur 3 colonnes
:::

::: {.four-columns}
Contenu sur 4 colonnes
:::
```

### Avec attribut col-count

```markdown
::: {.columns col-count=5}
Contenu sur 5 colonnes
:::
```

---

## Saut de colonne

```markdown
::: columnbreak
:::
```

⚠️ **Important :** Une ligne vide est requise après `:::` !

---

## Paramètres disponibles

### Espacement entre colonnes (columngap)

```markdown
::::: {.columns id=ID1 columngap=3em}
Contenu
:::::

::::: {.three-columns id=ID2 columngap=20px}
Contenu
:::::
```

**Unités acceptées :** px, pt, em, %, etc.

---

### Auto Layout (colonnes fluides)

```markdown
::::: {.columns id=ID3 auto-layout=true}
Contenu s'équilibre automatiquement
:::::

::::: {.columns id=ID4 fluid-columns=true}
Même effet
:::::
```

**Effet :** Le contenu se redistribue automatiquement entre les colonnes sans sauts manuels.

---

### Taille des colonnes

```markdown
::::: {.columns id=ID5 col-width=[25%, 75%]}
Colonne 1 (25%)
::: columnbreak
:::
Colonne 2 (75%)
:::::
```

---

### Bordure

```markdown
::::: {.columns id=ID6 border=off}
Sans bordure
:::::

::::: {.three-columns id=ID7 border=[off, on, off]}
Bordure uniquement sur colonne 2
:::::
```

**Valeurs :** `off`, `disabled`, `false`

---

### Ombre

```markdown
::::: {.columns id=ID8 shadow=off}
Sans ombre
:::::
```

**Valeurs :** `off`, `disabled`, `false`

---

### Alignement du texte

```markdown
::::: {.columns id=ID9 alignment=center}
Texte centré
:::::

::::: {.columns id=ID10 alignment=[left, center, right]}
Col 1 gauche, Col 2 centre, Col 3 droite
:::::
```

**Valeurs :** `left`, `center`, `right`

---


## Exemples pratiques

### Exemple 1 : Deux colonnes simples

```markdown
::::: {.columns id=exemple1}

# Colonne 1
Texte de la première colonne

::: columnbreak
:::

# Colonne 2
Texte de la deuxième colonne

:::::
```

---

### Exemple 2 : Trois colonnes avec espacement

```markdown
::::: {.three-columns id=exemple2 columngap=5px border=off}

**Liste 1**
- Item A
- Item B

::: columnbreak
:::

**Liste 2**
- Item C
- Item D

::: columnbreak
:::

**Liste 3**
- Item E
- Item F

:::::
```

::::: {.three-columns id=exemple2 columngap=5px border=off}

**Liste 1**
- Item A
- Item B

::: columnbreak
:::

**Liste 2**
- Item C
- Item D

::: columnbreak
:::

**Liste 3**
- Item E
- Item F
:::::
---

### Exemple 3 : Colonnes inégales sans bordure

```markdown
::::: {.columns id=exemple3 col-width=[30%, 70%] border=off}

## Sommaire
- Section 1
- Section 2
- Section 3

::: columnbreak
:::

## Contenu principal
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Sed do eiusmod tempor incididunt ut labore et dolore.

:::::
```

::::: {.columns id=exemple3 border=off}
###### Sommaire
- Section 1
- Section 2
- Section 3

::: columnbreak
:::
###### Contenu principal
- Lorem ipsum dolor sit amet, consectetur 
- adipiscing elit.
- Sed do eiusmod tempor incididunt ut labore et dolore.

:::::

### Exemple 4 : Auto-layout (équilibrage automatique)

```markdown
::::: {.columns id=exemple4 col-count=4 auto-layout=true}

# Section 1
Beaucoup de texte ici...

# Section 2
Un peu de texte...

# Section 3
Encore du texte...

# Section 4
Le plugin équilibre automatiquement sans columnbreak !

:::::
```

---

## Combinaison de paramètres

```markdown
::::: {.columns id=demo col-count=3 columngap=1.5em border=off shadow=off alignment=center auto-layout=true}

Contenu qui s'équilibre automatiquement
sur 3 colonnes centrées
sans bordure ni ombre
avec 1.5em d'espacement

:::::
```

---

## Raccourcis de paramètres

|Paramètre complet|Raccourci|
|---|---|
|`col-count`|`number-of-columns`|
|`col-width`|`column-size`, `col-size`|
|`columngap`|`column-spacing`|
|`alignment`|`text-align`, `content-align`|
|`auto-layout`|`fluid-columns`|

---

## ⚠️ Limitations Pandoc

**Non supporté :**

- ❌ Régions récursives (colonnes dans colonnes)
- ❌ Éléments "spanning" (qui traversent toutes les colonnes)
- ❌ Column rule (ligne de séparation personnalisée)
- ❌ Mode justified ou ragged

**Note :** `auto-layout` n'est PAS activé par défaut (contrairement à Pandoc PDF) pour des raisons de performance.

---

## Commandes Obsidian utiles

- **Insert Multi-Column Region** : Insère une région avec ID aléatoire
- **Fix Missing IDs** : Ajoute des ID manquants automatiquement

---

## Template de démarrage rapide

```markdown
::::: {.columns id=CHANGE_ME col-count=2}

Première colonne

::: columnbreak
:::

Deuxième colonne

:::::
```

**N'oublie pas de changer l'ID !**

---

