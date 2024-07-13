---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 15e733117b4458cc53dec309dad5bde8cb17029f
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![ de kaart van Pijpleidingen in Cloud Manager ](/help/assets/configure-pipelines/pipelines-card.png)

Door de ellipsieknoop naast elke pijpleiding te klikken kunt u de volgende acties voeren.

* [De pijplijn uitvoeren](#running-pipelines)
* [De pijplijn bewerken](#editing-pipelines)
* [De pijplijn verwijderen](#deleting-pipelines)
* [Details weergeven](#view-details)

Onder aan de lijst met pijpleidingen staan algemene opties.

* **voeg** toe - aan [ voeg een nieuwe productiepijpleiding ](/help/using/production-pipelines.md) toe of [ voeg nieuwe niet-productiepijpleiding ](/help/using/non-production-pipelines.md) toe
* **toon allen** - neemt de gebruiker aan het **scherm van Pijpleidingen** om alle pijpleidingen in een meer gedetailleerde lijst te bekijken
* **Info van de Reactie van de Toegang** - Toont de informatie noodzakelijk om tot de git van Cloud Manager toegang te hebben bewaarplaats
* **leer Meer** - navigeert aan CI/CD de middelen van de pijpleidingsdocumentatie.

## Venster Pijpleidingen {#pipelines}

Het **venster van Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Dit is nuttig aangezien het uitvoerigere informatie dan voorstelt wat in de [ Kaart van de Pijpleiding beschikbaar is.](#pipeline-card)

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het 0} Programma, ontvang of klik op** Pijpleidingen **tabel om op het** venster van de Pijpleidingen **te schakelen.**

1. Hier kunt u een lijst van alle pijpleidingen voor het programma zien evenals begin en einde pijpleidingsuitvoering zoals u in de **Kaart van Pijpleidingen** zou.

Tik op het pictogram of klik op het pictogram `i` om details over de laatste of huidige uitvoering van de pijpleiding weer te geven.

![ de uitvoeringsdetails van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-status.png)

Tapping of het klikken van **details van de Mening** zullen u aan de [ details van de pijpleidingsuitvoering nemen.](#view-details)

## Activiteitenvenster {#activity}

Het **venster van Activiteiten** toont een volledige lijst van alle pijplijnuitvoeringen voor het geselecteerde programma.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het 0} Programma, ontvang of klik op** Activiteit **lusje om aan het** venster van de Activiteit **over te schakelen.**

1. Hier ziet u een lijst van alle pijpleiding uitvoeringen voor het programma met inbegrip van huidige en historische executies.

Tik op het pictogram of klik op het pictogram `i` om details over de uitvoering van de geselecteerde pijpleiding weer te geven.

![ de uitvoeringsdetails van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-activity.png)

Tapping of het klikken van **details van de Mening** zullen u aan de [ details van de pijpleidingsuitvoering nemen.](#view-details)

## Lopende pijpleidingen {#running-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik op de ellipsknoop naast de pijpleiding u uitgezocht **Looppas** van het menu in werking stelt.

1. De pijpleidingslooppas begint en door de **Status** kolom wordt vermeld.

U kunt de details van de looppas zien door de ellipsknoop opnieuw te klikken en **[details van de Mening te selecteren.](#view-details)**

Afhankelijk van het type van pijpleiding, kunt u de looppas kunnen annuleren door de ellipsknoop opnieuw te klikken en **te selecteren annuleert**.

## Bewerkingspijplijnen {#editing-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik op de ellipsknoop naast de pijpleiding u **uitgeven en dan selecteren** van het menu uitgeven en wilt selecteren.

1. De **geeft de pijpleiding van de Productie uit** of **geeft niet-Productie pijplijn** dialoogvakvertoningen uit, toestaand u om de zelfde details uit te geven die u toen het creëren van de pijpleiding inging.

   * Zie de volgende pagina&#39;s voor details op alle gebieden en configuratieopties beschikbaar voor pijpleidingen.
      * [Productiepijpleidingen configureren](/help/using/production-pipelines.md)
      * [Niet-productiepijpleidingen configureren](/help/using/non-production-pipelines.md)

1. Klik op **Update** zodra u klaar bent met het uitgeven van de pijpleiding.

>[!NOTE]
>
>U kunt een lopende pijpleiding niet uitgeven.

## Verwijderen van pijpleidingen {#deleting-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik op de ellipsknoop naast de pijpleiding u uitgezocht **Schrapping** van het menu in werking stelt.

>[!NOTE]
>
>U kunt geen lopende pijpleiding schrappen.

## Details weergeven {#view-details}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik op de ellipsknoop naast de pijpleiding u uitgezocht **details van de Mening** van het menu in werking stelt.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![ details van de Pijpleiding ](/help/assets/configure-pipelines/pipeline-running-details.png)

Van hier kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie de plaatsing van de code van het document [ ](/help/using/code-deployment.md) voor meer informatie.

Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

Zodra een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

![ Overzicht van de Stap ](/help/assets/configure-pipelines/pipeline-step.png)

Tik of klik de **details van de Mening** verbinding om de **sectie van de Duur** te openbaren. Dit omvat de gemiddelde duur van de pijpleiding op basis van de historische trend voor dat programma.

![ Duur ](/help/assets/configure-pipelines/duration.png)

Als uw pijpleiding a **Code Scanning** stap bevatte, die kwesties opriep, kunt u de **knoop van de Details van de Download** tikken of klikken om een lijst van [ tests van de codekwaliteit ](/help/using/code-quality-testing.md) te bekijken die niet overgegaan.

![ de kwaliteitskwesties van de Code ](assets/managing-pipelines-code-quality-issues.png)

De kolom van de Plaats van het Dossier van het A **Project** is beschikbaar in het Csv- dossier om op de plaats van de beledigende code te wijzen. Deze kolom is de project-relatieve weg, terwijl de **kolom van de Plaats van het 0} Dossier {wordt geproduceerd.**

![ van het de aftasten van de code van het Project details ](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>U kunt details van een pijpleiding slechts bekijken die loopt of minstens eens in werking is gesteld.
