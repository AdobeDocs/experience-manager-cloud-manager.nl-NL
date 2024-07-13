---
title: Niet-productiepijpleidingen configureren
description: Leer hoe u Cloud Manager kunt gebruiken om niet-productiepijpleidingen te maken en te configureren voor de implementatie van uw code.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# Niet-productiepijpleidingen configureren {#configuring-non-production-pipelines}

Leer hoe u Cloud Manager kunt gebruiken om niet-productiepijpleidingen te maken en te configureren voor de implementatie van uw code. Als u eerst een meer conceptueel overzicht van zou willen hoe de pijpleidingen in Cloud Manager werken, te zien gelieve het document [ CI/CD Pijpleidingen.](/help/overview/ci-cd-pipelines.md)

## Overzicht {#overview}

Gebruikend de **Pijpleidingen** tegel in [!UICONTROL Cloud Manager], kan de **Manager van de Plaatsing** tot twee verschillende soorten pijpleidingen leiden.

* **de Pijpleidingen van de Productie** - De productiepijpleidingen van A zijn een doelgerichte pijpleiding die van een reeks georkestreerde stappen wordt gemaakt om broncode helemaal in productie te nemen.
* **niet-Productiepijpleidingen** - een niet productiepijplijn dient hoofdzakelijk code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

Dit document richt zich op niet-productiepijpleidingen. Voor details op hoe te om productiepijpleidingen te vormen zie het document [ Vormend de Pijpleidingen van de Productie.](/help/using/production-pipelines.md)

Er zijn twee soorten niet-productiepijpleidingen:

* **Pijpleidingen van de Kwaliteit van de Code** - Deze in werking gestelde codekwaliteit scant op de code in een git tak en voert de bouw en de stappen van de codekwaliteit uit.
* **Pijpleidingen van de Plaatsing** - naast het uitvoeren van de bouw en de stappen van de codekwaliteit zoals de pijpleidingen van de codekwaliteit, stellen deze pijpleidingen de code aan een niet productiemilieu op.

>[!NOTE]
>
>Een pijpleiding kan niet opstelling zijn tot zijn bijbehorende git bewaarplaats minstens één tak heeft en [ programmaopstelling ](/help/getting-started/program-setup.md) is volledig. Zie het document [ Opslagplaatsen van Cloud Manager ](/help/managing-code/managing-repositories.md) leren hoe te om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

## Een niet-productiepijpleiding toevoegen {#add-non-production-pipeline}

Zodra u opstelling uw programma hebt en minstens één milieu gebruikend Cloud Manager UI, bent u bereid om een niet productiepijplijn toe te voegen door deze stappen te volgen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com) en selecteert de aangewezen organisatie en het programma.

1. Open de Pipelinekaart van het homescherm van Cloud Manager. Klik op **toevoegen** en selecteren **toevoegen niet-ProductiePijpleiding**.

   ![ voeg niet-productiepijpleiding ](/help/assets/configure-pipelines/nonprod-pipeline-add1.png) toe

1. Op het **lusje van de Configuratie** van **voeg de dialoog van de Pijl van de Niet-Productie** toe, selecteer het type van pijpleiding u wilt creëren, of a **de Pijl van de Kwaliteit van de Code** of a **Pijpleiding van de Plaatsing**.

   ![ kies pijpleidingstype ](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Verstrek een beschrijving voor uw pijpleiding in het **gebied van de Naam van de Pijpleiding van de Niet-Productie**.

1. Als u verkoos om a **Pijpleiding van de Plaatsing toe te voegen**, selecteer het milieu van de doelplaatsing van **In aanmerking komende Milieu&#39;s van de Plaatsing** dropdown.

1. Verstrek de bewaarplaats waar de pijpleiding de code zou moeten terugwinnen.

   * **Bewaarplaats** - Deze opties bepalen waarvan git repo de pijpleiding de code zou moeten terugwinnen.
   * **de Tak van het Git** - deze optie bepaalt van welke tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.

1. Definieer uw implementatieopties.

   1. Onder **Trigger van de Plaatsing**, bepaal welke gebeurtenis de pijpleiding activeert.

      * **Handboek** - gebruik deze optie om de pijpleiding manueel te beginnen.
      * **op de Veranderingen van het Git** - Deze opties beginnen de pijpleiding wanneer de begaat aan de gevormde git tak worden toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

   1. Voor plaatsingspijpleidingen, onder **Belangrijk Metrisch Gedrag van Mislukt**, bepaal het gedrag van de pijpleiding wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet.

      * **vraag telkens als** - dit is het gebrek plaatsend en vereist handinterventie op om het even welke belangrijke mislukking.
      * **onmiddellijk het Eindigen** - als geselecteerd, zal de pijpleiding worden geannuleerd wanneer een belangrijke mislukking voorkomt. Dit is in feite het emuleren van een gebruiker die elke fout handmatig afwijst.
      * **gaat onmiddellijk** - als geselecteerd, zal de pijpleiding automatisch te werk wanneer een belangrijke mislukking voorkomt. Dit emuleert hoofdzakelijk een gebruiker manueel goedkeurend elke mislukking.

   1. **de Configuratie van Dispatcher** - de **rol van de Manager van de Plaatsing** kan een reeks inhoudspaden vormen die of van het geheime voorgeheugen van AEM Dispatcher ongeldig zullen worden gemaakt of zullen worden gespoeld wanneer een pijpleiding in werking wordt gesteld. Deze geheim voorgeheugenacties zullen als deel van de stap van de plaatsingspijpleiding worden uitgevoerd, enkel nadat om het even welke inhoudspakketten worden opgesteld. Bij deze instellingen wordt standaard AEM Dispatcher-gedrag gebruikt. Om te vormen:

      1. Onder **PAD** verstrekt een inhoudspad.
      1. Onder **TYPE**, selecteer de actie die op die weg moet worden genomen.

         * **Flush** - voer een geheim voorgeheugenschrapping uit.
         * **ongeldig maakt** ongeldig - voer een geheim voorgeheugenbevestiging uit, gelijkend op wanneer de inhoud van een auteursinstantie aan een het publiceren instantie wordt geactiveerd.
      1. Klik **toevoegen Weg** om uw gespecificeerde weg toe te voegen. U kunt maximaal 100 paden per omgeving toevoegen.

1. Klik **sparen** om uw pijpleiding te bewaren.

## De volgende stappen {#the-next-steps}

Zodra u de pijpleiding hebt gevormd, moet u uw code opstellen. Gelieve te zien de plaatsing van de code van het document [ ](/help/using/code-deployment.md) voor meer details.

## Videozelfstudie {#video-tutorial}

Deze video biedt een overzicht van het proces voor het maken van pijpleidingen, dat in dit document wordt beschreven.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
