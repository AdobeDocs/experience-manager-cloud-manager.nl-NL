---
title: Alleen werkgebied- en alleen-prod-pijplijnen
description: Leer hoe u het opvoeren en productielokaties kunt verdelen gebruikend specifieke pijpleidingen.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 70b7994435f7f0f587c134fab1fb66c6576386d9
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Pijpleidingen die uitsluitend bestemd zijn voor de productie van fase {#stage-prod-only}

Leer hoe u het opvoeren en productielokaties kunt verdelen gebruikend specifieke pijpleidingen.

>[!NOTE]
>
>Deze eigenschap is slechts beschikbaar aan [ het vroege adoptieprogramma ](/help/release-notes/current.md#early-adoption).

## Overzicht {#overview}

Staging- en productieomgevingen zijn nauw aan elkaar gekoppeld. Door gebrek, worden de plaatsingen aan hen verbonden aan één enkele pijpleiding. Dat wil zeggen, een plaatsingspijpleiding aan zowel de het opvoeren als productiemilieu&#39;s in dat programma opstelt. Hoewel deze koppeling normaal gesproken geschikt is, zijn er bepaalde gevallen waarin er nadelen zijn:

* Als u aan stadium-slechts wilt opstellen, verwerpt u **bevorderen aan Prod** stap in de pijpleiding. De uitvoering wordt echter gemarkeerd als geannuleerd.
* Als u de recentste code in een het opvoeren milieu aan productie wilt opstellen, moet u de volledige pijpleiding met inbegrip van de het opvoeren plaatsing opnieuw opstellen alhoewel geen code daar werd veranderd.
* De milieu&#39;s kunnen niet tijdens plaatsingen worden bijgewerkt. Als u de testomgeving enkele dagen lang pauzeert voordat u de productie promoot, blijft de productieomgeving vergrendeld en kan deze niet worden bijgewerkt. Dit scenario maakt niet-afhankelijke taken zoals het bijwerken van [ milieuvariabelen ](/help/getting-started/build-environment.md#environment-variables) onmogelijk.

De fase-slechts en prod-slechts pijpleidingen bieden oplossingen aan deze gebruiksgevallen door specifieke plaatsingsopties te verstrekken.

* **stadium-slechts de Pijpleidingen van de Plaatsing:** stelt slechts aan een het opvoeren milieu met de uitvoering op die eindigt zodra de plaatsing en de tests worden gedaan. Een alleen-fase pijpleiding gedraagt zich identiek aan de standaard gekoppelde volledige pijpleiding van de stapelprod maar zonder de stappen van de productieleiding (goedkeuring, programma, opstelling).
* **Prod-Enige Pijpleidingen van de Plaatsing:** stelt slechts aan productie op door een stadium te selecteren dat succesvol was. Dan het opstellen van zijn artefacten aan productie. Prod-enige pijpleidingen hergebruiken de artefacten van de werkgebiedplaatsing, die de bouwingsfase mijden.

De fase-slechts en prod-enige pijpleidingen worden niet uitgevoerd terwijl een volledig-stapelproductiepijplijn lopend is, en vice versa. Als zowel het stadium-slechts als de full-stack productiepijplijn de **gevormde trekker van de Veranderingen van het Git** hebben en aan de zelfde tak en de bewaarplaats richten, slechts wordt de stadium-enige pijpleiding automatisch begonnen. Pijpleidingen met alleen proxy&#39;s starten niet **`On Git Changes`** omdat deze niet rechtstreeks aan een opslagplaats zijn gekoppeld.

Prod-slechts pijpleidingen worden teweeggebracht manueel, aangezien zij niet direct met een bewaarplaats voor **op de Veranderingen van het Git** verbonden zijn.

Deze speciale pijpleidingen bieden meer flexibiliteit, maar u zou de volgende details van verrichting en aanbevelingen moeten noteren.

>[!NOTE]
>
>Pijpleidingen met alleen profielen maken altijd gebruik van artefacten uit de pijpleiding met alleen het werkgebied. Dit proces is nog steeds van toepassing, ook al heeft de standaard gekoppelde productiepijpleiding intussen iets anders ingezet.
>
>* Bijvoorbeeld scenario&#39;s kunnen leiden tot ongewenste terugdraaiversies van code.
>* De Adobe beveelt aan om de standaard gekoppelde productiepijpleiding niet meer te gebruiken zodra u begint met het gebruik van de pijpleidingen met alleen maar een fase en alleen een fase.
>* Als u nog steeds besluit om zowel de standaard gekoppelde pijpleidingen als de pijpleidingen met alleen fase/fase uit te voeren, dient u rekening te houden met het hergebruik van artefacten om terugdraaiversies van code te voorkomen.

## Pipetontwerp {#pipeline-creation}

Prod-slechts en stadium-enige pijpleidingen worden gecreeerd op een gelijkaardige manier aan de standaard gekoppelde [ productiepijpleidingen ](/help/using/production-pipelines.md) en [ niet productiepijpleidingen ](/help/using/non-production-pipelines.md). Zie deze documenten voor meer informatie.

1. In het **venster van Pijpleidingen**, klik **toevoegen Pijpleiding**.

   * Selecteer **toevoegen niet-ProductiePijpleiding** om een stadium-slechts pijpleiding tot stand te brengen.
   * Selecteer **Voeg de Uitrusting van de Productie slechts Pijpleiding** toe om een pro-enige pijpleiding tot stand te brengen.

   ![ Creërend een prod/stadium-enige pijpleiding ](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Bepaalde opties kunnen grijs worden weergegeven als de desbetreffende pijpleidingen al bestaan.
>
>* **voeg slechts de Pijpleiding van de Productie** toe is niet beschikbaar als een stadium-enige pijpleiding nog niet bestaat.
>* **voeg de Pijpleiding van de Productie** toe is niet beschikbaar als een standaard gekoppelde pijpleiding reeds bestaat.
>* Per programma zijn slechts één pijpleiding met alleen maar een fase en één pijpleiding toegestaan.

### Pijpleidingen met alleen werkgebied {#stage-only}

1. Zodra u **selecteert voeg niet-ProductiePipeline** optie toe, **voegt niet-ProductiePijl** dialoogdoos toe opent.
1. Om een stadium-enige pijpleiding tot stand te brengen, selecteer het werkgebiedmilieu in het **In aanmerking komende gebied van de Milieu van de Plaatsing** voor uw pijpleiding. Voltooi de resterende gebieden en klik **verdergaan**.

   ![ Creërend een stadium-enige pijpleiding ](/help/assets/configure-pipelines/stage-only.png)

1. Op het **Testen van het Stadium** lusje, kunt u het testen dan bepalen die in het het opvoeren milieu zou moeten worden uitgevoerd. Klik **sparen** om uw nieuwe pijpleiding te bewaren.

   ![ de parameters van de Test voor een stadium-enige pijpleiding ](/help/assets/configure-pipelines/stage-only-test.png)

### Pijpleidingen met alleen propaan {#prod-only}

1. Zodra u **selecteert voeg slechts de optie van de Pijl van de Productie** toe, **voeg slechts de dialoogdoos van de Pijl van de Productie toe** opent.
1. Verstrek de Naam van de a **Pijpleiding**. De resterende opties en functionaliteit van het dialoogvenster werken op dezelfde manier als de opties in het standaard dialoogvenster voor het maken van gekoppelde pijplijnen. Klik **sparen** om de pijpleiding te bewaren.

   ![ Creërend een productie-enige pijpleiding ](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Pijpleidingen met alleen profielen en alleen met werkruimten {#running}

Prod-slechts en stadium-enige pijpleidingen worden in werking gesteld op de zelfde manier als [ alle andere pijpleidingen in werking gesteld ](/help/using/managing-pipelines.md#running-pipelines). Zie die documentatie voor meer informatie.

Daarnaast kan een pijpleiding met alleen de mogelijkheid van een fase rechtstreeks worden geactiveerd vanaf de uitvoeringsdetails van een pijpleiding met alleen het werkgebied.

### Pijpleidingen met alleen werkgebied {#stage-only-run}

Een pijpleiding met alleen trapsgewijze uitloop loopt vrijwel op dezelfde manier als standaard gekoppelde pijpleidingen. Nochtans, aan het eind van de looppas, na de het testen stappen, bevordert a **bouwstijl** knoop verschijnt. Met deze knop kunt u een pijplijnuitvoering met alleen de mogelijkheid tot voorspelling starten met behulp van de artefacten die in het werkgebied zijn geïmplementeerd en deze in productie implementeren.

![ werkgebied-enige pijpleiding loopt ](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

**bevordert bouw** knoop slechts verschijnt als u op de recentste succesvolle stadium-enige pijpleidingsuitvoering bent. Zodra geklikt, vraagt het u om de looppas van de pro-enige pijpleiding te bevestigen of een pro-enige pijpleiding tot stand te brengen als er niet reeds bestaat.

### Pijpleidingen met alleen propaan {#prod-only-run}

Voor pijpleidingen met alleen modi is het belangrijk de bronartefacten te identificeren die voor de productie moeten worden gebruikt. Deze details kunnen in de **stap van de Voorbereiding van 0} Artefact worden gevonden.** U kunt naar die uitvoeringen navigeren voor meer details en logboeken.

![ details Artefact ](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
