---
title: Toegang tot opslagplaats
description: Leer hoe u toegang krijgt tot en beheer kunt maken van uw door Adobe beheerde it-opslagruimten met behulp van het beheer van uw eigen git-account in Cloud Manager.
source-git-commit: b15ef71ae24f51811798d2d25c8f75320e21c01f
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Toegang tot opslagplaats {#accessing-repos}

Leer hoe u toegang krijgt tot en beheer kunt maken van uw door Adobe beheerde it-opslagruimten met behulp van het beheer van uw eigen git-account in Cloud Manager.

## Toegang tot informatie over opslagplaats via de overzichtspagina {#overview-page}

Met Cloud Manager kunt u via de **Repo-info openen** de knoop is duidelijk beschikbaar op de pijpleidingskaart.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeren naar **Pijpleidingen** kaart van uw **Programmaoverzicht** pagina.

   ![De knop Repo-info openen op de milieucokaart](assets/pipelines-card.png)

1. Tik of klik op de knop **Repo-info openen** om de knop **Info opslagplaats** dialoogvenster en weergave:

   * De git-gebruikersnaam.
   * Het wachtwoord voor de it.
   * De URL naar de gegevensopslagruimte van Cloud Manager.
   * Vooraf gebouwde git-opdrachten waarmee u snel een externe server aan uw git-repo- en pushcode kunt toevoegen.

   ![Venster Info opslagplaats](assets/access-repo-info.png)

1. Om tot het wachtwoord toegang te hebben, moet een nieuw wachtwoord worden geproduceerd. Tik of klik op de knop **Wachtwoord genereren** knop.

1. Het genereren van wachtwoorden bevestigen in het dialoogvenster **Weet u zeker dat...** dialoogvenster door te tikken of te klikken **Wachtwoord genereren**.

   ![Het genereren van wachtwoorden bevestigen](assets/confirm-password-generation.png)

1. Het wachtwoord wordt gegenereerd en is zichtbaar voor kopiëren in het dialoogvenster **Wachtwoord** veld.

   * Als u een wachtwoord genereert, wordt het vorige wachtwoord ongeldig.
   * Cloud Manager slaat het wachtwoord niet op. Het is uw verantwoordelijkheid om dit wachtwoord veilig op te slaan.
   * Aangezien Cloud Manager het wachtwoord niet opslaat, moet u een nieuw wachtwoord opnieuw genereren als u het wachtwoord verliest.

   ![Voorbeeld van een gegenereerd wachtwoord](assets/generated-password.png)

Met behulp van deze referenties kunt u een lokale kopie van de opslagplaats klonen, wijzigingen aanbrengen in die lokale opslagplaats en eventuele wijzigingen in de code opnieuw doorvoeren naar de externe gegevensopslagruimte in Cloud Manager.

>[!NOTE]
>
>* De **Repo-info openen** deze optie is zichtbaar voor gebruikers met **Ontwikkelaar** of **Implementatiebeheer** rollen.
>* De **Repo-info openen** geeft alleen de toegangsgegevens van de opslagplaats weer voor opslagplaatsen die door Adobe worden beheerd. Informatie over toegang [privéopslagplaatsen](private-repositories.md) is niet beschikbaar in Cloud Manager.

## Toegang tot gegevens opslagplaats vanuit het venster Opslagplaatsen {#repositories-window}

An **Repo-info openen** is ook beschikbaar op de werkbalk van het dialoogvenster [**Opslagplaatsen** venster.](managing-repositories.md) het toont de zelfde informatie over de toegang tot van Adobe-beheerde bewaarplaatsen.

## Een toegangswachtwoord intrekken {#revoke-password}

U kunt een toegangswachtwoord op elk ogenblik intrekken. Om dit te doen, gelieve [Maak een ondersteuningsticket voor dit verzoek.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

Het kaartje zal met hoge prioriteit worden behandeld en moet binnen één dag worden ingetrokken.