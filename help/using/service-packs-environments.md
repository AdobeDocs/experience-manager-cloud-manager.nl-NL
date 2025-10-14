---
title: Service Pack-updates voor ontwikkelomgevingen - persoonlijke bèta
description: Leer hoe u de updates van het de dienstpak voor de milieu's van de Ontwikkeling door de gebruikersinterface van Cloud Manager kunt in werking stellen.
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Service Pack-updates voor ontwikkelomgevingen (persoonlijke bèta) {#stage-prod-only}

Leer hoe u de updates van het de dienstpak voor de milieu&#39;s van de Ontwikkeling door de gebruikersinterface van Cloud Manager kunt in werking stellen.

>[!NOTE]
>
>Deze eigenschap is slechts beschikbaar aan [&#x200B; het privé bètaprogramma &#x200B;](/help/release-notes/current.md#beta-program).

## Overzicht {#service-pack-updates-overview}

U kunt de updates van het de dienstpak voor de milieu&#39;s van de Ontwikkeling door de gebruikersinterface van Cloud Manager in werking stellen. Met deze functie kunt u controleren op beschikbare servicepack-updates en het installatieproces onafhankelijk beheren.

**Zeer belangrijke voordelen**

* Verstrekt grotere controle over de updates van het de dienstpak van Cloud Manager.
* Minder afhankelijk van Adobe Customer Success Engineers (CSE&#39;s) voor het starten van updates.
* Houdt het volledige updateproces door Cloud Manager bij.

**Huidige beperkingen**

* De optie voor zelfbedieningsupdate is alleen beschikbaar voor ontwikkelomgevingen.
* Beperkte foutmeldingen zijn beschikbaar voor mislukte updates.
* Als er problemen optreden, moet u contact opnemen met CSE&#39;s van Adobe voor verder onderzoek.

## Een servicepack-update starten

1. Meld u aan bij Cloud Manager met de rechten van Deployment Manager.
1. Navigeer naar de pagina Program Overview.
1. Onder de sectie van Milieu, klik ![&#x200B; Meer pictogram, ellips &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![&#x200B; Controle voor de update van het de dienstpak op drop-down menu &#x200B;](/help/using/assets/service-pack-check-for-updates.png)

1. Van het drop-down menu, klik ![&#x200B; Open in het lichte pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Controle voor Updates** om voor de beschikbare updates van het de dienstpak af te tasten.

   ![&#x200B; een lijst van beschikbare updates verschijnt die &#x200B;](/help/using/assets/service-pack-versions.png) beschikbaar zijn

1. Klik op de gewenste versie van het de dienstpak van de lijst.
1. Klik **Service Pack van de Update** om met het updateproces te beginnen.
1. Controleer de details in het bevestigingsdialoogvenster en bevestig de update.

   Zodra bevestigd, begint het installatieproces, en de vooruitgang kan in Cloud Manager worden gevolgd.

## De update van het de dienstpak volgen

Nadat u de update hebt gestart, kunt u de voortgang volgen op de pagina Activiteit voor Cloud Manager.

**om de update van het de dienstpak te volgen:**

1. Navigeer naar de pagina Activiteit vanaf het Cloud Manager-dashboard.
1. Zoek naar de ingang van de Installatie Service Pack.

   ![&#x200B; de installaties van het Pak van de Dienst &#x200B;](/help/using/assets/service-pack-installation.png)

1. Klik op het item om de gedetailleerde voortgang en statusupdates als volgt te bekijken:

   ![&#x200B; Voortgang van de installatie van het de dienstpak &#x200B;](/help/using/assets/service-pack-progression.png)

### Installatiefouten oplossen

* Als de installatie mislukt, activeert Cloud Manager automatisch een terugdraaiactie naar de vorige status.
* Als de kwesties blijven bestaan, klik **Logboek van de Download** om foutenlogboeken te verzamelen, dan de Steun van Adobe voor het oplossen van problemen te contacteren.

## De uitvoering van het servicepack goedkeuren of afwijzen

Zodra de installatie voltooit, wordt uw goedkeuring-of verwerping-vereist om de update te voltooien.

**om de uitvoering van het de dienstpak goed te keuren of te verwerpen:**

1. Open de pagina Activiteit in Cloud Manager.
1. Zoek de goedkeuringsaanvraag in behandeling voor de service pack-update.

   ![&#x200B; verwerp of keur de update van het de dienstpak &#x200B;](/help/using/assets/service-pack-reject-approve.png) goed

1. Voer een van de volgende handelingen uit:

   * Om de update te voltooien, klik **goedkeuren**.

   ![&#x200B; Goedkeuring van het de dienstpak &#x200B;](/help/using/assets/service-pack-approve.png)

   * Om de update te annuleren, klik **Weigeren**.
De installatie van het servicepack wordt geannuleerd en er worden geen wijzigingen toegepast.

   ![&#x200B; Afwijzing van het de dienstpak &#x200B;](/help/using/assets/service-pack-reject.png)
