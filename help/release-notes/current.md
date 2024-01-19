---
title: Opmerkingen bij de release 2024.1.0
description: Dit zijn de opmerkingen bij de release 2024.1.0 voor Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Opmerkingen bij de release 2024.1.0 voor Cloud Manager {#release-notes}

Op deze pagina worden de opmerkingen bij de release voor [!UICONTROL Cloud Manager] release 2024.1.0.

>[!NOTE]
>
>Raadpleeg voor de meest recente releaseopmerkingen voor Cloud Manager in AEM as a Cloud Service de [Cloud Manager in AEM opmerkingen bij de huidige release van as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Releasedatum {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] release 2024.1.0 is 17 januari 2024. De volgende release is gepland voor 16 februari 2024.

## Programma voor vroegtijdige adoptie {#early-adoption}

Maak deel uit van ons programma voor vroege goedkeuring en heb de kans om een aantal van de volgende kenmerken te testen

### Breng uw eigen GitHub {#byo-github}

Als u GitHub gebruikt om uw bewaarplaatsen te beheren, [u kunt code binnen uw bewaarplaatsen van GitHub door de Manager van de Wolk nu bevestigen.](/help/managing-code/byo-github.md) Door deze integratie is het niet nodig de code consistent te synchroniseren met de opslagplaats van de Adobe en kunt u terugtrekkingsverzoeken verifiëren voordat u ze samenvoegt in de hoofdvertakkingen.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `Grp-CloudManager_BYOG@adobe.com` van uw e-mailadres dat aan uw Adobe ID is gekoppeld.

## Opgeloste problemen {#bug-fixes}

* Er is een fout gecorrigeerd voor enkele hoekgevallen waarbij downloaden is mislukt als gevolg van de manier waarop de testtoepassing gegevens interpreteert, waardoor het totale foutenpercentage de test niet heeft doorstaan.
* Wanneer een bouwstijlstap met status eindigt `FAILED` vanwege een `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`, wordt deze nu correct beschreven als een fout vanwege samenvoegconflicten met de doelvertakking.