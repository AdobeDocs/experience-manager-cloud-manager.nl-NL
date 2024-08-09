---
title: Opmerkingen bij de release 2024.7.0
description: Meer informatie over de opmerkingen bij de release voor Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager 2024.7.0 {#release-notes}

Deze pagina documenteert de opmerkingen bij de release voor [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Voor de recentste versienota&#39;s voor Cloud Manager in AEM as a Cloud Service, zie [ Cloud Manager in AEM as a Cloud Service huidige versienota&#39;s ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Releasedatum {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] 2024.7.0 is 18 juli 2024. De volgende release is gepland voor 13 augustus 2024.

## Nieuwe functies {#what-is-new}

* De [ productiepijpleiding ](/help/using/production-pipelines.md#adding-production-pipeline) en [ niet-productiepijpleiding ](/help/using/non-production-pipelines.md#adding-non-production-pipeline) trekker **op de Veranderingen van het Git** om de pijpleiding op te starten begaat is nu beschikbaar voor [ privé bewaarplaatsen ](/help/managing-code/private-repositories.md).
* Een pre-productiepijplijn is slechts teweegbrengt manueel en kan niet als **op de Veranderingen van het Git** worden gevormd.
* Voor productie-enige pijpleidingen, omvat de lijst van promotable uitvoeringen uitvoeringen met een artefactversie groter dan de artefactversie die op het productiemilieu wordt opgesteld.
* [ Het AEM Archetype van het Project ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview) is bijgewerkt aan [ versie 49 ](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Word onderdeel van het Cloud Manager-programma voor vroegtijdige adoptie en heb de kans om een aantal van de volgende kenmerken te testen

### Pijpleidingen die uitsluitend bestemd zijn voor de productie {#staging-production-only-pipelines}

De steun voor [ staging-slechts en productie-enige pijpleidingen ](/help/using/stage-prod-only.md) wordt nu geïntroduceerd, latend u volledig-stapeldistributiepijpleidingen van de productie in kleinere, gespecialiseerde plaatsingen verdelen.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `Grp-cloudmanager_splitpipelines@adobe.com` via het e-mailadres dat bij uw Adobe ID hoort.
