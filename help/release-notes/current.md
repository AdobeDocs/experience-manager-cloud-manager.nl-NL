---
title: Opmerkingen bij de release voor Cloud Manager 2025.8.0
description: Meer informatie over de release van Cloud Manager 2025.8.0 op Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b64b8529e4c6072c9bcb7438dc2d89098d29115d
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.8.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.8.0 op Adobe Managed Services.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2025.8.0 is donderdag 7 augustus 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

De volgende geplande release is donderdag 4 september 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Nieuwe functies {#what-is-new}

* **Experience Hub van Adobe die spoedig komt**

  Vanaf 19 augustus 2025 start Adobe een gefaseerde uitrol van de nieuwe Experience Hub voor alle Adobe Experience Manager-gebruikers.

  Experience Hub is een eenduidig beginpunt dat gepersonaliseerde contextafhankelijke ervaringen biedt om gebruikers te helpen sneller doelstellingen te bereiken. De uitrol wordt uiterlijk op 26 augustus 2025 voltooid en beschikbaar gesteld aan alle gebruikers. De nieuwe Experience Hub is toegankelijk direct bij [ experience.adobe.com ](https://experience.adobe.com/). Meer leren, zie [ Adobe Experience Hub ](/help/experience-hub.md).

* **Staging-slechts en productie-enige pijpleidingen**

  Cloud Manager ondersteunt nu alleen staging- en alleen productie-pijpleidingen. Met deze functie kunt u implementaties van volledige stapelproductie splitsen in kleinere, doelspecifieke pijpleidingen. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![ voeg niet-productiepijpleidingsdialoogdoos met de Volledige geselecteerde radioknoop van de Code van de Stapel en het milieu van het Stadium toe ](/help/release-notes/assets/add-non-production-pipeline.png)

  Zie [ werkgebied-slechts en prod-slechts pijpleidingen ](/help/using/stage-prod-only.md).

* **de favorieten van de Pijpleiding**

  In deze versie, introduceert Cloud Manager de capaciteit om favoriete pijpleidingen vast te zetten, latend u specifieke pijpleidingen als favorieten zodat verschijnen zij bij de bovenkant van de lijst op de **pagina van de Pijpleidingen**. Deze verbetering maakt vaak betreden pijpleidingen gemakkelijker te vinden en te lopen. <!-- CMGR-68293 -->

  ![ Pijpleidingen duidelijk als favorieten ](/help/release-notes/assets/pipeline-favorites.png) *Twee pijpleidingen duidelijk als favorieten.*

  Zie [ pijpleidingsfavorieten van het Teken ](/help/using/managing-pipelines.md#pipeline-favorites).


## Beta-programma&#39;s {#beta-program}

Neem deel aan Cloud Manager Beta-programma&#39;s om exclusieve toegang te krijgen tot de volgende functies voordat ze in algemene zin worden uitgebracht.

De volgende mogelijkheden zijn momenteel beschikbaar:


### Je eigen gang (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/release-notes/assets/azure-repo.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [ de Tokens van de Toegang beheren ](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Bugfixes {#bug-fixes}

Er zijn geen significante insectenmoeilijke situaties in de versie van Cloud Manager van Juli.

<!--
Known Issues {#known-issues}

* A -->
