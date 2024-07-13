---
title: CI/CD-pijpleidingen
description: Leer over CI/CD pijpleidingen en hoe zij plaatsingen aan het opvoeren en productiemilieu's in Cloud Manager behandelen.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# CI/CD-pijpleidingen {#ci-cd-pipeline}

Leer over CI/CD pijpleidingen en hoe zij plaatsingen aan het opvoeren en productiemilieu&#39;s in Cloud Manager behandelen.

## Overzicht {#overview}

[!UICONTROL Cloud Manager] omvat een ononderbroken integratie/ononderbroken levering (CI/CD) kader, dat implementatieteams toestaat om nieuwe of bijgewerkte code snel te testen en te leveren. Bijvoorbeeld, kunnen de implementatieteams opstelling, vormen, en beginnen een geautomatiseerde pijpleiding CI/CD die Adobe coderend beste praktijken gebruikt om een grondig codescans uit te voeren en de hoogste codekwaliteit te verzekeren.

De CI/CD pijpleiding automatiseert ook eenheid en prestaties testende processen om plaatsingsefficiency te verhogen en proactief kritieke kwesties identificeren die na plaatsing duur zijn om te bevestigen. Implementatieteams hebben toegang tot een uitgebreid rapport met codeprestaties om inzicht te krijgen in mogelijke gevolgen voor KPI&#39;s en kritieke beveiligingsvalidaties als de code wordt geïmplementeerd in de productie.

## Het pijpleidingproces {#pipeline-process}

In dit diagram ziet u wat er gebeurt wanneer een release wordt geactiveerd in [!UICONTROL Cloud Manager] met behulp van een pijplijn.

![ het pijpleidingsproces ](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipetstap | Beschrijving |
|---|---|
| 1. Start een release | Een plaatsingsmanager brengt of manueel een versie teweeg, met een it begaat, of gebaseerd op een terugkomende planning. |
| 2. Release-tag maken | [!UICONTROL Cloud Manager] maakt een tag git om de release te markeren met een automatisch gegenereerd versienummer, bijvoorbeeld `2018.531.245527.0000001222` . |
| 3. Gebouwd als release met automatisch gegenereerde versie | [!UICONTROL Cloud Manager] bouwt de toepassing met het onlangs toegewezen versienummer. |
| 4. De kwaliteit van de code evalueren | [!UICONTROL Cloud Manager] scant de broncode en verstrekt een samenvatting alvorens de code aan het opvoeren milieu kan worden opgesteld. |
| 5. Opgeslagen artefact(en) | De versieartefacten worden opgeslagen voor later gebruik in de plaatsingsstappen. |
| 6. Automatische uitrol van artefact(en) naar AMS-AEM | Het releaseartefact wordt geïmplementeerd in de testomgeving. |
| 7. Triggerautomatische tests | [!UICONTROL Cloud Manager] voert prestatie- en beveiligingstests uit op het artefact. |
| 8. Invoering van productiestrempels | Nadat de geautomatiseerde tests zijn voltooid, start [!UICONTROL Cloud Manager] de implementatie op productie. |
| 9. [!UICONTROL Cloud Manager] vraagt om artefacten die moeten worden geïmplementeerd | [!UICONTROL Cloud Manager] trekt de opgeslagen versieartefacten. |
| 10. Artefacten bij de productie plaatsen | De releaseartefacten worden ingezet in de productieomgeving. |

### Hoe te Opstelling een CI/CD pijpleiding {#how-to-setup-a-ci-cd-pipeline}

Om meer over pijpleidingsconfiguratie te leren, zie de documenten [ Vormend de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ Vormend niet-ProductiePijpleidingen.](/help/using/non-production-pipelines.md)

## Kwaliteitsgates {#quality-gates}

De pijpleiding CI/CD verstrekt kwaliteitsspoorten, of goedkeuringscriteria, die moeten worden voldaan alvorens de code van het opvoerende milieu aan het plaatsingsmilieu kan worden verplaatst. Er liggen drie poorten in de pijplijn:

* Codekwaliteit
* Prestatietesten
* Beveiligingstests

Voor elk van deze poorten kunnen drie niveaus worden vastgesteld:

* **Kritieke** - de Kritieke kwesties die door de poort worden geïdentificeerd veroorzaken een directe mislukking van de pijpleiding.
* **Belangrijk** - de Belangrijke die kwesties door de poort worden geïdentificeerd veroorzaken de pijpleiding om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen of de kwesties met voeten treden, waarin de pijpleiding te werk gaat, of zij kunnen de kwesties goedkeuren, in welk geval de pijpleiding met een mislukking stopt.
* **Informatie** - de kwesties van de informatie die door de poort worden geïdentificeerd worden verstrekt puur voor informatiedoeleinden en hebben geen effect op de pijpleidingsuitvoering.

Dit is een voorbeeld van een codescan met geïdentificeerde problemen.

![ het aftasten van de Code voorbeeld ](/help/assets/quality-gate-failed.png)

### Gates instellen {#how-to-setup-gates}

Zie het document [ Vormend de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) voor details bij vestiging uw code, kwaliteit, en prestatiespoorten.
