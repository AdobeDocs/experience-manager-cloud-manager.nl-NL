---
title: Opmerkingen bij de release voor Cloud Manager 2025.2.0
description: Meer informatie over de release van Cloud Manager 2025.2.0 op Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.2.0 op Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.2.0 op Adobe Managed Services.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

*geen notable insecten of eigenschappen voor de versie van februari van Cloud Manager.*

De releasedatum voor [!UICONTROL Cloud Manager] 2025.2.0 is donderdag 13 februari 2025.

De volgende geplande release is donderdag 13 maart 2025.

## Nieuwe functies {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* Vanaf donderdag 13 februari 2025 gebruikt de stap voor de kwaliteit van de Cloud Manager-code nu een bijgewerkte SonarQube-versie 9.9.5.90363.

  De bijgewerkte regels, beschikbaar voor AMS bij [ deze verbinding ](/help/using/code-quality-testing.md#code-quality-testing-step), bepalen veiligheidsscores en codekwaliteit voor de pijpleidingen van Cloud Manager. Deze update kan van invloed zijn op uw kwaliteitswachttijden en kan implementaties blokkeren.

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de bewaarplaats van Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen degenen) en de **Trekker van de Plaatsing** aan **wordt geplaatst op de Veranderingen van het Git** beginnen nu automatisch.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
