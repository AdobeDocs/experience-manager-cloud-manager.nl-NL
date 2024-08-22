---
title: Het gereedschap Inhoud kopiëren
description: Met het Cloud Manager-programma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud kopiëren van door AMS gehoste AEM 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---


# Het gereedschap Inhoud kopiëren {#content-copy}

Met het Cloud Manager-programma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud kopiëren van door AMS gehoste AEM 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.

## Inleiding {#introduction}

De huidige, echte gegevens zijn waardevol voor het testen, de bevestiging, en de gebruiker-aanvaarding doeleinden. Met het gereedschap Inhoud kopiëren kunt u inhoud van uw productie-AMS-gehoste AEM 6.x-omgeving kopiëren naar testomgevingen of ontwikkelomgevingen. Deze workflow ondersteunt verschillende testscenario&#39;s.

Een inhoudsset definieert de inhoud die moet worden gekopieerd. Een inhoudenset bevat een lijst met JCR-paden met de inhoud die moet worden gekopieerd. De inhoud wordt verplaatst van een bronomgeving naar een doelomgeving. Alles gebeurt binnen hetzelfde Cloud Manager-programma.

De volgende paden zijn toegestaan in een inhoudsset:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Wanneer het kopiëren van inhoud, is het bronmilieu de bron van waarheid.

* Als u inhoud bewerkt in de doelomgeving, wordt deze overschreven door de broninhoud als de paden overeenkomen.
* Als de paden verschillend zijn, wordt de inhoud van de bron samengevoegd met de inhoud in de bestemming.

## Machtigingen {#permissions}

Om het hulpmiddel van het inhoudsexemplaar te gebruiken, moet de gebruiker aan de **rol van de Manager van de Plaatsing** in de bron en doelmilieu&#39;s worden toegewezen.

## Een inhoudsset maken {#create-content-set}

Voordat inhoud kan worden gekopieerd, moet een inhoudsset zijn gedefinieerd. Wanneer deze is gedefinieerd, kunnen inhoudssets opnieuw worden gebruikt om inhoud te kopiëren. Ga als volgt te werk om een inhoudenset te maken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht**, navigeer aan het **milieu&#39;s** scherm.

1. Van het **scherm van Milieu&#39;s**, navigeer aan de **Inhoudsreeksen** pagina.

1. Dichtbij het top-right van het scherm, klik **voeg Geplaatste Inhoud** toe.

   ![ Inhoudsreeksen ](/help/assets/content-sets.png)

1. Op het **lusje van Details** van de tovenaar, verstrek een naam en een beschrijving voor de geplaatste inhoud en klik **verdergaan**.

   ![ Inhoud plaatste details ](/help/assets/add-content-set-details.png)

1. Op het **lusje van de Wegen van de Inhoud** van de tovenaar, specificeer de wegen van de veranderlijke inhoud die in de inhoudreeks moet worden omvat.

   1. Ga de weg in **toevoegen omvat Weg** gebied.
   1. Klik **toevoegen Weg** om de weg aan de inhoudreeks toe te voegen.
   1. Klik **voeg Weg** opnieuw toe zonodig.

   ![ voegt wegen aan inhoud toe plaatste ](/help/assets/add-content-set-paths.png)

1. Als u de inhoudenset moet verfijnen of beperken, kunnen subpaden worden uitgesloten.

   1. In de lijst van inbegrepen wegen, klik **voeg sub-wegen** pictogram naast de weg toe u moet beperken.
   1. Voer het subpad in dat u wilt uitsluiten van het geselecteerde pad.
   1. Klik **uitsluiten Weg**.
   1. Nogmaals, sluit de klik **subpaden** uit om extra wegen toe te voegen om zonodig uit te sluiten.

   ![ Excluding wegen ](/help/assets/add-content-set-paths-excluded.png)

1. U kunt de opgegeven paden desgewenst wijzigen.

   1. Klik op `X` naast de uitgesloten subpaden om deze te verwijderen.
   1. Klik de ellipsknoop naast de wegen om **uit te geven** en **schrapt** opties.

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

1. Van de **pagina van het Overzicht**, navigeer aan het **milieu&#39;s** scherm.

1. Van het **scherm van Milieu&#39;s**, navigeer aan de **Inhoudsreeksen** pagina.

1. Selecteer een inhoud die van de console wordt geplaatst en selecteer **Inhoud van het Exemplaar** van het ellipsmenu.

   ![ exemplaar van de Inhoud ](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Een omgeving kan niet selecteerbaar zijn als:
   >
   >* De gebruiker beschikt niet over de juiste machtigingen.
   >* Het milieu heeft een lopende pijpleiding of een verrichting van de exemplaarinhoud lopend.

1. In het **de dialoogvakje van de inhoud van het 0} Exemplaar {, specificeer de bron en bestemmingsmilieu&#39;s voor uw actie van het inhoudsexemplaar.**
   * De regio&#39;s van de doelomgeving moeten dezelfde zijn als of een deel van de bronomgeving.

1. U kunt ervoor kiezen om paden voor uitsluiten te verwijderen of te behouden in de doelomgeving. Schakel het selectievakje `Do not delete exclude paths from destination` in om `exclude paths` te behouden die in de inhoudenset zijn opgegeven. Als het selectievakje is uitgeschakeld, worden paden uitgesloten uit de doelomgeving.

1. U kunt de versiegeschiedenis kopiëren van paden die van bron naar bestemmingsomgeving worden gekopieerd. Schakel het selectievakje `Copy Versions` in als u alle versiehistorie wilt kopiëren.

   ![ het Kopiëren inhoud ](/help/assets/copying-content.png)

1. Klik **Exemplaar**.

Het kopieerproces wordt gestart. De status van het kopieerproces wordt weerspiegeld in de console voor de geselecteerde inhoudenset.

## Kopieeractiviteit van inhoud {#copy-activity}

U kunt het statuut van uw exemplaarprocessen in de **pagina van de Activiteit van de Inhoud van het Exemplaar controleren**.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/), dan selecteer de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht**, navigeer aan het **milieu&#39;s** scherm.

1. Van het **scherm van Milieu&#39;s**, navigeer aan de **pagina van de Activiteit van de Inhoud van het Exemplaar**.

![ Activiteit van het Exemplaar van de Inhoud ](/help/assets/copy-content-activity.png)

### Statussen voor het kopiëren van inhoud {#statuses}

Wanneer u begint inhoud te kopiëren, kan het proces een van de volgende statussen hebben.

| Status | Beschrijving |
|---|---|
| In uitvoering | De bewerking voor het kopiëren van inhoud is aan de gang |
| Mislukt | Kopiëren van inhoud is mislukt |
| Voltooid | Kopie van inhoud voltooid |

## Beperkingen {#limitations}

Het gereedschap voor het kopiëren van inhoud heeft de volgende beperkingen.

* Een inhoudkopie kan niet worden uitgevoerd van een lagere omgeving naar een hogere omgeving.
* Kopiëren van inhoud kan alleen binnen dezelfde laag worden uitgevoerd. Dat wil zeggen, auteur of publicatieversie.
* Kopiëren van inhoud tussen programma&#39;s en regio&#39;s is niet mogelijk.
* Het exemplaar van de inhoud voor de opslag van wolkengegevens kan gebaseerde topologie slechts worden uitgevoerd wanneer de bron en bestemmingsmilieu op de zelfde wolkenleverancier en in het zelfde gebied zijn.
* Het uitvoeren van gelijktijdige bewerkingen voor het kopiëren van inhoud in dezelfde omgeving is niet mogelijk.
* Het exemplaar van de inhoud kan niet worden uitgevoerd als er om het even welke actieve verrichting die op of het bestemmings of bronmilieu zoals een pijpleiding CI/CD loopt.
* Per inhoudenset kunnen maximaal vijftig paden worden opgegeven. Uitgesloten paden zijn niet beperkt.
* Het gereedschap voor het kopiëren van inhoud mag niet worden gebruikt als een kloon- of spiegelgereedschap omdat het geen verplaatste of verwijderde inhoud van de bron kan bijhouden.
* Een inhoudkopie kan niet worden gepauzeerd of geannuleerd nadat deze is gestart.
* Met het gereedschap Inhoud kopiëren kopieert u elementen en Dynamic Media-metagegevens van de hogere omgeving naar de geselecteerde lagere omgeving. De gekopieerde activa moeten dan worden herverwerkt gebruikend het [ DAM werkschema van procesactiva ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/assets-workflow) op het lagere milieu om de respectieve configuratie van Dynamic Media te gebruiken.
* Het kopiëren van de inhoud gaat aanzienlijk sneller als de versiegeschiedenis niet wordt gekopieerd.
* [ de configuraties van Dynamic Media met activa groter dan 2 toegelaten GB ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) worden niet gesteund.
* Als de versiegeschiedenis niet wordt gekopieerd, verloopt het kopiëren van de inhoud aanzienlijk sneller.
* De regio&#39;s van de doelomgeving moeten dezelfde zijn als of een deel van de bronomgeving.

## Bekende problemen {#known-issues}

{{content-copy-known-issues}}
