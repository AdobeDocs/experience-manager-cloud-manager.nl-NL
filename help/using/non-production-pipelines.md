---
title: Een niet-productiepijplijn toevoegen
description: Leer hoe u Cloud Manager kunt gebruiken om niet-productiepijpleidingen te maken en te configureren voor de implementatie van uw code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 2a022c10ce64bb42d4bffd63bea01de25af0bd41
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 0%

---

# Een niet-productiepijpleiding toevoegen {#configuring-non-production-pipelines}

Leer hoe u Cloud Manager kunt gebruiken om niet-productiepijpleidingen te maken en te configureren voor de implementatie van uw code. Als u eerst een meer conceptueel overzicht van zou houden hoe de pijpleidingen in Cloud Manager werken, zie [&#x200B; CI/CD Pijpleidingen &#x200B;](/help/overview/ci-cd-pipelines.md).

## Overzicht {#overview}

Gebruikend de **Pijpleidingen** tegel in [!UICONTROL Cloud Manager], kan de **Manager van de Plaatsing** tot twee verschillende soorten pijpleidingen leiden.

* **de Pijpleidingen van de Productie** - De productiepijpleidingen van A zijn een doelgerichte pijpleiding die van een reeks georkestreerde stappen wordt gemaakt om broncode helemaal in productie te nemen.
* **niet-Productiepijpleidingen** - een niet productiepijplijn dient hoofdzakelijk code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

Dit document richt zich op niet-productiepijpleidingen. Voor details op hoe te om productiepijpleidingen te vormen zie het document [&#x200B; Vormend de Pijpleidingen van de Productie &#x200B;](/help/using/production-pipelines.md).

Er zijn twee soorten niet-productiepijpleidingen:

* **Pijpleidingen van de Kwaliteit van de Code** - Deze in werking gestelde codekwaliteit scant op de code in een tak van het Git en voert de bouw en de stappen van de codekwaliteit uit.
* **Pijpleidingen van de Plaatsing** - samen met het uitvoeren van de bouw en de stappen van de codekwaliteit zoals de pijpleidingen van de codekwaliteit, stellen deze pijpleidingen ook de code aan een niet productiemilieu op.

>[!NOTE]
>
>Een pijpleiding kan niet opstelling zijn tot zijn bijbehorende bewaarplaats van het Git minstens één tak heeft en [&#x200B; programmaopstelling &#x200B;](/help/getting-started/program-setup.md) is volledig. Zie [&#x200B; Opslagplaatsen van Cloud Manager &#x200B;](/help/managing-code/managing-repositories.md) leren om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

## Een nieuwe niet-productiepijplijn toevoegen {#add-non-production-pipeline}

Nadat u een programma en minstens één omgeving hebt ingesteld in de gebruikersinterface van Cloud Manager, kunt u niet-productiepijpleidingen toevoegen. Gebruik deze pijpleidingen om uw codekwaliteit te testen alvorens u aan productiemilieu&#39;s opstelt.

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com) en selecteert de aangewezen organisatie en het programma.

1. Open de Pipelinekaart van het homescherm van Cloud Manager. Klik **toevoegen**, dan uitgezocht **voeg niet-Productiepijpleiding** toe.

   ![&#x200B; voeg niet-productiepijpleiding &#x200B;](/help/assets/configure-pipelines/nonprod-pipeline-add1.png) toe

1. Op het **lusje van de Configuratie** van **voeg niet-Productie Pijpleiding** dialoogdoos toe, selecteer het type van pijpleiding u, of één van het volgende wilt tot stand brengen:

   * **Pijpleiding van de Kwaliteit van de Code** - creeert een pijpleiding die de code bouwt, eenheidstests in werking stelt, en codekwaliteit evalueert zonder aan een milieu op te stellen.
   * **Pijpleiding van de Plaatsing** - creeert een pijpleiding die de code bouwt, eenheidstests in werking stelt, codekwaliteit evalueert, en aan een milieu opstelt.

   ![&#x200B; kies pijpleidingstype &#x200B;](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB  Pijpleiding van de Kwaliteit van de Code - het lusje van de Configuratie ]

| Sectie | Optie | Beschrijving |
| --- | --- | --- |
| **Configuratie van de Pijpleiding** | **niet-productie Naam van de Pijpleiding** | Verstrek een beschrijving voor uw pijpleiding in het **gebied van de Naam van de Pijpleiding van de Niet-Productie**. |
|  | **het Testen** | Zichtbaar slechts wanneer het uitgeven van een niet productiepijplijn.<br> UI toont de het testen categorieën die de pijpleiding als deel van de bevestiging van de codekwaliteit loopt.<ul><li>**Statische het Testen van de Code** - analyseert de code voor kwaliteit en correctiekwesties.<li>**het Testen van de Lading/van Prestaties** - evalueert prestaties betrekking hebbend gedrag als deel van pijpleiding het testen.<li>**het Testen van de Veiligheid** - Controleert de code en pijpleidingsoutput voor veiligheid-verwante kwesties. |
| **de Opties van de Plaatsing** | **Trigger van de Plaatsing** | <ul><li>**Handboek** - laat u manueel de pijpleiding beginnen.<li>**op de Veranderingen van het Git** - begint de pijpleiding wanneer de begaat aan de gevormde tak van het Git worden toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel, zoals vereist beginnen. |
|  | **Belangrijk Metrisch Gedrag van Mislukt** | <ul><li>**vraag telkens als** - dit gedrag is het gebrek plaatsend en vereist handinterventie op om het even welke belangrijke mislukking.<li>**Geëindig onmiddellijk** - als geselecteerd, wordt de pijpleiding geannuleerd wanneer een belangrijke mislukking voorkomt. In feite emuleert het een gebruiker handmatig elke fout.<li>**gaat onmiddellijk** voort - als geselecteerd, gaat de pijpleidingsprocedure automatisch wanneer een belangrijke mislukking voorkomt. In feite emuleert het een gebruiker handmatig die elke fout goedkeurt.</li></ul> |
|  | **keurt na de controledoos van de Plaatsing van het Stadium goed** | Zichtbaar slechts wanneer het uitgeven van een niet productiepijplijn.<br> selecteer deze optie om goedkeuring na plaatsing aan het werkgebiedmilieu te vereisen alvorens de pijpleiding kan verdergaan. Als deze optie niet wordt geselecteerd, blijft de pijpleiding gebaseerd op het gevormde gedrag verdergaan. |

>[!TAB  Pijpleiding van de Plaatsing - het lusje van de Configuratie ]

| Sectie | Optie | Beschrijving |
| --- | --- | --- |
| **Configuratie van de Pijpleiding** | **niet-productie Naam van de Pijpleiding** | Verstrek een beschrijving voor uw pijpleiding in het **gebied van de Naam van de Pijpleiding van de Niet-Productie**. |
|   | **In aanmerking komende Milieu van de Plaatsing** | Als uw pijpleiding een plaatsingspijpleiding is, moet u selecteren welke milieu&#39;s waar Cloud Manager de code opstelt. |
|   | **het Testen** | Zichtbaar slechts wanneer het uitgeven van een niet productiepijplijn.<br> UI toont de het testen categorieën die de pijpleiding als deel van de bevestiging van de codekwaliteit loopt.<ul><li>**Statische het Testen van de Code** - analyseert de code voor kwaliteit en correctiekwesties.<li>**het Testen van de Lading/van Prestaties** - evalueert prestaties betrekking hebbend gedrag als deel van pijpleiding het testen.<li>**het Testen van de Veiligheid** - Controleert de code en pijpleidingsoutput voor veiligheid-verwante kwesties.</li></ul> |
| **de Opties van de Plaatsing** | **Trigger van de Plaatsing** | <ul><li>**Handboek** - laat u manueel de pijpleiding beginnen.<li>**op de Veranderingen van het Git** - begint de pijpleiding wanneer de begaat aan de gevormde tak van het Git worden toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel, zoals vereist beginnen. |
|   | **Belangrijk Metrisch Gedrag van Mislukt** | <ul><li>**vraag telkens als** - het gebrek dat en zet de gebruiker ertoe aan om te beslissen hoe te te te werk gaan wanneer belangrijke metrisch ontbreekt.<li>**onmiddellijk het Eindigen** - de pijpleiding wordt geannuleerd wanneer belangrijke metrisch ontbreekt. In feite emuleert het een gebruiker handmatig elke fout af.<li>**gaat onmiddellijk** voort - de pijpleiding gaat automatisch wanneer belangrijke metrisch ontbreekt. Het emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.</li></ul> |
|  | **keurt na de controledoos van de Plaatsing van het Stadium goed** | Zichtbaar slechts wanneer het uitgeven van een niet productiepijplijn.<br> selecteer deze optie om goedkeuring na plaatsing aan het werkgebiedmilieu te vereisen alvorens de pijpleiding kan verdergaan. Als deze optie niet wordt geselecteerd, blijft de pijpleiding gebaseerd op het gevormde gedrag verdergaan. |
|  | **Skip de veranderingen van de Balancer van de Lading** controledoos | Selecteer deze optie om te voorkomen dat de pijplijn tijdens de implementatie wijzigingen aanbrengt in het taakverdelingsmechanisme. |
|  | **Configuratie van Dispatcher** | De **rol van de Manager van de Plaatsing** kan een reeks inhoudspaden vormen die of ongeldig worden gemaakt of van het geheime voorgeheugen van AEM Dispatcher leeggemaakt wanneer een pijpleiding in werking wordt gesteld. Deze geheim voorgeheugenacties worden uitgevoerd als deel van de stap van de plaatsingspijpleiding, enkel nadat om het even welke inhoudspakketten worden opgesteld. Deze instellingen maken gebruik van de standaard AEM Dispatcher-functionaliteit. Ga als volgt te werk om `Dispatcher` te configureren:<ul><li>Onder **PAD**, verstrek een inhoudspad dat u de pijpleiding wilt leegmaken of ongeldig maken.<li>Onder **TYPE**, selecteer de actie die op die weg moet worden genomen.<ul><li>**Duw** - voer een geheim voorgeheugenschrapping op de gespecificeerde weg uit.</li><li>**ongeldig maakt** ongeldig - voer een geheim voorgeheugenbevestiging uit, gelijkend op wanneer de inhoud van een auteursinstantie aan een het publiceren instantie wordt geactiveerd.</li><li>Klik **toevoegen Weg** om uw gespecificeerde weg toe te voegen. U kunt maximaal 100 paden per omgeving toevoegen.</li></ul> |
| **Pijpleiding** | **controledoos van de Controle van de Ervaring 0&rbrace;** | Selecteer deze optie om een stap van de Controle van de Ervaring in de pijpleiding op te nemen. Wanneer toegelaten, omvat de pijpleiding de stap van de Controle van de Ervaring na de Code van Source tabel. |

>[!ENDTABS]

1. In de laag-juiste hoek van **voeg niet-Productie pijplijn** dialoogdoos toe, gaat de klik **&#x200B;**&#x200B;verder.
1. Selecteer het type van code de pijpleiding wordt gevormd om te bouwen en op te stellen.

>[!BEGINTABS]

>[!TAB  het lusje van de Code van Source - Volledige Code van de Stapel ]

Implementeert de volledige AEM-toepassing, inclusief de toepassingscode en standaard de configuratie van de weblaag.

| Sectie | Optie | Beschrijving |
| --- | --- | --- |
| **code van Source** | **Bewaarplaats** | Van de drop-down lijst, kies de bewaarplaats van het Git die de pijpleiding als zijn bron gebruikt. Cloud Manager bouwt code van de bewaarplaats die u hier kiest. |
|   | **de Tak van de Git** | Van de drop-down lijst, kies welke tak in de geselecteerde bewaarplaats de pijpleiding van zou moeten bouwen. De standaardwaarde is `main` . De pijpleiding gebruikt de gekozen tak als bron voor bouw en plaatsing. Indien nodig, verfrist de klik **&#x200B;**&#x200B;om de lijst van beschikbare takken voor de geselecteerde bewaarplaats bij te werken. Gebruik deze optie als een recent gemaakte vertakking niet in de lijst voorkomt. |
|   | **bouwt Strategie** | <ul><li>**Volledig bouwt** - bouwt alle modules in de bewaarplaats telkens<li>BETA **Smart bouwt** - bouwt slechts modules die sinds laatste zijn veranderd begaat.<br> leer meer over [&#x200B; gebruikend Slim bouwt in een niet productiepijpleiding &#x200B;](#about-smart-build).</li></ol>**Belangrijk**: De slimme Bouwstijl is beschikbaar slechts voor de pijpleidingen van de Kwaliteit van de Code van de Code van de Code van de Code van de Code van de Code van de Code en Dev de volledige plaatsingspijpleidingen. |
|   | **negeren de controledoos van de Configuratie van de Rij van het Web** | Selecteer deze optie om plaatsing van de configuratie van de Webrij in een Volledige codepijpleiding van de Stapel over te slaan. Laat de optie uitgeschakeld als u de configuratie van de weblaag samen met de code van de pijpleiding wilt implementeren. |
| **Pijpleiding** | **controledoos van de Controle van de Ervaring 0&rbrace;** | Selecteer deze optie om een stap van de Controle van de Ervaring in de pijpleiding op te nemen. Wanneer toegelaten, omvat de pijpleiding de stap van de Controle van de Ervaring na de Code van Source tabel. |

>[!TAB  Code Source - de Rij Config van het Web ]

Implementeert alleen weblaagconfiguratie, zoals Dispatcher-eigenschappen die worden gebruikt voor het opslaan, verwerken en leveren van webpagina&#39;s aan de client. Wanneer u **Configuratie van de Rij van het Web** selecteert, leidt Cloud Manager tot een pijpleiding specifiek aan de plaatsing van de Webrijconfiguratie.

Als een volledige stapelpijpleiding reeds bestaat, toont Cloud Manager een bericht dat het creëren van een de configuratiepijplijn van de Webrij de bestaande volledige stapelpijpleiding veroorzaakt om Web rijconfiguratie te negeren. Nadat u de de configuratiepijplijn van de Webrij creeert, beheert Cloud Manager de plaatsingen van de Webrijconfiguratie door die pijpleiding in plaats van de volledige stapelpijpleiding.

| Sectie | Optie | Beschrijving |
| --- | --- | --- |
| **code van Source** | **Bewaarplaats** | Selecteer in de vervolgkeuzelijst de Git-opslagplaats die de configuratie van de weblaag bevat. |
|   | **de Tak van de Git** | Selecteer de vertakking in de gekozen opslagplaats die Cloud Manager voor de implementatie gebruikt. Indien nodig, verfrist de klik **&#x200B;**&#x200B;om de lijst van beschikbare takken voor de geselecteerde bewaarplaats bij te werken. Gebruik deze optie als een recent gemaakte vertakking niet in de lijst voorkomt. |
|   | **Plaats van de Code** | Voer het pad in de geselecteerde opslagplaats in dat de weblaagconfiguratie bevat die u wilt implementeren. De standaardplaats is de bewaarplaatswortel (`/`). |

>[!ENDTABS]

1. Klik **sparen**.

## Het gebruiken van Slimme bouwt in een niet productiepijpleiding{#about-smart-build}

**Slimme Bouwstijl** in Cloud Manager is een geoptimaliseerde bouwstijlstrategie voor niet-productiepijpleidingen. De slimme Bouwstijl vermindert bouwstijltijden door modules in het voorgeheugen onder te brengen en slechts die modules te herbouwen die sinds de laatste succesvolle looppas zijn veranderd. Ongewijzigde modules worden opnieuw gebruikt vanuit cache, terwijl alleen de gewijzigde modules en hun afhankelijkheden worden herbouwd, waardoor de efficiëntie voor iteratieve ontwikkelingsworkflows wordt verbeterd.

Smart Build is momenteel alleen beschikbaar voor:

* Pijpleidingen voor codekwaliteit.
* Ontwikkelen van volledige-stapeldistributiepijpleidingen.

>[!NOTE]
>
>De eerste run na het inschakelen van Smart Build gedraagt zich als een Full Build omdat de cache leeg is.

Slimme build wordt aangeraden als u het volgende doet:
* U ontwikkelt en begaat actief frequente incrementele wijzigingen.
* Uw project bevat meerdere Geweven modules.
* Volledige builds nemen veel tijd in beslag.

De slimme Bouwstijl is niet altijd ideaal wanneer u het volgende hebt:
* Uw build is sterk afhankelijk van plug-ins die bewerkingen uitvoeren buiten de afhankelijkheidsgrafiek van Maven.
* U hebt bij elke uitvoering volledige validatie voor opnieuw samenstellen nodig.

### Werken met prestaties bij het bouwen{#smart-build-performance}

De prestatieswinst van het gebruiken van Slimme bouwt hangt van verscheidene factoren met inbegrip van het volgende af:

* Het aantal modules in het project.
* De frequentie en het bereik van code veranderen.
* De verdeling van gebiedsdelen over modules.

Over het algemeen, kunnen de projecten met vele onafhankelijke modules de grootste verbetering zien.

### Optie voor cache per module{#smart-build-cache-optout}

De slimme Bouwstijl verstrekt fijnkorrelige controle die u caching voor specifieke modules laat onbruikbaar maken. Dit is handig wanneer bepaalde modules:

* Gebruik plug-ins, zoals `exec-maven-plugin` of `maven-antrun-plugin` .
* Bestandsbewerkingen uitvoeren die niet worden bijgehouden door Geweven afhankelijkheden.
* Zorg voor inconsistente resultaten wanneer u de cache plaatst.

### caching uitschakelen voor een module{#smart-build-disable-caching}

U kunt de volgende eigenschap toevoegen aan het bestand `pom.xml` van de desbetreffende module:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Deze syntaxis dwingt de module om op elke pijpleidingsuitvoering opnieuw op te bouwen terwijl andere modules van caching blijven profiteren.

### Beperkingen en overwegingen bij het gebruik van Smart Build{#smart-build-limitations}

Houd rekening met het volgende wanneer u Slim bouwen gebruikt:

* Smart Build is afhankelijk van Maven-afhankelijkheidsanalyse.
* De veranderingen buiten de gebiedsdeelgrafiek kunnen rebuilds niet teweegbrengen.
* Sommige plug-ins zijn mogelijk niet volledig compatibel met caching.
* U kunt terug naar **Volledige Bouwstijl** op elk ogenblik schakelen door de niet productiepijpleiding uit te geven.

Als u onverwacht bouwt gedrag ontmoet, denk na onbruikbaar makend caching voor specifieke modules of tijdelijk het schakelen van uw bouwstijlstrategie aan **Hoogtepunt bouwt**.

### Problemen met Smart Build oplossen{#smart-build-troubleshoot}

| Probleem | Voorgestelde oplossingen |
| --- | --- |
| Buildresultaten zijn inconsistent | ・ Het in cache plaatsen van betrokken modules uitschakelen.<br>・ Het gedrag van de insteekmodule controleren (met name `exec`/`antrun` insteekmodules). |
| Geen prestatieverbetering | ・ Zorg ervoor dat de veelvoudige looppas (geheim voorgeheugen opwarmen) voorkwam.<br>・ Controleer als de meeste modules vaak veranderen. |
| Onverwachte artefacten of ontbrekende wijzigingen | ・ Herzie of de veranderingen buiten Gemaakt gebiedsdeel volgen zijn.<br>・ Gebruik **Volledig bouwt** voor controle. |

Zie [&#x200B; een niet-productiepijplijn &#x200B;](#add-non-production-pipeline) toevoegen toelaat Smart bouwt.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## De volgende stappen {#the-next-steps}

Nadat u de pijpleiding vormt, kunt u uw code opstellen. Zie [&#x200B; Plaatsing van de Code &#x200B;](/help/using/code-deployment.md) voor meer details.

## Videozelfstudie {#video-tutorial}

Deze video biedt een overzicht van het proces voor het maken van pijpleidingen, dat in dit document wordt beschreven.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
