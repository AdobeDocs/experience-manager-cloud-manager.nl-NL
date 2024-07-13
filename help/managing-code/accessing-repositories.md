---
title: Toegang tot opslagplaats
description: Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde it-opslagruimten met behulp van het zelfbedienings-git-accountbeheer van Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u toegang krijgt tot en beheer krijgt van uw door de Adobe beheerde it-opslagruimten met behulp van het zelfbedienings-git-accountbeheer van Cloud Manager.

## Toegang tot informatie over opslagplaats via de overzichtspagina {#overview-page}

Cloud Manager maakt het gemakkelijk om uw informatie van de bewaarplaatstoegang voor Adobe-geleide bewaarplaatsen terug te winnen door de **knoop van de Reparatie van de Toegang te gebruiken** beschikbaar hoofdzakelijk op de pijpleidingskaart.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan **Pijpleidingen** kaart van uw **pagina van het Overzicht van het Programma**.

   ![ de knoop van Info van de Reparatie van de Toegang op de kaart van Milieu ](assets/pipelines-card.png)

1. Tik of klik de **knoop van Info van de Reactie van de Toegang** om de **Info van de Bewaarplaats** dialoog en mening te openen:

   * De git-gebruikersnaam.
   * Het wachtwoord voor de it.
   * De URL naar de Cloud Manager-it-opslagplaats.
   * Vooraf gebouwde git-opdrachten waarmee u snel een externe server aan uw git-repo- en pushcode kunt toevoegen.

   ![ het venster van Info van de Bewaarplaats ](assets/access-repo-info.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. Om dit te doen, ontvang of klik **wachtwoord** knoop produceren.

1. Bevestig wachtwoordgeneratie in **bent u zeker..** dialoog door te tikken of te klikken **produceert wachtwoord**.

   ![ Bevestig wachtwoordgeneratie ](assets/confirm-password-generation.png)

1. Het wachtwoord wordt geproduceerd en is zichtbaar voor het kopiëren op het **gebied van het Wachtwoord**.

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat het wachtwoord niet op. Het is uw verantwoordelijkheid om dit wachtwoord veilig op te slaan.
   * Omdat Cloud Manager het wachtwoord niet opslaat, moet u een nieuw wachtwoord opnieuw genereren als u het wachtwoord verliest.

   ![ Voorbeeld van een geproduceerd wachtwoord ](assets/generated-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en, wanneer u klaar bent, wijzigingen in de code terugsturen naar de externe gegevensopslagruimte in Cloud Manager.

>[!NOTE]
>
>* De **optie van Info van de Reactie van de Toegang** is zichtbaar aan gebruikers met **Ontwikkelaar** of **de rollen van de Manager van de Plaatsing**.
>* De **knoop van Info van de Reactie van de Toegang** toont slechts de informatie van de bewaarplaatstoegang voor Adobe-beheerde bewaarplaatsen. De informatie van de toegang over [ privé bewaarplaatsen ](private-repositories.md) is niet beschikbaar in Cloud Manager.

## Toegang tot gegevens opslagplaats vanuit het venster Opslagplaatsen {#repositories-window}

Een **knoop van Info van de Reactie van de Toegang** is ook beschikbaar in de toolbar van het [**Venster van Bewaarplaatsen**.In ](managing-repositories.md) wordt dezelfde informatie weergegeven over de toegang tot opslagruimten met beheerde Adoben.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken. Om dit te doen, gelieve [ een steunkaartje voor dit verzoek tot stand te brengen.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

Het kaartje zal met hoge prioriteit worden behandeld en moet binnen één dag worden ingetrokken.
