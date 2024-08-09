---
title: Aangepaste machtigingen
description: Leer hoe u douanetoestemmingen kunt gebruiken om nieuwe profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma's, pijpleidingen en milieu's voor de gebruikers van de Managers van de Wolk te beperken.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 1%

---

# Aangepaste machtigingen {#custom-permissions}

Leer hoe u douanetoestemmingen kunt gebruiken om nieuwe profielen van de douanetoestemming met configureerbare toestemmingen tot stand te brengen om toegang tot programma&#39;s, pijpleidingen en milieu&#39;s voor de gebruikers van de Managers van de Wolk te beperken.

## Inleiding {#introduction}

Cloud Manager heeft een set vooraf gedefinieerde rollen die de toegang tot verschillende functies van cloudbeheer regelt:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Met aangepaste machtigingen kunnen gebruikers nieuwe aangepaste machtigingsprofielen maken met configureerbare machtigingen om de toegang voor gebruikers van Cloud Managers tot programma&#39;s, pijpleidingen en omgevingen te beperken.

>[!TIP]
>
>Voor details op vooraf bepaalde rollen, zie [ Op rol-Gebaseerde Toestemmingen ](/help/requirements/role-based-permissions.md).

## Aangepaste machtigingen gebruiken {#using}

Voor het maken en gebruiken van uw eigen aangepaste machtigingen zijn drie stappen vereist:

1. [ creeer een nieuw productprofiel ](#create).
1. [ wijs douanetoestemmingen aan het nieuwe productprofiel ](#assign-permissions) toe.
1. [ wijs gebruikers aan het nieuwe productprofiel ](#assign-users) toe.

In deze sectie worden deze stappen beschreven. U kunt het nuttig vinden om de [ Termijnen ](#terms) en [ Configurable 3} secties van Toestemmingen te zien aangezien u uw eigen douanetoestemmingen creeert.](#configurable-permissions)

>[!NOTE]
>
>U moet over de rechten van de productbeheerder in Admin Console hebben om nieuwe profielen tot stand te brengen en toestemmingen voor Cloud Manager te beheren.

### Een nieuw productprofiel maken {#create}

U moet eerst een nieuw productprofiel maken voordat u aangepaste machtigingen kunt toewijzen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/)

1. Selecteer het product **AEM Managed Services**.

1. Zoek en instantie met een naam die overeenkomt met het patroon `*-cloud-manager` en klik om gebruikers en machtigingen te beheren.

1. U wordt opnieuw gericht aan het **Producten** lusje van de Admin Console, waar u gebruikers en toestemmingen voor wolkenmanager kunt beheren. In de Admin Console, klik de **Nieuwe knoop van het Profiel**.

![ Nieuwe knoop van het Profiel ](/help/assets/admin-console-new-profile.png)

1. Geef de algemene details over het profiel op.

   * **het profielnaam van het Product** - een beschrijvende naam voor het profiel
   * **naam van de Vertoning** - een afgekorte naam die in UI (opties) zal worden getoond
   * **Beschrijving** - een informatieve beschrijving van het profiel die zijn doel (facultatief) verklaren
   * **breng gebruikers op de hoogte door e-mail** - wanneer geselecteerd, zullen de gebruikers per e-mail op de hoogte worden gebracht wanneer zij worden toegevoegd of uit dit profiel worden verwijderd.

1. Klik **sparen** wanneer volledig.

Het nieuwe productprofiel wordt opgeslagen en wordt weergegeven in de lijst met productprofielen in de Admin Console.

### Aangepaste machtigingen toewijzen aan profiel {#assign-permissions}

Nu u een nieuw productprofiel hebt, kunt u er aangepaste machtigingen aan toewijzen.

1. In de Admin Console, klik de naam van het [ nieuwe productprofiel u enkel ](#create) creeerde.

1. In het venster dat opent, selecteer het **lusje van Toestemmingen** om een lijst van editable toestemmingen te bekijken.

   ![ Bewerkbare toestemmingen ](/help/assets/permissions-tab.png)

1. Klik op **geef** verbinding van een toestemming uit om het uit te geven.

1. Het **geeft** venster van Toestemmingen uit opent.
   * De machtigingen die u in de vorige stap hebt geselecteerd, worden in de linkerkolom geselecteerd.
   * De toestemmingspunten beschikbaar voor taak voor de toestemming zijn in de middenkolom geëtiketteerd **Beschikbare Punten van de Toestemming**.
   * De toegewezen toestemmingspunten zijn in de juiste kolom geëtiketteerd **Inclusief Punten van de Toestemming**.

   ![ geef toestemmingspunten ](/help/assets/edit-permission-items.png) uit

1. Klik plus (`+`) pictogram naast het toestemmingspunt om het aan de kolom **toe te voegen omvatte Punten van de Toestemming**.

   * Klik op het pictogram `i` naast een machtigingsitem voor meer informatie.

1. Klik **toevoegen allen** knoop bij de bovenkant van de **Beschikbare 3} kolom van Toestemmingen {om alle toestemmingen toe te voegen.** Evenzo klik **verwijdert allen** om alle eerder geselecteerde toestemmingen te verwijderen.

1. Klik **sparen** wanneer u klaar bent met het bepalen van de toestemmingspunten voor uw nieuw productprofiel.

Uw nieuwe productprofiel wordt nu opgeslagen met de aangepaste machtigingen.

### Gebruikers toewijzen aan aangepaste machtigingen {#assign-users}

U kunt nu gebruikers toewijzen aan het nieuwe productprofiel dat u met aangepaste machtigingen hebt gemaakt.

1. In de Admin Console, klik de naam van het [ nieuwe productprofiel waaraan u enkel douanetoestemmingen ](#assign-permissions) toewees.

1. In het venster dat opent, selecteer de **Gebruikers** tabel.

1. Klik **toevoegen Gebruikers** knoop en wijs gebruikers aan uw nieuw productprofiel met douanetoestemmingen toe.

Zie de sectie **gebruikers en gebruikersgroepen aan een productprofiel** van het document [ toevoegen productprofielen voor ondernemingsgebruikers ](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html) voor meer details op hoe te om de Admin Console te gebruiken.

## Configureerbare machtigingen {#configurable-permissions}

De volgende machtigingen zijn beschikbaar voor het maken van aangepaste profielen.

| Machtiging | Beschrijving |
|---|---|
| Programmatoegang | Gebruikers toegang geven tot programma&#39;s |
| Programmabewerking | Gebruikers mogen programma&#39;s bewerken |
| Pipet maken | Gebruikers toestaan nieuwe pijpleidingen te maken |
| Pipet verwijderen | Gebruikers toestaan pijpleidingen te verwijderen |
| Pipet bewerken | Gebruikers toestaan pijpleidingen te bewerken |
| Productieimplementaties goedkeuren/afwijzen | Gebruikers toestaan een stap voor productieimplementatie goed te keuren of af te wijzen |
| Uitvoeringen pijplijn annuleren | Laat gebruikers uitvoeren pijpleidingen annuleren |
| Start van pijplijnuitvoering | Gebruikers toestaan nieuwe pijpleidinguitvoeringen te starten |
| Belangrijke metrische fouten negeren/negeren | Gebruikers toestaan belangrijke metrische fouten te negeren/af te wijzen |
| Plan voor productieimplementaties | Gebruikers toestaan een stap voor productieimplementatie te plannen |
| Toegang tot opslaggegevens | Gebruikers toegang geven tot dataopslag en een wachtwoord voor toegang genereren |
| Opslagplaats maken | Gebruikers toestaan nieuwe it-opslagruimten te maken |
| Opslagplaats verwijderen | Gebruikers mogen it-opslagruimten verwijderen |
| Bewerken opslagplaats | Gebruikers mogen it-opslagruimten bewerken |
| Code opslagplaats genereren | Gebruikers toestaan projecten te genereren op basis van het archetype |
| Inhoud kopiëren beheren | Gebruikers toestaan bewerkingen voor het kopiëren van inhoud te beheren |

### Rechten op organisatieniveau {#organization-level}

Machtigingen op organisatieniveau verwijzen naar machtigingen die altijd worden gegeven voor alle programma&#39;s in een organisatie.

De volgende machtigingen zijn bevoegdheden op organisatieniveau:

* **Toegang van Info van de Bewaarplaats** Dit huurder/organisatieniveau toestemming staat gebruikers toe om gebruikersbenaming, wachtwoord en bewaarplaats URL voor toegang te produceren en tot klantenproject bij te dragen.
   * Gebruikersnaam en wachtwoord voor toegang tot opslagplaats zijn hetzelfde voor alle repos op de org, maar de URL van de opslagplaats is uniek voor elk programma.
   * Zie [ Bewaarplaats van de Code van Source ](/help/requirements/source-code-repository.md) voor meer informatie.

## Voorwaarden {#terms}

De volgende termen worden gebruikt bij het maken en beheren van aangepaste machtigingen en vooraf gedefinieerde rollen.

| Term | Beschrijving |
|---|---|
| Vooraf gedefinieerde machtigingen | Vooraf bepaalde rollen zoals **BedrijfsEigenaar**, de Manager van de Plaatsing **, enz.** om verschillende functies van Cloud Manager te besturen. Voor details op vooraf bepaalde rollen, zie [ Op rol-Gebaseerde Toestemmingen ](/help/requirements/role-based-permissions.md). |
| Aangepaste machtigingen | Cloud Manager-functies waarmee gebruikers machtigingsprofielen kunnen maken om rollen te definiëren die de ondersteunde functies van Cloud Manager bepalen |
| Machtigingsprofiel | Gemaakt in de beheerconsole voor het beheer van configureerbare machtigingen die van toepassing zijn op gebruikers die deel uitmaken van het machtigingsprofiel |
| Configureerbare machtiging | Cloudbeheermachtigingen die kunnen worden geconfigureerd in machtigingsprofiel |
| Machtigingsitem | Een programma, milieu of pijpleidingsmiddel waarop een toestemming kan worden toegepast |

De punten van de toestemming verwijzen naar het werkingsgebied waar de toestemming zal worden toegepast. Doorgaans is dit een van de volgende:

| Type machtigingsitem | Voorbeeld | Beschrijving |
|---|---|---|
| Organisatie | organisatie:bedrijfA | Alle toepasselijke middelen van een organisatie. Een bron kan een programma, omgeving of pijpleiding zijn. Als de gebruiker een organisatie voor om het even welke toestemming toevoegt dan zullen alle nieuwe middelen in die organisatie ook die toestemming hebben. |
| Programma | Programma A | Alle toepasselijke middelen van een programma |
| Omgeving | Programma A: milieu | Van toepassing op een specifieke omgeving |
| Pijpleiding | Programma A : Pipeline | Van toepassing op een specifieke pijpleiding |

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen wanneer u aangepaste machtigingen gebruikt:

* A [ beperkte reeks toestemmingen is beschikbaar ](#configurable-permissions) voor het creëren van douaneprofielen.
* Middelen zoals programma, milieu, pijpleiding enz. die in Cloud Manager zijn gemaakt, kan twee minuten in beslag nemen om in Admin Console weer te geven voor configuratie van bevoegdheden.
* In zeldzame gevallen waarin de service met aangepaste machtigingen niet reageert, zijn vooraf gedefinieerde profielen nog steeds beschikbaar en hebben gebruikers in vooraf gedefinieerde profielen nog steeds de juiste toegang.

## Veelgestelde vragen {#faq}

### Welke machtigingsprofielen zijn vooraf gedefinieerde machtigingsprofielen?

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Voor details op vooraf bepaalde rollen, zie [ Op rol-Gebaseerde Toestemmingen ](/help/requirements/role-based-permissions.md).

### Wat gebeurt er met vooraf gedefinieerde machtigingsprofielen met inleiding tot aangepaste profielen?

De standaardproductprofielen en de rollen van de wolkenmanager blijven het zelfde werken zoals voordien.

### Kan ik vooraf gedefinieerde machtigingsprofielen bewerken?

Nee, standaardprofielen kunnen niet worden bewerkt. U kunt geen machtigingen toevoegen aan of verwijderen uit het standaardmachtigingsprofiel. U kunt alleen gebruikers toevoegen aan of verwijderen uit vooraf gedefinieerde profielen.

### Moet ik vooraf gedefinieerde machtigingsprofielen verwijderen, omdat aangepaste profielen nu beschikbaar zijn?

Vooraf gedefinieerde machtigingsprofielen mogen niet uit de Admin Console worden verwijderd.

### Kan ik gebruikers toevoegen aan meerdere machtigingsprofielen?

Ja, een gebruiker kan deel uitmaken van meerdere profielen, waaronder vooraf gedefinieerde en aangepaste machtigingsprofielen. Wanneer een gebruiker aan meerdere profielen wordt toegewezen, zijn de gecombineerde machtigingen van alle toegewezen machtigingsprofielen beschikbaar voor die gebruiker.

### Wat gebeurt als een gebruiker toestemming heeft om een milieu/pijpleiding uit te geven maar geen toegang tot een programma heeft dat het milieu/de pijpleiding bevat?

In dit geval zal de gebruiker tot het milieu of de pijpleiding niet kunnen toegang hebben als zij niet de **toestemmingen hebben van de Toegang van het 0} Programma die het milieu of de pijpleiding bevatten.**

### Wat gebeurt er als ik zowel AEM as a Cloud Service- als AMS-programma&#39;s in dezelfde IMS-org heb? Kan ik machtigingen van één profiel beheren? {#ams-and-aemaacs}

U moet voor elk producttype een apart profiel maken (dat wil zeggen een profiel voor AEM als Cloud Service en een profiel voor Adobe Managed Services of AMS).
