---
title: Content Copy for Environment Consistency
description: Met Content Copy in Cloud Manager kunnen gebruikers op aanvraag muterende inhoud kopiëren van door Managed Services gehoste Adobe Experience Manager 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 228006b424504306e916014bbe8543dc41ba43b5
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 0%

---


# Content Copy voor consistentie van omgeving {#content-copy}

Met Content Copy in Cloud Manager kunnen gebruikers op aanvraag muterende inhoud kopiëren van door Managed Services gehoste Adobe Experience Manager 6.x-productieomgevingen naar lagere omgevingen voor testdoeleinden.

## Info over Inhoud kopiëren {#introduction}

De huidige, echte gegevens zijn waardevol voor het testen, de bevestiging, en de gebruiker-aanvaarding doeleinden. Met Content Copy kunt u inhoud van uw productie-AMS-gehoste AEM 6.x-omgeving kopiëren naar testomgevingen of ontwikkelomgevingen. Deze workflow ondersteunt verschillende testscenario&#39;s.

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

Om de eigenschap van het Exemplaar van de Inhoud te gebruiken, moet de gebruiker aan de **rol van de Manager van de Plaatsing** in de bron en doelmilieu&#39;s worden toegewezen.

## Een inhoudsset maken {#create-content-set}

Voordat inhoud kan worden gekopieerd, moet een inhoudsset zijn gedefinieerd. Wanneer deze is gedefinieerd, kunnen inhoudssets opnieuw worden gebruikt om inhoud te kopiëren. Ga als volgt te werk om een inhoudenset te maken.

**om een geplaatste inhoud tot stand te brengen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openen.

1. Van het linkerzijmenu, onder **de pagina van de Diensten**, klik ![ pictogram van de Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **de Reeksen van de Inhoud**.

1. Vlak de hoger-juiste hoek van de pagina, klik **voeg Geplaatste Inhoud** toe.

   ![ Inhoudsreeksen ](/help/assets/content-sets.png)

1. In het **`Add Content Set`** dialoogvakje, op het **Details** lusje, in de **Naam** en **6} gebieden van de Beschrijving, typ een naam en facultatieve beschrijving voor de geplaatste inhoud, dan klik** verdergaan **.**

   ![ Inhoud plaatste details ](/help/assets/add-content-set-details.png)

1. Op het **lusje van de Wegen van de Inhoud**, op het **Weg** tekstgebied, specificeer een weg aan de inhoud die kan worden veranderd en in de inhoudreeks zou moeten worden omvat.

   Alleen paden die beginnen met `/content` , `/conf` , `/etc` , `/var/workflow/models` of `/var/commerce` , komen in aanmerking voor opname.

1. Klik **![Omslag toevoegen pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Weg** om (of omvat) de weg aan de inhoudreeks toe te voegen.

1. (Optioneel) Voeg desgewenst extra paden toe (maximaal 50) door de vorige twee stappen te herhalen. Anders gaat u door met de volgende stap.

   ![ voegt wegen aan inhoud toe plaatste ](/help/assets/add-content-set-paths.png)

1. (Optioneel) Als u de inhoudenset wilt verkleinen, kunt u desgewenst subpaden opgeven in een opgenomen inhoudspad dat moet worden uitgesloten.

   1. Aan het recht van een inbegrepen inhoudspad dat u wilt beperken, klik ![ het schrappingspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Typ in het tekstveld een relatief pad naar het hoofdpad dat in het dialoogvenster wordt weergegeven.
   1. Klik ![ het schrappingspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **uitsluiten Weg**.
   1. Herhaal indien nodig de stappen i. tot en met iii. hierboven om meer uitsluitingspaden toe te voegen; er is geen beperking. Anders gaat u door met de volgende stap.

   ![ Excluding wegen ](/help/assets/add-content-set-paths-excluded.png)

1. (Optioneel) Voer een van de volgende handelingen uit:

   1. Klik ![ Grootte 500 van de kruis ](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) rechts van een uitgesloten sub-weg om het te schrappen.
   1. Klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) aan het recht van een inbegrepen inhoudspad, dan klik **uitgeven** of **Schrapping**.

   ![ het Uitgeven weglijst ](/help/assets/add-content-set-excluded-paths.png)

1. Klik **creëren**. U kunt de inhoudenset nu gebruiken om inhoud te kopiëren tussen omgevingen.

## Een inhoudsset bewerken of verwijderen {#edit-content-set}

Wanneer u een inhoudsset bewerkt, moet u mogelijk de geconfigureerde paden uitbreiden om de uitgesloten subpaden zichtbaar te maken.

**om een geplaatste inhoud uit te geven of te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openen.

1. Van het linkerzijmenu, onder **Diensten**, klik ![ pictogram van de Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **de Reeksen van de Inhoud**.

1. In de lijst op de **pagina van de Reeksen van de Inhoud**, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) rechts van een inbegrepen inhoudspad, dan klik **uitgeven** of **Schrapping**.

![ geef inhoudreeks ](/help/assets/edit-content-set.png) uit


## Inhoud kopiëren {#copy-content}

Nadat u een inhoudsset hebt gemaakt, kunt u deze gebruiken om inhoud te kopiëren.

Een omgeving kan niet beschikbaar zijn voor selectie als een van de volgende voorwaarden van toepassing is:

* De gebruiker beschikt niet over de vereiste machtigingen.
* Er wordt momenteel een bewerking voor het kopiëren van pijpleidingen of inhoud uitgevoerd in de omgeving.

**om inhoud te kopiëren:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openen.

1. Van het linkerzijmenu, onder **Diensten**, klik ![ pictogram van de Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **de Reeksen van de Inhoud**.

1. In de lijst op de **pagina van de Reeksen van de Inhoud**, rechts van een inbegrepen inhoudsweg die u wilt kopiëren, ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) klikken, dan **Inhoud van het Exemplaar** klikken.

   ![ exemplaar van de Inhoud ](/help/assets/copy-content.png)

1. In het **de dialoogvakje van de inhoud van het 0} Exemplaar {, selecteer het** milieu van Source **en het** milieu van de Bestemming **voor uw actie van het inhoudsexemplaar.**

   * Regio&#39;s in een doelomgeving moeten een subset zijn van regio&#39;s in een bronomgeving.
   * Compatibiliteitsproblemen worden gecontroleerd voordat een handeling voor het kopiëren van inhoud wordt uitgevoerd. Wanneer u het **milieu van de Bestemming** selecteert, bevestigt het systeem automatisch de bron en bestemmingsmilieu&#39;s. Als de validatie mislukt, stopt het proces en wordt een foutbericht weergegeven in het dialoogvenster waarin de oorzaak van de fout wordt uitgelegd.

     ![ het Kopiëren inhoud ](/help/assets/copying-content.png)

1. (Optioneel) Voer een van de volgende handelingen uit:

   1. Om *te behouden* de uitgesloten wegen in het bestemmingsmilieu, controle **`Do not delete exclude paths from destination`**. Met deze instelling blijven de uitgesloten paden die in de inhoudenset zijn opgegeven intact.
   1. Om *te verwijderen* de uitgesloten wegen in het bestemmingsmilieu, uncheck **`Do not delete exclude paths from destination`**. Met deze instelling worden de uitgesloten paden verwijderd die in de inhoudenset zijn opgegeven.
   1. Om de versiegeschiedenis van wegen van het bronmilieu aan het bestemmingsmilieu te kopiëren, controleer **Versies van het Exemplaar**. Het proces van het inhoudsexemplaar is wezenlijk sneller wanneer de versiegeschiedenis *niet* wordt gekopieerd.



1. Klik **Exemplaar**. De status van het kopieerproces wordt weerspiegeld in de console voor de geselecteerde inhoudenset.

## De status Inhoud kopiëren controleren {#copy-activity}

U kunt het statuut van uw exemplaarprocessen in de **pagina van de Activiteit van de Inhoud van het Exemplaar controleren**.

**om de status van het Exemplaar van de Inhoud te controleren:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openen.

1. Van het linkerzijmenu, onder **Diensten**, klik ![ pictogram van de Geschiedenis ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **de Activiteit van de Inhoud van het Exemplaar**.

   ![ Activiteit van het Exemplaar van de Inhoud ](/help/assets/copy-content-activity.png)

   Een proces voor het kopiëren van inhoud kan een van de volgende statussen hebben:

   | Status | Beschrijving |
   | --- | --- |
   | In uitvoering | De bewerking voor het kopiëren van inhoud is aan de gang. |
   | Voltooid | Kopie van inhoud is voltooid. |
   | Mislukt | Kopiëren van inhoud is mislukt. |


## Beperkingen van inhoudskopie {#limitations}

* Een inhoudkopie kan niet worden uitgevoerd van een lagere omgeving naar een hogere omgeving.
* Kopiëren van inhoud kan alleen binnen dezelfde laag worden uitgevoerd. Dat wil zeggen, auteur of publicatieversie.
* Kopiëren van inhoud tussen programma&#39;s en regio&#39;s is niet mogelijk.
* Het exemplaar van de inhoud voor de opslag van wolkengegevens kan gebaseerde topologie slechts worden uitgevoerd wanneer de bron en bestemmingsmilieu op de zelfde wolkenleverancier en in het zelfde gebied zijn.
* Het uitvoeren van gelijktijdige bewerkingen voor het kopiëren van inhoud in dezelfde omgeving is niet mogelijk.
* Het exemplaar van de inhoud kan niet worden uitgevoerd als er om het even welke actieve verrichting die op of het bestemmings of bronmilieu zoals een pijpleiding CI/CD loopt.
* Kopie van inhoud mag niet worden gebruikt als een kloon- of mirroring-gereedschap omdat het geen verplaatste of verwijderde inhoud van de bron kan bijhouden.
* Een inhoudkopie kan niet worden gepauzeerd of geannuleerd nadat deze is gestart.
* Met Inhoud kopiëren worden elementen en Dynamic Media-metagegevens van de hogere omgeving naar de geselecteerde lagere omgeving gedupliceerd. De gekopieerde activa moeten dan worden herverwerkt gebruikend het [ DAM werkschema van procesactiva ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/assets-workflow) op het lagere milieu om de respectieve configuratie van Dynamic Media te gebruiken.
* [ de configuraties van Dynamic Media met activa groter dan 2 toegelaten GB ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) worden niet gesteund.
* De regio&#39;s van de doelomgeving moeten dezelfde zijn als of een deel van de bronomgeving.

## Bekende problemen {#known-issues}

{{content-copy-known-issues}}
