---
title: Beveiliging en privacy
description: Meer informatie over de beveiliging en privacy van uw code en artefactelementen in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Beveiliging en privacy {#security-and-privacy}

Meer informatie over de beveiliging en privacy van uw code en artefactelementen in Cloud Manager.

## Rollen en machtigingen {#roles}

[!UICONTROL Cloud Manager] heeft vooraf geconfigureerde rollen met de juiste machtigingen.

Om over de mogelijke rollen te leren u in de Admin Console en gebruikersroltoestemmingen kunt toewijzen, verwijs naar het document [ Op rol-Gebaseerde Toestemmingen.](/help/requirements/role-based-permissions.md)

## Bronisolatie {#resource-isolation}

[!UICONTROL Cloud Manager] -klanten hebben hun IMS-referenties nodig om te verifiëren dat alle machtigingen die aan [!UICONTROL Cloud Manager] zijn gekoppeld, aan hun IMS-organisaties zijn gekoppeld. Tijdens het instapproces zorgt het inrichtingsteam ervoor dat de bronisolatie wordt afgedwongen in [!UICONTROL Cloud Manager] .

## Gegevensbeveiliging {#data-security}

Code in [!UICONTROL Cloud Manager] wordt tijdens de doortocht versleuteld. De bindingen die Cloud Manager bouwt worden ook gecodeerd in transit en wanneer opgeslagen.

Elke klant krijgt zijn eigen git bewaarplaats en de code is veilig en niet gedeeld met andere organisaties.

## Gegevensprivacy {#data-privacy}

[!UICONTROL Cloud Manager] houdt zich aan de privacybeginselen die door Adobe worden gedefinieerd. Ontwikkelaars zetten code veilig in git repositories via HTTPS.

De gebruikersinterface van [!UICONTROL Cloud Manager] is gebaseerd op services die voldoen aan een algemeen besturingsframework van de Adobe dat. De gebruikersinterface van [!UICONTROL Cloud Manager] gebruikt beveiligde services van verschillende cloudproviders.
