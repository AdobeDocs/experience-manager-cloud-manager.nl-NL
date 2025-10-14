---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen beheert, inclusief het uitvoeren, bewerken en verwijderen ervan.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 91eda02d55134fba167f30830a142a80717e9083
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen beheert, inclusief het uitvoeren, bewerken en verwijderen ervan.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![&#x200B; de kaart van Pijpleidingen in Cloud Manager &#x200B;](/help/assets/configure-pipelines/pipelines-card.png)

Door ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast elke pijpleiding te klikken, kunt u de volgende acties nemen:

* [&#x200B; stel de pijpleiding &#x200B;](#running-pipelines) in werking.
* [&#x200B; geef de pijpleiding &#x200B;](#editing-pipelines) uit.
* [&#x200B; Schrap de pijpleiding &#x200B;](#deleting-pipelines).
* [&#x200B; details van de Mening &#x200B;](#view-details).

Onder aan de lijst met pijpleidingen staan de volgende algemene opties.

* **voeg** toe - aan [&#x200B; voeg een nieuwe productiepijpleiding &#x200B;](/help/using/production-pipelines.md) toe of [&#x200B; voeg een nieuwe niet-productiepijpleiding &#x200B;](/help/using/non-production-pipelines.md) toe.
* **toon allen** - neemt de gebruiker aan het **scherm van Pijpleidingen** om alle pijpleidingen in een meer gedetailleerde lijst te bekijken.
* **Info van de Reactie van de Toegang** - toont de informatie noodzakelijk om tot de bewaarplaats van de Git van Cloud Manager toegang te hebben.
* **leer Meer** - navigeert aan CI/CD de middelen van de pijpleidingsdocumentatie.

## Pagina met pijplijnen {#pipelines}

De **pagina van Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Deze lijst is nuttig omdat het uitvoerigere informatie dan voorstelt wat in de [&#x200B; kaart van Pijpleidingen &#x200B;](#pipeline-card) beschikbaar is.

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, klik het **Pijpleidingen** lusje om aan de **Pijpleidingen** pagina over te schakelen.

1. Hier kunt u een lijst van alle pijpleidingen voor het programma zien en pijpleidingsuitvoering beginnen en tegenhouden zoals u in de **Kaart van Pijpleidingen**.

Als u op het pictogram `i` klikt, worden de details van de laatste of huidige uitvoering van de pijplijn weergegeven.

![&#x200B; de uitvoeringsdetails van de Pijpleiding &#x200B;](/help/assets/configure-pipelines/pipeline-status.png)

Het klikken **details van de Mening** neemt u aan de [&#x200B; details van de pijpleidingsuitvoering &#x200B;](#view-details).

### Markeer favorieten voor pijpleidingen{#pipeline-favorites}

U kunt specifieke pijpleidingen als favorieten merken zodat verschijnen zij bij de bovenkant van de lijst op de **pagina van Pijpleidingen**. Hierdoor zijn vaak geopende pijpleidingen gemakkelijker te vinden en uit te voeren.

**om pijpleidingsfavorieten te merken:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Van de **pagina van het Overzicht van het 0&rbrace; Programma, klik ![&#x200B; het lusje van de Pijpleiding - het pictogram van het Werkschema &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)** Pijpleidingen **tabel.**
1. Voor de **pagina van de Pijpleidingen**, links van een pijpleidingsnaam en type, klik ![&#x200B; het overzichtspictogram van de Ster voor ongunstige pijpleiding &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_StarOutline_18_N.svg) om het aan uw favoriete lijst toe te voegen.
Alternatief, klik ![&#x200B; pictogram van de Ster voor een favoriete pijpleiding &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Star_18_N.svg) om de pijpleiding uit uw favorieten lijst te verwijderen.


## Activiteitenpagina {#activity}

De **pagina van Activiteiten** toont een volledige lijst van alle pijplijnuitvoeringen voor het geselecteerde programma.

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, klik het **lusje van de Activiteit** om aan de **pagina van de Activiteit** over te schakelen.

1. Hier ziet u een lijst van alle pijpleiding uitvoeringen voor het programma met inbegrip van huidige en historische executies.

Als u op het pictogram `i` klikt, worden meer details over de uitvoering van de geselecteerde pijpleiding weergegeven.

![&#x200B; de uitvoeringsdetails van de Pijpleiding &#x200B;](/help/assets/configure-pipelines/pipeline-activity.png)

Klik **details van de Mening** om [&#x200B; details van de pijpleidingsuitvoering &#x200B;](#view-details) te herzien.

## Een pijplijn uitvoeren {#run-one-pipeline}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.
1. Klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt, dan klik **Looppas**.

   De kolom van de Status wijst erop wanneer de pijpleidingslooppas begint.

   U kunt de details van de looppas zien door ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) opnieuw te klikken en **[details van de Mening](#view-details)** te klikken.

   Afhankelijk van het type van pijpleiding, kunt u de looppas kunnen annuleren door ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) opnieuw te klikken en **te klikken annuleert**.

## Meerdere pijpleidingen uitvoeren {#run-multiple-pipelines}

Met Cloud Manager kunt u meerdere pijpleidingen tegelijk uitvoeren, waardoor de efficiëntie van de implementatie voor klanten van Adobe Managed Services (AMS) wordt verbeterd. De **Looppas geselecteerde** eigenschap laat u veelvoudige pijpleidingen selecteren en hen teweegbrengen om meteen te lopen. Het vermindert de handmatige inspanning van het moeten pijpleidingen individueel in werking stellen en optimaliseert bouw en plaatsingswerkschema&#39;s.

**om veelvoudige pijpleidingen in werking te stellen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. Van het linkerzijmenu, klik ![&#x200B; pictogram van het Werkschema &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pijpleidingen**.
1. In de lijst op de **pagina van de Pijpleiding**, selecteer checkboxes naast de pijpleidingen u wilt lopen.
Indien noodzakelijk, klik ![&#x200B; pictogram van de Filter, trechter &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) **Filters** aan soortpijpleidingen door naam, of milieu, of opgesteld codetype, of een combinatie van alle drie.
1. Dichtbij de hoger-juiste hoek van de pagina, klik **Geselecteerde Looppas (x)**.
1. In de **Looppas geselecteerde pijpleidingen (x)** dialoogdoos, klik **Looppas (x)**.

   De **looppas** knoop wijst op het aantal pijpleidingen die kunnen te werk gaan. U hebt bijvoorbeeld vier pijpleidingen geselecteerd, maar er is al een pijpleiding actief. Of een omgeving die is gekoppeld aan een geselecteerde pijpleiding bestaat niet meer. In dergelijke gevallen wordt het systeem dienovereenkomstig aangepast. De knop wordt bijgewerkt naar &quot;Uitvoeren (3)&quot; om aan te geven dat drie pijpleidingen kunnen doorgaan.

1. De pijpleidingen beginnen lopend, en hun status wordt bijgewerkt in de **lijst van Pijpleidingen**.

## Pijpleidingen bewerken {#editing-pipelines}

U kunt geen pijpleiding uitgeven die loopt.

**om pijpleidingen uit te geven:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, navigeer aan de **Pijpleidingen** kaart.

1. Klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u wilt uitgeven, dan klikken **geeft** uit.

1. In **geeft de Pijpleiding van de Productie uit** of **geeft niet-Productie pijplijn** dialoogdoos uit, kunt u de zelfde details uitgeven die u tijdens pijpleidingsverwezenlijking inging.

   Zie [&#x200B; het Vormen de Pijpleidingen van de Productie &#x200B;](/help/using/production-pipelines.md) en [&#x200B; het Vormen niet-Productiepijpleidingen &#x200B;](/help/using/non-production-pipelines.md) voor details op de gebieden en configuratieopties beschikbaar voor pijpleidingen.

1. Wanneer u wordt gedaan, klik **Update**.

## Pijpleidingen verwijderen {#deleting-pipelines}

U kunt geen lopende pijpleiding schrappen.

**om pijpleidingen te schrappen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, navigeer aan de **Pijpleidingen** kaart.

1. Klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt, dan **Schrapping** klikken.


## Details van pijpleiding weergeven {#view-details}

U kunt details van een pijpleiding slechts bekijken die loopt of minstens eens in werking is gesteld.

**om pijpleidingsdetails te bekijken:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, navigeer aan de **Pijpleidingen** kaart.

1. Klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de pijpleiding die u in werking stelt, dan klik **Details van de Mening**.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![&#x200B; details van de Pijpleiding &#x200B;](/help/assets/configure-pipelines/pipeline-running-details.png)

Van hier, kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie de plaatsing van de code van het document [&#128279;](/help/using/code-deployment.md) voor meer informatie.

Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

Wanneer een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

![&#x200B; Overzicht van de Stap &#x200B;](/help/assets/configure-pipelines/pipeline-step.png)

Klik de **verbinding van de Details van de Mening** om de **sectie van de Duur** te openbaren. In dit deel wordt de gemiddelde duur van de pijpleiding vermeld op basis van de historische trend voor dat programma.

![&#x200B; Duur &#x200B;](/help/assets/configure-pipelines/duration.png)

Als uw pijpleiding a **Code Scanning** stap bevatte, die kwesties opriep, kunt u **Details van de Download** klikken om een lijst van [&#x200B; tests van de codekwaliteit &#x200B;](/help/using/code-quality-testing.md) te bekijken die niet overgegaan.

![&#x200B; de kwaliteitskwesties van de Code &#x200B;](assets/managing-pipelines-code-quality-issues.png)

De kolom van de Plaats van het Dossier van het A **Project** is beschikbaar in het Csv- dossier om op de plaats van de beledigende code te wijzen. Deze kolom is de project-relatieve weg, terwijl de **kolom van de Plaats van het 0&rbrace; Dossier &lbrace;wordt geproduceerd.**

![&#x200B; van het de aftasten van de code van het Project details &#x200B;](assets/managing-pipelines-code-quality-details.png)
