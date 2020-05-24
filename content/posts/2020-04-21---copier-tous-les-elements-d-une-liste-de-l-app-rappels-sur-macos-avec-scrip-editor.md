---
title: "Copier tous les éléments d'une liste de l'app Rappels sur macOS avec Scrip Editor"
date: "2020-04-21T13:27:23.000Z"
template: "post"
draft: false
slug: "copier-tous-les-elements-d-une-liste-de-l-app-rappels-sur-macos-avec-scrip-editor"
category: "macOS"
tags: 
  - "Français"
  - "macOS"
  - "Uncategorized FR"
description: "Dans l'application Reminders / Rappels de macOS, il n'est pas possible de copier tous les rappels d'un coup. Ce script permet de remédier à ce problème"
---

Dans l'application Reminders / Rappels de macOS, il n'est pas possible de copier tous les rappels d'un coup. Pas non plus de solution de copiage ou partage sur iOS. Et il est également impossible de copier le code HTML de l'app web sur icloud.com. Ce script permet de remédier à ce problème en ajoutant au clipboard tous les items d'une list de rappels qu'on peut sélectionner au lancement du script. Voici comment faire

1) Ouvrir Script Editor 
2) Copier/coller le code ci-dessous 
3) Sélectionnez "Javascript" dans le coin supérieur gauche 
4) Cliquez sur "Exécuter" (bouton play)

![Copier tous les éléments d'une liste de l'app Rappels sur macOS avec Scrip Editor](/media/2020-04-21---copier-tous-les-elements-d-une-liste-de-l-app-rappels-sur-macos-avec-scrip-editor/copier-tous-les-elements-dune-liste-de-lapp-rappels-sur-macos-avec-scrip-editor.png)

L'app reminder s'ouvrira si elle n'est pas déjà ouverte et il sera alors possible de choisir la liste dont on veut copier les items. Il ne reste ensuite plus qu'à les coller n'importe ou. Dans TextEdit par exemple.

```javascript
// set things up
var app = Application('Reminders');
app.includeStandardAdditions = true;

// choose list
var listName = app.chooseFromList(app.lists.name(), { withPrompt: "Which List?" });
if (listName) {

	// get the data from the list
	var remindersList = app.lists.byName(listName).reminders;
	var listNames = remindersList.name();
	var listCompleted = remindersList.completed();
	var listDueDates = remindersList.dueDate();
	var listBodies = remindersList.body();
	
	// create a single array
	var list = \[\];
	for(var i=0; i (a.name > b.name));
	//list.sort((a, b) => (a.dueDate > b.dueDate));
	
	// build text from list
	var text = "";
	var n = 0;
	for(var i=0; i // show message
	app.displayAlert("Reminders Copied", { message: n+" copied to the clipboard." });
}
```

Source : [How To Copy Reminders In macOS Catalina With a Script](https://macmost.com/how-to-copy-reminders-in-macos-catalina-with-a-script.html)
