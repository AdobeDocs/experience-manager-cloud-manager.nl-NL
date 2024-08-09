---
title: Het gereedschap Inhoud kopiëren
description: Met het Cloud Manager-programma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud kopiëren van hun AMS-gehoste AEM 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---


# Het gereedschap Inhoud kopiëren {#content-copy}

Met het Cloud Manager-programma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud kopiëren van hun AMS-gehoste AEM 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.

## Inleiding {#introduction}

De huidige, echte gegevens zijn waardevol voor het testen, de bevestiging, en de gebruiker-aanvaarding doeleinden. Met het gereedschap Inhoud kopiëren kunt u inhoud van uw productie-AMS-gehoste AEM 6.x-omgeving kopiëren naar een testomgeving.

De inhoud die moet worden gekopieerd, wordt gedefinieerd door een inhoudsset. Een inhoudsset bestaat uit een lijst met JCR-paden die de veranderbare inhoud bevatten die van een bronomgeving naar een doelomgeving binnen hetzelfde Cloud Manager-programma moet worden gekopieerd. De volgende paden zijn toegestaan in een inhoudsset.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Wanneer het kopiëren van inhoud, is het bronmilieu de bron van waarheid.

* Als de inhoud in de bestemmingsmilieu is gewijzigd, zal het door inhoud in de bron worden beschreven, als de wegen het zelfde zijn.
* Als de paden verschillend zijn, wordt de inhoud van de bron samengevoegd met de inhoud in de bestemming.

## Machtigingen {#permissions}

Om het hulpmiddel van het inhoudsexemplaar te gebruiken, moet de gebruiker aan de **rol van de Manager van de Plaatsing** in de bron en doelmilieu&#39;s worden toegewezen.

## Een inhoudsset maken {#create-content-set}

Voordat inhoud kan worden gekopieerd, moet een inhoudsset zijn gedefinieerd. Wanneer deze is gedefinieerd, kunnen inhoudssets opnieuw worden gebruikt om inhoud te kopiëren. Ga als volgt te werk om een inhoudenset te maken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Navigeer aan de **pagina van de Reeksen van de Inhoud** van het **milieu&#39;s** scherm.

1. Klik **toevoegen de Vastgestelde Inhoud** knoop bij top-right van het scherm.

   ![ Inhoudsreeksen ](/help/assets/content-sets.png)

1. Op het **lusje van Details** van de tovenaar, verstrek een naam en een beschrijving voor de geplaatste inhoud en klik **verdergaan**.

   ![ Inhoud plaatste details ](/help/assets/add-content-set-details.png)

1. Op het **lusje van de Wegen van de Inhoud** van de tovenaar, specificeer de wegen van de veranderlijke inhoud die in de inhoudreeks moet worden omvat.

   1. Ga de weg in **toevoegen omvat Weg** gebied.
   1. Klik **toevoegen de knoop van de Weg** om de weg aan de inhoudreeks toe te voegen.
   1. Klik opnieuw **toevoegen de knoop van de Weg** zonodig.

   ![ voegt wegen aan inhoud toe plaatste ](/help/assets/add-content-set-paths.png)

1. Als u de inhoudenset moet verfijnen of beperken, kunnen subpaden worden uitgesloten.

   1. In de lijst van inbegrepen wegen, klik **voeg sub-wegen** pictogram naast de weg toe u moet beperken.
   1. Voer het subpad in dat u onder het geselecteerde pad wilt uitsluiten.
   1. Klik **uitsluiten Weg**.
   1. Klik **toevoegen sluit subpaden** opnieuw uit om extra wegen toe te voegen om zonodig uit te sluiten.

   ![ Excluding wegen ](/help/assets/add-content-set-paths-excluded.png)

1. U kunt de opgegeven paden desgewenst wijzigen.

   1. Klik op de X naast de uitgesloten subpaden om deze te verwijderen.
   1. Klik de ellipsknoop naast wegen om **uit te openbaren geef** uit en **schrap** opties.

   ![ het Uitgeven weglijst ](/help/assets/add-content-set-excluded-paths.png)

1. Klik **creëren** om de inhoudreeks tot stand te brengen.

De inhoudenset kan nu worden gebruikt om inhoud tussen omgevingen te kopiëren.

>[!NOTE]
>
>U kunt maximaal 50 paden toevoegen aan een inhoudsset.
>Uitgesloten paden zijn niet beperkt.

## Een inhoudsset bewerken {#edit-content-set}

Voer vergelijkbare stappen uit als bij het maken van een stap Inhoud. In plaats van het klikken **voeg Geplaatste Inhoud** toe, selecteer een bestaande reeks van de console en selecteer **uitgeven** van het elliptische menu.

![ geef inhoudreeks ](/help/assets/edit-content-set.png) uit

Wanneer u de inhoudenset bewerkt, moet u mogelijk de geconfigureerde paden uitbreiden om de uitgesloten subpaden zichtbaar te maken.

## Inhoud kopiëren {#copy-content}

Nadat u een inhoudsset hebt gemaakt, kunt u deze gebruiken om inhoud te kopiëren. Ga als volgt te werk om inhoud te kopiëren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Navigeer aan de **pagina van de Reeksen van de Inhoud** van het **milieu&#39;s** scherm.

1. Selecteer een inhoud die van de console wordt geplaatst en selecteer **Inhoud van het Exemplaar** van het ellipsmenu.

   ![ exemplaar van de Inhoud ](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Een omgeving kan niet selecteerbaar zijn als:
   >
   >* De gebruiker beschikt niet over de juiste machtigingen.
   >* Het milieu heeft een lopende pijpleiding of een verrichting van de exemplaarinhoud lopend.

1. In de **inhoud van het Exemplaar** dialoog, specificeer de bron en de bestemming voor uw actie van het inhoudsexemplaar.

1. U kunt ervoor kiezen om de paden voor uitsluiten te verwijderen of te behouden in de doelomgeving. Schakel het selectievakje `Do not delete exclude paths from destination` in als u de in de inhoudenset opgegeven paden voor uitsluiten wilt behouden. Als het selectievakje uitgeschakeld blijft, worden paden uitgesloten uit de doelomgeving.

1. U kunt versiehistorie kopiëren van de paden die van bron naar doelomgeving worden gekopieerd. Schakel het selectievakje `Copy Versions` in als u alle versiehistorie wilt kopiëren.

   ![ het Kopiëren inhoud ](/help/assets/copying-content.png)

1. Klik **Exemplaar**.

Het kopieerproces wordt gestart. De status van het kopieerproces wordt weerspiegeld in de console voor de geselecteerde inhoudenset.

## Activiteit voor kopiëren van inhoud {#copy-activity}

U kunt het statuut van uw exemplaarprocessen in de **pagina van de Activiteit van de Inhoud van het Exemplaar controleren**.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Navigeer aan de **pagina van de Activiteit van de Inhoud van het Exemplaar** van het **milieu&#39;s** scherm.

![ Activiteit van het Exemplaar van de Inhoud ](/help/assets/copy-content-activity.png)

### Statussen van inhoud kopiëren {#statuses}

Wanneer u begint inhoud te kopiëren, kan het proces een van de volgende statussen hebben.

| Status | Beschrijving |
|---|---|
| In uitvoering | De bewerking voor het kopiëren van inhoud is aan de gang |
| Mislukt | Kopiëren van inhoud is mislukt |
| Voltooid | Kopie van inhoud voltooid |

## Beperkingen {#limitations}

Het gereedschap voor het kopiëren van inhoud heeft de volgende beperkingen.

* Een inhoudkopie kan niet worden uitgevoerd van een lagere omgeving naar een hogere omgeving.
* Het kopiëren van inhoud kan alleen worden uitgevoerd binnen dezelfde laag (dus auteur of publicatie).
* Kopiëren van inhoud tussen programma&#39;s en regio&#39;s is niet mogelijk.
* Inhoudskopie voor topologie op basis van gegevensopslag in de cloud kan alleen worden uitgevoerd wanneer de bron- en doelomgeving zich op dezelfde cloudprovider en hetzelfde gebied bevinden.
* Het uitvoeren van gelijktijdige bewerkingen voor het kopiëren van inhoud in dezelfde omgeving is niet mogelijk.
* Het exemplaar van de inhoud kan niet worden uitgevoerd als er om het even welke actieve verrichting die op of het doel of bronmilieu zoals een pijpleiding CI/CD loopt.
* Per inhoudenset kunnen maximaal vijftig paden worden opgegeven. Uitgesloten paden zijn niet beperkt.
* Het gereedschap voor het kopiëren van inhoud mag niet worden gebruikt als een kloon- of spiegelgereedschap omdat het geen verplaatste of verwijderde inhoud van de bron kan bijhouden.
* Een inhoudkopie kan niet worden gepauzeerd of geannuleerd nadat deze is gestart.
* Met het gereedschap voor het kopiëren van inhoud kopieert u elementen samen met dynamische metagegevens over media van de hogere omgeving naar de geselecteerde lagere omgeving.
   * De gekopieerde activa moeten dan worden herverwerkt gebruikend het [ DAM werkschema van procesactiva ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html) op het lagere milieu om de respectieve dynamische media configuratie te gebruiken.
* Het kopiëren van inhoud gaat aanzienlijk sneller als de versiegeschiedenis niet wordt gekopieerd.
