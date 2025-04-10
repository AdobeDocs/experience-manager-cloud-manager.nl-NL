---
title: Opmerkingen bij de release voor Cloud Manager 2025.4.0
description: Meer informatie over de release van Cloud Manager 2025.4.0 op Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 40d093ce7d6839fff4ba16f790c61b96cb88dda5
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.4.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.4.0 op Adobe Managed Services.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2025.4.0 is donderdag 10 april 2025.

De volgende geplande release is donderdag 8 mei 2025.

<!--
## What's new {#what-is-new}

* 
-->


## Programma voor vroegtijdige goedkeuring {#early-adoption}

Neem deel aan het Cloud Manager-programma voor vroegtijdige adoptie om exclusieve toegang te krijgen tot de volgende functies voordat ze algemeen worden uitgebracht.

Momenteel zijn de volgende mogelijkheden voor vroegtijdige adoptie beschikbaar:

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de bewaarplaats van Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen degenen) en de **Trekker van de Plaatsing** aan **wordt geplaatst op de Veranderingen van het Git** beginnen nu automatisch.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

### Pijpleidingen die uitsluitend bestemd zijn voor de productie {#staging-production-only-pipelines}

Adobe kondigt de introductie van steun voor [ staging-slechts en productie-enige pijpleidingen ](/help/using/stage-prod-only.md) aan. Met deze nieuwe functie kunt u distributiepijpleidingen voor volledige productie opsplitsen in kleinere, meer gespecialiseerde implementaties.

Als u deze eigenschap zou willen testen en terugkoppelen, e-mail [ Grp-cloudmanager_splitpipelines@adobe.com ](mailto:Grp-cloudmanager_splitpipelines@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID verstrekken.



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->



## Bugfixes {#bug-fixes}

* A

Bekende problemen {#known-issues}

* A —>
