---
title: Source Code Repository
description: Meer informatie over de git-opslagplaats die is ingericht voor elk programma dat u in Cloud Manager hebt.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Source Code Repository {#source-code-repository}

Meer informatie over de git-opslagplaats die is ingericht voor elk programma dat u in Cloud Manager hebt.

## Cloud Manager-opslagplaats {#cloud-manager-repository}

Uw [!UICONTROL AEM Managed Services] -abonnement bevat een opslagplaats voor broncode die is ingericht en beheerd door Adobe. Aan elk programma wordt één enkele en unieke it-opslagplaats toegewezen, waar uw bijbehorende code wordt opgeslagen en beveiligd.

Als beste praktijken, zou u altijd de Cloud Manager gokbewaarplaats moeten gebruiken, die leeg zonder om het even welke gevormde takken of steekproefprojecten komt. Als u de Cloud Manager git-opslagplaats wilt gebruiken, ontvangt u een token voor persoonlijke toegang waarmee u elke willekeurige git-client kunt gebruiken voor het maken van vertakkingen, het opslaan en ophalen van uw code, het vastleggen van de geschiedenis, enzovoort.

Voor meer informatie over hoe te opstellingstakken in git, zie [ het Vormen de Tanden van de Versie ](/help/getting-started/configuring-branches.md).

Voor meer informatie over hoe te om de Cloud Manager git bewaarplaats met de pijpleiding te gebruiken CI/CD, zie [ de Pijpleidingen van de Productie vormen ](/help/using/production-pipelines.md) en [ Vormend niet-ProductiePijpleidingen ](/help/using/non-production-pipelines.md) om meer te leren.

## Bewaarplaats op locatie {#on-premise-repository}

U hebt mogelijk een bestaande git-opslagplaats en wilt deze blijven gebruiken. In dat geval kunt u de git-functie gebruiken voor meerdere externe opslagruimten. De ontwikkeling van dag tot dag zou in uw git-opslagplaats blijven plaatsvinden. Wanneer een releasevertakking gereed is voor implementatie op productie, kunt u uw nieuwste code naar de Cloud Manager git-opslagplaats duwen en de Cloud Manager CI/CD-pijplijn activeren.

Om gemeenschappelijke git bevelen te bekijken, zie het [ Blad van de Controle van de it ](https://education.github.com/git-cheat-sheet-education.pdf) op de website GitHub.
