---
title: Toegang tot opslagplaats
description: Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde Git-opslagruimten met behulp van het zelf-service Git-accountbeheer van Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 04fbc4a3fdba8b108055d66a4fdb1a31994cb18e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u toegang krijgt tot en beheer kunt maken van uw door Adobe beheerde Git-opslagruimten met behulp van het zelf-service Git-accountbeheer in Cloud Manager.

## Toegang tot gegevens in de opslagplaats via de overzichtspagina {#overview-page}

Cloud Manager maakt het gemakkelijk om uw informatie van de bewaarplaatstoegang voor Adobe-geleide bewaarplaatsen terug te winnen gebruikend **RepoInfo van de Toegang** van de **Pijpleidingen** kaart.

Het **de dialoogvakje van Info van de Bewaarplaats** laat u de volgende toegangsinformatie voor Adobe-beheerde bewaarplaatsen zien:

* De Git-gebruikersnaam.
* Het wachtwoord voor Actief.
* De URL naar de Cloud Manager Git-opslagplaats.
* De vooraf gebouwde bevelen van de Git om een ver aan uw reactie van de Git en duwcode toe te voegen snel.

  ![ het venster van Info van de Bewaarplaats ](assets/repository-info.png)

De informatie van de toegang over [ privé bewaarplaatsen ](/help/managing-code/private-repositories.md) is niet beschikbaar in Cloud Manager.

De **eigenschap van Info van de Reactie van de Toegang** is zichtbaar aan gebruikers met **Ontwikkelaar** of **de rollen van de Manager van de Plaatsing**.

**om tot gegevensopslagplaats van de pagina van het Overzicht toegang te hebben:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, onder de **Pipelines** kaart, klik **Info van de Reactie van de Toegang**.

   ![ Info van de Reparatie van de Toegang op de kaart van Pijpleidingen ](/help/managing-code/assets/pipelines-card2.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. In het **de dialoogvakje van Info van de Bewaarplaats**, uitgezochte **produceert wachtwoord**.

1. In de bevestigingsdialoogdoos, produceert de uitgezochte **wachtwoord**.

1. Aan het recht van het **1&rbrace; gebied van het Wachtwoord &lbrace;, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) om het wachtwoord aan het klembord te kopiëren.**

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat het wachtwoord niet op. Het is uw verantwoordelijkheid om het wachtwoord veilig op te slaan.
   * Omdat Cloud Manager het wachtwoord niet opslaat, moet u een nieuw wachtwoord opnieuw genereren als u het wachtwoord verliest.

   ![ het wachtwoord van het Exemplaar in de dialoogdoos van Info van de Bewaarplaats ](/help/managing-code/assets/repository-copy-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en, wanneer u klaar bent, wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

## Toegang tot opslaggegevens vanuit het venster Opslagplaatsen {#repositories-window}

De **eigenschap van Info van de Reactie van de Toegang** is ook beschikbaar bij [**Bewaarplaatsen** pagina ](/help/managing-code/managing-repositories.md). Het toont de zelfde informatie over de toegang tot van Adobe-beheerde bewaarplaatsen.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken.

Om dit te doen, [ creeer een steunkaartje voor dit verzoek ](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support). Het kaartje wordt met hoge prioriteit behandeld en wordt gewoonlijk binnen één dag ingetrokken.
