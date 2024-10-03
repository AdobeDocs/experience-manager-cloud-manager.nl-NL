---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen beheert, inclusief het uitvoeren, bewerken en verwijderen ervan.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen beheert, inclusief het uitvoeren, bewerken en verwijderen ervan.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![ de kaart van Pijpleidingen in Cloud Manager ](/help/assets/configure-pipelines/pipelines-card.png)

Door de ellipsieknoop naast elke pijpleiding te klikken, kunt u de volgende acties voeren:

* [ stel de pijpleiding ](#running-pipelines) in werking.
* [ geef de pijpleiding ](#editing-pipelines) uit.
* [ Schrap de pijpleiding ](#deleting-pipelines).
* [ details van de Mening ](#view-details).

Onder aan de lijst met pijpleidingen staan de volgende algemene opties.

* **voeg** toe - aan [ voeg een nieuwe productiepijpleiding ](/help/using/production-pipelines.md) toe of [ voeg een nieuwe niet-productiepijpleiding ](/help/using/non-production-pipelines.md) toe.
* **toon allen** - neemt de gebruiker aan het **scherm van Pijpleidingen** om alle pijpleidingen in een meer gedetailleerde lijst te bekijken.
* **Info van de Reactie van de Toegang** - toont de informatie noodzakelijk om tot de bewaarplaats van de Git van Cloud Manager toegang te hebben.
* **leer Meer** - navigeert aan CI/CD de middelen van de pijpleidingsdocumentatie.

## Pagina met pijplijnen {#pipelines}

De **pagina van Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Deze lijst is nuttig omdat het uitvoerigere informatie dan voorstelt wat in de [ kaart van Pijpleidingen ](#pipeline-card) beschikbaar is.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, klik het **Pijpleidingen** lusje om aan de **Pijpleidingen** pagina over te schakelen.

1. Hier kunt u een lijst van alle pijpleidingen voor het programma zien en pijpleidingsuitvoering beginnen en tegenhouden zoals u in de **Kaart van Pijpleidingen**.

Als u op het pictogram `i` klikt, worden de details van de laatste of huidige uitvoering van de pijplijn weergegeven.

![ de uitvoeringsdetails van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-status.png)

Het klikken **details van de Mening** neemt u aan de [ details van de pijpleidingsuitvoering ](#view-details).

## Activiteitenpagina {#activity}

De **pagina van Activiteiten** toont een volledige lijst van alle pijplijnuitvoeringen voor het geselecteerde programma.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, klik het **lusje van de Activiteit** om aan de **pagina van de Activiteit** over te schakelen.

1. Hier ziet u een lijst van alle pijpleiding uitvoeringen voor het programma met inbegrip van huidige en historische executies.

Als u op het pictogram `i` klikt, worden meer details over de uitvoering van de geselecteerde pijpleiding weergegeven.

![ de uitvoeringsdetails van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-activity.png)

Klik **details van de Mening** om [ details van de pijpleidingsuitvoering ](#view-details) te herzien.

## Pijpleidingen uitvoeren {#running-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.
1. Klik de ellipsknoop naast de pijpleiding die u in werking stelt, dan van het menu, uitgezochte **Looppas**.

   De kolom van de Status wijst erop wanneer de pijpleidingslooppas begint.

   U kunt de details van de looppas zien door de ellipsknoop opnieuw te klikken en **[details van de Mening](#view-details)** te selecteren.

   Afhankelijk van het type van pijpleiding, kunt u de looppas kunnen annuleren door de ellipsknoop opnieuw te klikken en **te selecteren annuleert**.

## Pijpleidingen bewerken {#editing-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding die u, dan van het menu wilt uitgeven, uitgezocht **uitgeven**.

1. De **geeft de pijpleiding van de Productie uit** of **geeft niet-Productie pijplijn** dialoogdoos uit verschijnt. U kunt de zelfde details uitgeven die u tijdens pijpleidingsverwezenlijking inging.

   Zie [ het Vormen de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ het Vormen niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md) voor details op de gebieden en configuratieopties beschikbaar voor pijpleidingen.

1. Klik **Update** wanneer u wordt gedaan.

>[!NOTE]
>
>U kunt een lopende pijpleiding niet uitgeven.

## Pijpleidingen verwijderen {#deleting-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u in werking stelt, dan van het menu, uitgezocht **Schrapping**.

>[!NOTE]
>
>U kunt geen lopende pijpleiding schrappen.

## Details weergeven {#view-details}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u in werking stelt, dan van het menu, uitgezochte **details van de Mening**.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![ details van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-running-details.png)

Van hier, kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie de plaatsing van de code van het document [ ](/help/using/code-deployment.md) voor meer informatie.

Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

Wanneer een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

![ Overzicht van de Stap ](/help/assets/configure-pipelines/pipeline-step.png)

Klik de **verbinding van de Details van de Mening** om de **sectie van de Duur** te openbaren. In dit deel wordt de gemiddelde duur van de pijpleiding vermeld op basis van de historische trend voor dat programma.

![ Duur ](/help/assets/configure-pipelines/duration.png)

Als uw pijpleiding a **Code Scanning** stap bevatte, die kwesties opriep, kunt u de **knoop van de Details van de Download** klikken om een lijst van [ tests van de codekwaliteit ](/help/using/code-quality-testing.md) te bekijken die niet overgegaan.

![ de kwaliteitskwesties van de Code ](assets/managing-pipelines-code-quality-issues.png)

De kolom van de Plaats van het Dossier van het A **Project** is beschikbaar in het Csv- dossier om op de plaats van de beledigende code te wijzen. Deze kolom is de project-relatieve weg, terwijl de **kolom van de Plaats van het 0} Dossier {wordt geproduceerd.**

![ van het de aftasten van de code van het Project details ](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>U kunt details van een pijpleiding slechts bekijken die loopt of minstens eens in werking is gesteld.
