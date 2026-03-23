---
title: CI/CD-pijpleidingen
description: Leer over CI/CD pijpleidingen en hoe zij plaatsingen aan het opvoeren en productiemilieu's in Cloud Manager behandelen.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: b7e651b72d1943aef69c1c69915d4752a6163931
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 1%

---


# Cd/cd-pijpleidingen {#ci-cd-pipeline}

Leer over CI/CD pijpleidingen en hoe zij plaatsingen aan het opvoeren en productiemilieu&#39;s in Cloud Manager behandelen.

## Overzicht {#overview}

[!UICONTROL Cloud Manager] omvat een ononderbroken integratie/ononderbroken levering (CI/CD) kader, dat implementatieteams toestaat om nieuwe of bijgewerkte code snel te testen en te leveren. De teams van de implementatie kunnen opstelling, vormen, en beginnen een geautomatiseerde pijpleiding CI/CD. Deze pijplijn volgt de codeerbeste praktijken van Adobe om een uitvoerige codescan uit te voeren en de hoogste codekwaliteit te verzekeren.

De CI/CD pijpleiding automatiseert ook eenheid en prestaties testende processen om plaatsingsefficiency te verhogen en proactief kritieke kwesties identificeren die na plaatsing duur zijn om te bevestigen. Implementatieteams hebben toegang tot een uitgebreid rapport met codeprestaties om inzicht te krijgen in mogelijke gevolgen voor KPI&#39;s en kritieke beveiligingsvalidaties als de code wordt geïmplementeerd in de productie.

## Over het pijpleidingsproces {#pipeline-process}

In het volgende diagram ziet u wat er gebeurt wanneer een release wordt geactiveerd in [!UICONTROL Cloud Manager] via een pijplijn.

![ het pijpleidingsproces ](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipetstap | Beschrijving |
| --- | --- |
| &#x200B;1. Een release starten | Een plaatsingsmanager brengt of manueel een versie teweeg, met een Git begaan, of gebaseerd op een terugkomende planning. |
| &#x200B;2. Een releasetag maken | [!UICONTROL Cloud Manager] maakt een tag Git om de release te markeren met een automatisch gegenereerd versienummer, bijvoorbeeld `2018.531.245527.0000001222` . |
| &#x200B;3. Gebouwd als release met automatisch gegenereerde versie | [!UICONTROL Cloud Manager] bouwt de toepassing met het onlangs toegewezen versienummer. |
| &#x200B;4. Codekwaliteit evalueren | [!UICONTROL Cloud Manager] scant de broncode en verstrekt een samenvatting alvorens de code aan het opvoeren milieu kan worden opgesteld. |
| &#x200B;5. Versiepunten opgeslagen | De versieartefacten worden opgeslagen voor later gebruik in de plaatsingsstappen. |
| &#x200B;6. Automatische implementatie van artefacten op AMS AEM-ophaling | Het releaseartefact wordt geïmplementeerd in de testomgeving. |
| &#x200B;7. Automatische tests activeren | [!UICONTROL Cloud Manager] voert prestatie- en beveiligingstests uit op het artefact. |
| &#x200B;8. Implementatie van productitrigger | Nadat de geautomatiseerde tests zijn voltooid, start [!UICONTROL Cloud Manager] de implementatie op productie. |
| &#x200B;9. [!UICONTROL Cloud Manager] krijgt artefacten om te implementeren | [!UICONTROL Cloud Manager] trekt de opgeslagen versieartefacten. |
| &#x200B;10. Artefacten implementeren voor productie | De releaseartefacten worden ingezet in de productieomgeving. |

### Snellere builds met Smart Build {#use=smart-build}

Cloud Manager gebruikt nu een geoptimaliseerde bouwstijlstrategie genoemd **Slim bouwt**, die module-vlakke caching gebruikt om het bouwstijlproces te versnellen. Tijdens elke bouw, slechts worden de modules die zijn veranderd herbouwd, terwijl de onveranderde modules van het geheime voorgeheugen opnieuw worden gebruikt.

De slimme Bouwstijl is beschikbaar voor de Kwaliteit van de Code en Dev Volledige de plaatsingspijpleidingen van de Stapel slechts.

Zie [ een niet-productiepijpleiding ](/help/using/non-production-pipelines.md#add-non-production-pipeline) en [ over het gebruiken van Slimme bouwt in een niet-productiepijpleiding ](/help/using/non-production-pipelines.md#about-smart-build) toevoegen.


### Hoe te opstelling een pijpleiding CI/CD {#how-to-setup-a-ci-cd-pipeline}

Om meer over pijpleidingsconfiguratie te leren, zie de documenten [ Vormend de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ Vormend niet-Productie Pijpleidingen ](/help/using/non-production-pipelines.md).

## Kwaliteitskloven {#quality-gates}

De pijpleiding CI/CD verstrekt kwaliteitsspoorten, of goedkeuringscriteria, die moeten worden voldaan alvorens de code van het opvoerende milieu aan het plaatsingsmilieu kan worden verplaatst. Er liggen drie poorten in de pijplijn:

* Codekwaliteit
* Prestatietesten
* Beveiligingstests

Voor elk van deze poorten kunnen drie niveaus worden vastgesteld:

* **Kritieke** - de Kritieke kwesties die door de poort worden geïdentificeerd veroorzaken een directe mislukking van de pijpleiding.
* **Belangrijk** - de Belangrijke die kwesties door de poort worden geïdentificeerd veroorzaken de pijpleiding om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen de kwesties met voeten treden, toestaand de pijpleiding om te werk te gaan. Alternatief, kunnen zij de kwesties goedkeuren, veroorzakend de pijpleiding om met een mislukking te stoppen.
* **Informatie** - de kwesties van de informatie die door de poort worden geïdentificeerd worden verstrekt puur voor informatiedoeleinden en hebben geen effect op de pijpleidingsuitvoering.

Hieronder ziet u een voorbeeld van een codescan met geïdentificeerde problemen.

![ het aftasten van de Code voorbeeld ](/help/assets/quality-gate-failed.png)

### Gates instellen {#how-to-setup-gates}

Zie het document [ Vormend de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) voor details bij vestiging uw code, kwaliteit, en prestatiespoorten.
