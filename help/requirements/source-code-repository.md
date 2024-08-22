---
title: Source Code Repository
description: Meer informatie over de Git-opslagplaats die is ingericht voor elk programma dat u in Cloud Manager hebt.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Source-codeopslagplaats {#source-code-repository}

Meer informatie over de Git-opslagplaats die is ingericht voor elk programma dat u in Cloud Manager hebt.

## Cloud Manager-opslagplaats {#cloud-manager-repository}

Uw [!UICONTROL AEM Managed Services] -abonnement bevat een opslagplaats voor broncode die is ingericht en beheerd door Adobe. Aan elk programma wordt één enkele en unieke Git-opslagplaats toegewezen, waar uw bijbehorende code wordt opgeslagen en beveiligd.

Als beste praktijken, zou u altijd de bewaarplaats van de Git van Cloud Manager moeten gebruiken, die leeg zonder enige gevormde takken of steekproefprojecten komt. Cloud Manager biedt een privé toegangstoken voor zijn gegevensopslagplaats van de Git, die u om het even welke cliënt van de Git laat gebruiken om takken tot stand te brengen, code te beheren, wor geschiedenis terug te winnen, en meer.

Voor meer informatie over hoe te opstellings takken in Git, zie [ Vormend de Tanden van de Versie ](/help/getting-started/configuring-branches.md).

Voor meer informatie over hoe te om de bewaarplaats van het Git van Cloud Manager met de pijpleiding te gebruiken CI/CD, zie [ de Pijpleidingen van de Productie vormen ](/help/using/production-pipelines.md) en [ Vormend niet-ProductiePijpleidingen ](/help/using/non-production-pipelines.md) om meer te leren.

## Opslagplaats op locatie {#on-premise-repository}

U hebt mogelijk een bestaande Git-opslagplaats en wilt deze blijven gebruiken. In dat geval kunt u de Git-functie gebruiken voor meerdere externe opslagruimten. De ontwikkeling van dag tot dag zou in uw Git-opslagplaats blijven plaatsvinden. Wanneer een releasevertakking gereed is voor implementatie op productie, kunt u uw nieuwste code naar de Cloud Manager Git-opslagplaats drukken en de Cloud Manager CI/CD-pijplijn activeren.

Om gemeenschappelijke bevelen van het Git te bekijken, zie het [ Vondst van de Git ](https://education.github.com/git-cheat-sheet-education.pdf).
