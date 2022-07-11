---
title: Opmerkingen bij de release 2021.11.0
description: Volg deze pagina voor informatie over Cloud Manager Release 2021.11.0
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Opmerkingen bij de release 2021.11.0 {#release-notes-for}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!UICONTROL Cloud Manager] Release 2021.11.0.

>[!NOTE]
>Zie [Opmerkingen bij de huidige release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) om de meest recente releaseopmerkingen voor Cloud Manager in AEM as a Cloud Service te bekijken.

## Releasedatum {#release-date}

De releasedatum voor [!UICONTROL Cloud Manager] Versie 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 16 december 2021.

## Wat is er nieuw? {#whats-new}

* De Vastleggingsidentiteitskaart van het Git zal nu in de details van de pijpleidingsuitvoering worden getoond die het gemakkelijker maken om de code te volgen die werd gebouwd.

* De `x-request-id` responsheader is nu zichtbaar in de API-afspeelruimte op [www.adobe.io](https://www.adobe.io/). Deze kopbal is nuttig wanneer het voorleggen van de kwesties van de klantenzorg voor het oplossen van problemen.

* Als gebruiker zie ik een pijplijnkaart met nulpijpleidingen die mij de juiste begeleiding biedt.

* Een nieuwe pagina van de Activiteit is nu beschikbaar waar de activiteiten zoals pijpleiding en codeuitvoering samen met hun bijbehorende details kunnen worden bekeken. In de loop der tijd zullen de activiteiten die op deze pagina worden vermeld, in het toepassingsgebied worden uitgebreid, samen met de verstrekte gegevens.

* Er is nu een nieuwe pagina met pijplijnen beschikbaar met een statuspop-up, zodat u de samenvatting van de details eenvoudig kunt bekijken. De uitvoeringen van de pijpleiding kunnen samen met hun bijbehorende details worden bekeken.

* De Edit Pijpleiding API steunt nu het plaatsen van de invalidatie van de verzender en spoelwegen.

* De Edit Pijpleiding API steunt nu het veranderen van het milieu dat in de plaatsingsfasen wordt gebruikt.

* Voor grote pakketten is een optimalisatie in het OakPal-scanproces geïntroduceerd.

* Het CSV-bestand voor kwaliteitsafgifte bevat nu de tijdstempel voor elke kwaliteitsuitgave.

* De knop Beheren op de pagina Omgevingen is niet meer zichtbaar in de gebruikersinterface.

## Opgeloste problemen {#bug-fixes}

* Bepaalde unorthodox bouwt configuraties resulteerde in onnodige dossiers die in het geheime voorgeheugen van Maven van de pijpleiding worden opgeslagen die in vreemde netwerk I/O resulteerde toen het beginnen en het tegenhouden van de bouwstijlcontainer.

* De PATCH API van de pijpleiding ontbreekt als de plaatsingsfase niet bestaat.

* De `ClientlibProxyResourceCheck` de kwaliteitsregel leverde fout-positieve problemen op wanneer er clientbibliotheken waren met algemene basispaden.

* Foutbericht wanneer het maximale aantal opslagplaatsen is bereikt, geeft geen reden voor de fout aan.

* In zeldzame gevallen faalden de pijpleidingen vanwege een onjuiste herbehandeling van bepaalde responscodes.