---
title: Gebruikers en rollen toevoegen
description: Leer hoe u de Admin Console gebruikt om gebruikers en rollen toe te voegen en profielen te maken.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 012359b4ecf872ece036b27b48fededf150493d2
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 3%

---


# Gebruikers en rollen toevoegen {#add-users-and-roles}

Voor veel functies in [!UICONTROL Cloud Manager] zijn specifieke machtigingen vereist. Zo kunnen alleen bepaalde gebruikers de prestatiekernindicatoren (KPI&#39;s) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers, die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

>[!NOTE]
>
>Als u [!UICONTROL Cloud Manager] wilt gebruiken, hebt u een Adobe ID en de Adobe Managed Services-productcontext nodig.

## Roldefinities {#role-definitions}

De volgende tabel geeft een overzicht van de rollen in Cloud Manager.

| [!UICONTROL Cloud Manager] rol | Beschrijving |
| --- | --- |
| Business Owner | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen, en het met voeten treden van belangrijke 3-tier mislukkingen wanneer noodzakelijk. |
| Program Manager | Zij gebruiken [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kunnen belangrijke 3-rij mislukkingen goedkeuren wanneer noodzakelijk. |
| Deployment Manager | Beheert plaatsingsverrichtingen en gebruikt [!UICONTROL Cloud Manager] om het opvoeren en productielokaties uit te voeren, CI/CD pijpleidingen uit te geven, en kritieke 3-rij mislukkingen goed te keuren wanneer nodig. Ze hebben ook toegang tot de Git-opslagplaats. |
| Developer | Ontwikkelt en test de code van de douanetoepassing en gebruikt hoofdzakelijk [!UICONTROL Cloud Manager] om plaatsingsstatus te bekijken en kan tot de bewaarplaats van de Git voor codeverplichtingen toegang hebben. |
| Klantsuccesvolle technicus | CSE steunt over het algemeen klantensucces voor klanten AMS. Ze werken met [!UICONTROL Cloud Manager] om implementaties uit te voeren die CSE-controle vereisen. |
| Inhoudsauteur | Over het algemeen werken ze niet met [!UICONTROL Cloud Manager] , maar gebruiken ze wellicht de [!UICONTROL Cloud Manager] -programmaschakeloptie om toegang te krijgen tot AEM. |

>[!NOTE]
>
>De ontwikkelaarspersona in de Admin Console is niet gerelateerd aan de rol van de ontwikkelaar in [!UICONTROL Cloud Manager] .

## Een productprofiel maken met de Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] -rollen worden beheerd vanuit de Admin Console. Specifieke rollidmaatschappen worden verstrekt door de gebruiker aan een [!UICONTROL Cloud Manager] productprofiel toe te voegen.

De Admin Console is een centrale locatie voor het beheer van uw Adobe-rechten in uw hele organisatie. Meer over Adobe Admin Console leren, zie [ Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html).

Een beheerder moet nieuwe productprofielen maken onder de [!UICONTROL AEM Managed Services] Productcontext om op rollen gebaseerde machtigingen toe te wijzen aan [!UICONTROL Cloud Manager] -gebruikers, die overeenkomen met elk van de vier [!UICONTROL Cloud Manager] -rollen.

* Business Owner
* Deployment Manager
* Developer
* Program Manager

Met de Admin Console gebruikers of groepen maken of toevoegen aan deze productprofielen.

>[!IMPORTANT]
>
>Wegens een huidige beperking in Admin Console en Cloud Manager, kunnen de profielen niet met **worden bewaard Geen toestemmingen** geselecteerd. Als u dit probeert, treedt er een backend-fout op. Dit gedrag beïnvloedt de verwezenlijking van de profielen van de Manager van de Plaatsing. Als tijdelijke oplossing selecteert u ten minste één machtiging bij het maken van een nieuw profiel.

**om een productprofiel tot stand te brengen gebruikend Admin Console:**

1. Meld u aan bij de Admin Console op [`https://adminconsole.adobe.com` ](https://adminconsole.adobe.com) .

1. Klik het **Overzicht** lusje, dan klik het product u op de **Producten en de kaart van de Diensten** wilt uitgeven. Als het daar niet vermeld is, gebruik het **Producten** lusje om van het product de plaats te bepalen en het te klikken.

   ![ Admin consoleoverzicht tabel ](/help/assets/admin-console-overview.png)

1. Op het **lusje van Producten**, klik het milieu waarvoor u gebruikers/groepen aan productprofielen wilt toevoegen.

   ![ Admin consoleproducten tabel ](/help/assets/admin-console-product.png)

1. Op het **lusje van het Profiel van het 0} Product {van het product, klik** Nieuw Profiel **om een nieuw profiel toe te voegen.**

   ![ Nieuw profiel ](/help/assets/admin-console-product-profiles.png)

1. Geef de informatie op om een nieuwe rol in te stellen voor [!UICONTROL Cloud Manager] .

   * **de Naam van het Profiel** - de **Naam van het Profiel** kan om het even wat zijn, hoewel om verwarring te vermijden wordt het geadviseerd om de waarden in de **Geadviseerde kolom van de Naam van het Profiel** te gebruiken.
   * **Naam van de Vertoning** - de **Naam van de Vertoning** moet de technische waarde zijn die door [!UICONTROL Cloud Manager] wordt bepaald (zie de volgende lijst).
   * **Groep van de Toestemming** - u kunt een toestemmingsgroep voor het profiel (niet altijd beschikbaar) kiezen.

     >[!IMPORTANT]
     >
     >Wegens een huidige beperking in Admin Console en Cloud Manager, kunnen de profielen niet met **worden bewaard Geen toestemmingen** geselecteerd. Als u dit probeert, treedt er een backend-fout op. Dit gedrag beïnvloedt de verwezenlijking van de profielen van de Manager van de Plaatsing. Als tijdelijke oplossing selecteert u ten minste één machtiging bij het maken van een nieuw profiel.

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

1. In Admin Console, kies de **Gebruikers** tabel.

   ![ Gebruikers tabel ](/help/assets/admin-console-users.png)

1. Klik **Gebruikers** in het linkernavigatievenster en klik dan een gebruiker om het te wijzigen.

1. Klik ![ Meer pictogram, ellips ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) in de **Producten** sectie en klik **uitgeven**.

   ![ geef gebruiker ](/help/assets/admin-console-edit-user.png) uit

1. In **geef producten en gebruikersgroepen** dialoogdoos uit, klik ![ voeg pictogram toe, plus teken ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) en selecteer de profielen om aan de gebruiker toe te wijzen.

   * Als de gebruiker reeds aan de rollen wordt toegewezen, voegt ![ pictogram toe, plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) knoop is uitgeven knoop (een potlood), maar werkt de zelfde manier.

   ![ geef producten en gebruikersgroepen ](/help/assets/admin-console-edit-products-and-user-groups.png) uit

1. Klik **sparen** om de profielen aan de gebruiker te bewaren.

Herhaal de zelfde stappen om profielen aan gebruikersgroepen toe te wijzen, maar selecteer **Groepen van de Gebruiker** van het linkernavigatievenster op het **Gebruikers** lusje. Klik een gebruikersgroep en selecteer de **Toegewezen Profielen van het Product** klik **toewijzen het Profiel van het Product** om profielen toe te wijzen.

![ wijs profielen aan groep ](/help/assets/admin-console-edit-user-groups.png) toe
