---
title: Gebruikersreis
description: In dit document worden de verschillende instapscenario's beschreven en wordt uitgelegd hoe u aan de slag gaat met Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---


# Gebruikersreis {#user-journey}

Als Adobe Experience Manager-gebruiker kunt u:

* Wees nieuw om te AEM.
* Wees momenteel bezig met AEM 6.x.
* U moet een upgrade uitvoeren naar AEM versie 6.5 om [!UICONTROL Cloud Manager] te kunnen gebruiken.

In dit document worden deze scenario&#39;s beschreven en wordt uitgelegd hoe u aan de slag gaat met [!UICONTROL Cloud Manager] .

>[!NOTE]
>
>[!UICONTROL Cloud Manager] is alleen beschikbaar voor Adobe Managed Services (AMS)-klanten die AEM 6.4 of hoger gebruiken.

## Onboarding {#onboarding}

Het instapproces verschilt afhankelijk van de vraag of u nieuw bent voor AMS of een bestaande AMS-klant bent.

### Nieuw bij Adobe Managed Services {#new-to-ams}

Als nieuwe klant wordt u als onderdeel van het instapproces aan Adobe Managed Services aangemeld bij [!UICONTROL Cloud Manager] .

Als onderdeel van het instapproces ontvangt u een welkomstbericht met de volgende informatie:

* De URL voor toegang [!UICONTROL Cloud Manager]
* Instructies voor aanmelden bij [!UICONTROL Experience Cloud]
* Instructies voor het gebruik van de Admin Console voor het beheer van uw gebruikers en hun respectieve machtigingen, zodat zij [!UICONTROL Cloud Manager] indien nodig kunnen openen.

### Bestaande Adobe Managed Services-klant {#existing-customer}

Als bestaande klant van AMS, zult u eerst uw bestaande productie en non-production milieu&#39;s aan AEM 6.4 of hoger moeten bevorderen.

Tijdens het uitvoeren van de upgrade gaat u naar Cloud Manager en ontvangt u de URL voor toegang tot [!UICONTROL Cloud Manager] . Bovendien moet u voor gebruikers die toegang moeten krijgen tot [!UICONTROL Cloud Manager] de Admin Console gebruiken om ze en hun respectievelijke machtigingen te beheren.

Uw bestaande AEM-project moet ook voldoen aan de aanbevolen aanbevolen best practices, aangezien u [!UICONTROL Cloud Manager] gaat gebruiken voor het implementeren van nieuwe codewijzigingen in uw AEM.

Om extra informatie over de voordelen te krijgen om aan AEM 6.5 te bevorderen, zie het document [ Bevorderend aan AEM 6.5 ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html).

## Toegang verkrijgen tot [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

U krijgt toegang tot [!UICONTROL Cloud Manager] en uw AEM door u eenvoudig aan te melden bij de landingspagina van [!UICONTROL Experience Cloud] met behulp van uw Adobe Identity Management-referenties en AEM te selecteren via de interface van de oplossingsschakeler.

Nadat u zich voor het eerst hebt aangemeld bij [!UICONTROL Cloud Manager] , hebt u rechtstreeks vanuit de [!UICONTROL Cloud Manager] -gebruikersinterface toegang tot uw AEM. U bent nu klaar om alle mogelijkheden van [!UICONTROL Cloud Manager] te verkennen en uw eerste codevertakking voor te bereiden om te worden geïmplementeerd in uw werkgebied- en productieomgeving.

Om met [!UICONTROL Cloud Manager] begonnen te worden, zie het document [ Eerste Login van de Tijd ](/help/getting-started/first-time-login.md).

Voor extra informatie over AEM, zie het document [ Opstellend en het Onderhouden ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html).

## Aan de slag met [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Nadat u zich hebt aangemeld bij [!UICONTROL Cloud Manager] , kunt u aan de slag gaan met uw AEM project door:

1. De omgeving van de gegevensopslagruimte instellen.
1. Uw team en rollen instellen.
   * Rollidmaatschappen worden toegewezen door de gebruiker aan een [!UICONTROL Cloud Manager] -profiel toe te voegen met de Admin Console.
1. Stel de broncodevertakkingen in de it-opslagplaats in.
1. Het bepalen van uw doelstellingen in termen van lading en prestaties KPIs.
1. Het bepalen van testscenario&#39;s om uw code aan uw stadium en productiemilieu&#39;s met succes op te stellen zodra alle kwaliteitscontroles succesvol zijn overgegaan.

## End-to-end reis {#end-to-end-journey}

Dit diagram illustreert de reis van de klant op een hoog niveau wanneer het gebruiken van [!UICONTROL Cloud Manager] CI/CD pijpleiding voor het opstellen van uw codeveranderingen in uw het opvoeren en productiemilieu&#39;s.

![ reis van begin tot eind ](/help/assets/screen_shot_2018-05-15at124004pm.png)
