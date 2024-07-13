---
title: Belangrijke concepten
description: Zoals alle krachtige hulpmiddelen, omvat Cloud Manager vele concepten en termijnen. Dit document geeft een overzicht van een aantal van de belangrijkste documenten die u nodig hebt als u Cloud Manager gaat gebruiken.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 67621fb2dbb0c32371b2ffc16ec45f47daf04e05
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Belangrijke concepten {#key-concepts}

Zoals alle krachtige hulpmiddelen, omvat Cloud Manager vele concepten en termijnen. Dit document geeft een overzicht van een aantal van de belangrijkste documenten die u nodig hebt als u Cloud Manager gaat gebruiken.

## Toepassing {#application}

Een toepassing is de reeks aanpassingen en configuraties die door een klant worden gecreeerd om de onderliggende [ oplossing ](#solution) (zoals AEM Sites of AEM Assets) voor hun specifieke gebruiksgevallen en behoeften aan te passen. Een toepassing is een logische eenheid die uit veelvoudige [ artefacten kan worden samengesteld.](#artifact)

Een voorbeeldtoepassing is de fictieve [ WKND lifestyle toepassing.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

## Artefact {#artifact}

Een artefact is een plaatsbare eenheid en is het resultaat van één of ander bouwstijlproces dat broncode in één enkele eenheid omzet. Bijvoorbeeld een ZIP-bestand met de broncode.

## Artefactopslagplaats {#artifact-repository}

Een artefactbewaarplaats is een opslagplaats waar klant-specifieke [ artefacten ](#artifact) worden bewaard en worden beveiligd.

## Omgeving {#environment}

Een milieu is één enkele cluster van virtuele machines binnen a [ programma.](#program) Deze AEM bestaat bijvoorbeeld uit een ontwerpinstantie (optioneel met een extra koude stand-by ontwerpinstantie), nul of meer publicatieinstanties, een of meer dispatcherinstanties en een taakverdelingsmechanisme.

## git Repository {#git-repository}

Een git bewaarplaats is een plaats waar klant-specifieke broncode wordt opgeslagen en toegankelijk [ gebruikend git.](https://git-scm.com)

## Instantie {#instance}

Een instantie is een specifieke virtuele server die de AEM [ oplossing in werking stelt.](#solution) Instanties vertegenwoordigen één logische eenheid vanuit een implementatieperspectief.

## Organisatie {#organization}

Een organisatie is een constructie van de Adobe die een ondernemingsklant vertegenwoordigt. Eén bedrijf kan meerdere organisaties hebben, afhankelijk van de manier waarop deze zijn ingericht in het Identity Management System (IMS) van Adobe.

## Pijpleiding {#pipeline}

Een pijpleiding is een reeks plaatsingsstappen die in opeenvolging worden uitgevoerd.

## Product {#product}

Een product is een specifieke reeks functionaliteit binnen a [ oplossing ](#solution) vergunning gegeven door een organisatie. De verschillende [ programma&#39;s ](#program) binnen een organisatie kunnen op verschillende reeksen producten, bijvoorbeeld, AEM Sites, AEM Assets, of AEM Forms worden gemachtigd.

## Programma {#program}

Een programma is een reeks milieu&#39;s die een logische groepering van klanteninitiatieven steunen, gewoonlijk die aan een gekochte overeenkomsten van het de dienstniveau (SLA) beantwoorden. Elk programma heeft precies één productieomgeving en kan vele niet-productieomgevingen hebben.

## Oplossing {#solution}

Een oplossing is een van de Adobe [!UICONTROL Experience Cloud] -oplossingen. Bijvoorbeeld Adobe Experience Manager, Adobe Target of Adobe Analytics.

## Stap {#step}

Een stap is een gevormde instructieset die één of andere eenheid van het werk als bouwsteen van a [ pijpleiding verwezenlijkt.](#pipeline)
