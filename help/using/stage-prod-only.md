---
title: Alleen werkgebied- en alleen-prod-pijplijnen
description: Leer hoe u het opvoeren en productielokaties kunt verdelen gebruikend specifieke pijpleidingen.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: c238caa22fdd71ae6aefd098331b626b9b951a0f
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Pijpleidingen, alleen voor de productie {#stage-prod-only}

Leer hoe u het opvoeren en productielokaties kunt verdelen gebruikend specifieke pijpleidingen.

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor [het programma voor vroegtijdige adoptie .](/help/release-notes/current.md#early-adoption)

## Overzicht {#overview}

Staging- en productieomgevingen zijn nauw aan elkaar gekoppeld. Door gebrek, worden de plaatsingen aan hen verbonden aan één enkele pijpleiding. Dat is een plaatsingspijpleiding aan zowel de het opvoeren als productiemilieu&#39;s in dat programma opstelt. Hoewel deze koppeling normaal gesproken geschikt is, zijn er bepaalde gevallen waarin er nadelen zijn:

* Als u alleen in het werkgebied wilt implementeren, kunt u dit alleen doen door het **Promoten naar product** stap in de pijplijn. De uitvoering wordt echter gemarkeerd als geannuleerd.
* Als u wenst om de recentste code in een het opvoeren milieu aan productie op te stellen, moet u de volledige pijpleiding met inbegrip van de het opvoeren plaatsing opnieuw opstellen alhoewel geen code daar werd veranderd.
* Aangezien omgevingen niet tijdens implementaties kunnen worden bijgewerkt, als u de testomgeving meerdere dagen wilt pauzeren en testen voordat u de productieomgeving promoot, kan de productieomgeving niet worden bijgewerkt. Hierdoor worden niet-afhankelijke taken zoals bijwerken [omgevingsvariabelen](/help/getting-started/build-environment.md#environment-variables) onmogelijk.

De fase-slechts en prod-slechts pijpleidingen bieden oplossingen aan deze gebruiksgevallen door specifieke plaatsingsopties te verstrekken.

* **Implementatiepijplijnen alleen in het werkgebied** Stel slechts in een het opvoeren milieu met de uitvoering in beëindigt zodra de plaatsing en de tests worden gedaan.
   * Een alleen-fase pijpleiding gedraagt zich identiek aan de standaard gekoppelde volledige pijpleiding van de stapelprod maar zonder de stappen van de productieleiding (goedkeuring, programma, opstelling).
* **Implementatie-pijplijnen (alleen op basis van profielen)** alleen implementeren in een productieomgeving met de optie om een met succes voltooide en gevalideerde uitvoering in het werkgebied te selecteren en de artefacten op de pod in te zetten.
   * Prod-enige pijpleidingen zullen de artefacten van de plaatsingen van het stadium hergebruiken, die de bouwfase overslaan.

Noch worden de stadium-enige noch de prod-enige pijpleidingen uitgevoerd terwijl een volledig-stapelproductiepijpleiding loopt en vice versa. Als zowel de productiepijpleiding voor de fase-alleen als de productiepijpleiding voor de volledige-stackfase **Wijzigingen in Git** trigger geconfigureerd en wijst naar dezelfde vertakking en opslagplaats, alleen de alleen-werkgebiedpijplijn wordt automatisch gestart. Er worden geen proefpijpleidingen gestart **Wijzigingen in Git** omdat ze niet rechtstreeks aan een opslagplaats zijn gekoppeld.

Deze speciale pijpleidingen bieden meer flexibiliteit, maar noteer de volgende details van de werking en aanbevelingen.

>[!NOTE]
>
>Pijpleidingen met alleen maar profielen gebruiken altijd de artefacten van de uitsluitend in het stadium gelegen pijpleiding, ongeacht wat er intussen via de standaard gekoppelde productiepijpleiding in het stadium is uitgezet.
>
>* Dit kan leiden tot ongewenste terugdraaiversies van code.
>* De Adobe beveelt aan om de standaard gekoppelde productiepijpleiding niet meer te gebruiken zodra u begint met het gebruik van de pijpleidingen met alleen maar een fase en alleen een fase.
>* Als u nog steeds besluit om zowel de standaard gekoppelde pijpleidingen als de pijpleidingen met alleen fase/fase uit te voeren, dient u rekening te houden met het hergebruik van artefacten om terugdraaiversies van code te voorkomen.

## Pipetontwerp {#pipeline-creation}

Pijpleidingen met alleen profielen en alleen trapsgewijze pijpleidingen worden op vergelijkbare wijze aangelegd als de standaard gekoppelde pijpleidingen [productiepijpleidingen](/help/using/production-pipelines.md) en [niet-productiepijpleidingen.](/help/using/non-production-pipelines.md) Zie deze documenten voor meer informatie.

1. In de **Pijpleidingen** venster, tikken of klikken **Pipet toevoegen**.

   * Selecteren **Niet-productiepijpleiding toevoegen** om een alleen-werkgebiedpijplijn te maken.
   * Selecteren **Uitsluitend productie toevoegen Pipet** om een pijplijn met alleen maar een pod te maken.

   ![Een pijplijn maken die alleen in het werkgebied kan worden weergegeven](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Bepaalde opties kunnen grijs worden weergegeven als de desbetreffende pijpleidingen al bestaan.
>
>* **Uitsluitend productie toevoegen Pipet** is niet beschikbaar als er nog geen pijpleiding bestaat die alleen in het werkgebied kan worden uitgevoerd.
>* **Productiepijpleiding toevoegen** niet beschikbaar als er al een standaard gekoppelde pijpleiding bestaat.
>* Per programma zijn slechts één pijpleiding met alleen maar een fase en één pijpleiding toegestaan.

### Alleen met werkgebied uitgeruste pijpleidingen {#stage-only}

1. Wanneer u de **Niet-productiepijpleiding toevoegen** de **Niet-productiepijpleiding toevoegen** wordt geopend.
1. Selecteer de werkgebiedomgeving in het deelvenster **In aanmerking komende implementatieomgevingen** veld voor uw pijpleiding. Vul de overige velden in en tik of klik op **Doorgaan**.

   ![Een alleen-werkgebiedpijplijn maken](/help/assets/configure-pipelines/stage-only.png)

1. Op de **Werkgebiedtests** kunt u vervolgens testen definiëren die moeten worden uitgevoerd in de testomgeving. Tik of klik op **Opslaan** om uw nieuwe pijpleiding te redden.

   ![Testparameters voor een alleen-werkgebiedpijpleiding](/help/assets/configure-pipelines/stage-only-test.png)

### Pijpleidingen, alleen met behulp van propaan {#prod-only}

1. Wanneer u de **Uitsluitend productie toevoegen Pipet** de **Uitsluitend productie toevoegen Pipet** wordt geopend.
1. Geef een **Naam pijpleiding**. De resterende opties en functionaliteit van het dialoogvenster werken hetzelfde als die in het standaarddialoogvenster voor het maken van gekoppelde pijplijnen. Tik of klik op **Opslaan** om de pijpleiding te redden.

   ![Een alleen voor de productie bestemde pijpleiding maken](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Uitvoeren van alleen-Prod en alleen-werkgebiedpijplijnen {#running}

Pijpleidingen met alleen maar profielen en alleen trapsgewijze pijpleidingen worden op dezelfde manier uitgevoerd als [alle andere pijpleidingen worden aangelegd.](/help/using/managing-pipelines.md#running-pipelines) Zie die documentatie voor meer informatie.

Daarnaast kan een pijpleiding met alleen de mogelijkheid van een fase rechtstreeks worden geactiveerd vanaf de uitvoeringsdetails van een pijpleiding met alleen het werkgebied.

### Alleen met werkgebied uitgeruste pijpleidingen {#stage-only-run}

Een pijpleiding met alleen trapsgewijze uitloop loopt vrijwel op dezelfde manier als standaard gekoppelde pijpleidingen. Na de teststappen echter wordt na de uitvoering een **Opbouwen bevorderen** staat u toe om een pro-enige pijpleidingsuitvoering te beginnen die de artefacten gebruikt die op stadium door deze uitvoering worden opgesteld en hen op productie opstelt.

![Uitvoeren van een alleen-werkgebiedpijpleiding](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

De **Opbouwen bevorderen** wordt alleen weergegeven als u op de meest recente, succesvolle uitvoering van de alleen-werkgebiedpijplijn bent. Nadat u op de pijplijn hebt getikt of erop hebt geklikt, wordt u gevraagd om de uitvoering van de alleen-lezen pijplijn te bevestigen of om een alleen-lezen pijplijn te maken als deze nog niet bestaat.

### Pijpleidingen, alleen met behulp van propaan {#prod-only-run}

Voor pijpleidingen die alleen voor de productie bestemd zijn, is het van belang de bronartefacten te identificeren die voor de productie zullen worden gebruikt. Deze gegevens vindt u in het dialoogvenster **Voorbereiding van artefact** stap. U kunt naar die uitvoeringen navigeren voor meer details en logboeken.

![Details van artefact](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
