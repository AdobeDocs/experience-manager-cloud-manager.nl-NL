---
title: Opmerkingen bij de release voor Cloud Manager 2025.1.0
description: Meer informatie over de release van Cloud Manager 2025.1.0 over Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
source-git-commit: 434740b5ad2dafd5a6c55d0272cf5effdfa6baac
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.1.0 over Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Meer informatie over de release van [!UICONTROL Cloud Manager] 2025.1.0 over Adobe Managed Services.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Releasedatums {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

De releasedatum voor [!UICONTROL Cloud Manager] 2025.1.0 is woensdag 22 januari 2024.

De volgende geplande release is donderdag 13 februari 2025.

## Nieuwe functies {#what-is-new}

**Regels van de Kwaliteit van de Code - Songaaar de Verbetering van de Kubus:** de stap van de Kwaliteit van de Code van Cloud Manager zal beginnen SonarQube Server 9.9 met de versie van Cloud Manager 2025.2.0 te gebruiken, die voor Donderdag, 13 februari, 2025 wordt gepland.

Om voor te bereiden, zijn de bijgewerkte regels SonarQube nu beschikbaar bij [ Regels van de Kwaliteit van de Code ](/help/using/code-quality-testing.md#code-quality-testing-step).

U kunt de nieuwe regels &quot;vroege controle&quot;door de volgende variabele van de pijpleidingstekst (zie hieronder schermafbeelding) te plaatsen:

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Stel bovendien de volgende variabele in om ervoor te zorgen dat de stap voor de codekwaliteit wordt uitgevoerd voor dezelfde commit (wordt normaal gesproken overgeslagen voor dezelfde `commitId`):

`CM_DISABLE_BUILD_REUSE` = `true`

![ pagina van de Configuratie van Variabelen ](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>De Adobe adviseert het creëren van een nieuwe pijpleiding van de Kwaliteit van CI/CD Code, die aan de zelfde tak wordt gevormd zoals uw belangrijkste productiepijplijn. Plaats de aangewezen variabelen *vóór* 13 februari, versie 2025 om te bevestigen dat de nieuwe gedwongen regels geen blockers introduceren.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
