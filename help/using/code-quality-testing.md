---
title: Testen van de codekwaliteit
description: Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 38cf86a5effa201afdc8e00d8f33582fc06214d7
workflow-type: tm+mt
source-wordcount: '2844'
ht-degree: 0%

---


# Testen van de codekwaliteit {#code-quality-testing}

Leer hoe het testen van de codekwaliteit van pijpleidingen werkt en hoe het de kwaliteit van uw plaatsingen kan verbeteren.

## Inleiding {#introduction}

Tijdens de uitvoering van de pijpleiding wordt een aantal metriek gevangen en vergeleken met of de belangrijkste prestatiesindicatoren (KPIs) die door de bedrijfseigenaar worden bepaald of aan normen die door Adobe Managed Services worden geplaatst.

Deze worden gerapporteerd met behulp van een drieledig ratingsysteem.

## Waarderingen met drie lagen {#three-tiered-ratings}

Er liggen drie poorten in de pijplijn:

* Codekwaliteit
* Prestatietesten
* Beveiligingstests

Voor elk van deze poorten is er een structuur met drie lagen voor problemen die door de poort worden geïdentificeerd.

* **Kritiek** - dit zijn kwesties die een directe mislukking van de pijpleiding veroorzaken.
* **Belangrijk** - dit zijn kwesties die de pijpleiding veroorzaken om een gepauzeerde staat in te gaan. Een plaatsingsmanager, projectmanager, of bedrijfseigenaar kunnen of de kwesties met voeten treden, waarin de pijpleiding te werk gaat, of zij kunnen de kwesties goedkeuren, in welk geval de pijpleiding met een mislukking stopt. De opheffing van belangrijke mislukkingen is onderworpen aan a [ onderbreking.](/help/using/code-deployment.md#timeouts)
* **Info** - dit zijn kwesties die puur voor informatiedoeleinden worden verstrekt en geen effect op pijpleidingsuitvoering hebben.

>[!NOTE]
>
>In een slechts pijpleiding van de codekwaliteit, kunnen de belangrijke mislukkingen in de gate van de codekwaliteit niet worden met voeten getreden aangezien de het testen stap van de codekwaliteit de definitieve stap in de pijpleiding is.

## Testen van de codekwaliteit {#code-quality-testing-step}

Deze stap evalueert de kwaliteit van uw toepassingscode, die het belangrijkste doel van een code slechts pijpleiding van de kwaliteit is, en onmiddellijk na de bouwstijlstap in alle niet productie en productiepijpleidingen wordt uitgevoerd. Gelieve te verwijzen naar het document [ Vormend niet-ProductiePijpleidingen ](/help/using/non-production-pipelines.md) om meer te leren.

Testen van de codekwaliteit scant de broncode om ervoor te zorgen dat deze aan bepaalde kwaliteitscriteria voldoet. Dit wordt geïmplementeerd door een combinatie van SonarQube-analyse, inhoudspakketonderzoek met behulp van OakPAL en validatie van verzenders met behulp van het Dispatcher Optimization Tool.

Er zijn meer dan 100 regels die generieke Java-regels en AEM-specifieke regels combineren. Sommige van de AEM-specifieke regels worden gecreeerd gebaseerd op beste praktijken van AEM Techniek en worden bedoeld als [ Regels van de Kwaliteit van de Code van de Douane.](/help/using/custom-code-quality-rules.md)

>[!TIP]
>
>U kunt de volledige lijst van regels [ downloaden gebruikend deze verbinding.](/help/assets/CodeQuality-rules-latest-AMS.xlsx)

De resultaten van het testen van de codekwaliteit worden geleverd als classificatie zoals samengevat in deze lijst.

| Naam | Definitie | Categorie | Drempel voor fout |
|--- |--- |--- |--- |
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
>Verwijs naar [ metrische definities SonarQube ](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) voor meer gedetailleerde informatie.

>[!NOTE]
>
>Meer over de de kwaliteitsregels van de douanecode leren die door [!UICONTROL Cloud Manager] worden uitgevoerd, gelieve te verwijzen naar de 1} Regels van de Kwaliteit van de Code van de Document {.](custom-code-quality-rules.md)[

### Werken met valse positieven {#dealing-with-false-positives}

Het kwaliteitscontroleproces is niet perfect en zal soms ten onrechte problemen identificeren die eigenlijk niet problematisch zijn. Dit wordt als vals positief bedoeld.

In deze gevallen kan de broncode worden geannoteerd met de standaard Java `@SuppressWarnings` -annotatie die de regel-id opgeeft als het annotatiekenmerk. Bijvoorbeeld, één gemeenschappelijk vals positief is dat de regel SonarQube om hardcoded wachtwoorden te ontdekken agressief kan zijn over hoe een hard - gecodeerd wachtwoord wordt geïdentificeerd.

De volgende code is vrij gemeenschappelijk in een AEM project, dat code heeft om met één of andere externe dienst te verbinden.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube zal dan een blokkeerkwetsbaarheid veroorzaken. Maar na het herzien van de code, erkent u dat dit geen kwetsbaarheid is en kan de code met aangewezen regelidentiteitskaart annoteren.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Maar als de code eigenlijk dit was:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dan is de correcte oplossing het hardcoded wachtwoord te verwijderen.

>[!NOTE]
>
>Hoewel het aan te raden is om de `@SuppressWarnings` -annotatie zo specifiek mogelijk te maken (dus alleen de specifieke instructie of het specifieke blok dat de uitgave veroorzaakt, van annoteren te voorzien), is het mogelijk om op klasseniveau notities te maken.

## Beveiligingstests {#security-testing}

[!UICONTROL Cloud Manager] stelt de bestaande Controle van de Gezondheid van de Veiligheid van de Veiligheid op het opvoeren milieu na plaatsing in werking en meldt de status door UI. De resultaten worden samengevoegd van alle AEM in de omgeving.

Deze zelfde gezondheidscontroles kunnen op elk ogenblik door de Console van het Web of het Dashboard van Verrichtingen worden uitgevoerd.

Als een van de gevallen melding maakt van een mislukking voor een bepaalde gezondheidscontrole, mislukt het hele milieu die gezondheidscontrole. Net als bij het testen van de kwaliteit en de prestaties van de code, worden deze gezondheidscontroles in categorieën ingedeeld en gerapporteerd met behulp van het driegistaire gatingsysteem. Het enige verschil is dat er geen drempelwaarde is voor het testen van de veiligheid. Alle gezondheidscontroles worden wel of niet uitgevoerd.

In de volgende tabel staan de gezondheidscontroles.

| Naam | Implementatie van gezondheidscontrole | Categorie |
|---|---|---|
| Gereedheid van API voor bevestiging van de firewall voor deserialisatie is acceptabel. | [ Readiness van de Firewall van de Bevestiging API van Deserialization ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritiek |
| De firewall voor deserialization is functioneel. | [ Functionele Firewall Deserialization ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritiek |
| De firewall voor deserialization wordt geladen. | [ Geladen Firewall Deserialization ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritiek |
| `AuthorizableNodeName` -implementatie stelt geen machtigbare id beschikbaar in de knooppuntnaam/het pad. | [ Vergunnbare Generatie van de Naam van de Knoop ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Kritiek |
| Standaardwachtwoorden zijn gewijzigd. | [ Standaard Login Rekeningen ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | Kritiek |
| Standaard GET-servlet wordt beveiligd tegen DOS-aanvallen. | Sling Get Servlet | Kritiek |
| De Sling Java Script-handler wordt op de juiste wijze geconfigureerd. | JavaScript-handler afspelen | Kritiek |
| De Sling JSP manager van het Manuscript wordt gevormd geschikt. | JSP-scripthandler afspelen | Kritiek |
| SSL is correct geconfigureerd. | SSL-configuratie | Kritiek |
| Er is geen duidelijk onveilig beleid voor gebruikersprofielen gevonden. | Standaardtoegang gebruikersprofiel | Kritiek |
| Het filter van de Verwijzer van de Verkoop wordt gevormd om aanvallen te verhinderen CSRF. | [ het Verkopen Filter van de Verwijzer ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Belangrijk |
| De Adobe Granite HTML Library Manager is op de juiste wijze geconfigureerd. | Config. van Bibliotheekbeheer CQ HTML | Belangrijk |
| De CRXDE-ondersteuningspakket is uitgeschakeld. | CRXDE-ondersteuning | Belangrijk |
| Sling DavEx-bundel en -servlet zijn uitgeschakeld. | DavEx Health Check | Belangrijk |
| Voorbeeldinhoud is niet geïnstalleerd. | Voorbeelden van inhoudspakketten | Belangrijk |
| Zowel het WCM-aanvraagfilter als het WCM-foutopsporingsfilter zijn uitgeschakeld. | [ Configuratie van Filters WCM ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | Belangrijk |
| De verkoop WebDAV bundel en servlet worden gevormd geschikt. | WebDAV Health Check | Belangrijk |
| De webserver is geconfigureerd om te voorkomen dat wordt geklikt. | Webserverconfiguratie | Belangrijk |
| Replicatie maakt geen gebruik van de gebruiker `admin` . | Replicatie- en transportgebruikers | Info |

## Prestatietesten {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager voert prestatietests voor AEM Sites-programma&#39;s uit. De prestatietest wordt ongeveer 30 minuten in werking gesteld door virtuele gebruikers (containers) te draaien die daadwerkelijke gebruikers simuleren om tot pagina&#39;s in het opvoeren milieu&#39;s toegang te hebben om verkeer te simuleren. Deze pagina&#39;s worden gevonden gebruikend een kruipper.

#### Virtuele gebruikers {#virtual-users}

Het aantal virtuele gebruikers of containers die door Cloud Manager worden gesponnen wordt gedreven door KPIs (reactietijd en pagina&#39;s/min) die door de gebruiker met de **rol van de Bedrijfs Eigenaar** wordt bepaald terwijl [ creërend of het programma uitgeeft.](/help/getting-started/program-setup.md) Op basis van de gedefinieerde KPI&#39;s worden maximaal 10 containers gesponnen die werkelijke gebruikers simuleren. De pagina&#39;s die voor het testen zijn geselecteerd, worden gesplitst en toegewezen aan elke virtuele gebruiker.

#### Crawler {#crawler}

Vóór het begin van de testperiode van 30 minuten, zal Cloud Manager de het opvoeren omgeving kruipen gebruikend een reeks van één of meerdere zaadURLs die door de Ingenieur van het Succes van de Klant wordt gevormd. Vanaf deze URL&#39;s wordt de HTML van elke pagina geïnspecteerd en worden koppelingen in de breedteeerste modus doorlopen.

* Dit schuifproces is standaard beperkt tot maximaal 5000 pagina&#39;s.
* Het maximumaantal te testen pagina&#39;s kan worden overschreven door de [ pijpleidingsvariabele ](/help/getting-started/build-environment.md#pipeline-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES` te plaatsen.
   * Toegestane waarden zijn `2000` - `7000` .
* De verzoeken van de kruipper hebben een vaste onderbreking van 10 seconden.

#### Paginasets voor testen {#page-sets}

Pagina&#39;s worden geselecteerd door drie paginasets. Cloud Manager gebruikt de toegangslogboeken van de AEM instanties over productie en het opvoeren milieu&#39;s om de volgende emmers te bepalen.

* **Populaire Levende Pagina&#39;s** - Deze optie wordt geselecteerd om ervoor te zorgen dat de populairste pagina&#39;s die door levende klanten worden betreden worden getest. Cloud Manager leest het toegangslogboek en bepaalt de hoogste 25 meest toegankelijke pagina&#39;s van live klanten om een lijst met top `Popular Live Pages` te genereren. De doorsnede hiervan die ook aanwezig zijn op de testomgeving wordt dan gekropen op de testomgeving.

* **Andere Levende Pagina&#39;s** - Deze optie wordt geselecteerd om ervoor te zorgen dat de pagina&#39;s die buiten de hoogste 25 populaire levende pagina&#39;s vallen die niet populair kunnen zijn, maar belangrijk om zijn te testen, worden getest. Net als bij populaire live pagina&#39;s worden deze opgehaald uit het toegangslogboek en moeten ze ook aanwezig zijn in de testomgeving.

* **Nieuwe Pagina&#39;s** - Deze optie wordt geselecteerd om nieuwe pagina&#39;s te testen die slechts aan het opvoeren en nog niet aan productie kunnen worden opgesteld, maar moeten worden getest.

##### Verspreiding van verkeer over geselecteerde paginasets {#distribution-of-traffic}

U kunt overal van één tot alle drie reeksen op het **Testen** lusje van uw [ pijpleidingsconfiguratie kiezen.](/help/using/production-pipelines.md) De verdeling van het verkeer is gebaseerd op het aantal geselecteerde reeksen. Dit betekent dat als alle drie zijn geselecteerd, 33% van de totale paginaweergaven naar elke set wordt verplaatst. Als er twee zijn geselecteerd, gaat 50% naar elke set. Als één wordt geselecteerd, gaat 100% van het verkeer naar die reeks.

Laten we dit voorbeeld bekijken.

* Er is een splitsing van 50/50 tussen de populaire live pagina&#39;s en nieuwe paginasets.
* Andere actieve pagina&#39;s worden niet gebruikt.
* De nieuwe paginaset bevat 3000 pagina&#39;s.
* De paginaweergaven per minuut KPI is ingesteld op 200.

Gedurende de testperiode van 30 minuten:

* Elk van de 25 pagina&#39;s in de populaire set live pagina&#39;s wordt 120 keer weergegeven: `((200 * 0.5) / 25) * 30 = 120`
* Elk van de 3000 pagina&#39;s in de nieuwe paginaset wordt één keer geraakt: `((200 * 0.5) / 3000) * 30 = 1`

#### Testen en rapporteren {#testing-reporting}

Cloud Manager voert het testen van de prestaties voor AEM Sites-programma&#39;s uit door pagina&#39;s standaard voor een testperiode van 30 minuten als niet-geverifieerde gebruiker op de testpublicatieserver aan te vragen. Het meet de virtuele user-generated metriek (reactietijd, foutentarief, meningen per minuut, enz.) voor elke pagina en voor alle instanties op systeemniveau (CPU, geheugen, netwerkgegevens).

In de volgende tabel wordt een overzicht gegeven van de prestatietestmatrix met behulp van het driegrafeerde gatsysteem.

| Metrisch | Categorie | Drempel voor fout |
|---|---|---|
| Foutfrequentie paginaverzoek | Kritiek | >= 2% |
| CPU-gebruikssnelheid | Kritiek | >= 80% |
| Wachttijd schijf-IO | Kritiek | >= 50% |
| 95e responstijd met percentage | Belangrijk | >= KPI op programmaniveau |
| Piekresponstijd | Belangrijk | >= 18 seconden |
| Weergaven per minuut | Belangrijk | &lt; KPI op programmaniveau |
| Gebruik van schijfbandbreedte | Belangrijk | >= 90% |
| Netwerkbandbreedtegebruik | Belangrijk | >= 90% |
| Aanvragen per minuut | Info | >= 6000 |

Verwijs naar de sectie [ Voor authentiek verklaarde Prestaties Testen ](#authenticated-performance-testing) voor meer details bij het gebruiken van basisauthentificatie voor prestaties het testen voor Plaatsen en Assets.

>[!NOTE]
>
>Zowel auteur- als publicatieinstanties worden tijdens de testperiode gecontroleerd. Als geen metrische waarde voor één instantie wordt verkregen, wordt die metrische waarde als onbekend gerapporteerd en zal de overeenkomstige stap ontbreken.

#### Geverifieerde prestaties testen {#authenticated-performance-testing}

Indien nodig kunnen AMS-klanten met geverifieerde sites een gebruikersnaam en wachtwoord opgeven die Cloud Manager zal gebruiken om toegang te krijgen tot de website tijdens het testen van de prestaties van sites.

De gebruikersnaam en het wachtwoord worden opgegeven als pijpleidingvariabelen met de namen `CM_PERF_TEST_BASIC_USERNAME` en `CM_PERF_TEST_BASIC_PASSWORD` .

De gebruikersnaam moet in een `string` -variabele worden opgeslagen en het wachtwoord moet in een `secretString` -variabele worden opgeslagen. Als beide van deze worden gespecificeerd, zal elk verzoek van de kruipper van de prestatietest en de test virtuele gebruikers deze geloofsbrieven als Basisauthentificatie van HTTP bevatten.

Voer de volgende handelingen uit om deze variabelen in te stellen met de Cloud Manager CLI:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Gelieve te verwijzen naar de ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) API documentatie van de Variabelen van de Lijn van de Gebruiker 0} Patch om te leren hoe te om API te gebruiken.[

### AEM Assets {#aem-assets}

Cloud Manager voert de prestatie-tests voor AEM Assets-programma&#39;s uit door elementen gedurende een testperiode van 30 minuten herhaaldelijk te uploaden.

#### Voorschrift aan boord {#onboarding-requirement}

Voor het testen van Assets-prestaties zal uw Customer Success Engineer een `cloudmanager` gebruiker en wachtwoord maken tijdens het instappen van de auteur in de testomgeving. Voor de teststappen voor prestaties is een gebruiker vereist met de naam `cloudmanager` en het bijbehorende wachtwoord dat door de CSE is ingesteld. Deze mag niet uit de instantie van de auteur worden verwijderd en de machtigingen mogen niet worden gewijzigd. Dit zal waarschijnlijk mislukken bij het testen van de Assets-prestaties.

#### Afbeeldingen en Assets voor tests {#assets-for-testing}

Klanten kunnen hun eigen middelen uploaden om te testen. Dit kan van de **Opstelling van de Pijpleiding worden gedaan** of **geeft** scherm uit. Algemene afbeeldingsindelingen, zoals JPEG, PNG, GIF en BMP, worden ondersteund in combinatie met Photoshop-, Illustrator- en Postscript-bestanden.

Als er geen afbeeldingen zijn geüpload, gebruikt Cloud Manager een standaardafbeelding en PDF-documenten voor het testen.

#### Distributie van Assets voor tests {#distribution-of-assets}

De distributie van hoeveel activa van elk type per minuut worden geupload wordt geplaatst in de **Opstelling van de Pijpleiding** of **geeft** scherm uit.

Als bijvoorbeeld een splitsing van 70/30 wordt gebruikt en er tien elementen per minuut worden geüpload, worden 7 afbeeldingen en 3 documenten per minuut geüpload.

#### Testen en rapporteren {#testing-and-reporting}

Cloud Manager maakt een map op de instantie van de auteur met de gebruikersnaam en het wachtwoord die door de CSE zijn ingesteld. Assets wordt vervolgens geüpload naar de map met behulp van een opensource-bibliotheek. De tests die door Assets worden in werking gesteld worden het testen stap geschreven gebruikend een [ open bronbibliotheek.](https://github.com/adobe/toughday2) Zowel de verwerkingstijd voor elk element als de verschillende metingen op systeemniveau worden over de testduur van 30 minuten gemeten. Met deze functie kunt u zowel afbeeldingen als PDF-documenten uploaden.

>[!TIP]
>
>Gelieve te verwijzen naar het document [ vormen de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) om meer te leren. Verwijs naar de Opstelling van het document [ Programma ](/help/getting-started/program-setup.md) om te leren hoe te opstelling uw programma en uw KPIs te bepalen.

### Resultaten van het testen van prestaties Grafieken {#performance-testing-results-graphs}

Een aantal metriek is beschikbaar in de **dialoog van de Test van Prestaties**

![ Lijst van metriek ](/help/assets/understand_test-results-screen1.png)

De metrische deelvensters kunnen worden uitgevouwen om een grafiek weer te geven, om een koppeling naar een download te bieden of om beide weer te geven.

![ Metriek die als grafiek ](/help/assets/screen_shot_2018-09-05at83933pm.png) wordt uitgebreid

Deze functionaliteit is beschikbaar voor de volgende metriek.

* **Gebruik van cpu** - een grafiek van het gebruik van cpu tijdens de testperiode

* **Schijf I/O wacht Tijd** - een grafiek van schijf I/O wacht tijd tijdens de testperiode

* **Tarief van de Fout van de Pagina** - een grafiek van paginafouten per minuut tijdens de testperiode
   * Een CSV-bestandenlijst met pagina&#39;s die tijdens de test een fout hebben veroorzaakt

* **het Gebruik van de Bandbreedte van de Schijf** - een grafiek van het gebruik van de schijfbandbreedte tijdens de testperiode

* **Gebruik van de Bandbreedte van het Netwerk** - een grafiek van het gebruik van de netwerkbandbreedte tijdens de testperiode

* **Piekresponstijd** - Een grafiek van de piekresponstijd per minuut tijdens de testperiode

* **95th Percentile Tijd van de Reactie** - een grafiek van 95th percentile reactietijd per minuut tijdens de testperiode
   * Een CSV-bestandenlijst met pagina&#39;s waarvan de responstijd van 95% de gedefinieerde PKI heeft overschreden

## Optimalisatie van inhoudspakketscannen {#content-package-scanning-optimization}

In het kader van het kwaliteitsanalyseproces voert Cloud Manager een analyse uit van de inhoudspakketten die door de Maven-build worden geproduceerd. Cloud Manager biedt optimalisaties om dit proces te versnellen, die effectief zijn wanneer bepaalde verpakkingsbeperkingen worden nageleefd. Het meest significant is de optimalisering die voor projecten wordt uitgevoerd die één enkel inhoudspakket uitvoeren, dat algemeen als &quot;allen&quot;pakket wordt bedoeld, dat een aantal andere inhoudspakketten bevat die door de bouwstijl worden geproduceerd, die als overgeslagen worden gemerkt. Wanneer Cloud Manager dit scenario detecteert in plaats van het &quot;all&quot;-pakket uit te pakken, worden de afzonderlijke inhoudspakketten direct gescand en gesorteerd op basis van afhankelijkheden. Neem bijvoorbeeld de volgende build-uitvoer.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (overgeslagen-content-package)

Als de enige items binnen `myco-all-1.0.0-SNAPSHOT.zip` de twee overgeslagen inhoudspakketten zijn, worden de twee ingesloten pakketten gescand in plaats van het &quot;all&quot;-inhoudspakket.

Voor projecten die tientallen ingebedde pakketten produceren, is deze optimalisering getoond om naar boven van 10 minuten per pijpleidingsuitvoering te besparen.

Een speciaal geval kan voorkomen wanneer het &quot;alle&quot;inhoudspakket een combinatie overgeslagen inhoudspakketten en bundels OSGi bevat. Als `myco-all-1.0.0-SNAPSHOT.zip` bijvoorbeeld de twee ingesloten pakketten bevat die eerder zijn vermeld en een of meer OSGi-bundels, wordt een nieuw, minimaal inhoudspakket samengesteld met alleen de OSGi-bundels. Dit pakket krijgt altijd de naam `cloudmanager-synthetic-jar-package` en de opgenomen bundels worden in `/apps/cloudmanager-synthetic-installer/install` geplaatst.

>[!NOTE]
>
>* Deze optimalisatie heeft geen invloed op de pakketten die worden geïmplementeerd op AEM.
>* Omdat de overeenkomst tussen de ingesloten inhoudspakketten en de overgeslagen inhoudspakketten is gebaseerd op bestandsnamen, kan deze optimalisatie niet worden uitgevoerd als meerdere overgeslagen inhoudspakketten exact dezelfde bestandsnaam hebben of als de bestandsnaam tijdens het insluiten is gewijzigd.
