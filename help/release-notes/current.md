---
title: Opmerkingen bij de release voor Cloud Manager 2024.12.0
description: Meer informatie over de release van Cloud Manager 2024.12.0 over Adobe Managed Services.
feature: Release Information
source-git-commit: ee79124a012106e53ffaaf9462202712f7078809
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2024.12.0 over Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2024.12.0 over Adobe Managed Services.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

De releasedatum voor [!UICONTROL Cloud Manager] 2024.12.0 is 5 december 2024.

De volgende geplande release is 23 januari 2025.

## Nieuwe functies {#what-is-new}

* De stap AEM Codekwaliteit gebruikt nu SonarQube 9.9 Server, die de oudere versie 7.4 vervangt. Deze verbetering brengt extra veiligheid, prestaties, en controles van de codekwaliteit, die uitvoerigere analyse en dekking voor uw projecten aanbieden. <!-- CMGR-45683 -->

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de opslagplaats van de Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

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
