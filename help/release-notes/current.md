---
title: Opmerkingen bij de release voor Cloud Manager 2025.10.0
description: Meer informatie over de release van Cloud Manager 2025.10.0 op Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: f62191a1b9dd67ea1e999e2db0bb05de66bf73f2
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Release-aantekeningen voor Cloud Manager 2025.10.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.10.0 op Adobe Managed Services.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2025.10.0 is donderdag 2 oktober 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

De volgende geplande release is donderdag 6 november 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nieuwe functies {#what-is-new}

De release van oktober Cloud Manager bevat geen belangrijke nieuwe functies.


## Beta-programma&#39;s {#beta-program}

Neem deel aan Cloud Manager Beta-programma&#39;s om exclusieve toegang te krijgen tot de volgende functies voordat ze in algemene zin worden uitgebracht.

De volgende mogelijkheden zijn momenteel beschikbaar:

### Uitbreidbaarheid en aanpassing van Experience Hub {#exp-hub-extensibility}

[ Experience Hub ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) dient als uw ingangspunt aan AEM, die voor de behoeften van uw organisatie wordt aangepast. Vertel Adobe over uw bestaande AEM UI-extensies, zodat ze u kunnen helpen deze extensies zo weinig mogelijk in Experience Hub in te schakelen.

![ Diagram van de rekbaarheid en aanpassingswerkschema van Experience Hub ](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Sluit aangepaste ervaringen in Experience Hub in om het dashboard van uw organisatie uit te breiden en aan te passen. Naast ingebouwde widgets Adobe, voeg uw eigen gebruiken toe gebruikend het [ kader van de Uitbreidbaarheid 0} UI. ](https://developer.adobe.com/uix/docs/) Creëer op JavaScript gebaseerde UI-apps en zorg ervoor dat deze aan uw gebruikers worden gepresenteerd, zodat ze aan de specifieke vereisten en workflows voldoen.

Geïnteresseerd in de bèta? E-mail [ beta_exphubextensibility@adobe.com ](mailto:beta_exphubextensibility@adobe.com) met uw Adobe OrgID en een korte beschrijving van de aanpassing u van plan bent te creëren.

### Snellere builds met module caching {#quick-build-cm-pipelines}

Een nieuw bouwstijlmodel compileert slechts veranderde modules (eerder dan de volledige repo) gebruikend module-vlakke caching om bouwstijltijden te verkorten. Het is van toepassing op code-kwaliteit, volledig-stapel, en stadium-slechts pijpleidingen.

![ geeft de Dialoogvenster van de Pijpleiding van de Niet-Productie uit die de twee opties van de Strategie van de Bouwstijl tonen die Volledige Bouwstijl en Slimme zijn ](/help/release-notes/assets/non-production-pipeline-edit.png)
*geef de de dialoogdoos uit van de Pijpleiding van de Niet-Productie die de twee opties toont van de Strategie van de Bouwstijl die Volledig zijn bouwt en Smart bouwt.*

In **voeg/geef de dialoogdoos van de Pijpleiding** toe, onder het **lusje van de Code van Source**, laat een nieuwe **Bouw Strategie** sectie u één van de volgende bouwstijlopties kiezen:

* **Volledig bouwt** — bouwt alle modules in de bewaarplaats op elke looppas.
* **Slim bouwt** — bouwt slechts modules die sinds laatste worden veranderd begaan, die algemene bouwtijd verkort.

U controleert welke pijpleidingen gebruiken **Slimme bouwstijl**. Tijdens bèta, verschijnt deze optie slechts voor **Kwaliteit van de Code** en **Dev de 3} pijpleidingen van de Plaatsing.**

Geïnteresseerd? E-mail [ beta_quickbuild_cmpipelines@adobe.com ](mailto:beta_quickbuild_cmpipelines@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


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

Er zijn geen significante insectenmoeilijke situaties in de versie van Oktober Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
