---
title: Beveiliging en privacy
description: Meer informatie over de beveiliging en privacy van uw code en artefactelementen in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Veiligheid en privacy {#security-and-privacy}

Meer informatie over de beveiliging en privacy van uw code en artefactelementen in Cloud Manager.

## Rollen en machtigingen {#roles}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen.

Om over de mogelijke rollen te leren u in de Admin Console en gebruikersroltoestemmingen kunt toewijzen, zie [ Op rol-Gebaseerde Toestemmingen ](/help/requirements/role-based-permissions.md).

## Bronisolatie {#resource-isolation}

[!UICONTROL Cloud Manager] -klanten hebben hun IMS-referenties nodig om te verifiëren dat alle machtigingen die aan [!UICONTROL Cloud Manager] zijn gekoppeld, aan hun IMS-organisaties zijn gekoppeld. Tijdens het instapproces zorgt het inrichtingsteam ervoor dat de bronisolatie wordt afgedwongen in [!UICONTROL Cloud Manager] .

## Gegevensbeveiliging {#data-security}

Code in [!UICONTROL Cloud Manager] wordt tijdens de doortocht versleuteld. De bindingen die Cloud Manager bouwt worden ook gecodeerd in transit en wanneer opgeslagen.

Elke klant krijgt zijn eigen opslagplaats van het Git en de code wordt beveiligd en niet gedeeld met andere organisaties.

## Gegevensprivacy {#data-privacy}

[!UICONTROL Cloud Manager] houdt zich aan de privacybeginselen die door Adobe worden gedefinieerd. Ontwikkelaars plaatsen code veilig in Git-opslagplaatsen via HTTPS.

De gebruikersinterface van [!UICONTROL Cloud Manager] is gebaseerd op services die voldoen aan een gemeenschappelijk besturingsframework voor Adoben. De gebruikersinterface van [!UICONTROL Cloud Manager] gebruikt beveiligde services van verschillende cloudproviders.
