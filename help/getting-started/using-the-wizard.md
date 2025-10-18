---
title: De wizard Nieuw project gebruiken
description: Volg deze pagina om te leren hoe u de wizard kunt gebruiken om een AEM Application Project te maken.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: b98e1711f1f98f52977dd6cb4cd2bc834d81a360
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# De nieuwe projectwizard gebruiken {#using-the-wizard}

Als u als nieuwe klant aan Cloud Manager wordt toegevoegd, ontvangt u een lege Git-opslagplaats. Om u te helpen begonnen worden, biedt de Manager van de Wolk een tovenaar aan om een minimaal AEM-project tot stand te brengen dat op het [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) als uitgangspunt wordt gebaseerd.

Voer de volgende stappen uit om een AEM-project te maken met de wizard.

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com) en selecteer de juiste organisatie.

1. Als u niet reeds hebt, [ creeer uw programma ](program-setup.md). Wanneer het programma wordt gemaakt, detecteert Cloud Manager dat de opslagplaatsen nog niet zijn ingesteld. Een speciale kaart van call-to-action verschijnt dan op het **scherm van het Overzicht**.

   ![ creeer project CTA ](/help/assets/image2018-10-3_14-29-44.png)

1. Klik **creëren** om de tovenaar te beginnen en belangrijke waarden te verstrekken.

   * **Titel** - de titel van het project. Standaard wordt de naam van het programma ingesteld.
   * **Nieuwe Naam van de Tak** - de aanvankelijke tak van uw bewaarplaatsen van het Git. De standaardwaarde is `main` .

   ![ waarden van het Project ](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Het dialoogvenster heeft een lade die kan worden geopend door op de handgreep naar de onderkant te klikken. In zijn uitgebreide vorm, toont de dialoogdoos alle configuratieparameters voor het het projectarchetype van AEM. Deze parameters hebben standaardwaarden die op de **Titel** worden geproduceerd u reeds verstrekte en vereisen geen wijziging. Ze worden hier uitgelegd voor uw informatie.

   ![ Gedetailleerde archetype parameters ](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klik **creeer** om het starterproject tot stand te brengen door archetype te gebruiken en aan de genoemde tak van het Git te begaan.

U hebt nu een basisproject. Het is tijd om uw pijpleidingen op te zetten.

## Bestaande of migrerende klanten {#existing-migrating}

Als u een huidige Adobe Managed Services (AMS)-klant bent of een AEM-klant op locatie die migreert, hebt u waarschijnlijk al een projectcode in Git of een ander versiebeheersysteem.

In dergelijke gevallen kunt u uw project importeren in de Cloud Manager Git-opslagplaats.
