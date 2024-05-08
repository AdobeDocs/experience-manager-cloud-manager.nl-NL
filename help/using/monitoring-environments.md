---
title: Controleomgevingen
description: Leer hoe u uw omgevingen kunt controleren in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: ab527beb706ab73a14cc933a3414873dee6b7a9e
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---


# Controleomgevingen {#monitoring-environments}

Leer hoe u uw omgevingen kunt controleren in Cloud Manager.

## Metrische drempelwaarden {#thresholds}

Systeemcontrole in [!UICONTROL Cloud Manager] wordt gedaan door de individuele instanties binnen een milieu te observeren en een verscheidenheid van metriek voor elke instantie te volgen. Elke metrische waarde heeft twee gedefinieerde drempelwaarden: een waarschuwingsdrempel en een kritieke drempelwaarde.

Als metrisch zijn over zijn kritieke drempel is, wordt het beschouwd om in een kritieke staat te zijn. Als een metrische waarde boven de waarschuwingsdrempel (maar onder de kritische drempel) ligt, wordt deze als een waarschuwingsstatus beschouwd. De drempelwaarden worden vastgesteld door Adobe Managed Services en kunnen worden weergegeven in [!UICONTROL Cloud Manager]. In de meeste gevallen zijn drempels consistent tussen klanten, maar er zijn gevallen waarin Adobe Managed Services drempelwaarden zal aanpassen om aan specifieke klantenvereisten te voldoen. Vragen over de drempelwaarden moeten worden gericht aan uw Customer Success Engineer (CSE).

## Toegang tot systeemcontrole {#accessing-system-monitoring}

Volg deze stappen om tot de Controle van het Systeem toegang te hebben.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) en selecteert u de gewenste organisatie en het juiste programma.

1. Tik of klik op de knop met de ovaal van het programma dat u wilt controleren en selecteer de knop **Controle tonen** -optie.

   ![Instellingen](/help/assets/first-timea1.png)

De **Rapporten** pagina wordt geopend om informatie over systeemcontrole weer te geven.

## Overzicht van systeemcontrole {#system-monitoring-overview}

De **Systeembewaking** van de **Rapporten** De pagina bevat een overzicht van de gecontroleerde omgevingen in het programma en rapporteert over de gezondheid op hoog niveau in vier verschillende categorieën:

* Host
* Opslag
* Netwerk
* Toepassing

De status in elke categorie is een overzicht van de afzonderlijke meetwaarden. Als om het even welke metrisch in een categorie in de kritieke staat is, is de gehele categorie in een kritieke staat voor de overzichtspagina. Dezelfde samenvatting kan op milieuniveau en op instantieniveau worden bekeken.

![Systeemcontrole](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Wanneer u naar deze pagina navigeert, zijn de exemplaren van de productieomgeving standaard zichtbaar, maar kunnen ook andere omgevingen worden weergegeven.

## System Monitoring Detail {#system-monitoring-detail}

Tik of klik op een van de categoriekolommen van een bepaald exemplaar of op de titel van een bepaalde categorie in de linkernavigatie om de details van bepaalde metriek weer te geven. Elke detailpagina bevat een reeks grafieken voor de meetgegevens in die categorie. U kunt de metriek voor alle instanties in een milieu of voor een specifieke instantie bekijken. U kunt schakelen tussen de omgeving en instanties met de vervolgkeuzelijsten in de rechterbovenhoek.

![Omgeving selecteren](/help/assets/System_Monitoring1.png)

De navigatie op de linkerzijde zal de beschikbare metriek binnen de momenteel geselecteerde categorie tonen waarvoor er gegevens voor de momenteel geselecteerde milieu en instanties zijn.

Een individuele grafiek zal de status en een grafiek van de gegevens in tijd samen met de drempels tonen. Als er meerdere instanties worden weergegeven, bevinden de gegevens van elke instantie zich in een aparte reeks.

![Metrische grafiek](/help/assets/Monitoring_Graphs1.png)

Individuele reeksen kunnen op een grafiek worden verborgen door op de reeks in de legenda te klikken.
Als u bijvoorbeeld op de waarschuwingsdrempelreeks klikt, ziet u alleen de kritieke drempel.

![Grafiek wijzigen](/help/assets/Monitoring_Graphs2.png)

### Metrische definities {#metric-definitions}

#### Host {#host}

* **Laden per kern**: Het aantal processen dat wordt uitgevoerd door de CPU of dat zich in een wachtstand bevindt, gemiddeld over een periode van één (load1), vijf (load5) en vijftien (load15) minuten
* **Procesaantal**: Het aantal momenteel geopende processen
* **Aantal gebruikers**: Het aantal gebruikers met een actieve shellsessie
* **Geheugenverbruik**: Het percentage systeemgeheugen dat momenteel is toegewezen
* **JVM-geheugen**: De grootte (in megabytes) van de toegewezen Java-heap
* **Ruimte van de oude generatie**: Het percentage JVM-geheugen van de oude generatie dat momenteel is toegewezen

#### Netwerk {#network}

* **Poortcontrole CQ**: De reactietijd in seconden om tot de haven van de AEM of van de Verzender toegang te hebben
   * Er zijn verschillende maatstaven voor auteur, publicatie en verzender.

#### Opslag {#storage}

* **Schijfruimte**: De gebruikte schijfruimte (in megabytes) voor elk koppelpunt op de host
   * Er zijn verschillende meetwaarden voor elk koppelingspunt.
   * Er zijn minstens metriek voor `/` en `/mnt`, maar mogelijk zijn aanvullende meetgegevens voor het koppelingspunt beschikbaar, afhankelijk van de specifieke instantieconfiguratie.
* **Mapgrootte**
* **AEM Segmentarchief**: De gebruikte schijfruimte (in gigabytes) voor de AEM Segment Store

#### Toepassing {#application}

* **Replication Agent**: De tijd (in seconden) voor een testreplicatiegebeurtenis
   * Er zijn afzonderlijke metriek voor elke replicatieagent.
* **Dispatcher Flush**: Het aantal items dat zich momenteel in de verzendingswachtrij bevindt

## SLA-rapportage {#sla-reporting}

U kunt de prestaties van uw productie AEM milieu met betrekking tot uw overeenkomst van het de dienstniveau (SLA) zien.

In de volgende grafiek wordt de maandelijkse SLA-prestaties voor 2019 weergegeven.

![SLA 2018-grafiek](/help/assets/SLA-Reports-one.png)

Net als bij systeemgrafieken worden bij het verschuiven van een gegevenspunt de specifieke waarden voor die maand weergegeven.

![Rollover gegevenspunt](/help/assets/SLA-Reports-two.png)

De **Gebeurtenisanalyse** in deze grafiek wordt de reeks incidenten weergegeven die zich tijdens het geselecteerde jaar voor het programma hebben voorgedaan. Elk incident heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![Gebeurtenisanalyse](/help/assets/sla-reporting3.png)

## SLA-waarden {#sla-metrics}

* **Auteurscontract**: Dit is SLA die in uw contract met Adobe Managed Services voor de auteursrij wordt bepaald.
* **AMS Author SLA**: Dit is de gemeten uptime van de productiefabrikant van de laag die door Adobe of onze verkopers wordt veroorzaakt.
* **Auteur SLA**: Dit is de gemeten uptime van de auteurslaag die geplande onderbreking zoals onderhoudsvensters negeert.
* **Eindgebruikerscontract**: Dit is de SLA die is gedefinieerd in uw contract met Adobe Managed Services voor de publicatielijst.
* **AMS-SLA eindgebruiker**: Dit is de gemeten uptime van de productie publiceer de incidenten van de lijstfactoring die door Adobe of onze verkopers worden veroorzaakt.
* **SLA eindgebruiker**: Dit is de gemeten uptime van de publicatielaag die geplande downtime, zoals onderhoudvensters, negeert.

## Videozelfstudie {#video-tutorial}

Deze video biedt een overzicht van het gebruik van de diagrammen die zijn gemaakt door Cloud Manager Reports voor een weergave in uw programmaomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
