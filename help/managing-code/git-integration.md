---
title: Git Integration met Adobe Cloud Manager
description: Deze videoreeks doorloopt de opstelling en de integratie van een klant-beheerde (op-gebouw) gogegevensopslagplaats met Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Git Integration met Adobe Cloud Manager

Adobe Cloud Manager wordt geleverd met één git-opslagplaats die wordt gebruikt om code te implementeren met behulp van Cloud Manager CI/CD-leidingen. U kunt de Cloud Manager git-opslagplaats buiten de box gebruiken of u hebt ook de mogelijkheid om een op-premise of door de klant beheerde git-opslagplaats te integreren met Cloud Manager.

## Overzicht van GIT-integratie

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In deze videoreeks worden verschillende gebruiksgevallen besproken met betrekking tot de integratie van een door de klant beheerde it-opslagplaats met Cloud Manager.

* [Beginsynchronisatie](#initial-sync)
* [Basisvertakkingsstrategie](#branching-strategy)
* [Ontwikkeling van de functiescherm](#feature-development)
* [Implementatie van productie](#production-deployment)
* [Releasetags synchroniseren](#sync-tags)

Deze videoreeks veronderstelt een basiskennis van git en broncontrolebeheer. Zie de [ extra middelen hieronder ](#additional-resources) voor meer details op git.

De stappen en naamgevingsconventies die in deze videoreeks worden beschreven, zijn enkele aanbevolen werkwijzen voor het werken met een door de klant beheerde it-opslagplaats en Cloud Manager. Verwacht wordt dat de getoonde conventies en workflows zullen worden aangepast voor individuele ontwikkelingsteams.

Voor een volledig overzicht van Cloud Manager, zie [ Inleiding aan Cloud Manager ](/help/introduction.md).

## Beginsynchronisatie {#initial-sync}

De eerste stappen voor het synchroniseren van een door de klant beheerde it-opslagplaats met Cloud Manager git-opslagplaats.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basisvertakkingsstrategie {#branching-strategy}

Opstelling een basis vertakkende strategie om uit Cloud Manager [ productie ](/help/using/production-pipelines.md) en [ niet productiepijpleidingen ](/help/using/non-production-pipelines.md) voordeel te halen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Ontwikkeling van de functiescherm {#feature-development}

Gebruik een eigenschapvertakking om codeveranderingen in een klant-beheerde git bewaarplaats te isoleren en met Cloud Manager te synchroniseren git bewaarplaats om een niet productiepijplijn voor codekwaliteit en bevestiging te gebruiken het testen.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementatie van productie {#production-deployment}

Voorbereiden van code voor een productierelease in een door de klant beheerde it-opslagplaats en synchroniseren met de Cloud Manager git-opslagplaats om deze te implementeren in testomgevingen en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Releasetags synchroniseren {#sync-tags}

Synchroniseer releasetags van een Cloud Manager-it-opslagplaats naar een door de klant beheerde it-opslagplaats, zodat u kunt zien welke code is geïmplementeerd in testomgevingen en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Aanvullende bronnen {#additional-resources}

* [Cloud Manager Introduction](/help/introduction.md)
* [ Middelen GitHub ](https://try.github.io)
* [ Atlassian Tutorials van het Git ](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [ Git Cheat Sheet ](https://education.github.com/git-cheat-sheet-education.pdf)
