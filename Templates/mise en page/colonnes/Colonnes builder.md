<%*
// Récupération des paramètres
const nbCol = parseInt(await tp.system.prompt("Nombre de colonnes ?", "2"));
const gap = await tp.system.prompt("Espacement (ex: 2em) ?", "1.5em");
const border = await tp.system.suggester(["Avec bordure", "Sans bordure"], ["on", "off"]);
const id = tp.date.now("YYYYMMDDHHmmss");

// Construction de l'ouverture
tR += `::::: {.columns id=${id} col-count=${nbCol} columngap=${gap} border=${border}}\n\n`;

// Construction des colonnes
for(let i = 1; i <= nbCol; i++) {
    tR += `Colonne ${i}\n\n`;
    
    // Ajouter columnbreak sauf pour la dernière colonne
    if(i < nbCol) {
        tR += `::: columnbreak\n:::\n\n`;
    }
}

// Fermeture
tR += `:::::\n`;
_%>