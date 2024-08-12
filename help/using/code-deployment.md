---
title: Codeimplementatie
description: Leer hoe u uw code implementeert en wat er gebeurt in Cloud Manager wanneer u dat doet.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: a7dc30ed31e87ab486f0b279b70c850a33a903eb
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 0%

---


# Codeimplementatie {#code-deployment}

Leer hoe u uw code implementeert en wat er gebeurt in Cloud Manager wanneer u dat doet.

## Code implementeren met Cloud Manager {#deploying-code-with-cloud-manager}

Zodra u uw productiepijplijn, met inbegrip van de noodzakelijke bewaarplaats en milieu&#39;s hebt gevormd, bent u bereid om uw code op te stellen.

1. Klik **opstellen** van Cloud Manager om het plaatsingsproces te beginnen.

   ![ Deploy knoop ](/help/assets/Deploy1.png)

1. De **het schermvertoningen van de Uitvoering van de Pijpleiding**. Klik **bouwen** om het proces te beginnen.

   ![ bouwt knoop ](/help/assets/Deploy2.png)

Het bouwstijlproces begint het proces van de codeplaatsing met inbegrip van de volgende stappen:

* Werkgebiedimplementatie
* Werkgebied testen
* Implementatie van productie

U kunt de stappen van diverse plaatsingsprocessen herzien door logboeken te bekijken, of resultaten voor de testende criteria te herzien.

## Implementatiestappen {#deployment-steps}

Een aantal acties komt tijdens elke stap van de plaatsing voor, die in deze sectie wordt beschreven. Zie {de Details van het Proces van de Plaatsing 0} ](#deployment-process) voor technische details van hoe de code zelf achter-de-scènes wordt opgesteld.[

### Implementatiestap werkgebied {#stage-deployment}

De **plaatsing van het Stadium** stap omvat de volgende acties:

* **Bevestiging**: Deze stap zorgt ervoor dat de pijpleiding wordt gevormd om de momenteel beschikbare middelen te gebruiken. Bijvoorbeeld, dat de gevormde tak bestaat en dat de milieu&#39;s beschikbaar zijn.
* **Bouwstijl &amp; het Testen van de Eenheid**: Deze stap stelt een inperkt bouwstijlproces in werking. Zie [ het Milieu van de Bouwstijl ](/help/getting-started/build-environment.md) voor details.
* **Scannen van de Code**: Deze stap evalueert de kwaliteit van uw toepassingscode. Zie [ Begrijpend de Resultaten van de Test ](/help/using/code-quality-testing.md) voor details op het het testen proces.
* **opstellen aan Stadium**

![ plaatsing van het Stadium ](/help/assets/Stage_Deployment1.png)

### Teststap werkgebied {#stage-testing}

De **het testen van het Stadium** stap omvat de volgende acties:

* **het Testen van de Veiligheid**: Deze stap evalueert het veiligheidseffect van uw code op het AEM milieu. Zie het document [ Begrijpend de Resultaten van de Test ](/help/using/code-quality-testing.md) voor details op het het testen proces.
   * **het Testen van Prestaties**: Deze stap evalueert de prestaties van uw code. Zie [ Begrijpend de Resultaten van de Test ](/help/using/code-quality-testing.md) voor details op het het testen proces.

### Implementatiestap voor productie {#production-deployment}

De **stap van de Plaatsing van de Productie** omvat de volgende acties:

* **Toepassing voor Goedkeuring**
   * Deze optie wordt toegelaten terwijl het vormen van de pijpleiding.
   * Gebruikend deze optie, kunt u of uw productieplaatsing plannen of **nu** klikken om de productieleiding onmiddellijk uit te voeren.
* **Plaatsing van de Productie van het Programma**
   * Deze optie wordt toegelaten terwijl het vormen van de pijpleiding.
   * De geplande datum en tijd worden gespecificeerd in termen van de tijdzone van de gebruiker.
     ![ plaatsing van het Programma ](/help/assets/Production_Deployment1.png)
* **CSE Steun** (als toegelaten)
* **opstellen aan Productie**

![ plaatsing van de Productie ](/help/assets/Prod_Deployment1.png)

Zodra uw plaatsing volledig is, is uw code in zijn gerichte milieu en u kunt de logboeken bekijken.

![ Volledige Plaatsing van de Plaatsing ](/help/assets/Production_Deployment2.png)

## Tijdstippen {#timeouts}

De volgende stappen worden uit uitgevoerd als er op feedback van gebruikers wordt gewacht:

| Stap | Time-out |
|--- |--- |
| Testen van de codekwaliteit | 7 dagen |
| Beveiligingstests | 7 dagen |
| Prestatietesten | 7 dagen |
| Goedkeuringsaanvraag (fase) | 7 dagen |
| Goedkeuringsaanvraag (productie) | 14 dagen |
| Implementatie van planningsproductie | 14 dagen |
| Implementatie van beheerde productie | 14 dagen |

## Implementatieproces — details {#deployment-process}

Cloud Manager uploadt alle doelbestanden/*.zip die tijdens het productieproces worden geproduceerd naar een opslaglocatie. Deze artefacten worden teruggewonnen van deze plaats tijdens opstellen fasen van de pijpleiding.

Wanneer Cloud Manager aan niet productietopologieën opstelt, is het doel de plaatsing zo snel mogelijk te voltooien en daarom worden de artefacten aan alle knopen gelijktijdig opgesteld als volgt:

1. Cloud Manager bepaalt of elk artefact een AEM- of Dispatcher-pakket is.
1. Cloud Manager verwijdert alle verzenders van het taakverdelingsmechanisme om de omgeving tijdens de implementatie te isoleren.

   * Tenzij anders geconfigureerd, kunt u wijzigingen in ontwikkelings- en staging-implementaties overslaan in het taakverdelingsmechanisme. Dat wil zeggen, voor de ontwikkelomgeving, stappen loskoppelen en koppelen in zowel niet-productiepijpleidingen, als voor de halteomgeving van de productiepijpleiding.

   ![ overslaan taakverdelingsmechanisme ](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Naar verwachting zullen 1-1-1 klanten deze functie gebruiken.

1. Elk AEM artefact wordt opgesteld aan elke AEM instantie via de Manager APIs van het Pakket, met pakketgebiedsdelen die de plaatsingsorde bepalen.

   * Voor meer informatie over hoe u pakketten kunt gebruiken om nieuwe functionaliteit te installeren, inhoud over te brengen tussen instanties, en file bewaarplaats inhoud. Zie [ Manager van het Pakket ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >Alle AEM artefacten worden opgesteld aan zowel de auteur als de uitgevers. De wijzen van de looppas zouden moeten worden leveraged wanneer de knoop-specifieke configuraties worden vereist. Meer over leren hoe de looppas-wijzen u toestaan om uw AEM instantie voor een specifiek doel te stemmen, zie de [ sectie van de Wijzen van de Looppas van het document die aan AEM as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes) opstellen.

1. Het Dispatcher-artefact wordt als volgt op elke Dispatcher geïmplementeerd:

   1. Van de huidige configuraties wordt een back-up gemaakt en naar een tijdelijke locatie gekopieerd.
   1. Alle configuraties worden verwijderd, behalve de onveranderlijke bestanden. Zie [ Configuraties van Dispatcher ](/help/getting-started/dispatcher-configurations.md) voor meer details. Op deze manier worden de mappen gewist, zodat er geen zwevende bestanden achterblijven.
   1. Het artefact wordt geëxtraheerd naar de map `httpd` . Onveranderbare bestanden worden niet overschreven. Wijzigingen die u aanbrengt in onveranderlijke bestanden in de Git-opslagplaats, worden genegeerd op het moment van implementatie. Deze bestanden vormen de kern van het AMS Dispatcher-framework en kunnen niet worden gewijzigd.
   1. Apache voert een configuratietest uit. Als er geen fouten worden gevonden, wordt de service opnieuw geladen. Als er een fout optreedt, worden de configuraties hersteld vanaf de back-up, wordt de service opnieuw geladen en wordt de fout geretourneerd naar Cloud Manager.
   1. Elk pad dat in de pijplijnconfiguratie is opgegeven, wordt ongeldig gemaakt of verwijderd uit het Dispatcher-cachegeheugen.

   >[!NOTE]
   >
   >Cloud Manager verwacht dat het Dispatcher-artefact de volledige bestandenset bevat. Alle Dispatcher-configuratiebestanden moeten aanwezig zijn in de Git-opslagplaats. Ontbrekende bestanden of mappen leiden tot een implementatiefout.

1. Nadat alle AEM- en Dispatcher-pakketten naar alle knooppunten zijn geïmplementeerd, worden de verzenders weer toegevoegd aan het taakverdelingsmechanisme en is de implementatie voltooid.

   >[!NOTE]
   >
   >U kunt veranderingen van het taakverdelingsmechanisme in ontwikkeling en het opvoeren Inzet overslaan. Dat wil zeggen, voor de ontwikkelomgeving loskoppelen en stappen koppelen in zowel niet-productiepijpleidingen als voor de halteomgeving van de productiepijplijn.

### Implementatie naar productiefase {#deployment-production-phase}

Het proces voor het opstellen aan productietopologieën verschilt lichtjes om effect aan AEM plaatsbezoekers te minimaliseren.

Productieimplementaties volgen doorgaans dezelfde stappen als hierboven, maar op een voortschrijdende manier:

1. Implementeer AEM pakketten naar de auteur.
1. Dispatcher1 loskoppelen van het taakverdelingsmechanisme.
1. Implementeer AEM pakketten om te publiceren1 en het Dispatcher-pakket om Dispatcher1 parallel te verzenden, de Dispatcher-cache leeg te maken.
1. Plaats dispatcher1 terug in het taakverdelingsmechanisme.
1. Als dispatcher1 weer in bedrijf is, koppelt u dispatcher2 af van het taakverdelingsmechanisme.
1. Implementeer AEM pakketten om te publiceren2 en het Dispatcher-pakket naar dispatcher2 in parallelle, flush Dispatcher cache.
1. Plaats dispatcher2 terug in het taakverdelingsmechanisme.

Dit proces gaat verder tot de plaatsing alle uitgevers en verzenders in de topologie heeft bereikt.

## Uitvoermodus noodleiding {#emergency-pipeline}

In kritieke situaties, zouden de klanten van Adobe Managed Services codeveranderingen in hun stadium en productiemilieu&#39;s kunnen moeten onmiddellijk opstellen. Hierdoor kunnen ze de volledige Cloud Manager-testcyclus omzeilen.

Om deze situaties het hoofd te bieden, kan de Cloud Manager-productiepijplijn in noodsituaties worden uitgevoerd. Als deze modus wordt gebruikt, worden de stappen voor de beveiligings- en prestatietest niet uitgevoerd. Alle andere stappen, met inbegrip van om het even welke gevormde goedkeuringsstappen, worden uitgevoerd zoals op de normale wijze van de pijpleidingsuitvoering.

>[!NOTE]
>
>De functie voor de uitvoering van de noodpijpleiding wordt per programma geactiveerd. De activering wordt uitgevoerd door Succestechnici van de Klant.

### Uitvoermodus voor noodpijpleiding gebruiken {#using-emergency-pipeline}

Wanneer u de uitvoering van een productiepijplijn start, kunt u kiezen tussen de normale modus of de noodmodus in een dialoogvenster. Deze optie is beschikbaar als de functie voor het uitvoeren van de noodpijpleiding voor het programma wordt geactiveerd. Deze optie is beschikbaar als de functie is ingeschakeld.

![ de pijpleidingsopties van de Looppas ](/help/assets/execution-emergency1.png)

Wanneer het bekijken van de pagina van de details van de pijpleidingsuitvoering voor een uitvoering die op noodwijze wordt in werking gesteld, tonen de broodkruimels bij de bovenkant van het scherm een indicator dat de pijpleiding op noodwijze uitvoert.

![ de wijzebroodkruimels van de Noodsituatie ](/help/assets/execution-emergency2.png)

Het uitvoeren van een pijplijn in noodmodus kan ook via de Cloud Manager API of CLI worden uitgevoerd. Als u een uitvoering wilt starten in de noodmodus, dient u een `PUT` -verzoek in bij het eindpunt van de uitvoering van de pijpleiding met de queryparameter `?pipelineExecutionMode=EMERGENCY` of, wanneer u de CLI gebruikt:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Het opnieuw uitvoeren van een Plaatsing van de Productie {#reexecute-deployment}

In zeldzame gevallen kunnen de stappen van de productielocatie om voorbijgaande redenen ontbreken. In deze gevallen kunt u de stap voor productieimplementatie opnieuw uitvoeren zolang deze is voltooid, ongeacht of deze is gelukt, geannuleerd of mislukt. De heruitvoering wordt gesteund door de zelfde pijpleiding te gebruiken die uit de volgende drie stappen bestaat:

1. **bevestigt stap** - de zelfde bevestiging die tijdens een normale pijpleidingsuitvoering voorkomt.
1. **bouwstijlstap** - in de context van een heruitvoering, kopieert de bouwstijlstap artefacten en voert niet eigenlijk een nieuw bouwstijlproces uit.
1. **de stap van de productieplaatsing** - gebruikt de zelfde configuratie en de opties zoals de stap van de productieplaatsing in een normale pijpleidingsuitvoering.

In dergelijke omstandigheden waar een heruitvoering mogelijk is, verstrekt de pagina van de de statuspagina van de productiepijpleiding **re-execute** optie naast de gebruikelijke **Download bouwt logboek** optie.

![ re-execute optie in het venster van het pijpleidingsoverzicht ](/help/assets/re-execute.png)

>[!NOTE]
>
>In een heruitvoering, wordt de bouwstijlstap geëtiketteerd in UI om erop te wijzen dat het artefacten kopieert, niet re-bouwt.

### Beperkingen {#limitations}

* Het opnieuw uitvoeren van de stap van de productieplaatsing is slechts beschikbaar voor de laatste uitvoering.
* Heruitvoering is niet beschikbaar voor terugdraaiacties of het uitvoeren van push-updates.
* Als de laatste uitvoering is mislukt op een willekeurig punt vóór de stap voor de implementatie van de productie, is het niet mogelijk de productie opnieuw uit te voeren.


### API opnieuw uitvoeren {#reexecute-api}

Naast het zijn beschikbaar in UI, kunt u [ Cloud Manager API ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) gebruiken om wederuitvoeringen teweeg te brengen en uitvoeringen te identificeren die als re-uitvoeringen werden teweeggebracht.

#### Een nieuwe uitvoering activeren {#triggering}

Om een heruitvoering teweeg te brengen, moet een `PUT` verzoek aan de Verbinding van de HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` op de productie worden gemaakt stapstaat.

* Als deze koppeling aanwezig is, kan de uitvoering vanaf die stap opnieuw worden gestart.
* Als dit niet het geval is, kan de uitvoering niet vanaf die stap opnieuw worden gestart.

Deze verbinding is slechts ooit beschikbaar voor de productie stelt stap op.

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

De syntaxis van de waarde `href` van de HAL-koppeling is slechts een voorbeeld en de werkelijke waarde moet altijd worden gelezen van de HAL-koppeling en niet worden gegenereerd.

Als u een `PUT` -aanvraag naar dit eindpunt verzendt, levert dit een `201` -reactie op als dit lukt. De responsinstantie is de representatie van de nieuwe uitvoering. Deze functionaliteit is vergelijkbaar met het starten van een normale uitvoering via de API.

#### Een nieuwe uitvoering identificeren {#identifying}

Het systeem identificeert opnieuw uitgevoerde uitvoeringen door de waarde `RE_EXECUTE` op het trekkergebied.