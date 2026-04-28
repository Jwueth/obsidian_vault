<%*
const tableType = await tp.system.suggester(
    ["Tableau standard", "Liste de tâches", "Comparaison Avantages/Inconvénients", "Timeline/Dates"],
    ["standard", "tasks", "pros-cons", "timeline"]
);

if (tableType === "standard") {
    const nbCol = parseInt(await tp.system.prompt("Nombre de colonnes ?", "3"));
    const nbRows = parseInt(await tp.system.prompt("Nombre de lignes ?", "5"));
    
    tR += "| ";
    for(let i = 1; i <= nbCol; i++) {
        tR += `Colonne ${i}`;
        if(i < nbCol) tR += " | ";
    }
    tR += " |\n";
    tR += "| " + Array(nbCol).fill("-----").join(" | ") + " |\n";
    
    for(let row = 1; row <= nbRows; row++) {
        tR += "| " + Array(nbCol).fill("  ").join(" | ") + " |\n";
    }
}

else if (tableType === "tasks") {
    const nbRows = parseInt(await tp.system.prompt("Nombre de tâches ?", "5"));
    
    tR += "| Tâche | Status | Priorité | Deadline |\n";
    tR += "| :---- | :----: | :------: | :------: |\n";
    
    for(let i = 1; i <= nbRows; i++) {
        tR += "| Tâche " + i + " | ⏳ | Moyenne |  |\n";
    }
}

else if (tableType === "pros-cons") {
    const nbItems = parseInt(await tp.system.prompt("Nombre d'items ?", "3"));
    
    tR += "| ✅ Avantages | ❌ Inconvénients |\n";
    tR += "| :----------- | :--------------- |\n";
    
    for(let i = 1; i <= nbItems; i++) {
        tR += "|  |  |\n";
    }
}

else if (tableType === "timeline") {
    const nbEvents = parseInt(await tp.system.prompt("Nombre d'événements ?", "5"));
    
    tR += "| Date | Événement | Détails |\n";
    tR += "| :--: | :-------- | :------ |\n";
    
    for(let i = 1; i <= nbEvents; i++) {
        tR += "|  |  |  |\n";
    }
}
_%>