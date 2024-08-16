---
title: Gebruikersreis
description: Meer informatie over de verschillende instapscenario's en Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Reis gebruiker {#user-journey}

Als gebruiker van de AEM (Adobe Experience Manager), past u waarschijnlijk één van de volgende scenario&#39;s:

* Je bent nieuw om te AEM.
* U gebruikt momenteel AEM 6.x.
* U moet een upgrade uitvoeren naar AEM 6.5 om [!UICONTROL Cloud Manager] te kunnen gebruiken.

In dit document worden deze drie scenario&#39;s beschreven en wordt uitgelegd hoe u aan de slag gaat met [!UICONTROL Cloud Manager] .

>[!NOTE]
>
>[!UICONTROL Cloud Manager] is alleen beschikbaar voor Adobe Managed Services (AMS)-klanten die AEM 6.4 of hoger gebruiken.

## Onboarding {#onboarding}

Het instapproces verschilt afhankelijk van de vraag of u nieuw bent voor AMS of een bestaande AMS-klant bent.

### Nieuw bij Adobe Managed Services {#new-to-ams}

Als nieuwe klant wordt u als onderdeel van het instapproces aan Adobe Managed Services aangemeld bij [!UICONTROL Cloud Manager] .

Als onderdeel van het instapproces ontvangt u een welkomstbericht dat het volgende bevat:

* De URL die moet worden geopend [!UICONTROL Cloud Manager].
* Instructies voor het aanmelden bij [!UICONTROL Experience Cloud] .
* Instructies voor het gebruik van de Admin Console voor het beheer van uw gebruikers en hun respectieve machtigingen, zodat zij [!UICONTROL Cloud Manager] indien nodig kunnen openen.

### Huidige Adobe Managed Services-klant {#existing-customer}

Als bestaande klant van AMS, moet u eerst uw bestaande productie en non-production milieu&#39;s aan AEM 6.4 of hoger bevorderen.

Tijdens de upgrade gaat u naar Cloud Manager en ontvangt u de URL voor toegang tot [!UICONTROL Cloud Manager] . Bovendien moet u voor gebruikers die toegang moeten krijgen tot [!UICONTROL Cloud Manager] de Admin Console gebruiken om ze en hun respectievelijke machtigingen te beheren.

Uw bestaande AEM project moet ook voldoen aan de aanbevolen aanbevolen best practices, omdat u [!UICONTROL Cloud Manager] gaat gebruiken voor het implementeren van nieuwe codewijzigingen in uw AEM.

Om extra informatie over de voordelen te krijgen om aan AEM 6.5 te bevorderen, zie [ Bevorderend aan AEM 6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Toegang [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Meld u aan bij de bestemmingspagina van [!UICONTROL Experience Cloud] met uw Identity Management-gegevens voor Adobe. Selecteer AEM van de oplossingsschakelaar om [!UICONTROL Cloud Manager] en uw AEM-omgevingen te openen.

Nadat u zich voor het eerst hebt aangemeld bij [!UICONTROL Cloud Manager] , hebt u rechtstreeks vanuit de gebruikersinterface van [!UICONTROL Cloud Manager] toegang tot uw AEM. U bent nu klaar om alle mogelijkheden van [!UICONTROL Cloud Manager] te verkennen en uw eerste codevertakking voor te bereiden om te worden geïmplementeerd in uw werkgebied- en productieomgeving.

Om met [!UICONTROL Cloud Manager] begonnen te worden, zie [ Eerste Login van de Tijd ](/help/getting-started/first-time-login.md).

Voor extra informatie over AEM, zie [ het Opstellen en het Onderhouden ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Aan de slag met [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Nadat u zich bij [!UICONTROL Cloud Manager] hebt aangemeld, kunt u als volgt aan de slag gaan met uw AEM project:

1. Stel de omgeving van de gegevensopslagruimte in.
1. Stel uw team en rollen in. Rollidmaatschappen worden toegewezen door de gebruiker aan een [!UICONTROL Cloud Manager] -profiel toe te voegen met de Admin Console.
1. Stel de broncodevertakkingen in de Git-opslagplaats in.
1. Definieer uw doelstellingen in termen van belasting en prestaties KPIs (Zeer belangrijke Indicatoren van Prestaties).
1. Definieer testscenario&#39;s om uw code met succes te implementeren in de werkgebied- en productieomgeving nadat alle kwaliteitscontroles zijn geslaagd.

## Eind-aan-eind reis {#end-to-end-journey}

Dit diagram illustreert de klantenreis op een hoog niveau wanneer het gebruiken van de [!UICONTROL Cloud Manager] CI/CD pijpleiding voor het opstellen van uw codeveranderingen in uw het opvoeren en productiemilieu&#39;s.

![ reis van begin tot eind ](/help/assets/screen_shot_2018-05-15at124004pm.png)
