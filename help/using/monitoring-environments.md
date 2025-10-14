---
title: Omgevingen bewaken
description: Leer hoe u uw omgevingen in Cloud Manager kunt bewaken.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Monitoromgevingen {#monitoring-environments}

Leer hoe u uw omgevingen in Cloud Manager kunt bewaken.

## Metrische drempels {#thresholds}

Systeemcontrole in [!UICONTROL Cloud Manager] wordt uitgevoerd door de afzonderlijke instanties binnen een omgeving te observeren en een aantal verschillende meetgegevens voor elke instantie te volgen. Elke metrisch heeft twee bepaalde drempels: a *waarschuwings* drempel en a *kritieke* drempel.

Als een metrische waarde boven de waarschuwingsdrempel (maar onder de kritische drempel) ligt, wordt deze als een waarschuwingsstatus beschouwd.

Als metrisch zijn over zijn kritieke drempel is, wordt het beschouwd om in een kritieke staat te zijn.

Adobe Managed Services stelt de drempelwaarden in, die u kunt weergeven in [!UICONTROL Cloud Manager] . In de meeste gevallen zijn drempels consistent tussen klanten, maar er zijn gevallen waarin Adobe Managed Services drempelwaarden bewerkt die overeenkomen met specifieke klantenvereisten. Verricht om het even welke vragen die u over de drempels aan uw Ingenieur van het Succes van de Klant hebt (CSE).

## Toegangssysteemcontrole {#accessing-system-monitoring}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com) en selecteert de aangewezen organisatie en het programma.

1. Klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) van het programma dat u wilt controleren.
1. In het menu, onder **beheert**, klik **tonen Controle** om de **pagina van Rapporten** te openen die systeem controleinformatie toont.

   ![&#x200B; Montages &#x200B;](/help/assets/first-timea1.png)

.

## Overzicht van systeembewaking {#system-monitoring-overview}

De **sectie van de Controle van het Systeem** van de **pagina van Rapporten** maakt een lijst van de gecontroleerde milieu&#39;s in het programma. Zij rapporteert over hun gezondheid op hoog niveau in de volgende vier afzonderlijke categorieën:

* Host
* Opslag
* Netwerk
* Toepassing

De status in elke categorie is een overzicht van de afzonderlijke meetwaarden. Als om het even welke metrisch in een categorie in de kritieke staat is, is de volledige categorie in een kritieke staat ten behoeve van de overzichtspagina. Dezelfde samenvatting kan op milieuniveau en op instantieniveau worden bekeken.

![&#x200B; Controle van het Systeem overzicht &#x200B;](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Wanneer u naar deze pagina navigeert, zijn de exemplaren van de productieomgeving standaard zichtbaar, maar kunnen ook andere omgevingen worden weergegeven.

## System Monitoring Detail {#system-monitoring-detail}

Als u de details van bepaalde metriek wilt weergeven, klikt u op een van de categoriekolommen van een specifiek exemplaar of op de titel van de categorie in de linkernavigatie. Elke detailpagina bevat een reeks grafieken voor de meetgegevens in die categorie. U kunt de metriek voor alle instanties in een milieu of voor een specifieke instantie bekijken. U kunt schakelen tussen de omgeving en instanties met de vervolgkeuzelijsten in de rechterbovenhoek.

![&#x200B; Uitgezochte milieu &#x200B;](/help/assets/System_Monitoring1.png)

De navigatie op de linkerzijde toont de beschikbare metriek binnen de momenteel geselecteerde categorie waarvoor er gegevens voor de momenteel geselecteerde milieu en instanties zijn.

Een individuele grafiek toont de status en een grafiek van de gegevens in tijd samen met de drempels. Wanneer meerdere instanties worden weergegeven, bevinden de gegevens van elke instantie zich in een aparte reeks.

![&#x200B; Grafiek van Metriek &#x200B;](/help/assets/Monitoring_Graphs1.png)

Individuele reeksen kunnen op een grafiek worden verborgen door op de reeks in de legenda te klikken.
Als u bijvoorbeeld op de waarschuwingsdrempelreeks klikt, ziet u alleen de kritieke drempel.

![&#x200B; wijzig grafiek &#x200B;](/help/assets/Monitoring_Graphs2.png)

### Metrische definities {#metric-definitions}

#### Host {#host}

* **`Load Per Core`**: Het aantal processen dat de CPU uitvoert. Of, het aantal een rij gevormde processen die in een wachtende staat gemiddeld over één (lading1), vijf (lading5), en vijftien (load15) minieme periode zijn.
* **P`rocess Count`**: Het aantal processen momenteel open.
* **`User Count`**: Het aantal gebruikers met een actieve shellsessie.
* **`Memory Usage`**: Het percentage systeemgeheugen dat momenteel is toegewezen.
* **`JVM Memory`**: De grootte (in megabytes) van de toegewezen Java-heap.
* **`Old Generation Space`**: Het percentage geheugen van de oude JVM-generatie dat momenteel is toegewezen.

#### Netwerk {#network}

* **`CQ Port Check`**: De responstijd in seconden voor toegang tot de AEM- of Dispatcher-poort. Er zijn verschillende maatstaven voor auteur, publicatie en Dispatcher.

#### Opslag {#storage}

* **`Disk Space`**: De gebruikte schijfruimte (in megabytes) voor elk koppelingspunt op de host. Er zijn verschillende meetwaarden voor elk koppelingspunt. Er zijn minimaal metriek voor `/` en `/mnt` , maar er kunnen aanvullende meetpunten beschikbaar zijn, afhankelijk van de specifieke instantieconfiguratie.
* **`Folder Size`**
* **`AEM Segment Store`**: De gebruikte schijfruimte (in gigabytes) voor de AEM Segment Store.

#### Toepassing {#application}

* **`Replication Agent`**: De tijd (in seconden) voor een testreplicatiegebeurtenis
   * Er zijn afzonderlijke metriek voor elke replicatieagent.
* **`Dispatcher Flush`**: Het aantal items dat zich momenteel in de Dispatcher-wachtrij bevindt

## SLA-rapportage {#sla-reporting}

U kunt de prestaties van uw AEM-productieomgeving zien in verhouding tot uw service level agreement (SLA) waarvoor u een contract hebt gesloten.

In de volgende grafiek wordt het maandelijkse SLA-resultaat voor 2019 weergegeven.

![&#x200B; SLA 2018 grafiek &#x200B;](/help/assets/SLA-Reports-one.png)

Net als bij systeemgrafieken worden bij het verschuiven van een gegevenspunt de specifieke waarden voor die maand weergegeven.

![&#x200B; het puntrollover van Gegevens &#x200B;](/help/assets/SLA-Reports-two.png)

De **sectie van de Analyse van de Gebeurtenis** onder deze grafiek toont de reeks incidenten die voor het programma tijdens het momenteel geselecteerde jaar voorkwamen. Elk incident heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![&#x200B; de analyse van de Gebeurtenis &#x200B;](/help/assets/sla-reporting3.png)

## SLA-meetgegevens {#sla-metrics}

* **`Author Contract`**: De SLA die in uw contract met Adobe Managed Services is gedefinieerd voor de auteurslaag.
* **`AMS Author SLA`**: De gemeten uptime van de productiefunctie, incidenten die worden veroorzaakt door leveranciers of door Adobe.
* **`Author SLA`**: De gemeten uptime van de auteurslaag die geplande onderbreking zoals onderhoudsvensters negeert.
* **`End User Contract`**: De SLA die in uw contract met Adobe Managed Services is gedefinieerd voor de publicatielaag.
* **`AMS End User SLA`**: De gemeten uptime van de uitgeverij van de productie, factoring incidenten die door verkopers of door Adobe worden veroorzaakt.
* **`End User SLA`**: De gemeten uptime van de publicatielaag waarbij geplande downtime, zoals onderhoudvensters, wordt genegeerd.

## Videozelfstudie {#video-tutorial}

Deze video biedt een overzicht van het gebruik van de diagrammen die door Cloud Manager Reports zijn gemaakt voor een weergave in uw programmaomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
