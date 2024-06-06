---
title: Opmerkingen bij de release 2024.6.0
description: Dit zijn de opmerkingen bij de release 2024.6.0 voor Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Opmerkingen bij de release 2024.6.0 voor Cloud Manager {#release-notes}

Op deze pagina worden de opmerkingen bij de release voor [!UICONTROL Cloud Manager] release 2024.6.0.

>[!NOTE]
>
>Raadpleeg voor de meest recente releaseopmerkingen voor Cloud Manager in AEM as a Cloud Service de [Cloud Manager in AEM opmerkingen bij de huidige release van as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Releasedatum {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] release 2024.6.0 is 6 juni 2024. De volgende release is gepland voor 11 juli 2024.

## Wat is er nieuw? {#what-is-new}

* U kunt nu [gebruik uw eigen GitHub-repositories](/help/managing-code/private-repositories.md) als bronnen voor zowel volledig-stapelpijpleidingen als frontpijpleidingen.
   * Bovendien kunt u uit bewaarplaatsen GitHub met voordeel halen [git-submodules;](/help/managing-code/git-submodules.md) voorzien u van verbeterde controle over de auto-geproduceerde pijpleidingen die voor de bevestiging van het trekkingsverzoek worden gebruikt en het toestaan van u om gedrag voor cruciale metriek tijdens de fase van het codescannen te bepalen.
   * [U kunt ook](/help/managing-code/github-check-config.md) om de rapportgeschiedenis op GitHub te bewaren, noem de pijpleiding, en plaats pijpleidingsvariabelen om uw behoeften aan te passen.
* Er zijn nieuwe OakPal-regels toegevoegd aan de [Codekwaliteitsscan van Cloud Manager.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * Elke nieuwe regel die vanaf juni 2024 wordt toegevoegd, is een onverbrekelijke verandering.
   * U wordt aangespoord deze problemen zo snel mogelijk aan te pakken, aangezien deze nieuwe regels ertoe zullen leiden dat pijpleidingen mislukken vanaf de release Cloud Manager August 2024.

## Programma voor vroegtijdige adoptie {#early-adoption}

Maak deel uit van ons programma voor vroege goedkeuring en heb de kans om een aantal van de volgende kenmerken te testen

### Pijpleidingen, alleen voor de productie {#staging-production-only-pipelines}

Ondersteuning voor [pijpleidingen die uitsluitend bestemd zijn voor de productie](/help/using/stage-prod-only.md) is geïntroduceerd, toelatend u om volledig-stapelpijpleidingen van de productieleiding in kleinere, gespecialiseerde plaatsingen te verdelen.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar  `Grp-cloudmanager_splitpipelines@adobe.com` van uw e-mailadres dat aan uw Adobe ID is gekoppeld.
