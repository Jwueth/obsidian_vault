<%*
const tableType = await tp.system.suggester(
    ["Tableau standard", "Comparaison Projets/Solutions", "5 Pourquoi", "Avantages/Inconvénients", "Timeline/Dates"],
    ["standard", "comparison", "5why", "pros-cons", "timeline"]
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

else if (tableType === "comparison") {
    const nbSolutions = parseInt(await tp.system.prompt("Nombre de solutions à comparer ?", "3"));
    
    tR += "| Critère | ";
    for(let i = 1; i <= nbSolutions; i++) {
        tR += `Solution ${String.fromCharCode(64 + i)}`;
        if(i < nbSolutions) tR += " | ";
    }
    tR += " |\n";
    
    tR += "| :------ | ";
    for(let i = 1; i <= nbSolutions; i++) {
        tR += ":--------:";
        if(i < nbSolutions) tR += " | ";
    }
    tR += " |\n";
    
    // Critères prédéfinis
    const criteres = ["💰 Coût", "⏱️ Temps", "⚙️ Complexité", "🎯 ROI", "🔒 Risques"];
    for(let critere of criteres) {
        tR += `| ${critere} | `;
        for(let i = 1; i <= nbSolutions; i++) {
            tR += " ";
            if(i < nbSolutions) tR += " | ";
        }
        tR += " |\n";
    }
}

else if (tableType === "5why") {
    const probleme = await tp.system.prompt("Quel est le problème initial ?", "Problème");
    
    tR += "| Niveau | Pourquoi ? | Réponse |\n";
    tR += "| :----: | :--------- | :------ |\n";
    tR += `| 0 | Problème initial | ${probleme} |\n`;
    
    for(let i = 1; i <= 5; i++) {
        tR += `| ${i} | Pourquoi ? |  |\n`;
    }
    
    tR += "| ✅ | **Cause racine** | **INSÉRER ICI** |\n";
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

