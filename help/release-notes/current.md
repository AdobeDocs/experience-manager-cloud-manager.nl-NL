---
title: Opmerkingen bij de release voor Cloud Manager 2025.6.0
description: Meer informatie over de release van Cloud Manager 2025.5.0 op Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 38d398caf2323b603afd293aa9152308fefd323f
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.6.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.6.0 op Adobe Managed Services.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2025.6.0 is donderdag 5 juni 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

De volgende geplande release is donderdag 10 juli 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Nieuwe functies {#what-is-new}

* **Staging-slechts en productie-enige pijpleidingen**

  Cloud Manager ondersteunt nu alleen staging- en alleen productie-pijpleidingen. Met deze functie kunt u implementaties van volledige stapelproductie splitsen in kleinere, doelspecifieke pijpleidingen. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![ voeg niet-productiepijpleidingsdialoogdoos met de Volledige geselecteerde radioknoop van de Code van de Stapel en het milieu van het Stadium toe ](/help/release-notes/assets/add-non-production-pipeline.png)

  Zie [ werkgebied-slechts en prod-slechts pijpleidingen ](/help/using/stage-prod-only.md).

* **de favorieten van de Pijpleiding**

  In deze versie, introduceert Cloud Manager de capaciteit om favoriete pijpleidingen vast te zetten, latend u specifieke pijpleidingen als favorieten zodat verschijnen zij bij de bovenkant van de lijst op de **pagina van de Pijpleidingen**. Deze verbetering maakt vaak betreden pijpleidingen gemakkelijker te vinden en te lopen. <!-- CMGR-68293 -->

  ![ Pijpleidingen duidelijk als favorieten ](/help/release-notes/assets/pipeline-favorites.png) *Twee pijpleidingen duidelijk als favorieten.*

  Zie [ pijpleidingsfavorieten van het Teken ](/help/using/managing-pipelines.md#pipeline-favorites).


## Private bètaprogramma {#beta-program}

Neem deel aan een Cloud Manager Private beta-programma om exclusieve toegang te krijgen tot de volgende functies voordat ze in het algemeen worden uitgebracht.

De volgende persoonlijke bètamogelijkheden zijn momenteel beschikbaar:


### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

**breng Uw Eigen eigenschap van het Git** (BYOG) is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de bewaarplaats van Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen degenen) en de **Trekker van de Plaatsing** aan **wordt geplaatst op de Veranderingen van het Git** beginnen nu automatisch.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

#### Toegangstokens beheren{#access-tokens}

Gebruik **beheert de Tokens van de Toegang** eigenschap, samen met BYOG, om, toegangstokens te bekijken anders te noemen en te schrappen verbonden aan externe breng Uw Eigen bewaarplaatsen van het Git, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [ de Tokens van de Toegang beheren ](/help/managing-code/manage-access-tokens.md).

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.


## Opgeloste problemen {#bug-fixes}

* AEM Cloud Manager wijst nu correct Maven bouwstijlmislukkingen in kaart die door 409 fouten (conflicten) worden veroorzaakt wanneer het halen van klantartefacten aan een klant-veroorzaakt mislukking. Deze verandering verbetert foutenoverseinen door tussen interne fouten en kwesties met betrekking tot de opstelling van het klantenmilieu te onderscheiden. <!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
