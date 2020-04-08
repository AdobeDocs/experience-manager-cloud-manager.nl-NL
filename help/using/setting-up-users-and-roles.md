---
title: Gebruikers en rollen toevoegen
seo-title: Gebruikers en rollen toevoegen
description: 'null'
seo-description: U kunt specifieke rollidmaatschappen toewijzen door de gebruiker aan een Profiel van het Product van de Manager van de Wolk in de Console Admin toe te voegen. Volg deze sectie voor meer informatie.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: a96500b57c980d31d3a70341d8be7b92ae73a1c5

---


# Gebruikers en rollen toevoegen {#add-users-and-roles}

Veel functies in [!UICONTROL Cloud Manager] vereisen specifieke machtigingen om te werken. Zo kunnen alleen bepaalde gebruikers de KPI&#39;s (Key Performance Indicators) voor een programma instellen. Deze toestemmingen worden logisch gezien gegroepeerd in rollen.

[!UICONTROL Cloud Manager] definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Zakelijke eigenaar
* Programmabeheerder
* Implementatiebeheer
* Ontwikkelaar

>[!CAUTION]
>
>U moet beschikken over een Adobe-id en de productcontext van Adobe Managed Services om deze te kunnen gebruiken. [!UICONTROL Cloud Manager]

## Roldefinities {#role-definitions}

>[!NOTE]
>
>De ontwikkelaarspersona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

De volgende tabel geeft een overzicht van de rollen:

| [!UICONTROL Cloud Manager] Rollen | Beschrijving |
|--- |--- |
| Zakelijke eigenaar | Verantwoordelijk voor het bepalen van KPIs, het goedkeuren van productieplaatsingen en het met voeten treden van belangrijke 3-tier mislukkingen. |
| Programmabeheerder | Gebruikt [!UICONTROL Cloud Manager] om teamopstelling uit te voeren, status te herzien en KPIs te bekijken. Kan belangrijke fouten met drie niveaus goedkeuren. |
| Implementatiebeheer | Beheert implementatiebewerkingen. Gebruikt [!UICONTROL Cloud Manager] om werkgebied/productieplaatsingen uit te voeren. Kan CI/CD pijpleidingen uitgeven. Kan belangrijke fouten met drie niveaus goedkeuren. Kan toegang krijgen tot de Git-opslagplaats. |
| Ontwikkelaar | Ontwikkelt en test aangepaste toepassingscode. Wordt voornamelijk gebruikt [!UICONTROL Cloud Manager] om de status weer te geven. Kan toegang krijgen tot de Git-opslagplaats voor code commit. |
| Klantsuccesvolle technicus | Over het algemeen ondersteunt het succes van klanten met AMS. Interactie met [!UICONTROL Cloud Manager] voor het uitvoeren van plaatsingen die controle CSE vereisen. |
| Inhoudsauteur | Over het algemeen heeft dit geen invloed op [!UICONTROL Cloud Manager]de interactie. Kan de Schakelaar van het Programma gebruiken [!UICONTROL Cloud Manager] (die van [!UICONTROL Experience Cloud]) is genavigeerd om tot AEM toegang te hebben. |

## Beheerconsole gebruiken om een profiel te maken {#using-admin-console-to-create-a-profile}

Rollen worden beheerd voor [!UICONTROL Cloud Manager] vanuit de Adobe Admin Console. Specifieke rollidmaatschappen worden verstrekt door de gebruiker aan een Profiel van het [!UICONTROL Cloud Manager] Product in Console Admin toe te voegen.

U kunt specifieke rollidmaatschappen toewijzen door de gebruiker aan een [!UICONTROL Cloud Manager]-**productprofiel** in de Admin Console van Adobe toe te voegen. Dit is een centrale plaats voor het beheren van uw Adobe-rechten in uw hele organisatie. Raadpleeg de documentatie voor [Beheerconsole](https://helpx.adobe.com/enterprise/using/admin-console.html) voor meer informatie over de Admin Console van Adobe.

>[!NOTE]
>
>Als u toegang wilt tot de beheerconsole en uw team wilt instellen (gebruikers en rollen), opent u een browser en gaat u naar [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Om de juiste rolgebaseerde machtigingen aan gebruikers van [!UICONTROL Cloud Manager] te verstrekken moet een beheerder in de **Organisatie** van de klant nieuwe productprofielen maken onder de [!UICONTROL AEM Managed Services]-productcontext.

Om de aangewezen op rol-gebaseerde toestemmingen aan [!UICONTROL Cloud Manager] gebruikers te verstrekken, als beheerder moet u vier nieuwe Profielen van het Product onder de Context van het [!UICONTROL AEM Managed Services] Product creëren die aan elk van de vier [!UICONTROL Cloud Manager] rollen beantwoordt:

* Zakelijke eigenaar
* Implementatiebeheer
* Ontwikkelaar
* Programmabeheerder

U kunt gebruikers/groepen maken of toevoegen aan deze productprofielen met de [beheerconsole](https://adminconsole.adobe.com/) voor [!UICONTROL Cloud Manager], zoals in de onderstaande afbeelding wordt getoond:

1. Meld u aan bij de beheerconsole en klik op **Nieuw profiel** om een nieuw profiel toe te voegen.

   ![](assets/admin_console_roles-1.png)

1. Vul de velden in om een nieuwe rol in te stellen voor [!UICONTROL Cloud Manager].

   Voer **Profielnaam** en **Weergavenaam** in om een nieuw profiel te maken. Bovendien kunt u een **Machtigingsgroep** voor het profiel selecteren.

   Klik op **Gereed** om de stap voor het maken van het profiel te voltooien.

   >[!NOTE]
   >
   >Bij het maken van deze productprofielen moet de **Weergavenaam** de technische waarde zijn die wordt gedefinieerd door [!UICONTROL Cloud Manager] (zie onderstaande tabel). De **Profielnaam** kan om het even wat zijn, hoewel het om verwarring te vermijden wordt aangeraden de waarden in de kolom *Aanbevolen profielnaam* hieronder te gebruiken. Als u dit wilt doen, schakelt u bij het maken van het productprofiel de optie **Zelfde als profielnaam** uit en geeft u de bijbehorende waarde op als de **Weergavenaam**.

   | **Rol** | **Weergavenaam (vereist)** | **Aanbevolen profielnaam** |
   |---|---|---|
   | Zakelijke eigenaar | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol bedrijfseigenaar |
   | Implementatiebeheer | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol van implementatiebeheer |
   | Ontwikkelaar | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol van ontwikkelaar |
   | Programmabeheerder | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Rol van programmamanager |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Nadat u een productprofiel hebt gemaakt, kunt u gebruikers (of groepen) toevoegen aan deze productprofielen.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)
