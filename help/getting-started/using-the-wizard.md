---
title: De wizard Nieuw project gebruiken
description: Volg deze pagina om te leren hoe u de wizard kunt gebruiken om een AEM Application Project te maken
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# De wizard Nieuw project gebruiken {#using-the-wizard}

Als u als nieuwe klant aan Cloud Manager wordt toegevoegd, krijgt u een lege git-opslagplaats. Om u te helpen begonnen worden, biedt de Manager van de Wolk een tovenaar aan om een minimaal AEM project tot stand te brengen dat op [ wordt gebaseerd AEM Archetype van het Project ](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) als uitgangspunt.

Voer de volgende stappen uit om een AEM project te maken met de wizard.

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com) en selecteer de juiste organisatie.

1. Als u niet reeds hebt, [ creeer uw programma.](program-setup.md) Zodra het programma wordt gecreeerd, zal Cloud Manager erkennen dat de bewaarplaatsen nog niet opstelling zijn en een speciale vraag-aan-actie kaart wordt getoond op het **2} scherm van het Overzicht {.**

   ![ creeer project CTA ](/help/assets/image2018-10-3_14-29-44.png)

1. Klik **creëren** om de tovenaar te beginnen en belangrijke waarden te verstrekken.

   * **Titel** - dit is de titel van het project en is door gebrek geplaatst aan de naam van het programma.
   * **Nieuwe Naam van de Tak** - dit is de aanvankelijke tak van uw gokbewaarplaatsen en door gebrek zal zijn `main`.

   ![ waarden van het Project ](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Het dialoogvenster heeft een lade die kan worden geopend door op de handgreep naar de onderkant te klikken. In zijn uitgebreide vorm, toont de dialoog alle configuratieparameters voor het AEM project archetype. Deze parameters hebben standaardwaarden die op de **Titel** worden geproduceerd u reeds verstrekte en vereisen geen wijziging. Ze worden hier uitgelegd voor uw informatie.

   ![ Gedetailleerde archetype parameters ](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klik **creeer** om het starterproject tot stand te brengen door het archetype te gebruiken en aan de genoemde git tak te begaan.

U hebt nu een basisproject! Nu kun je je pijpleidingen opzetten.

## Bestaande of migrerende klanten {#existing-migrating}

Als u een huidige klant van de Adobe Managed Services (AMS) of een klant op-gebouw AEM aan wie migreert bent, hebt u waarschijnlijk reeds projectcode in git of een ander systeem van de versiecontrole.

In dergelijke gevallen importeert u uw project in de Cloud Manager git-opslagplaats.
