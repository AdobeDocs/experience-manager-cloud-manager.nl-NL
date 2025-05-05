---
title: Testen van de codekwaliteit
description: Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: f5e6ac81c6454730850bb7e884d82be48d2f8525
workflow-type: tm+mt
source-wordcount: '2789'
ht-degree: 0%

---


# Codekwaliteitstests {#code-quality-testing}

Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.

## Inleiding {#introduction}

Tijdens pijpleidingsuitvoering, vangt de software een aantal metriek. Deze metriek worden dan vergeleken met de Belangrijkste Indicatoren van Prestaties (KPIs) die door de bedrijfseigenaar worden bepaald. Of ze worden vergeleken met normen die door Adobe Managed Services zijn vastgesteld.

Deze resultaten worden gerapporteerd met behulp van een drieledig ratingsysteem.

## Driegelaagde ratings {#three-tiered-ratings}

Er liggen drie poorten in de pijplijn:

* Codekwaliteit
* Prestatietesten
* Beveiligingstests

Voor elk van deze poorten is er een structuur met drie lagen voor problemen die door de poort worden geïdentificeerd.

* **Kritieke** - Kwesties die een directe mislukking van de pijpleiding veroorzaken.
* **Belangrijk** - Kwesties die de pijpleiding veroorzaken om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kan of de kwesties met voeten treden. Als ze dat doen, gaat de pijpleiding door zoals bedoeld. Alternatief, kunnen zij de kwesties goedkeuren, veroorzakend de pijpleiding om met een mislukking te stoppen. De opheffing van belangrijke mislukkingen is onderworpen aan a [ onderbreking ](/help/using/code-deployment.md#timeouts).
* **Info** - Kwesties die puur voor informatiedoeleinden worden verstrekt en geen effect op pijpleidingsuitvoering hebben.

>[!NOTE]
>
>In een slechts pijpleiding van de codekwaliteit, kunnen de belangrijke mislukkingen in de gate van de codekwaliteit niet worden met voeten getreden aangezien de het testen stap van de codekwaliteit de definitieve stap in de pijpleiding is.

## Codekwaliteitstests {#code-quality-testing-step}

Deze testende stap evalueert de kwaliteit van uw toepassingscode, die het belangrijkste doel van een code kwaliteit-slechts pijpleiding is. Het wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie- en productiepijpleidingen. Meer leren, ga [ Vormend niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md).

Testen van de codekwaliteit scant de broncode om ervoor te zorgen dat deze aan bepaalde kwaliteitscriteria voldoet.

De software implementeert deze met behulp van een combinatie van SonarQube-analyse, inhoudspakketonderzoek met OakPAL en Dispatcher-validatie met het Dispatcher Optimization Tool.

Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. Sommige van de AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld als [ Regels van de Kwaliteit van de Code van de Douane ](/help/using/custom-code-quality-rules.md).

U kunt de huidige volledige lijst van regels [ downloaden gebruikend deze verbinding ](/help/assets/CodeQuality-rules-latest-AMS.xlsx).

>[!IMPORTANT]
>
>Beginnend Donderdag, 13 Februari, 2025 (Cloud Manager 2025.2.0), gebruikt de Kwaliteit van de Code van Cloud Manager een bijgewerkte versie SonarQube 9.9 en een bijgewerkte lijst van regels die u hier [ kunt downloaden ](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx).

De resultaten van het testen van de codekwaliteit worden geleverd als classificatie zoals samengevat in deze lijst.

| Naam | Definitie | Categorie | Drempel voor fout |
| --- | --- | --- | --- |
| Beveiligingsbeoordeling | A = Geen kwetsbaarheden <br/> B = minstens 1 minder kleine kwetsbaarheid <br/> C = minstens 1 belangrijke kwetsbaarheid <br/> D = minstens 1 kritieke kwetsbaarheid <br/> E = minstens 1 blokkeerkwetsbaarheid | Kritiek | &lt; B |
| Betrouwbaarheidsbeoordeling | A = Geen bugs <br/> B = minstens 1 minder kleine insect <br/> C = minstens 1 belangrijke insect <br/> D = minstens 1 kritieke insect <br/> E = minstens 1 blocker bugs | Belangrijk | &lt; C |
| Onderhoudsverklaring | Gedefinieerd door de openstaande herstelkosten voor code ruikt als een percentage van de tijd dat al naar de toepassing is gegaan <br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Belangrijk | &lt; A |
| Dekking | Gedefinieerd door een combinatie van de dekking van de testlijn en de voorwaarde met de volgende formule: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Voorwaarden die ten minste één keer als `true` zijn geëvalueerd tijdens het uitvoeren van eenheidstests</li><li>`CF` = Voorwaarden die ten minste één keer als `false` zijn geëvalueerd tijdens het uitvoeren van eenheidstests</li><li>`LC` = Covered lines = lines_to_cover - uncover_lines</li><li>`B` = totaal aantal voorwaarden</li><li>`EL` = totaal aantal uitvoerbare regels (lines_to_cover)</li></ul> | Belangrijk | &lt; 50% |
| Overgeslagen eenheidstests | Aantal overgeslagen eenheidstests | Info | > 1 |
| Problemen openen | Algemene uitgiftypen - Vulnerabilities, Bugs en Codefragmenten | Info | > 0 |
| Gedupliceerde lijnen | Gedefinieerd als het aantal regels dat is betrokken bij gedupliceerde blokken. Een codeblok wordt als gedupliceerd beschouwd onder de volgende omstandigheden.<br> niet-Java Projecten:<ul><li>Er moeten ten minste 100 opeenvolgende en gedupliceerde tokens zijn.</li><li>Deze tokens moeten ten minste worden verspreid over: </li><li>30 regels code voor COBOL </li><li>20 coderegels voor ABAP </li><li>10 coderegels voor andere talen</li></ul>Java-projecten:<ul></li><li> Er moeten minstens tien opeenvolgende en gedupliceerde instructies zijn, ongeacht het aantal tokens en regels.</li></ul>Verschillen in inspringing en in letterlijke tekenreeksen worden genegeerd wanneer duplicaten worden gedetecteerd. | Info | > 1% |
| Compatibiliteit met Cloud Service | Aantal geïdentificeerde kwesties van de Verenigbaarheid van de Cloud Service | Info | > 0 |

>[!NOTE]
>
>Voor meer gedetailleerde informatie, {de metrische definities van 0} SonarQube [&#128279;](https://docs.sonarsource.com/sonarqube-server/latest/user-guide/code-metrics/metrics-definition/).

>[!NOTE]
>
>Meer over de de kwaliteitsregels van de douanecode leren die door [!UICONTROL Cloud Manager] worden uitgevoerd, zie [ de Regels van de Kwaliteit van de Code van de Douane ](custom-code-quality-rules.md).

### Omgaan met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en identificeert soms problemen die eigenlijk niet problematisch zijn. Dit scenario wordt een vals positief scenario genoemd.

In deze gevallen kan de broncode worden geannoteerd met de standaard Java `@SuppressWarnings` -annotatie die de regel-id opgeeft als het annotatiekenmerk. Bijvoorbeeld, één gemeenschappelijk vals positief is dat de regel SonarQube om hardcoded wachtwoorden te ontdekken agressief kan zijn over hoe een hard - gecodeerd wachtwoord wordt geïdentificeerd.

De volgende code is vrij gemeenschappelijk in een AEM project, dat code heeft om met één of andere externe dienst te verbinden.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube vergroot vervolgens een kwetsbaarheid voor blokkers. Maar na het herzien van de code, erkent u dat deze kwestie geen kwetsbaarheid is en kan de code met aangewezen regelidentiteitskaart annoteren.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Nochtans, als de code eigenlijk het volgende was:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dan is de correcte oplossing het hardcoded wachtwoord te verwijderen.

>[!NOTE]
>
>Het wordt aanbevolen de annotatie `@SuppressWarnings` zo specifiek mogelijk te maken. Dat wil zeggen dat u alleen de specifieke instructie of het specifieke blok aanwijst die de uitgave veroorzaakt. Het is echter mogelijk om notities te maken op klasseniveau. Dit maakt een bredere onderdrukking van waarschuwingen mogelijk.

## Beveiligingstest {#security-testing}

[!UICONTROL Cloud Manager] stelt de bestaande Controle van de Gezondheid van de Veiligheid van de Veiligheid op het opvoeren milieu na plaatsing in werking en meldt de status door UI. De resultaten worden samengevoegd van alle AEM in de omgeving.

Deze zelfde gezondheidscontroles kunnen op elk ogenblik door de Console van het Web of het Dashboard van Verrichtingen worden uitgevoerd.

Als een van de gevallen melding maakt van een mislukking voor een bepaalde gezondheidscontrole, mislukt het hele milieu die gezondheidscontrole. Net als bij het testen van de kwaliteit en de prestaties van de code, worden deze gezondheidscontroles in categorieën ingedeeld en gerapporteerd met behulp van het driegistaire gatingsysteem. Het enige verschil is dat er geen drempel is als er veiligheidstests zijn. Alle gezondheidscontroles worden wel of niet uitgevoerd.

In de volgende tabel staan de gezondheidscontroles.

| Naam | Implementatie van gezondheidscontrole | Categorie |
|---|---|---|
| Gereedheid van API voor bevestiging van de firewall voor deserialisatie is acceptabel. | [ Readiness van de Firewall van de Bevestiging API van Deserialization ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Kritiek |
| De firewall voor deserialization is functioneel. | [ Functionele Firewall Deserialization ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Kritiek |
| De firewall voor deserialization wordt geladen. | [ Geladen Firewall Deserialization ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Kritiek |
| `AuthorizableNodeName` -implementatie stelt geen machtigbare id beschikbaar in de knooppuntnaam/het pad. | [ Vergunnbare Generatie van de Naam van de Knoop ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security-checklist#security) | Kritiek |
| Standaardwachtwoorden zijn gewijzigd. | [ Standaard Login Rekeningen ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | Kritiek |
| Standaard GET-servlet wordt beveiligd tegen DOS-aanvallen. | Sling Get Servlet | Kritiek |
| De Sling JavaScript-handler wordt op de juiste wijze geconfigureerd. | Sling JavaScript Handler | Kritiek |
| De Sling JSP manager van het Manuscript wordt gevormd geschikt. | JSP-scripthandler afspelen | Kritiek |
| SSL is correct geconfigureerd. | SSL-configuratie | Kritiek |
| Er is geen duidelijk onveilig beleid voor gebruikersprofielen gevonden. | Standaardtoegang gebruikersprofiel | Kritiek |
| Het filter van de Verwijzer van de Verkoop wordt gevormd om aanvallen te verhinderen CSRF. | [ het Verkopen Filter van de Verwijzer ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security-checklist#security) | Belangrijk |
| De Adobe Granite HTML Library Manager is op de juiste wijze geconfigureerd. | Config. van Bibliotheekbeheer CQ HTML | Belangrijk |
| De CRXDE-ondersteuningspakket is uitgeschakeld. | CRXDE-ondersteuning | Belangrijk |
| Sling DavEx-bundel en -servlet zijn uitgeschakeld. | DavEx Health Check | Belangrijk |
| Voorbeeldinhoud is niet geïnstalleerd. | Voorbeelden van inhoudspakketten | Belangrijk |
| Zowel het WCM-aanvraagfilter als het WCM-foutopsporingsfilter zijn uitgeschakeld. | [ Configuratie van Filters WCM ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | Belangrijk |
| De verkoop WebDAV bundel en servlet worden gevormd geschikt. | WebDAV Health Check | Belangrijk |
| De webserver is geconfigureerd om te voorkomen dat wordt geklikt. | Webserverconfiguratie | Belangrijk |
| Replicatie maakt geen gebruik van de gebruiker `admin` . | Replicatie- en transportgebruikers | Info |

## Prestatietests {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager voert prestatietests voor AEM Sites-programma&#39;s uit. De prestatietest wordt ongeveer 30 minuten in werking gesteld door virtuele gebruikers (containers) te draaien die daadwerkelijke gebruikers simuleren om tot pagina&#39;s in het opvoeren milieu&#39;s toegang te hebben om verkeer te simuleren. Deze pagina&#39;s worden gevonden gebruikend een kruipper.

#### Virtuele gebruikers {#virtual-users}

Cloud Manager spint omhoog virtuele gebruikers of containers die op KPIs (reactietijd en pagina&#39;s/min) worden gebaseerd die door de **rol van de BedrijfsEigenaar** worden geplaatst. Deze KPIs wordt geplaatst terwijl [ creërend of het uitgeven van het programma ](/help/getting-started/program-setup.md).

Op basis van de gedefinieerde KPI&#39;s worden maximaal tien containers gesponnen die werkelijke gebruikers simuleren. De pagina&#39;s die voor het testen zijn geselecteerd, worden gesplitst en toegewezen aan elke virtuele gebruiker.

#### Crawler {#crawler}

Vóór het begin van de testperiode van 30 minuten kruipt Cloud Manager de testomgeving met behulp van een set van een of meer zaadURL&#39;s die door de Klantsuccesingenieur zijn geconfigureerd. Vanaf deze URL&#39;s wordt de HTML van elke pagina geïnspecteerd en worden koppelingen in de breedteeerste modus doorlopen.

* Dit schuifproces is standaard beperkt tot maximaal 5000 pagina&#39;s.
* Het maximumaantal te testen pagina&#39;s kan worden overschreven door de [ pijpleidingsvariabele ](/help/getting-started/build-environment.md#pipeline-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES` te plaatsen.
   * Toegestane waarden zijn `2000` - `7000` .
* De verzoeken van de kruipper hebben een vaste onderbreking van 10 seconden.

#### Paginasets voor testen {#page-sets}

Drie paginasets selecteren de pagina&#39;s. Cloud Manager gebruikt de toegangslogboeken van de AEM instanties over productie en het opvoeren milieu&#39;s om de volgende emmers te bepalen.

* **Populaire Levende Pagina&#39;s** - verzekert dat de populairste pagina&#39;s die door levende klanten worden betreden worden getest. Cloud Manager leest het toegangslogboek en bepaalt de hoogste 25 meest toegankelijke pagina&#39;s door levende klanten om een lijst van bovenkant te produceren `Popular Live Pages`. Het snijpunt van deze pagina&#39;s die ook aanwezig zijn in de testomgeving, wordt vervolgens gekropen in de testomgeving.

* **Andere Levende Pagina&#39;s** - verzekert dat de pagina&#39;s die buiten de hoogste 25 populaire levende pagina&#39;s vallen die niet populair kunnen zijn, maar belangrijk zijn te testen, worden getest. Net als bij populaire live pagina&#39;s worden deze uit het toegangslogboek geëxtraheerd en moeten ze ook aanwezig zijn in de testomgeving.

* **Nieuwe Pagina&#39;s** - test nieuwe pagina&#39;s die slechts aan het opvoeren en nog niet aan productie kunnen zijn opgesteld, maar moeten worden getest.

##### Verdeling van verkeer over geselecteerde paginasets {#distribution-of-traffic}

U kunt overal van één tot alle drie reeksen op het **Testen** lusje van uw [ pijpleidingsconfiguratie ](/help/using/production-pipelines.md) kiezen. De verdeling van verkeer is gebaseerd op het aantal geselecteerde reeksen. Als alle drie zijn geselecteerd, wordt 33% van de totale paginaweergaven in elke set geplaatst. Als er twee zijn geselecteerd, gaat 50% naar elke set. Als één wordt geselecteerd, gaat 100% van het verkeer naar die reeks.

Laten we dit voorbeeld bekijken.

* Er is een splitsing van 50/50 tussen de populaire live pagina&#39;s en nieuwe paginasets.
* Andere actieve pagina&#39;s worden niet gebruikt.
* De nieuwe paginaset bevat 3000 pagina&#39;s.
* De KPI *paginameningen per minuut* worden geplaatst aan 200.

Gedurende de testperiode van 30 minuten:

* Elk van de 25 pagina&#39;s in de populaire set live pagina&#39;s wordt 120 keer weergegeven: `((200 * 0.5) / 25) * 30 = 120`
* Elk van de 3000 pagina&#39;s in de nieuwe paginaset wordt één keer geraakt: `((200 * 0.5) / 3000) * 30 = 1`

#### Testen en rapporteren {#testing-reporting}

Cloud Manager voert het testen van de prestaties voor AEM Sites-programma&#39;s uit door pagina&#39;s standaard voor een testperiode van 30 minuten als niet-geverifieerde gebruiker op de testpublicatieserver aan te vragen. Het meet de virtuele user-generated metriek (reactietijd, foutentarief, meningen per minuut, etc.) voor elke pagina en diverse systeem-vlakke metriek (CPU, geheugen, voorzien van een netwerkgegevens) voor alle instanties.

In de volgende tabel wordt een overzicht gegeven van de prestatietestmatrix met behulp van het driegrafeerde gatsysteem.

| Metrisch | Categorie | Drempel voor fout |
|---|---|---|
| Foutfrequentie paginaverzoek | Kritiek | >= 2% |
| CPU-gebruiksfrequentie | Kritiek | >= 80% |
| Wachttijd schijf-IO | Kritiek | >= 50% |
| 95e responstijd met percentage | Belangrijk | >= KPI op programmaniveau |
| Piekresponstijd | Belangrijk | >= 18 seconden |
| Weergaven per minuut | Belangrijk | &lt; KPI op programmaniveau |
| Gebruik van schijfbandbreedte | Belangrijk | >= 90% |
| Netwerkbandbreedtegebruik | Belangrijk | >= 90% |
| Aanvragen per minuut | Info | >= 6000 |

Zie [ Voor authentiek verklaarde prestaties het testen ](#authenticated-performance-testing) voor meer details bij het gebruiken van basisauthentificatie voor prestaties het testen voor Plaatsen en Assets.

>[!NOTE]
>
>Zowel auteur- als publicatieinstanties worden tijdens de test gecontroleerd. Als geen metrische waarde voor één instantie wordt verkregen, wordt die metrische waarde gerapporteerd als onbekend en mislukt de corresponderende stap.

#### Geverifieerde prestaties testen {#authenticated-performance-testing}

Indien nodig kunnen AMS-klanten met geverifieerde sites een gebruikersnaam en wachtwoord opgeven die door Cloud Manager worden gebruikt om toegang te krijgen tot de website tijdens het testen van de prestaties van sites.

De gebruikersnaam en het wachtwoord worden opgegeven als pijpleidingvariabelen met de namen `CM_PERF_TEST_BASIC_USERNAME` en `CM_PERF_TEST_BASIC_PASSWORD` .

De gebruikersnaam wordt opgeslagen in een `string` -variabele en het wachtwoord wordt opgeslagen in een `secretString` -variabele. Als beide variabelen worden gespecificeerd, bevat elk verzoek van de kruipper van de prestatietest en de test virtuele gebruikers deze geloofsbrieven als Basisauthentificatie van HTTP.

Voer de volgende handelingen uit om deze variabelen in te stellen met de Cloud Manager CLI:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Zie [ de variabelen van de gebruikerspijpleiding van het Patch ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) API documentatie leren hoe te om API te gebruiken.

### AEM Assets {#aem-assets}

Cloud Manager voert prestatietests uit voor AEM Assets-programma&#39;s door elementen herhaaldelijk gedurende 30 minuten te uploaden.

#### Verplichting aan boord {#onboarding-requirement}

Voor het testen van Assets-prestaties maakt uw Customer Success Engineer een `cloudmanager` gebruiker en wachtwoord tijdens het instappen van de auteur in de testomgeving. Voor de teststappen voor prestaties is een gebruiker vereist met de naam `cloudmanager` en het bijbehorende wachtwoord dat door de CSE is ingesteld.

Deze methode zou in de auteursinstantie met zijn toestemmingen onveranderd moeten blijven. Het wijzigen of verwijderen ervan kan ertoe leiden dat Assets-prestatietests mislukken.

#### Afbeeldingen en Assets voor testdoeleinden {#assets-for-testing}

Klanten kunnen hun eigen middelen uploaden om te testen. Dit proces kan van de **Opstelling van de Pijpleiding** worden gedaan of **&#x200B;**&#x200B;scherm uitgeven. Algemene afbeeldingsindelingen, zoals JPEG, PNG, GIF en BMP, worden ondersteund in combinatie met Photoshop-, Illustrator- en Postscript-bestanden.

Als er geen afbeeldingen zijn geüpload, gebruikt Cloud Manager een standaardafbeelding en PDF-documenten voor het testen.

#### Distributie van Assets voor tests {#distribution-of-assets}

De distributie van hoeveel activa van elk type per minuut worden geupload wordt geplaatst in de **Opstelling van de Pijpleiding** of **geeft** scherm uit.

Als bijvoorbeeld een splitsing van 70/30 wordt gebruikt en er 10 elementen per minuut worden geüpload, worden 7 afbeeldingen en 3 documenten per minuut geüpload.

#### Testen en rapporteren {#testing-and-reporting}

Cloud Manager maakt een map op de auteurinstantie met de gebruikersnaam en het wachtwoord die door de CSE-instelling worden ingesteld. Assets wordt vervolgens geüpload naar de map met behulp van een opensource-bibliotheek. De tests die door Assets worden in werking gesteld worden het testen stap geschreven gebruikend een [ open bronbibliotheek ](https://github.com/adobe/toughday2). Zowel de verwerkingstijd voor elk element als de verschillende metingen op systeemniveau worden over de testduur van 30 minuten gemeten. Met deze functie kunt u zowel afbeeldingen als PDF-documenten uploaden.

>[!TIP]
>
>Zie [ productiepijpleidingen ](/help/using/production-pipelines.md) vormen om meer te leren. Zie [&#128279;](/help/getting-started/program-setup.md) de Opstelling van het 0&rbrace; Programma leren hoe te opstelling uw programma en uw KPIs bepalen.

### Prestatietestresultaten {#performance-testing-results-graphs}

Een aantal metriek is beschikbaar in de **de dialoogdoos van de Test van Prestaties**.

![ Lijst van metriek ](/help/assets/understand_test-results-screen1.png)

De metrische deelvensters kunnen worden uitgevouwen om een grafiek weer te geven, om een koppeling naar een download te bieden of om beide weer te geven.

![ Metriek die als grafiek ](/help/assets/screen_shot_2018-09-05at83933pm.png) wordt uitgebreid

Deze functionaliteit is beschikbaar voor de volgende metriek.

* **het Gebruik van CPU** - een grafiek van het gebruik van CPU tijdens de testperiode

* **Schijf I/O wacht Tijd** - een grafiek van schijf I/O wacht tijd tijdens de testperiode

* **Tarief van de Fout van de Pagina** - een grafiek van paginafouten per minuut tijdens de testperiode
   * Een CSV-bestand met pagina&#39;s die een fout hebben veroorzaakt tijdens de test

* **het Gebruik van de Bandbreedte van de Schijf** - een grafiek van het gebruik van de schijfbandbreedte tijdens de testperiode

* **Gebruik van de Bandbreedte van het Netwerk** - een grafiek van het gebruik van de netwerkbandbreedte tijdens de testperiode

* **Piekresponstijd** - Een grafiek van de piekresponstijd per minuut tijdens de testperiode

* **95th Percentile Tijd van de Reactie** - een grafiek van 95th percentile reactietijd per minuut tijdens de testperiode
   * Een CSV-bestandenlijst met pagina&#39;s waarvan de responstijd van 95% de gedefinieerde PKI heeft overschreden

## Optimalisatie van scannen van inhoudspakketten {#content-package-scanning-optimization}

In het kader van het kwaliteitsanalyseproces voert Cloud Manager een analyse uit van de inhoudspakketten die door de Maven-build worden geproduceerd. Cloud Manager biedt optimalisaties om dit proces te versnellen, dat effectief is wanneer bepaalde verpakkingsbeperkingen worden nageleefd.

De belangrijkste optimalisatie is voor projecten die één enkel &quot;all&quot;pakket uitvoeren, dat andere inhoudspakketten bevat die door de bouwstijl worden geproduceerd, die als overgeslagen worden gemerkt. Wanneer Cloud Manager dit scenario detecteert in plaats van het &quot;all&quot;-pakket uit te pakken, worden de afzonderlijke inhoudspakketten direct gescand en gesorteerd op basis van afhankelijkheden. Neem bijvoorbeeld de volgende build-uitvoer.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)

Als de enige items binnen `myco-all-1.0.0-SNAPSHOT.zip` de twee overgeslagen inhoudspakketten zijn, worden de twee ingesloten pakketten gescand in plaats van het &quot;all&quot;-inhoudspakket.

Voor projecten die tientallen ingebedde pakketten produceren, is deze optimalisering getoond om naar boven van 10 minuten per pijpleidingsuitvoering te besparen.

Een speciaal geval kan voorkomen wanneer het &quot;alle&quot;inhoudspakket een combinatie overgeslagen inhoudspakketten en bundels OSGi bevat. Als `myco-all-1.0.0-SNAPSHOT.zip` bijvoorbeeld de twee eerder vermelde ingesloten pakketten en een of meer OSGi-pakketten bevat, wordt een nieuw, minimaal inhoudspakket samengesteld met alleen de OSGi-bundels. Dit pakket krijgt altijd de naam `cloudmanager-synthetic-jar-package` en de opgenomen bundels worden in `/apps/cloudmanager-synthetic-installer/install` geplaatst.

>[!NOTE]
>
>* Deze optimalisatie heeft geen invloed op de pakketten die worden geïmplementeerd op AEM.
>* Het afstemmen tussen ingesloten en overgeslagen inhoudspakketten is gebaseerd op bestandsnamen. Deze optimalisatie mislukt als meerdere overgeslagen inhoudspakketten dezelfde bestandsnaam hebben of als de bestandsnaam tijdens het insluiten verandert.
