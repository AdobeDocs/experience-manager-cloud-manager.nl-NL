---
title: Omgevingen bewaken
description: Leer hoe u uw omgevingen in Cloud Manager kunt bewaken.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---


# Monitoromgevingen {#monitoring-environments}

Leer hoe u uw omgevingen in Cloud Manager kunt bewaken.

## Metrische drempels {#thresholds}

Systeemcontrole in [!UICONTROL Cloud Manager] wordt uitgevoerd door de afzonderlijke instanties binnen een omgeving te observeren en een aantal verschillende meetgegevens voor elke instantie te volgen. Elke metrisch heeft twee bepaalde drempels: a *waarschuwings* drempel en a *kritieke* drempel.

Als een metrische waarde boven de waarschuwingsdrempel (maar onder de kritische drempel) ligt, wordt deze als een waarschuwingsstatus beschouwd.

Als metrisch zijn over zijn kritieke drempel is, wordt het beschouwd om in een kritieke staat te zijn.

Adobe Managed Services stelt de drempelwaarden in, die u kunt weergeven in [!UICONTROL Cloud Manager] . In de meeste gevallen zijn drempels consistent tussen klanten, maar er zijn gevallen waarin Adobe Managed Services drempelwaarden bewerkt om aan specifieke klantenvereisten te voldoen. Verricht om het even welke vragen die u over de drempels aan uw Ingenieur van het Succes van de Klant hebt (CSE).

## Toegangssysteemcontrole {#accessing-system-monitoring}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com) en selecteert de aangewezen organisatie en het programma.

1. Klik op de knop met de ellips van het programma dat u wilt controleren.
1. In het menu, onder **leidt** rubriek, klik **tonen Controle** om de **pagina van Rapporten** te openen die systeem controleinformatie toont.

   ![ Montages ](/help/assets/first-timea1.png)

.

## Overzicht van systeembewaking {#system-monitoring-overview}

De **sectie van de Controle van het Systeem** van de **pagina van Rapporten** maakt een lijst van de gecontroleerde milieu&#39;s in het programma. Zij rapporteert over hun gezondheid op hoog niveau in de volgende vier afzonderlijke categorieën:

* Host
* Opslag
* Netwerk
* Toepassing

De status in elke categorie is een overzicht van de afzonderlijke meetwaarden. Als om het even welke metrisch in een categorie in de kritieke staat is, is de volledige categorie in een kritieke staat ten behoeve van de overzichtspagina. Dezelfde samenvatting kan op milieuniveau en op instantieniveau worden bekeken.

![ Controle van het Systeem overzicht ](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Wanneer u naar deze pagina navigeert, zijn de exemplaren van de productieomgeving standaard zichtbaar, maar kunnen ook andere omgevingen worden weergegeven.

## System Monitoring Detail {#system-monitoring-detail}

Als u de details van bepaalde metriek wilt weergeven, klikt u op een van de categoriekolommen van een specifiek exemplaar of op de titel van de categorie in de linkernavigatie. Elke detailpagina bevat een reeks grafieken voor de meetgegevens in die categorie. U kunt de metriek voor alle instanties in een milieu of voor een specifieke instantie bekijken. U kunt schakelen tussen de omgeving en instanties met de vervolgkeuzelijsten in de rechterbovenhoek.

![ Uitgezochte milieu ](/help/assets/System_Monitoring1.png)

De navigatie op de linkerzijde toont de beschikbare metriek binnen de momenteel geselecteerde categorie waarvoor er gegevens voor de momenteel geselecteerde milieu en instanties zijn.

Een individuele grafiek toont de status en een grafiek van de gegevens in tijd samen met de drempels. Wanneer meerdere instanties worden weergegeven, bevinden de gegevens van elke instantie zich in een aparte reeks.

![ Grafiek van Metriek ](/help/assets/Monitoring_Graphs1.png)

Individuele reeksen kunnen op een grafiek worden verborgen door op de reeks in de legenda te klikken.
Als u bijvoorbeeld op de waarschuwingsdrempelreeks klikt, ziet u alleen de kritieke drempel.

![ wijzig grafiek ](/help/assets/Monitoring_Graphs2.png)

### Metrische definities {#metric-definitions}

#### Host {#host}

* **Lading per Kern**: Het aantal processen dat cpu uitvoert. Of, het aantal een rij gevormde processen die in een wachtende staat gemiddeld over één (lading1), vijf (lading5), en vijftien (load15) minieme periode zijn.
* **Telling van het Proces**: Het aantal processen momenteel open.
* **Aantal van de Gebruiker**: Het aantal gebruikers met een actieve shell zitting.
* **Gebruik van het Geheugen**: Het percentage momenteel toegewezen systeemgeheugen.
* **JVM Geheugen**: De grootte (in megabytes) van de toegewezen heap van Java.
* **Oude Ruimte van de Generatie**: Het percentage van JVM oud die generatiegeheugen momenteel wordt toegewezen.

#### Netwerk {#network}

* **Controle van de Haven CQ**: De reactietijd in seconden om tot de AEM of haven van Dispatcher toegang te hebben. Er zijn verschillende maatstaven voor auteur, publicatie en Dispatcher.

#### Opslag {#storage}

* **Ruimte van de Schijf**: De gebruikte schijfruimte (in megabytes) voor elk onderstelpunt op de gastheer. Er zijn verschillende meetwaarden voor elk koppelingspunt. Er zijn minimaal metriek voor `/` en `/mnt` , maar er kunnen aanvullende meetpunten beschikbaar zijn, afhankelijk van de specifieke instantieconfiguratie.
* **de Grootte van de Omslag**
* **AEM de Opslag van het Segment**: De gebruikte schijfruimte (in gigabytes) voor de Opslag van het Segment van de AEM.

#### Toepassing {#application}

* **Agent van de Replicatie**: De tijd (in seconden) voor een gebeurtenis van de testreplicatie
   * Er zijn afzonderlijke metriek voor elke replicatieagent.
* **de Duw van Dispatcher**: Het aantal punten momenteel in de Dispatcher leegmaken rij

## SLA-rapportage {#sla-reporting}

U kunt de prestaties van uw productie AEM milieu met betrekking tot uw contractuele overeenkomst van het de dienstniveau zien (SLA).

In de volgende grafiek wordt het maandelijkse SLA-resultaat voor 2019 weergegeven.

![ SLA 2018 grafiek ](/help/assets/SLA-Reports-one.png)

Net als bij systeemgrafieken worden bij het verschuiven van een gegevenspunt de specifieke waarden voor die maand weergegeven.

![ het puntrollover van Gegevens ](/help/assets/SLA-Reports-two.png)

De **sectie van de Analyse van de Gebeurtenis** onder deze grafiek toont de reeks incidenten die voor het programma tijdens het momenteel geselecteerde jaar voorkwamen. Elk incident heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![ de analyse van de Gebeurtenis ](/help/assets/sla-reporting3.png)

## SLA-meetgegevens {#sla-metrics}

* **het Contract van de Auteur**: SLA bepaalde in uw contract met Adobe Managed Services voor de auteursrij.
* **de Auteur SLA van AMS**: De gemeten uptime van de rij van de productiauteur, factoring incidenten die door verkopers of door Adobe worden veroorzaakt.
* **Auteur SLA**: Gemeten uptime van de auteursrij die geplande onderbreking zoals onderhoudsvensters negeert.
* **Eind - gebruikerscontract**: SLA bepaalde in uw contract met Adobe Managed Services voor publiceer rij.
* **SLA van het Eind van AMS**: De gemeten uptimes van de productie publiceren rij, factoringsincidenten die door verkopers of door Adobe worden veroorzaakt.
* **SLA van het Eind**: Gemeten uptime van publiceer rij die geplande onderbreking zoals onderhoudsvensters negeert.

## Videozelfstudie {#video-tutorial}

Deze video biedt een overzicht van het gebruik van de diagrammen die door Cloud Manager Reports zijn gemaakt voor een weergave in uw programmaomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
