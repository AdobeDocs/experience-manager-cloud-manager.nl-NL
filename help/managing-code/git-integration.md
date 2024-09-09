---
title: Git Integration met Adobe Cloud Manager
description: Deze videoreeks doorloopt de opstelling en de integratie van een klant-beheerde (on-premise) opslagplaats van de Git met Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# Git integration met Adobe Cloud Manager

Adobe Cloud Manager wordt geleverd met één Git-opslagplaats die wordt gebruikt om code te implementeren met behulp van Cloud Manager CI/CD-leidingen. U kunt de Cloud Manager Git-opslagplaats buiten de box gebruiken of u hebt ook de mogelijkheid om een op-premise of door de klant beheerde Git-opslagplaats te integreren met Cloud Manager.

## Overzicht van Git-integratie

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In deze videoreeks worden verschillende gebruiksgevallen besproken met betrekking tot de integratie van een door de klant beheerde Git-opslagplaats met Cloud Manager.

* [Beginsynchronisatie](#initial-sync)
* [Basisvertakkingsstrategie](#branching-strategy)
* [Ontwikkeling van de functiescherm](#feature-development)
* [Implementatie van productie](#production-deployment)
* [Releasetags synchroniseren](#sync-tags)

Deze videoreeks veronderstelt een basiskennis van Git en broncontrolebeheer. Zie de [ extra middelen hieronder ](#additional-resources) voor meer details op Git.

De stappen en naamgevingsconventies die in deze videoreeks worden beschreven, zijn enkele aanbevolen werkwijzen voor het werken met een door de klant beheerde Git-opslagplaats en Cloud Manager. Verwacht wordt dat de getoonde conventies en workflows zullen worden aangepast voor individuele ontwikkelingsteams.

Voor een volledig overzicht van Cloud Manager, zie [ Inleiding aan Cloud Manager ](/help/introduction.md).

## Eerste synchronisatie {#initial-sync}

Eerste stappen voor het synchroniseren van een door de klant beheerde Git-opslagplaats met de Cloud Manager Git-opslagplaats.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basisvertakkingsstrategie {#branching-strategy}

Opstelling een basis vertakkende strategie om uit Cloud Manager [ productie ](/help/using/production-pipelines.md) en [ niet productiepijpleidingen ](/help/using/non-production-pipelines.md) voordeel te halen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Ontwikkeling van filialen {#feature-development}

Gebruik een eigenschapvertakking om codeveranderingen in een klant-geleide opslagplaats van de Git te isoleren en met de opslagplaats van de Git van Cloud Manager te synchroniseren om een niet productiepijplijn voor codekwaliteit en validatietests te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementatie van productie {#production-deployment}

Voorbereiden van code voor een productievrijgave in een door de klant beheerde Git-opslagplaats en synchroniseren met de Cloud Manager Git-opslagplaats om te implementeren in testomgevingen en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Release-labels synchroniseren {#sync-tags}

U kunt releasetags van een Cloud Manager Git-opslagplaats synchroniseren naar een door de klant beheerde Git-opslagplaats. Deze mogelijkheid biedt inzicht in welke code is geïmplementeerd in zowel testomgevingen als productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Aanvullende bronnen {#additional-resources}

* [Cloud Manager Introduction](/help/introduction.md)
* [ Middelen GitHub ](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [ Atlassian Tutorials van het Git ](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [ Git Cheat Sheet ](https://education.github.com/git-cheat-sheet-education.pdf)
