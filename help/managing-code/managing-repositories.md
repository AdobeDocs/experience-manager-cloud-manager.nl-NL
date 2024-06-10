---
title: Opslagplaatsen beheren in Cloud Manager
description: Leer hoe u uw git-opslagruimten maakt, weergeeft en bewerkt in Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 73add7bee892769d1b3864e3238aff26bf96162d
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# Opslagplaatsen voor Cloud Manager {#cloud-manager-repos}

Leer hoe u uw git-opslagruimten maakt, weergeeft en bewerkt in Cloud Manager.

## Overzicht {#overview}

Opslagplaatsen worden gebruikt om de code van uw project op te slaan en te beheren met behulp van Git. Voor elk programma dat u maakt in Cloud Manager is een opslagplaats met beheerde Adobe gemaakt.

U kunt desgewenst extra opslagruimten voor Adobe-beheer maken en ook uw eigen persoonlijke opslagruimten toevoegen. Alle opslagruimten die bij uw programma horen, kunnen worden weergegeven in de **Opslagplaatsen** venster.

In Cloud Manager gemaakte opslagruimten kunnen ook worden geselecteerd wanneer u pijpleidingen toevoegt of bewerkt. Zie [CI-CD-pijpleidingen](/help/overview/ci-cd-pipelines.md) voor meer informatie.

Er is één enkele primaire bewaarplaats of een tak voor om het even welke bepaalde pijpleiding. Met [ondersteuning voor git-submodules,](git-submodules.md) veel secundaire vertakkingen kunnen tijdens de bouwperiode worden opgenomen .

## Venster Opslagplaatsen {#repositories-window}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Van de **Programmaoverzicht** pagina, selecteert u de **Opslagplaatsen** tab naar **Opslagplaatsen** pagina.

1. De **Opslagplaatsen** worden alle aan uw programma gekoppelde opslagruimten weergegeven.

   ![Venster Opslagplaatsen](assets/repositories.png)

De **Opslagplaatsen** venster bevat informatie over de opslagplaatsen:

* Het type gegevensopslagruimte
   * **Adobe** geeft opslagruimten aan die door Adobe worden beheerd
   * **GitHub** wijst op privé bewaarplaatsen GitHub die u beheert
* Toen het werd gemaakt
* Pijpleidingen die zijn gekoppeld aan de opslagplaats

U kunt de repository selecteren in het venster en op de elliptische knop klikken om actie te ondernemen in de geselecteerde repository.

* **[Branches controleren / Project maken](#check-branches)** (alleen beschikbaar voor opslagplaatsen voor Adoben)
* **[Repository-URL kopiëren](#copy-url)**
* **[Weergeven en bijwerken](#view-update)**
* **[Verwijderen](#delete)**

![Handelingen in opslagplaats](assets/repository-actions.png)

## Opslagplaatsen toevoegen {#adding-repositories}

Tik of klik op de knop **Opslagplaats toevoegen** in de **Opslagplaatsen** venster om het **Opslagplaats toevoegen** wizard.

![wizard Opslagplaats toevoegen](assets/add-repository-wizard.png)

Cloud Manager ondersteunt beide opslagruimten die door Adobe worden beheerd (**Opslagplaats Adobe**) en uw eigen zelfbeheerde opslagplaatsen (**Particuliere opslagplaats**). De vereiste velden zijn afhankelijk van het type opslagplaats dat u wilt toevoegen. Raadpleeg de volgende documenten voor meer informatie.

* [Opslagplaatsen voor Adoben toevoegen in Cloud Manager](adobe-repositories.md)
* [Persoonlijke opslagplaatsen toevoegen in Cloud Manager](private-repositories.md)

>[!NOTE]
>
>* Een gebruiker moet de rol hebben **Implementatiebeheer** of **Zakelijke eigenaar** om een gegevensopslagruimte te kunnen toevoegen.
>* Er geldt een limiet van 300 gegevensbanken voor alle programma&#39;s in een bepaalde onderneming of IMS-organisatie.

## Repo-info openen {#repo-info}

Wanneer u uw opslagruimten in de **Opslagplaatsen** venster, kunt u de details bekijken over hoe te om tot Adobe-beheerde bewaarplaatsen programmatically toegang te hebben door te tikken of te klikken **Repo-info openen** in de werkbalk.

![Informatie over opslagplaats](assets/access-repo-info.png)

De **Info opslagplaats** venster wordt geopend met de details. Zie het document voor meer informatie over het benaderen van gegevens in de repository [Toegang tot gegevens opslagplaats.](accessing-repositories.md)

## Branches controleren {#check-branches}

De **Branches controleren / Project maken** actie voert twee functies uit afhankelijk van de staat van de bewaarplaats.

* Als de opslagplaats nieuw wordt gecreeerd, leidt de actie tot een steekproefproject dat op wordt gebaseerd [het AEM project archetype.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview)
* Als de gegevensopslagplaats reeds het steekproefproject heeft gecreeerd, controleert het de staat van de bewaarplaats en zijn takken en meldt terug als het steekproefproject reeds bestaat.

![Vertakkingen controleren, actie](assets/check-branches.png)

## Repository-URL kopiëren {#copy-url}

De **Repository-URL kopiëren** de actie kopieert URL van de bewaarplaats die in **Opslagplaatsen** naar het klembord voor gebruik elders.

## Weergeven en bijwerken {#view-update}

De **Weergeven en bijwerken** handeling opent de **Opslagplaats bijwerken** in. Met deze functie kunt u de **Naam** en **URL-voorvertoning opslagplaats** en de **Beschrijving** van de gegevensopslagruimte.

![Gegevens in de opslagplaats weergeven en bijwerken](assets/update-repository.png)

## Verwijderen {#delete}

De **Verwijderen** de actie verwijdert de bewaarplaats uit uw project. Een opslagplaats kan niet worden geschrapt als het met een pijpleiding wordt geassocieerd.

![Verwijderen](assets/delete.png)

Wanneer een opslagplaats wordt verwijderd in Cloud Manager, wordt deze gemarkeerd als verwijderd en is deze niet langer toegankelijk voor de gebruiker, maar wordt deze in het systeem onderhouden voor hersteldoeleinden.

Als u een nieuwe repository probeert te maken nadat u een repository met dezelfde naam hebt verwijderd, ontvangt u het foutbericht `An error has occurred while trying to create repository. Please contact your CSE or Adobe Support.`

Als u dit foutbericht ontvangt, neemt u contact op met de Adobe Support zodat deze gebruikers kunnen helpen de naam van de verwijderde opslagplaats te wijzigen of een andere naam voor de nieuwe opslagplaats kunnen kiezen.
