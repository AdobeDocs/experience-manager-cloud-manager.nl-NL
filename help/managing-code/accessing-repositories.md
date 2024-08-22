---
title: Toegang tot opslagplaats
description: Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde Git-opslagruimten met behulp van het zelf-service Git-accountbeheer van Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u toegang krijgt tot en beheer kunt maken van uw door Adobe beheerde Git-opslagruimten met behulp van het zelf-service Git-accountbeheer in Cloud Manager.

## Toegang tot gegevens in de opslagplaats via de overzichtspagina {#overview-page}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van uw **pagina van het Overzicht van het Programma**.

   ![ de knoop van Info van de Reparatie van de Toegang op de kaart van Milieu ](assets/pipelines-card.png)

1. Klik **Info van de Reactie van de Toegang**. In **Info van de Bewaarplaats voor...** dialoogdoos, kunt u het volgende bekijken:

   * De Git-gebruikersnaam.
   * Het wachtwoord voor Actief.
   * De URL naar de Cloud Manager Git-opslagplaats.
   * De vooraf gebouwde bevelen van de Git om een ver aan uw reactie van de Git en duwcode toe te voegen snel.

   ![ het venster van Info van de Bewaarplaats ](assets/access-repo-info.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. Klik op **`Generate password`**.

1. In **bent u zeker..** dialoogdoos, bevestig de wachtwoordgeneratie door **te klikken produceert wachtwoord**.

   ![ Bevestig wachtwoordgeneratie ](assets/confirm-password-generation.png)

1. Op het **gebied van het Wachtwoord**, wordt het wachtwoord geproduceerd. Klik op het pictogram Kopiëren om het naar het klembord te kopiëren.

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat uw toegangswachtwoord niet op. Zorg ervoor dat u dit wachtwoord veilig opslaat.
   * Als u het wachtwoord verliest, moet u nieuwe produceren.

   ![ Voorbeeld van een geproduceerd wachtwoord ](assets/generated-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en, wanneer u klaar bent, wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

>[!NOTE]
>
>* De **optie van Info van de Reactie van de Toegang** is zichtbaar aan gebruikers met de **rol van de Ontwikkelaar**, of de **rol van de Manager van de Plaatsing**, of allebei.
>* De **knoop van Info van de Reactie van de Toegang** toont slechts de informatie van de bewaarplaatstoegang voor Adobe-beheerde bewaarplaatsen. De informatie van de toegang over [ privé bewaarplaatsen ](private-repositories.md) is niet beschikbaar in Cloud Manager.

## Toegang tot opslaggegevens vanuit het venster Opslagplaatsen {#repositories-window}

De **knoop van Info van de Reactie van de Toegang** is ook beschikbaar op de toolbar van het [**venster van Bewaarplaatsen** ](managing-repositories.md). Het toont de zelfde informatie over de toegang tot van Adobe-beheerde bewaarplaatsen.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken. [ creeer een steunkaartje voor zulk een verzoek ](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support).

Het ticket wordt met hoge prioriteit behandeld en wordt doorgaans binnen één dag ingetrokken.
