---
tags:
  - catégories
---
views:
  - type: table
    name: Table
    filters:
      and:
        - Catégories.contains(link("Catégorie/Concepts", "Concepts"))
        - '!file.name.contains("Template")'
    order:
      - file.name
      - Thématiques
      - Projet
    sort:
      - property: file.tags
        direction: ASC
    columnSize:
      file.name: 507
      note.Thématiques: 620