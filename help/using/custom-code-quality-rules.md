---
title: Aangepaste regels voor codekwaliteit
description: Ontdek de specificaties van de aangepaste codecwaliteitsregels die door Cloud Manager worden uitgevoerd tijdens het testen van de codekwaliteit. Deze regels zijn gegrond in beste praktijken van AEM Techniek.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '3482'
ht-degree: 0%

---


# Aangepaste regels voor codekwaliteit {#custom-code-quality-rules}

Leer details over de de kwaliteitsregels van de douanecode die door Cloud Manager als deel van [ worden uitgevoerd codekwaliteit het testen ](/help/using/code-quality-testing.md), op beste praktijken van AEM Techniek wordt gebaseerd.

>[!NOTE]
>
>De hier gegeven codevoorbeelden zijn slechts voor illustratieve doeleinden. Zie {de documentatie van Concepten van 0} SonarQube ](https://docs.sonarsource.com/sonarqube/latest/) om over zijn concepten en kwaliteitsregels te leren.[

>[!NOTE]
>
>Volledige SonarQube-regels zijn niet beschikbaar voor downloaden vanwege informatie die eigendom is van de Adobe. U kunt de volledige lijst van regels [ downloaden gebruikend deze verbinding ](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Lees dit document verder voor beschrijvingen en voorbeelden van de regels.

## SonarQube-regels {#sonarqube-rules}

In de volgende sectie worden SonarQube-regels beschreven die door Cloud Manager worden uitgevoerd.

### Gebruik geen potentieel gevaarlijke functies {#do-not-use-potentially-dangerous-functions}

* **Sleutel**: CQRules:CWE-676
* **Type**: Vulnerability
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

De methoden `Thread.stop()` en `Thread.interrupt()` kunnen problemen veroorzaken die moeilijk te reproduceren zijn, en soms ook beveiligingskwetsbaarheden. Het gebruik ervan moet zorgvuldig worden gecontroleerd en gevalideerd. Over het algemeen is het doorgeven van berichten een veiligere manier om vergelijkbare doelen te bereiken.

#### Niet-compatibele code {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Compatibele code {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Gebruik geen opmaaktekenreeksen die extern kunnen worden beheerd {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Sleutel**: CQRules:CWE-134
* **Type**: Vulnerability
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

Het gebruiken van een formaatkoord van een externe bron (zoals een verzoekparameter of user-generated inhoud) kan een toepassing aan ontkenning van de dienstaanvallen blootstellen. Er zijn omstandigheden waarin een indelingstekenreeks extern kan worden beheerd, maar alleen is toegestaan vanuit vertrouwde bronnen.

#### Niet-compatibele code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-aanvragen moeten altijd socket- en verbindingstime-outs hebben {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Sleutel**: CQRules:ConnectionTimeoutMechanism
* **Type**: Bug
* **Ernst**: Kritiek
* **sinds**: Versie 2018.6.0

Wanneer het uitvoeren van HTTP- verzoeken van binnen een AEM toepassing, is het kritiek dat juiste onderbrekingen worden gevormd om onnodig draadverbruik te vermijden. Helaas hebben zowel de standaard HTTP Client van Java™, `java.net.HttpUrlConnection`, als de wijd gebruikte cliënt van de Componenten van Apache HTTP geen standaardonderbreking. Daarom moeten onderbrekingen uitdrukkelijk worden gevormd. Als beste praktijken, zouden deze onderbrekingen niet meer dan 60 seconden moeten zijn.

#### Niet-compatibele code {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Compatibele code {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### De objecten `ResourceResolver` moeten altijd worden gesloten {#resourceresolver-objects-should-always-be-closed}

* **Sleutel**: CQRules:CQBP-72
* **Type**: Code Smell
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

`ResourceResolver` Objecten die uit `ResourceResolverFactory` zijn opgehaald, gebruiken systeembronnen. Hoewel er maatregelen zijn om deze bronnen terug te winnen wanneer een `ResourceResolver` niet meer in gebruik is, is het efficiënter om geopende `ResourceResolver` -objecten expliciet te sluiten door de methode `close()` aan te roepen.

Een veelvoorkomend misverstand is dat `ResourceResolver` -objecten die zijn gemaakt met een bestaande JCR-sessie, niet expliciet moeten worden gesloten. Een andere misvatting is dat door het sluiten van deze objecten de onderliggende JCR-sessie wordt gesloten. Dat is niet het geval. Ongeacht hoe een `ResourceResolver` wordt geopend, moet deze worden gesloten wanneer deze niet meer wordt gebruikt. Omdat `ResourceResolver` de `Closeable` -interface implementeert, is het ook mogelijk om de `try-with-resources` -syntaxis te gebruiken in plaats van `close()` expliciet aan te roepen.

#### Niet-compatibele code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Compatibele code {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Gebruik geen slingerservletpaden om servlets te registreren {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Sleutel**: CQRules:CQBP-75
* **Type**: Code Smell
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

Zoals die in de [ het Schuiven documentatie ](https://sling.apache.org/documentation/the-sling-engine/servlets.html) wordt beschreven, binden servlets door wegen worden ontmoedigd. Padgebonden servers kunnen geen standaard JCR-toegangsbesturingselementen gebruiken en vereisen daarom extra beveiligingsstrengheid. In plaats van het gebruiken van weg-gebonden servlets, wordt het geadviseerd om knopen in de bewaarplaats tot stand te brengen en servlets te registreren door middeltype.

#### Niet-compatibele code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Afgehandelde uitzonderingen zouden moeten worden geregistreerd of geworpen, niet allebei {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Sleutel**: CQRules:CQBP-44-CatchAndOrLogOrThrow
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

In het algemeen, zou een uitzondering precies één keer moeten worden geregistreerd. Het registreren van uitzonderingen kan veelvoudige tijden verwarring veroorzaken omdat het onduidelijk is hoeveel keer een uitzondering voorkwam. Het meest gangbare patroon dat tot dit probleem leidt, is het registreren en het werpen van een gevangen uitzondering.

#### Niet-compatibele code {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Compatibele code {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Loginstructies die direct worden gevolgd door throw-instructies vermijden {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Sleutel**: CQRules:CQBP-44-OpeenvolgendLogAndThrow
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Een ander gemeenschappelijk patroon te vermijden is een bericht te registreren en dan onmiddellijk een uitzondering te werpen. Deze kwestie wijst over het algemeen erop dat het uitzonderingsbericht omhoog gedupliceerd in logboekdossiers eindigt.

#### Niet-compatibele code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Compatibele code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Meld u niet aan bij INFO wanneer u GET- of HEAD-verzoeken afhandelt {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Sleutel**: CQRules:CQBP-44-LogInfoInGetOrHeadRequests
* **Type**: Code Smell
* **Ernst**: Klein

In het algemeen, zou het INFO logboekniveau moeten worden gebruikt om belangrijke acties te afbakenen en, door gebrek, AEM wordt gevormd om bij het INFO niveau of boven te registreren. GET- en HEAD-methoden mogen nooit alleen-lezen zijn en vormen dus geen belangrijke acties. Het registreren op het niveau INFO in antwoord op GET of HEAD verzoeken zal waarschijnlijk tot significante logboeklawaai leiden, die het moeilijker maken om nuttige informatie in logboekdossiers te identificeren. Wanneer het behandelen van GET of HEAD- verzoeken, zou het registreren op de WARN of niveaus van de FOUT moeten zijn als iets verkeerd is gegaan. Voor diepere het oplossen van problemeninformatie, zou het registreren op het DEBUG of niveau van TRACE moeten zijn.

>[!NOTE]
>
>Dit werkschema is niet op access.log-type registreren voor elk verzoek van toepassing.

#### Niet-compatibele code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Compatibele code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Gebruik `Exception.getMessage()` niet als de eerste parameter van een logboekinstructie {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Sleutel**: CQRules:CQBP-44-ExceptionGetMessageIsFirstLogParam
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Als beste praktijken, zouden de logboekberichten contextuele informatie over moeten verstrekken waar in de toepassing een uitzondering is voorgekomen. Terwijl de context ook door stapelsporen te gebruiken kan worden bepaald, over het algemeen zal het logboekbericht gemakkelijker zijn te lezen en te begrijpen. Dientengevolge, wanneer het registreren van een uitzondering, is het een slechte praktijk om het bericht van de uitzondering als logboekbericht te gebruiken. Het uitzonderingsbericht zou moeten specificeren wat fout ging. In tegenstelling, zou het logboekbericht de lezer over moeten informeren wat de toepassing deed toen de uitzondering voorkwam. Het uitzonderingsbericht wordt nog geregistreerd. Door uw eigen bericht te specificeren, zijn de logboeken gemakkelijker te begrijpen.

#### Niet-compatibele code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Compatibele code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Aanmelden van vangstblokken moet zich op het WARN- of FOUTniveau bevinden {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Sleutel**: CQRules:CQBP-44-WrongLogLevelInCatchBlock
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Zoals de naam al aangeeft, moeten Java™-uitzonderingen altijd in uitzonderlijke omstandigheden worden gebruikt. Dientengevolge, wanneer een uitzondering wordt gevangen, is het belangrijk om ervoor te zorgen dat de logboekberichten op het aangewezen niveau worden geregistreerd: of WARN of FOUT. Dit zorgt ervoor dat die berichten correct in de logboeken verschijnen.

#### Niet-compatibele code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Compatibele code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Stapelsporen niet naar de console afdrukken {#do-not-print-stack-traces-to-the-console}

* **Sleutel**: CQRules:CQBP-44-ExceptionPrintStackTrace
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

De context is kritiek wanneer het begrip van logboekberichten. Wanneer u `Exception.printStackTrace()` gebruikt, wordt alleen de stacktracering uitgevoerd naar de standaardfoutenstream, waardoor alle context verloren gaat. Als in een toepassing met meerdere threads, zoals AEM, meerdere uitzonderingen parallel met deze methode worden afgedrukt, kunnen de stacksporen elkaar overlappen, wat tot grote verwarring leidt. De uitzonderingen zouden door het registrerenkader slechts moeten worden geregistreerd.

#### Niet-compatibele code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Compatibele code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Niet uitvoeren naar standaarduitvoer of standaardfout {#do-not-output-to-standard-output-or-standard-error}

* **Sleutel**: CQRules:CQBP-44-LogLevelConsolePrinters
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Het registreren in AEM zou altijd door het registrerenkader, SLF4J moeten worden gedaan. De uitvoer rechtstreeks naar de standaarduitvoer of standaardfoutenstromen verliest de structurele en contextuele informatie die door het registrerenkader wordt verstrekt en kan, soms, prestatieskwesties veroorzaken.

#### Niet-compatibele code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Compatibele code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Vermijd hardcodeerde `/apps` en `/libs` paden {#avoid-hardcoded-apps-and-libs-paths}

* **Sleutel**: CQRules:CQBP-71
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Paden die beginnen met `/libs` en `/apps` , moeten gewoonlijk niet worden gecodeerd. Deze paden worden doorgaans opgeslagen ten opzichte van het zoekpad voor de splitsing, dat standaard op `/libs,/apps` staat. Het gebruik van het absolute pad kan leiden tot subtiele defecten die pas later in de levenscyclus van het project verschijnen.

#### Niet-compatibele code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Compatibele code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling Planner dient niet te worden gebruikt {#sonarqube-sling-scheduler}

* **Sleutel**: CQRules:AMSCORE-554
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Gebruik Sling Scheduler niet voor taken waarvoor een gegarandeerde uitvoering is vereist. Het verkopen van Geplande Banen garandeert uitvoering en beter geschikt voor zowel gegroepeerde als niet-gegroepeerde milieu&#39;s.

Zie [ Apache het Sling Event en de documentatie van de Verwerking van de Baan ](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) om meer over te leren hoe het Verschuiven van Banen in gegroepeerde milieu&#39;s worden behandeld.

### AEM vervangen API&#39;s mogen niet worden gebruikt {#sonarqube-aem-deprecated}

* **Sleutel**: AMSCORE-553
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Het AEM API-oppervlak wordt voortdurend herzien om te bepalen voor welke API&#39;s het gebruik wordt ontmoedigd en dus als afgekeurd wordt beschouwd.

Deze API&#39;s zijn vaak verouderd met de standaard Java™- *@Deprecated* -annotatie en worden dus herkend door `squid:CallToDeprecatedMethod` .

Er zijn echter gevallen waarin een API in de context van AEM verouderd is, maar in andere contexten niet mag worden vervangen. Deze regel identificeert deze tweede klasse.

## Regels voor OakPAL-inhoud {#oakpal-rules}

In de volgende sectie worden de OakPAL-controles beschreven die door Cloud Manager worden uitgevoerd.

>[!NOTE]
>
>OakPAL is een framework dat inhoudspakketten valideert met behulp van een zelfstandige Oak-opslagplaats. Een AEM partner en winnaar van de prijs van 2019 AEM Rock Star North America ontwikkelden deze prijs.

### Klanten moeten product-API&#39;s die met @ProviderType zijn geannoteerd, niet implementeren of uitbreiden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Sleutel**: CQBP-84
* **Type**: Bug
* **Ernst**: Kritiek
* **sinds**: Versie 2018.7.0

De AEM-API bevat Java™-interfaces en -klassen die alleen door aangepaste code moeten worden gebruikt, maar niet geïmplementeerd. Alleen AEM de interface `com.day.cq.wcm.api.Page` implementeert.

Het toevoegen van nieuwe methodes aan deze interfaces beïnvloedt bestaande code niet, die de toevoeging van nieuwe methodes achterwaarts-compatibel maken. Nochtans, als de douanecode één van deze interfaces uitvoert, heeft die douanecode een achterwaarts-verenigbaarheidsrisico voor de klant geïntroduceerd.

AEM annoteert interfaces en klassen die uitsluitend zijn bedoeld voor de implementatie ervan met `org.osgi.annotation.versioning.ProviderType` of, soms, de oudere annotatie `aQute.bnd.annotation.ProviderType` . Deze regel detecteert instanties waarbij aangepaste code een dergelijke interface implementeert of een klasse uitbreidt.

#### Niet-compatibele code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Klantpakketten mogen geen knooppunten maken of bewerken onder `/libs` {#oakpal-customer-package}

* **Sleutel**: BannedPath
* **Type**: Bug
* **Ernst**: Blocker
* **sinds**: Versie 2019.6.0

Het is al lang een goede gewoonte om de `/libs` -inhoudsstructuur in de AEM-inhoudsopslagruimte als alleen-lezen te beschouwen voor klanten. Als u knooppunten en eigenschappen wijzigt onder `/libs` , ontstaat een aanzienlijk risico voor belangrijke en kleine updates. Bewerkingen aan `/libs` worden alleen via officiële Adoben uitgevoerd.

### De pakketten zouden geen dubbele configuraties OSGi moeten bevatten {#oakpal-package-osgi}

* **Sleutel**: DuplicateOsgiConfigurations
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Een gemeenschappelijk probleem dat in complexe projecten voorkomt is waar de zelfde component OSGi veelvoudige tijden wordt gevormd. Deze kwestie leidt tot een dubbelzinnigheid over welke configuratie operabel is. Deze regel is &quot;runmode-bewust&quot;in die zin dat het slechts kwesties identificeert waar de zelfde component veelvoudige tijden op de zelfde looppaswijze of de combinatie looppaswijzen wordt gevormd.

#### Niet-compatibele code {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compatibele code {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Configureren en installatiemappen mogen alleen OSGi-knooppunten bevatten {#oakpal-config-install}

* **Sleutel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Om veiligheidsredenen zijn paden die `/config/` en `/install/` bevatten, alleen leesbaar voor gebruikers met administratieve bevoegdheden in AEM en moeten deze paden alleen worden gebruikt voor OSGi-configuraties en OSGi-bundels. Als u andere typen inhoud onder paden plaatst die deze segmenten bevatten, resulteert dit in toepassingsgedrag dat per ongeluk verschilt tussen gebruikers met en zonder beheerdersrechten.

Een veelvoorkomend probleem is het gebruik van knooppunten met de naam `config` in dialoogvensters van componenten of wanneer u de configuratie van de teksteditor voor inlinebewerking opgeeft. Om dit probleem op te lossen, moet de naam van het desbetreffende knooppunt worden gewijzigd in een compatibele naam. Voor de configuratie van de RTF-editor gebruikt u de eigenschap `configPath` op het knooppunt `cq:inplaceEditing` om de nieuwe locatie op te geven.

#### Niet-compatibele code {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Compatibele code {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakketten mogen elkaar niet overlappen {#oakpal-no-overlap}

* **Sleutel**: PackageOverlaps
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Gelijkaardig aan de [ Pakketten zouden niet Dubbele regel van de Configuraties moeten bevatten OSGi ](#oakpal-package-osgi), is deze kwestie een gemeenschappelijk probleem op complexe projecten waar de zelfde knoopweg aan door veelvoudige afzonderlijke inhoudspakketten wordt geschreven. Terwijl het gebruiken van inhoudspakketgebiedsdelen kan worden gebruikt om een verenigbaar resultaat te verzekeren, is het beter om overlappingen volledig te vermijden.

### De standaardontwerpmodus mag geen klassieke UI zijn {#oakpal-default-authoring}

* **Sleutel**: ClassicUIAuthoringMode
* **Type**: De Verenigbaarheid van de Code Smell /Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

De configuratie OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` bepaalt de standaard auteurswijze binnen AEM. Omdat Klassieke UI sinds AEM 6.4 is afgekeurd, wordt een kwestie nu opgeheven wanneer de standaard auteurswijze aan Klassieke UI wordt gevormd.

### Componenten met dialoogvensters moeten beschikken over aanraakdialoogvensters {#oakpal-components-dialogs}

* **Sleutel**: ComponentWithOnlyClassicUIDialog
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

AEM Componenten met een Klassieke UI-dialoogvenster moeten ook een Touch UI-dialoogvenster hebben voor optimaal ontwerp en optimale compatibiliteit met het implementatiemodel van de Cloud Service, dat geen ondersteuning biedt voor Klassieke UI. Deze regel verifieert de volgende scenario&#39;s:

* Een component met een klassieke UI-dialoogvenster (dat wil zeggen een `dialog` onderliggende node) moet een overeenkomend Touch UI-dialoogvenster hebben (dat wil zeggen een `cq:dialog` onderliggende node).
* Een component met een klassieke UI-ontwerpdialoogvenster (dat wil zeggen een `design_dialog` -knooppunt) moet een corresponderend dialoogvenster voor het aanraakinterface-ontwerp hebben (dat wil zeggen een `cq:design_dialog` onderliggende node).
* Een component met zowel een dialoogvenster voor klassieke gebruikersinterface als een dialoogvenster voor klassieke gebruikersinterface moet zowel een corresponderend dialoogvenster voor aanraakinterface als een overeenkomstig dialoogvenster voor aanraakgebruikersinterface hebben.

De documentatie van de Hulpmiddelen van de Modernisering van het AEM verstrekt details en tooling voor hoe te om componenten van Klassieke UI in Aanraakinterface om te zetten. Zie [ de documentatie van Hulpmiddelen van de Modernisering van de AEM ](https://opensource.adobe.com/aem-modernize-tools/) voor meer details.

### De omgekeerde replicatiemiddelen zouden niet moeten worden gebruikt {#oakpal-reverse-replication}

* **Sleutel**: ReverseReplication
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Steun voor omgekeerde replicatie is niet beschikbaar in de plaatsingen van de Cloud Service, zoals die in [ wordt beschreven de Nota&#39;s van de Versie: Verwijdering van de Agenten van de Replicatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

De klanten die omgekeerde replicatie gebruiken zouden Adobe voor alternatieve oplossingen moeten contacteren.

### De middelen in volmacht-toegelaten cliëntbibliotheken zouden in een omslag genoemde middelen moeten zijn {#oakpal-resources-proxy}

* **Sleutel**: ClientlibProxyResource
* **Type**: Bug
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM clientbibliotheken kunnen statische bronnen bevatten, zoals afbeeldingen en lettertypen. Zoals die in [ wordt beschreven Gebruikend de cliënt-Kant documentatie van Bibliotheken ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), wanneer het gebruiken van pro-xied cliëntbibliotheken moeten deze statische middelen in een kindomslag genoemd `resources` worden bevat om effectief op publiceer instanties van verwijzingen te worden voorzien.

#### Niet-compatibele code {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Compatibele code {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Gebruik van workflowprocessen die niet compatibel zijn met Cloud Servicen {#oakpal-usage-cloud-service}

* **Sleutel**: CloudServiceIncompatibleWorkflowProcess
* **Type**: Code Smell
* **Ernst**: Blocker
* **sinds**: Versie 2021.2.0

Met de overstap naar Asset micro-services voor de verwerking van bedrijfsmiddelen op AEM Cloud Service zijn verschillende workflowprocessen die werden gebruikt in on-premise en AMS-versies van AEM niet ondersteund of onnodig geworden.

Het migratiehulpmiddel in de [ as a Cloud Service GitHub bewaarplaats van AEM Assets ](https://github.com/adobe/aem-cloud-migration) kan worden gebruikt om werkschemamodellen tijdens migratie aan AEM as a Cloud Service bij te werken.

### Het gebruik van statische sjablonen wordt afgeraden ten gunste van bewerkbare sjablonen {#oakpal-static-template}

* **Sleutel**: StaticTemplateUsage
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Terwijl het gebruik van statische malplaatjes in AEM Projecten historisch algemeen is geweest, worden de editable malplaatjes hoogst geadviseerd aangezien zij de meeste flexibiliteit verstrekken en extra eigenschappen steunen die niet in statische malplaatjes aanwezig zijn. Meer informatie kan in de [ Malplaatjes van de Pagina worden gevonden - editable documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

De migratie van statisch aan editable malplaatjes kan grotendeels worden geautomatiseerd gebruikend [ AEM Moderniseringshulpmiddelen ](https://opensource.adobe.com/aem-modernize-tools/).

### Het gebruik van oudere basiscomponenten wordt afgeraden {#oakpal-usage-legacy}

* **Sleutel**: LegacyFoundationComponentUsage
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

De oudere Componenten van de Stichting (namelijk componenten onder `/libs/foundation`) zijn afgekeurd voor verscheidene AEM versies ten gunste van de [ Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction). Het gebruik van de componenten van de erfenisStichting als basis voor douanecomponenten, hetzij door bedekking of overerving, wordt ontmoedigd en zou in de overeenkomstige kerncomponent moeten worden omgezet.

[ AEM Moderniseringshulpmiddelen ](https://opensource.adobe.com/aem-modernize-tools/) kunnen deze omzetting vergemakkelijken.

### Definitieknooppunten van aangepaste zoekindex moeten onderliggende knooppunten van `/oak:index` zijn {#oakpal-custom-search}

* **Sleutel**: OakIndexLocation
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service vereist dat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) directe onderliggende knooppunten van `/oak:index` zijn. Indexen op andere locaties moeten worden verplaatst om compatibel te zijn met AEM Cloud Service. Meer informatie over onderzoeksindexen kan in het [ Onderzoek van de Inhoud en het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing) worden gevonden.

### Definitieknooppunten van aangepaste zoekindex moeten een compatVersion van 2 hebben {#oakpal-custom-search-compatVersion}

* **Sleutel**: IndexCompatVersion
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service vereist dat in definities van aangepaste zoekindexen (dat wil zeggen knooppunten van het type `oak:QueryIndexDefinition` ) de eigenschap `compatVersion` is ingesteld op `2` . AEM Cloud Service ondersteunt geen andere waarde. Meer informatie over onderzoeksindexen kan in het [ Onderzoek van de Inhoud en het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing) worden gevonden.

### Afstammende knooppunten van definitieknooppunten van de aangepaste zoekindex moeten van het type zijn `nt:unstructured` {#oakpal-descendent-nodes}

* **Sleutel**: IndexDescendantNodeType
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Problemen met moeilijk op te lossen problemen kunnen optreden wanneer een definitieknoopknooppunt van een aangepaste zoekindex niet-geordende onderliggende knooppunten bevat. Om dergelijke knooppunten te voorkomen, raadt Adobe aan dat alle afstammende knooppunten van een knooppunt `oak:QueryIndexDefinition` van het type `nt:unstructured` zijn.

### definitieknooppunten van aangepaste zoekindex moeten een onderliggende node met de naam `indexRules` bevatten die onderliggende items bevat {#oakpal-custom-search-index}

* **Sleutel**: IndexRulesNode
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Een correct gedefinieerd definitieknoopknooppunt van een aangepaste zoekindex moet een onderliggend knooppunt met de naam `indexRules` bevatten en dit knooppunt moet ten minste één onderliggend knooppunt hebben. Meer informatie kan in de [ documentatie van Oak ](https://jackrabbit.apache.org/oak/docs/query/lucene.html) worden gevonden.

### Definitieknooppunten van aangepaste zoekindex moeten de naamgevingsconventies volgen {#oakpal-custom-search-definitions}

* **Sleutel**: IndexName
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service vereist dat de definities van de douaneonderzoeksindex (namelijk knopen van type `oak:QueryIndexDefinition`) na een specifiek patroon moeten worden genoemd dat op [ wordt beschreven Inhoud Onderzoek en het Indexeren ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### De de definitieknooppunten van de onderzoeksindex van de douane moeten indextype lucene gebruiken {#oakpal-index-type-lucene}

* **Sleutel**: IndexType
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service vereist dat definities van aangepaste zoekindexen (dat wil zeggen knooppunten van het type `oak:QueryIndexDefinition` ) een eigenschap `type` hebben met de waarde ingesteld op `lucene` . Indexering met oudere indextypen moet worden bijgewerkt voordat u naar AEM Cloud Service gaat. Zie het [ Onderzoek van de Inhoud en het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) voor meer informatie.

### Definitieknooppunten van aangepaste zoekindex mogen geen eigenschap met de naam `seed` bevatten {#oakpal-property-name-seed}

* **Sleutel**: IndexSeedProperty
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service staat definities van aangepaste zoekindexen (dat wil zeggen knooppunten van het type `oak:QueryIndexDefinition` ) niet toe om een eigenschap met de naam `seed` te bevatten. Indexering met deze eigenschap moet worden bijgewerkt voordat u naar AEM Cloud Service gaat. Zie het [ Onderzoek van de Inhoud en het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) voor meer informatie.

### Definitieknooppunten van aangepaste zoekindex mogen geen eigenschap met de naam `reindex` bevatten {#oakpal-reindex-property}

* **Sleutel**: IndexReindexProperty
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

AEM Cloud Service staat definities van aangepaste zoekindexen (dat wil zeggen knooppunten van het type `oak:QueryIndexDefinition` ) niet toe om een eigenschap met de naam `reindex` te bevatten. Indexering met deze eigenschap moet worden bijgewerkt voordat u naar AEM Cloud Service gaat. Zie het [ Onderzoek van de Inhoud en het Indexeren documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) voor meer informatie.

### De definitieknooppunten van de index moeten niet in het inhoudspakket worden opgesteld UI {#oakpal-ui-content-package}

* **Sleutel**: IndexNotUnderUIContent
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat toe dat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) niet worden geïmplementeerd in het pakket met UI-inhoud.

>[!WARNING]
>
>U wordt aangespoord om deze kwestie zo spoedig mogelijk te behandelen omdat het pijpleidingen kan veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/release-notes/current.md).

### Aangepaste indexdefinitie van type in volledige tekst `damAssetLucene` moet correct worden voorafgegaan door `damAssetLucene` {#oakpal-dam-asset-lucene}

* **Sleutel**: CustomFulltextIndexesOfTheDamAssetCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat toe dat aangepaste full-text indexdefinities van het type `damAssetLucene` worden voorafgegaan door andere items dan `damAssetLucene` .

>[!WARNING]
>
>U wordt aangespoord om deze kwestie zo spoedig mogelijk te behandelen omdat het pijpleidingen kan veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/release-notes/current.md).

### Indexdefinitieknooppunten mogen geen eigenschappen met dezelfde naam bevatten {#oakpal-index-property-name}

* **Sleutel**: DuplicateNameProperty
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) niet toe om eigenschappen met dezelfde naam te bevatten

>[!WARNING]
>
>U wordt aangespoord om deze kwestie zo spoedig mogelijk te behandelen omdat het pijpleidingen kan veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/release-notes/current.md).

### Het is niet toegestaan bepaalde buiten de box-indexdefinities aan te passen {#oakpal-customizing-ootb-index}

* **Sleutel**: RestrictIndexCustomization
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat ongeoorloofde wijzigingen van de volgende OOTB-indexen niet toe:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>U wordt aangespoord om deze kwestie zo spoedig mogelijk te behandelen omdat het pijpleidingen kan veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/release-notes/current.md).

### De configuratie van de tokenizers in de analysatoren moet met de naam `tokenizer` worden gemaakt. {#oakpal-tokenizer}

* **Sleutel**: AnalyzerTokenizerConfigCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service verbiedt het maken van kenizers met onjuiste namen in analysatoren. Tokenizers moeten altijd als `tokenizer` worden gedefinieerd.

### Configuratie van indexeringsdefinities mag geen spaties bevatten {#oakpal-indexing-definitions-spaces}

* **Sleutel**: PathSpacesCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.7.0

AEM Cloud Service staat het maken van indexdefinities met spaties niet toe.

## Dispatcher-optimalisatiefunctie {#dispatcher-optimization-tool-rules}

In de volgende sectie worden de door Cloud Manager uitgevoerde controles van het Dispatcher Optimization Tool (DOT) weergegeven. Volg de verbindingen voor elke controle voor zijn definitie en details GitHub.

* [ de configuratie onverwachte tokens van Dispatcher ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [ de configuratie van Dispatcher onovertroffen citaat ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [ de configuratie van Dispatcher ontbrekende steun ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [ de configuratieextra steun van Dispatcher ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [ de configuratie van Dispatcher mist verplicht Bezit ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [ Dispatcher configuratie afgekeurd bezit ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [ niet gevonden configuratie van Dispatcher ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [ Httpd configuratie omvat niet gevonden dossier ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [ de configuratie algemene van Dispatcher ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [ Dispatcher publiceert landbouwbedrijfgeheime voorgeheugen zou `serveStaleOnError` toegelaten ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled) moeten hebben

* [ Dispatcher publiceert landbouwbedrijffilters zou het gebrek moeten bevatten ontkent regels van de versie 6.x.x van AEM archetype ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [ Dispatcher publiceert landbouwbedrijfgeheime voorgeheugen `statfileslevel` bezit zou >= 2 ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2) moeten zijn

* [ Dispatcher publiceert landbouwbedrijf `gracePeriod` bezit zou >= 2 ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2) moeten zijn

* [ Elk landbouwbedrijf van Dispatcher zou een unieke naam ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name) moeten hebben

* [ Dispatcher publiceert landbouwbedrijfgeheime voorgeheugen zou zijn `ignoreUrlParams` regels moeten hebben die in een manier van de lijst van gewenste personen worden gevormd ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [ Dispatcher publiceert landbouwbedrijffilters zou de toegestane het Verdelen selecteurs op een wijze van de lijst van gewenste personen moeten specificeren ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [ Dispatcher publiceert landbouwbedrijffilters zou de toegestane het achtervoegselpatronen van het Sling op een wijze van de lijst van gewenste personen moeten specificeren ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [ gebruikt niet &quot;vereisen allen verleend&quot;richtlijn in een sectie van de Folder VirtualHost met een wortel folder-weg ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
