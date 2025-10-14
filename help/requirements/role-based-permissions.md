---
title: Op rollen gebaseerde machtigingen
description: Meer informatie over vooraf geconfigureerde, op rollen gebaseerde machtigingen van Cloud Manager voor het beheer van de toegang tot uw cloudbronnen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 3%

---


# Op rollen gebaseerde machtigingen {#role-based-permissions}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code door te sturen naar de Git-opslagplaats. Een bedrijfseigenaar heeft verschillende toestemmingen die hen toestaan om de belangrijkste prestatiesindicatoren (KPIs) te bepalen en plaatsingen goed te keuren.

>[!NOTE]
>
>In deze documentatie worden op rollen gebaseerde machtigingen voor Cloud Manager for Adobe Managed Services (AMS) beschreven.
>
>De gelijkwaardige documentatie voor AEM as a Cloud Service kan in het document [&#x200B; Inleiding aan Cloud Manager &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) in de documentatie van AEM as a Cloud Service worden gevonden.

## Gebruikersrollen {#user-roles}

Het beheer van de rol voor [!UICONTROL Cloud Manager] wordt gedaan gebruikend [&#x200B; Admin Console &#x200B;](https://helpx.adobe.com/nl/enterprise/using/admin-console.html). Elke gebruiker van [!UICONTROL Cloud Manager] moet lid zijn van de IMS-organisatie van de klant en over de Adobe Managed Services-productcontext beschikken. U kunt leden van specifieke rollen toevoegen door de gebruiker toe te voegen aan een [!UICONTROL Cloud Manager] -productprofiel in de Admin Console.

Meer over leren hoe te opstelling uw rollen, zie [&#x200B; de Gebruikers en Rollen van de Vestiging &#x200B;](/help/requirements/users-and-roles.md).

De volgende tabel bevat een lijst met de rollen die u in de Admin Console kunt toewijzen.

| [!UICONTROL Cloud Manager] rol | Beschrijving |
|---|---|
| Business Owner | De primaire gebruiker die de initiële [!UICONTROL Cloud Manager] opstelling voltooit en verantwoordelijk is voor het bepalen van KPIs, het goedkeuren van productieleidingen, en het met voeten treden van belangrijke drie-rij mislukkingen wanneer noodzakelijk. |
| Inhoudsauteur | De gebruiker communiceert doorgaans niet met Cloud Manager, maar kan de Cloud Manager-programmaschakeloptie (die vanuit Experience Cloud is navigeerd) gebruiken om toegang te krijgen tot Adobe Experience Manager (AEM). |
| Klantsuccesvolle technicus | De gebruiker ondersteunt vooral het succes van AMS-klanten en werkt met [!UICONTROL Cloud Manager] aan implementaties. Deze implementaties vereisen toezicht van een Adobe Customer Success Engineer (CSE). |
| Deployment Manager | De gebruiker beheert de implementatiebewerkingen met behulp van [!UICONTROL Cloud Manager] voor het uitvoeren van stage- en productieimplementaties, kan indien nodig belangrijke 3-laagse fouten goedkeuren en heeft toegang tot de Git-opslagruimte. |
| Developer | De gebruiker ontwikkelt en test de code van de douanetoepassing, hoofdzakelijk gebruikt [!UICONTROL Cloud Manager] om plaatsingsstatus te bekijken, en heeft geëngageerd-toegang tot de bewaarplaats van de Git. |
| Program Manager | De gebruiker gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke drie-rij mislukkingen goedkeuren wanneer noodzakelijk. |

## Gebruikersmachtigingen {#user-permissions}

Elk van de rollen heeft specifieke, bijbehorende preconfigured toestemmingen. De volgende lijst maakt een lijst van de beschikbare toestemmingen en de rollen die hen kunnen uitvoeren.

| Machtiging | Beschrijving | Business Owner | Deployment Manager | Program Manager | Developer | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | KPI&#39;s van programma lezen | x | x | x | x | x |
| `Write Application` | Programma instellen of bewerken | x | | | | |
| `Add Program` | Nieuw programma toevoegen | x |  |  |  |  |
| `Read Environment` | Zie omgevingsdetails | x | x | x | x | x |
| `Create Execution` | Pijpleiding starten | x | x | x | | |
| `Read Execution` | Zie uitvoeringsstatus | x | x | x | x | x |
| `Resume Execution` | Mogelijkheid om uitvoering te hervatten wanneer gepauzeerd | x | x | x | | x |
| `Execution Approve Deploy to Production` | Live goedkeuring bieden | x | x | x | | |
| `Execution Schedule Deploy to Production` | Implementatie van productieplanning | x | x | x | | x |
| `Execution Deploy to Production` | Toepassing implementeren op productie wanneer gepauzeerd voor CSE-toezicht |  |  |  |  | x |
| `Execution Cancel` | Huidige uitvoering annuleren |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | Belangrijke kwaliteitsgate-fouten goedkeuren | x | x | x |  |  |
| `Pipeline Create` | Gasleiding instellen/bewerken |  | x |  |  |  |
| `Pipeline Read` | Zie details over pijpleidingen | x | x | x | x | x |
| `Pipeline Write` | Gasleiding instellen/bewerken |  | x |  |  |  |
| P`ipeline Modify Approval` | Hiermee kunt u de optie Bedrijfseigenaar bewerken |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | Staat het uitgeven van de CSE toezichtoptie toe |  | x |  |  |  |
| `Pipeline Delete` | Staat pijpleiding toe schrapping |  | x |  |  |  |
| `Step Read` | Zie de resultaten van de metrische gegevens voor de stapkwaliteit | x | x | x | x | x |
| `Generate Personal Access Token` | Toegangsgat |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Meer over leren hoe te opstelling uw gebruikers, zie [&#x200B; de Gebruikers en Rollen van de Vestiging &#x200B;](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Aangepaste machtigingsprofielen met configureerbare machtigingen zijn ook beschikbaar. Zie [&#x200B; de Toestemmingen van de Douane &#x200B;](/help/using/custom-permissions.md) voor meer details.
