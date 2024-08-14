---
title: Gebruikers en rollen toevoegen
description: Leer hoe u de Admin Console gebruikt om gebruikers en rollen toe te voegen en profielen te maken.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 6%

---


# Gebruikers en rollen toevoegen {#add-users-and-roles}

Voor veel functies in [!UICONTROL Cloud Manager] zijn specifieke machtigingen vereist. Zo kunnen alleen bepaalde gebruikers de prestatiekernindicatoren (KPI&#39;s) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!NOTE]
>
>Als u [!UICONTROL Cloud Manager] wilt gebruiken, hebt u een Adobe ID en de Adobe Managed Services-productcontext nodig.

## Roldefinities {#role-definitions}

Deze lijst vat de rollen samen.

| [!UICONTROL Cloud Manager] Rol | Beschrijving |
|--- |--- |
| Business Owner | Deze gebruiker is verantwoordelijk voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het overschrijven van belangrijke 3-tivelige fouten indien nodig. |
| Program Manager | Deze gebruiker gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke 3-rij mislukkingen goedkeuren wanneer noodzakelijk. |
| Deployment Manager | Deze gebruiker beheert implementatiebewerkingen en gebruikt [!UICONTROL Cloud Manager] om testimplementaties/productieimplementaties uit te voeren, CI-/CD-pijpleidingen te bewerken, belangrijke fouten met drie lagen indien nodig goed te keuren en toegang te krijgen tot de git-opslagruimte. |
| Developer | Deze gebruiker ontwikkelt en test de code van de douanetoepassing en gebruikt hoofdzakelijk [!UICONTROL Cloud Manager] om plaatsingsstatus te bekijken en kan tot de git bewaarplaats voor codeverplichtingen toegang hebben. |
| Klantsuccesvolle technicus | Deze gebruiker ondersteunt doorgaans het succes van de klant voor AMS-klanten en communiceert met [!UICONTROL Cloud Manager] voor het uitvoeren van implementaties die CSE-toezicht vereisen. |
| Inhoudsauteur | Deze gebruiker communiceert doorgaans niet met [!UICONTROL Cloud Manager] , maar gebruikt mogelijk de programmaschakeloptie [!UICONTROL Cloud Manager] om toegang te krijgen tot AEM. |

>[!NOTE]
>
>De ontwikkelaarspersoon in de Admin Console heeft geen verband met de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager] .

## Beheerconsole gebruiken om een profiel te maken {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] rollen worden beheerd vanuit de Admin Console. Specifieke rollidmaatschappen worden verstrekt door de gebruiker aan een [!UICONTROL Cloud Manager] productprofiel toe te voegen.

De Admin Console is een centrale plaats voor het beheren van uw rechten van de Adobe over uw volledige organisatie. Raadpleeg de documentatie voor [Beheerconsole](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) voor meer informatie over de Admin Console van Adobe.

Om [!UICONTROL Cloud Manager] -gebruikers de juiste op rollen gebaseerde machtigingen te kunnen geven, moet een beheerder in de organisatie van de klant nieuwe productprofielen maken onder de [!UICONTROL AEM Managed Services] productcontext die overeenkomt met elk van de vier [!UICONTROL Cloud Manager] -rollen:

* Business Owner
* Deployment Manager
* Developer
* Program Manager

Met de Admin Console kunt u gebruikers/groepen maken of toevoegen aan deze productprofielen.

1. Meld u aan bij de Admin Console op [`https://adminconsole.adobe.com` ](https://adminconsole.adobe.com) .

1. Klik het **Overzicht** lusje, klik het product u op de **Producten en de diensten** kaart wilt wijzigen. Als het daar niet vermeld is, gebruik het **Producten** lusje om van het product de plaats te bepalen en het te klikken.

   ![ Admin consoleoverzicht tabel ](/help/assets/admin-console-overview.png)

1. Op het **lusje van Producten**, klik het milieu waarvoor u gebruikers/groepen aan productprofielen wilt toevoegen.

   ![ Admin consoleproducten tabel ](/help/assets/admin-console-product.png)

1. Op het **lusje van het Profiel van het 0} Product {van het product, klik** Nieuw Profiel **om een nieuw profiel toe te voegen.**

   ![ Nieuw profiel ](/help/assets/admin-console-product-profiles.png)

1. Geef de informatie op om een nieuwe rol in te stellen voor [!UICONTROL Cloud Manager] .

   * **de Naam van het Profiel** - de **Naam van het Profiel** kan om het even wat zijn, hoewel om verwarring te vermijden wordt het geadviseerd om de waarden in de **Geadviseerde kolom van de Naam van het Profiel** te gebruiken.
   * **Naam van de Vertoning** - de **Naam van de Vertoning** moet de technische waarde zijn die door [!UICONTROL Cloud Manager] wordt bepaald (zie de volgende lijst).
   * **Groep van de Toestemming** - u kunt een toestemmingsgroep voor het profiel (niet altijd beschikbaar) kiezen.

   ![ Creërend een nieuw profiel ](/help/assets/screen_shot_2018-05-04at171819.png)

   | Rol | Weergavenaam (vereist) | Aanbevolen profielnaam |
   |---|---|---|
   | Business Owner | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol bedrijfseigenaar |
   | Deployment Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol van Deployment Manager |
   | Developer | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol van ontwikkelaar |
   | Program Manager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol van Program Manager |


1. Klik **Gedaan** om het nieuwe profiel te bewaren.

## Profielen toewijzen aan gebruikers of gebruikersgroepen {#assign-profiles}

Nadat u productprofielen hebt gemaakt, kunt u gebruikers of gebruikersgroepen aan deze profielen toewijzen.

1. Meld u aan bij de Admin Console op [`https://adminconsole.adobe.com` ](https://adminconsole.adobe.com) .

1. In de Admin Console, kies de **Gebruikers** tabel.

   ![ Gebruikers tabel ](/help/assets/admin-console-users.png)

1. Klik **Gebruikers** in het linkernavigatievenster en klik dan een gebruiker om het te wijzigen.

1. Klik de ellipsknoop in de **Producten** sectie en selecteer **uitgeven**.

   ![ geef gebruiker ](/help/assets/admin-console-edit-user.png) uit

1. In **geef producten en gebruikersgroepen** dialoogdoos uit, klik de plus knoop en selecteer de profielen om aan de gebruiker toe te wijzen.

   * Als de gebruiker reeds aan de rollen wordt toegewezen, is de plus knoop een uitgeven knoop (een potlood), maar werkt de zelfde manier.

   ![ geef producten en gebruikersgroepen ](/help/assets/admin-console-edit-products-and-user-groups.png) uit

1. Klik **sparen** om de profielen aan de gebruiker te bewaren.

Herhaal de zelfde stappen om profielen aan gebruikersgroepen toe te wijzen, maar selecteer **Groepen van de Gebruiker** van het linkernavigatievenster op het **Gebruikers** lusje. Klik een gebruikersgroep en selecteer **Toegewezen Profielen van het Product** tabel en klik **toewijs het Profiel van het Product** om profielen toe te wijzen.

![ wijs profielen aan groep ](/help/assets/admin-console-edit-user-groups.png) toe
