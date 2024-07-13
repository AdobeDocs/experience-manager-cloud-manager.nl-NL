---
title: GitHub-controleannotaties
description: Leer hoe de controles GitHub PRs voor uw privé bewaarplaatsen annoteert om u te verstrekken zult nuttig terugkoppelen.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 210d40a5e12b40fd84efc461c6a1c48559120837
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# GitHub-controleannotaties {#github-annotations}

Leer hoe de controles GitHub PRs voor uw privé bewaarplaatsen annoteert om u te verstrekken zult nuttig terugkoppelen.

## Overzicht {#overview}

Als u [ privé bewaarplaatsen ](private-repositories.md) voor uw programma van Cloud Manager gebruikt, worden de controles in GitHub automatisch in werking gesteld voor elk trekkingsverzoek. Deze worden voorzien van nuttige informatie om u te helpen om het even welke kwesties met uw code zo snel mogelijk begrijpen.

![ Voorbeeld van GitHub controleannotaties ](assets/github-check-annotations.png)

{de kwaliteit van de 0} Code ](/help/using/code-quality-testing.md) kwesties die door [ worden ontdekt SonarQube ](/help/using/custom-code-quality-rules.md) zijn duidelijk vermeld.[

![ Voorbeeld van de annotatie van de codekwestie ](assets/github-check-annotations-example.png)

De exacte coderegel met de uitgave is opgegeven en u kunt erop klikken om de relevante code weer te geven. Deze annotaties worden gegeven voor alle code kwesties, niet alleen die veranderd in het trekkingsverzoek.

![ Voorbeeld van de annotatie van de codekwestie ](assets/github-check-annotations-example-code.png)

Alle geannoteerde lijnen worden samengevoegd op het **Gewijzigde Dossiers** lusje op het trekkingsverzoek GitHub. Annotaties voor bestanden die niet zijn gewijzigd in de pull-aanvraag, worden in hun eigen sectie weergegeven.

![ Voorbeeld van aantekeningen op veranderde dossiers tabel ](assets/github-check-annotations-files-changed.png)

## Codekwaliteitspijplijnen {#code-quality-pipelines}

De [ resultaten van de codekwaliteit ](/help/using/code-quality-testing.md) zijn ook zichtbaar in de pijpleiding die automatisch door Cloud Manager bij de bodem van de **Controles** tabel wordt teweeggebracht. Het is ook toegankelijk van de **Details** van de controle van het trekkingsverzoek.

![ Voorbeeld van annotaties ](assets/github-check-annotations-code-quality.png)

![ Voorbeeld van annotaties ](assets/github-check-annotations-code-quality-2.png)

U kunt de problemen ook visualiseren in de vorm van een CSV. Dit kan door [ worden teruggewonnen het bekijken van de details van de pijpleidingsuitvoering in Cloud Manager.](/help/using/managing-pipelines.md)
