---
title: Opmerkingen bij de release voor Cloud Manager 2025.10.0
description: Meer informatie over de release van Cloud Manager 2025.10.0 op Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 25eebd297fe2cdd82d4905fac9ae38e1ce46153f
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Release-aantekeningen voor Cloud Manager 2025.10.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.10.0 op Adobe Managed Services.

Zie ook de [&#x200B; huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2025.10.0 is donderdag 2 oktober 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

De volgende geplande release is donderdag 6 november 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nieuwe functies {#what-is-new}







## Beta-programma&#39;s {#beta-program}

Neem deel aan Cloud Manager Beta-programma&#39;s om exclusieve toegang te krijgen tot de volgende functies voordat ze in algemene zin worden uitgebracht.

De volgende mogelijkheden zijn momenteel beschikbaar:

### Uitbreidbaarheid en aanpassing van Experience Hub {#exp-hub-extensibility}

[&#x200B; Experience Hub &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) dient als uw ingangspunt aan AEM, die voor de behoeften van uw organisatie wordt aangepast. Vertel Adobe over uw bestaande AEM UI-extensies, zodat ze u kunnen helpen deze extensies zo weinig mogelijk in Experience Hub in te schakelen.

![&#x200B; Diagram van de rekbaarheid en aanpassingswerkschema van Experience Hub &#x200B;](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Sluit aangepaste ervaringen in Experience Hub in om het dashboard van uw organisatie uit te breiden en aan te passen. Naast ingebouwde widgets Adobe, voeg uw eigen gebruiken toe gebruikend het [&#x200B; kader van de Uitbreidbaarheid 0&rbrace; UI. &#x200B;](https://developer.adobe.com/uix/docs/) Creëer op JavaScript gebaseerde UI-apps en zorg ervoor dat deze aan uw gebruikers worden gepresenteerd, zodat ze aan de specifieke vereisten en workflows voldoen.

Geïnteresseerd in de bèta? E-mail [&#x200B; beta_exphubextensibility@adobe.com &#x200B;](mailto:beta_exphubextensibility@adobe.com) met uw Adobe OrgID en een korte beschrijving van de aanpassing u van plan bent te creëren.

### Snellere builds met module caching {#quick-build-cm-pipelines}

Een nieuw bouwstijlmodel compileert slechts veranderde modules (eerder dan de volledige repo) gebruikend module-vlakke caching om bouwstijltijden te verkorten. Het is van toepassing op code-kwaliteit, volledig-stapel, en stadium-slechts pijpleidingen.

Geïnteresseerd in de bèta? E-mail [&#x200B; beta_quickbuild_cmpipelines@adobe.com &#x200B;](mailto:beta_quickbuild_cmpipelines@adobe.com) met uw Adobe OrgID en identiteitskaart van het Programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### Je eigen gang (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [&#x200B; externe bewaarplaatsen in Cloud Manager &#x200B;](/help/managing-code/external-repositories.md) toevoegen.

![&#x200B; voeg de dialoogdoos van de Bewaarplaats &#x200B;](/help/release-notes/assets/azure-repo.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [&#x200B; Grp-CloudManager_BYOG@adobe.com &#x200B;](mailto:grp-cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [&#x200B; de Tokens van de Toegang beheren &#x200B;](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Bugfixes {#bug-fixes}

Er zijn geen significante insectenmoeilijke situaties in de versie van Oktober Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
