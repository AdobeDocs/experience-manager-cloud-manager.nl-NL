---
title: Op rollen gebaseerde machtigingen
description: Meer informatie over vooraf geconfigureerde, op rollen gebaseerde machtigingen van Cloud Manager voor het beheer van de toegang tot uw cloudbronnen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fc1bc626dc18d25ce8c5bbae71396b234b5676db
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 2%

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code door te sturen naar de git-opslagplaats. Een bedrijfseigenaar heeft verschillende toestemmingen die hen toestaan om de belangrijkste prestatiesindicatoren (KPIs) te bepalen en plaatsingen goed te keuren.

>[!NOTE]
>
>In deze documentatie worden op rollen gebaseerde machtigingen voor Cloud Manager for Adobe Managed Services (AMS) beschreven.
>
>De gelijkwaardige documentatie voor AEM as a Cloud Service kan in het document [ Inleiding aan Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction.html#role-based-permissions) in de documentatie van AEM as a Cloud Service worden gevonden.

## Gebruikersrollen {#user-roles}

Rolbeheer voor [!UICONTROL Cloud Manager] wordt gedaan gebruikend de [ Admin Console.](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) Elke gebruiker van [!UICONTROL Cloud Manager] moet lid zijn van de IMS-organisatie van de klant en over de Adobe Managed Services-productcontext beschikken. Specifieke rollidmaatschappen worden verstrekt door de gebruiker aan een [!UICONTROL Cloud Manager] productprofiel in de Admin Console toe te voegen.

Meer over leren hoe te om uw rollen te opstelling zie het document [ VestigingsGebruikers en Rollen.](/help/requirements/users-and-roles.md)

Deze lijst maakt een lijst van de rollen u in de Admin Console kunt toewijzen.

| [!UICONTROL Cloud Manager] Rol | Beschrijving |
|---|---|
| Business Owner | Dit is de primaire gebruiker die de eerste [!UICONTROL Cloud Manager] -installatie voltooit en verantwoordelijk is voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het negeren van belangrijke 3-laagfouten indien nodig. |
| Program Manager | Deze gebruiker gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke drie-rij mislukkingen goedkeuren wanneer noodzakelijk. |
| Deployment Manager | Deze gebruiker beheert de implementatiebewerkingen met behulp van [!UICONTROL Cloud Manager] voor het uitvoeren van werkings- en productieimplementaties, kan indien nodig belangrijke fouten op drie niveaus goedkeuren en heeft toegang tot de opslagruimte voor it. |
| Developer | Deze gebruiker ontwikkelt en test de code van de douanetoepassing, hoofdzakelijk gebruikt [!UICONTROL Cloud Manager] om plaatsingsstatus te bekijken, en heeft toegang tot de git bewaarplaats begaan. |
| Klantsuccesvolle technicus | Deze gebruiker ondersteunt doorgaans het succes van de klant voor AMS-klanten en communiceert met [!UICONTROL Cloud Manager] met het doel implementaties uit te voeren waarvoor toezicht van de Customer Success Engineer (CSE) vereist is. |
| Inhoudsauteur | Deze gebruiker communiceert doorgaans niet met Cloud Manager, maar kan de Cloud Manager-programmaschakeloptie (die vanuit Experience Cloud is genavigeerd) gebruiken om toegang te krijgen tot Adobe Experience Manager (AEM). |

## Gebruikersmachtigingen {#user-permissions}

Elk van de rollen heeft specifieke bijbehorende preconfigured toestemmingen. Deze lijst maakt een lijst van de beschikbare toestemmingen en de rollen die hen kunnen uitvoeren.


| Machtiging | Beschrijving | Business Owner | Deployment Manager | Program Manager | Developer | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Toepassing lezen | KPI&#39;s van programma lezen | x | x | x | x | x |
| Toepassing schrijven | Programma instellen of bewerken | x |  |  |  |  |
| Programma toevoegen | Nieuw programma toevoegen | x |  |  |  |  |
| Leesomgeving | Zie omgevingsdetails | x | x | x | x | x |
| Uitvoering maken | Pijpleiding starten | x | x | x |  |  |
| Uitvoering lezen | Zie uitvoeringsstatus | x | x | x | x | x |
| Uitvoering hervatten | Kan uitvoering hervatten wanneer gepauzeerd | x | x | x |  | x |
| Implementatie Goedkeuren Distributie naar productie | Live goedkeuring bieden | x | x | x |  |  |
| Implementatieschema Distribueren naar productie | Implementatie van productieplanning | x | x | x |  | x |
| Implementatie Distribueren naar productie | Toepassing implementeren op productie wanneer gepauzeerd voor CSE-toezicht |  |  |  |  | x |
| Uitvoering annuleren | Huidige uitvoering annuleren |  |  | x |  |  |
| Uitvoering heeft kwaliteitsfouten genegeerd | Belangrijke kwaliteitsgate-fouten goedkeuren | x | x | x |  |  |
| Pipet maken | Gasleiding instellen/bewerken |  | x |  |  |  |
| Pipet gelezen | Zie details over pijpleidingen | x | x | x | x | x |
| Pipet schrijven | Opstelling/geeft pijpleiding uit. |  | x |  |  |  |
| Goedkeuring pijpleiding wijzigen | Hiermee kunt u de optie Bedrijfseigenaar bewerken |  | x |  |  |  |
| Door pijplijn beheerde implementatie wijzigen | Staat het uitgeven van de CSE toezichtoptie toe |  | x |  |  |  |
| Pipet verwijderen | Staat pijpleiding toe schrapping |  | x |  |  |  |
| Stap lezen | Zie de resultaten van de metrische gegevens voor de stapkwaliteit | x | x | x | x | x |
| Token voor persoonlijke toegang genereren | Toegangsuitrusting |  | x |  | x |  |

Meer over leren hoe te opstelling uw gebruikers zien het document [ VestigingsGebruikers en Rollen.](/help/requirements/users-and-roles.md)

>[!TIP]
>
>Aangepaste machtigingsprofielen met configureerbare machtigingen zijn ook beschikbaar. Gelieve te zien de toestemmingen van de Douane van het document [ ](/help/using/custom-permissions.md) voor meer details.
