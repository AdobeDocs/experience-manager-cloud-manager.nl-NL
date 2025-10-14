---
title: Belangrijke concepten
description: Zoals alle krachtige hulpmiddelen, omvat Cloud Manager vele concepten en termijnen. Dit document geeft een overzicht van een aantal van de belangrijkste documenten die u nodig hebt als u Cloud Manager gaat gebruiken.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Belangrijkste concepten {#key-concepts}

Zoals alle krachtige hulpmiddelen, omvat Cloud Manager vele concepten en termijnen. Dit document geeft een overzicht van een aantal van de belangrijkste documenten die u nodig hebt als u Cloud Manager gaat gebruiken.

## Toepassing {#application}

Een toepassing is de reeks aanpassingen en configuraties die door een klant worden gecreeerd om de onderliggende [&#x200B; oplossing &#x200B;](#solution) (zoals AEM Sites of AEM Assets) voor hun specifieke gebruiksgevallen en behoeften aan te passen. Een toepassing is een logische eenheid die uit veelvoudige [&#x200B; artefacten &#x200B;](#artifact) kan worden samengesteld.

Een voorbeeldtoepassing is de fictieve [&#x200B; WKND lifestyle toepassing &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefact {#artifact}

Een artefact is een plaatsbare eenheid en is het resultaat van één of ander bouwstijlproces dat broncode in één enkele eenheid omzet. Bijvoorbeeld een ZIP-bestand met de broncode.

## Artefaciliteit {#artifact-repository}

Een artefactbewaarplaats is een opslagplaats waar klant-specifieke [&#x200B; artefacten &#x200B;](#artifact) worden bewaard en worden beveiligd.

## Omgeving {#environment}

Een milieu is één enkele cluster van virtuele machines binnen a [&#x200B; programma &#x200B;](#program). Voor AEM bestaat deze omgeving uit een ontwerpinstantie (optioneel met een extra koude stand-by ontwerpinstantie), nul of meer publicatieinstanties, een of meer Dispatcher-instanties en een taakverdelingsmechanisme.

## Git-opslagplaats {#git-repository}

Een bewaarplaats van het Git is een plaats waar klant-specifieke broncode wordt opgeslagen en toegankelijk [&#x200B; gebruikend Git &#x200B;](https://git-scm.com) is.

## Instantie {#instance}

Een instantie is een specifieke virtuele server die de AEM [&#x200B; oplossing &#x200B;](#solution) in werking stelt. De instanties vertegenwoordigen één enkele logische eenheid vanuit een plaatsingsperspectief.

## Organisatie {#organization}

Een organisatie is een constructie van de Adobe die een ondernemingsklant vertegenwoordigt. Eén bedrijf kan meerdere organisaties hebben, afhankelijk van de manier waarop deze zijn ingericht in het Identity Management System (IMS) van Adobe.

## Pijpleiding {#pipeline}

Een pijpleiding is een reeks plaatsingsstappen die in opeenvolging in werking worden gesteld of &quot;uitgevoerd&quot;.

## Product {#product}

Een product is een specifieke reeks functionaliteit binnen a [&#x200B; oplossing &#x200B;](#solution) vergunning gegeven door een organisatie. De verschillende [&#x200B; programma&#39;s &#x200B;](#program) binnen een organisatie kunnen op verschillende reeksen producten, bijvoorbeeld, AEM Sites, AEM Assets, of AEM Forms worden gemachtigd.

## Programma {#program}

Een programma is een reeks milieu&#39;s die een logische groepering van klanteninitiatieven steunen, die gewoonlijk aan een gekochte overeenkomsten van het de dienstniveau (SLA) beantwoorden. Elk programma heeft precies één productieomgeving en kan vele niet-productieomgevingen hebben.

## Oplossing {#solution}

Een oplossing is een van de Adobe [!UICONTROL Experience Cloud] -oplossingen. Bijvoorbeeld Adobe Experience Manager, Adobe Target of Adobe Analytics.

## Stap {#step}

Een stap is een gevormde instructieset die één of andere eenheid van het werk als bouwsteen van a [&#x200B; pijpleiding &#x200B;](#pipeline) verwezenlijkt.
