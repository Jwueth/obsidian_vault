<%*
// Récupération des paramètres
const nbCol = parseInt(await tp.system.prompt("Nombre de colonnes ?", "3"));
const nbRows = parseInt(await tp.system.prompt("Nombre de lignes (sans l'en-tête) ?", "3"));
const withHeader = await tp.system.suggester(["Avec en-tête", "Sans en-tête"], [true, false]);
const alignment = await tp.system.suggester(
    ["Tout à gauche", "Tout au centre", "Tout à droite", "Personnalisé"], 
    ["left", "center", "right", "custom"]
);

// Fonction pour créer les séparateurs d'alignement
function getAlignSeparator(align) {
    if (align === "left") return ":-----";
    if (align === "center") return ":----:";
    if (align === "right") return "-----:";
    return "------"; // default
}

// Demander les en-têtes si avec header
let headers = [];
if (withHeader) {
    for(let i = 1; i <= nbCol; i++) {
        const header = await tp.system.prompt(`Nom de la colonne ${i} ?`, `Colonne ${i}`);
        headers.push(header);
    }
}

// Demander l'alignement personnalisé si choisi
let alignments = [];
if (alignment === "custom") {
    for(let i = 1; i <= nbCol; i++) {
        const align = await tp.system.suggester(
            [`Colonne ${i}: Gauche`, `Colonne ${i}: Centre`, `Colonne ${i}: Droite`],
            ["left", "center", "right"]
        );
        alignments.push(align);
    }
} else {
    // Tous les colonnes ont le même alignement
    alignments = Array(nbCol).fill(alignment);
}

// Construction du tableau
// En-tête si demandé
if (withHeader) {
    tR += "| " + headers.join(" | ") + " |\n";
    tR += "| " + alignments.map(a => getAlignSeparator(a)).join(" | ") + " |\n";
}

// Lignes de données
for(let row = 1; row <= nbRows; row++) {
    let cells = [];
    for(let col = 1; col <= nbCol; col++) {
        cells.push("  ");
    }
    tR += "| " + cells.join(" | ") + " |\n";
}
_%>
