---
title: Het project instellen
description: Leer hoe u uw project instelt zodat u het kunt beheren en implementeren met Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 1%

---


# Projectinstelling {#setting-up-your-project}

Leer hoe u uw project instelt zodat u het kunt beheren en implementeren met Cloud Manager.

## Bestaande projecten wijzigen {#modifying-project-setup-details}

Bestaande AEM projecten moeten zich aan enkele basisregels houden om met succes met Cloud Manager te kunnen worden gebouwd en geïmplementeerd.

* Projecten moeten worden gebouwd met Apache Maven.
* Er moet een `pom.xml` -bestand aanwezig zijn in de hoofdmap van de it-opslagplaats.
   * Dit bestand `pom.xml` kan verwijzen naar zoveel submodules (die op hun beurt weer andere submodules kunnen hebben) als nodig.
   * U kunt verwijzingen naar extra bewaarplaatsen van het Artefact toevoegen Maven in uw `pom.xml` dossiers.
   * De toegang tot [ wachtwoord-beschermde artefactrepositories ](#password-protected-maven-repositories) wordt gesteund wanneer gevormd. Toegang tot door het netwerk beveiligde gegevensbestanden voor artefacten wordt echter niet ondersteund.
* Implementeerbare inhoudspakketten worden gedetecteerd door te zoeken naar ZIP-bestanden voor inhoudspakketten in een map met de naam `target` .
   * Elk aantal submodules kan inhoudspakketten produceren.
* Implementeerbare Dispatcher-artefacten worden ontdekt door te zoeken naar `zip` -bestanden in submappen van `target` named `conf` en `conf.d` .
* Als er meer dan één inhoudspakket is, wordt de volgorde van pakketimplementaties niet gegarandeerd.
* Als een specifieke orde nodig is, kunnen de gebiedsdelen van het inhoudspakket worden gebruikt om de orde te bepalen.
* De pakketten kunnen [ worden overgeslagen ](#skipping-content-packages) van plaatsing.

## Geweven profielen activeren in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In sommige beperkte gevallen, kunt u uw bouwstijlproces lichtjes moeten variëren wanneer het binnen Cloud Manager loopt in tegenstelling tot wanneer het op ontwikkelaarwerkstations loopt. Voor deze gevallen, [ Gemaakt Profielen ](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) kunnen worden gebruikt om te bepalen hoe de bouwstijl in verschillende milieu&#39;s, met inbegrip van Cloud Manager verschillend zou moeten zijn.

De activering van een Geweven Profiel binnen Cloud Manager bouwt milieu zou moeten worden gedaan door `CM_BUILD` [ milieu veranderlijke ](/help/getting-started/build-environment.md#environment-variables) omgevingsvariabele te zoeken. Omgekeerd moet een profiel dat alleen buiten de Cloud Manager-ontwikkelomgeving moet worden gebruikt, worden uitgevoerd door te zoeken naar de afwezigheid van deze variabele.

Als u bijvoorbeeld alleen een eenvoudig bericht wilt uitvoeren wanneer de build in Cloud Manager wordt uitgevoerd, doet u het volgende:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Om dit profiel op een ontwikkelaarwerkstation te testen, kunt u of het op de bevellijn (met `-PcmBuild`) of in uw Geïntegreerde Ontwikkelomgeving (winde) toelaten.

En als u een eenvoudig bericht wilde uitvoeren slechts wanneer de bouwstijl buiten Cloud Manager in werking wordt gesteld, zou u dit doen:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Ondersteuning voor met wachtwoord beveiligde gegevensopslagruimte {#password-protected-maven-repositories}

Artefacten van een met een wachtwoord beveiligde Maven-opslagplaats mogen alleen zeer voorzichtig worden gebruikt, aangezien code die via dit mechanisme wordt geïmplementeerd, niet door alle kwaliteitsregels wordt uitgevoerd die in Cloud Manager worden geïmplementeerd. Het wordt geadviseerd om de bronnen van Java evenals de volledige code van de projectbron samen met het binaire getal op te stellen.

>[!TIP]
>
>Artefacten van met een wachtwoord beveiligde Maven-repositories mogen alleen in zeldzame gevallen worden gebruikt en voor code die niet aan AEM is gekoppeld.

Om een wachtwoord-beschermde Gegeven bewaarplaats van Cloud Manager te gebruiken, specificeer het wachtwoord (en naar keuze, de gebruikersbenaming) als geheime [ Variabele van de Pijpleiding ](/help/getting-started/build-environment.md#pipeline-variables) en verwijs dan dat geheim binnen een dossier genoemd `.cloudmanager/maven/settings.xml` in de git bewaarplaats. Dit dossier volgt het ](https://maven.apache.org/settings.html) schema van het Dossier van Montages 0} Maven.[

Wanneer het Cloud Manager-constructieproces start, wordt het `<servers>` -element in dit bestand samengevoegd met het `settings.xml` -standaardbestand dat door Cloud Manager wordt geleverd. Server-id&#39;s die beginnen met `adobe` en `cloud-manager` worden beschouwd als gereserveerd en mogen niet worden gebruikt door aangepaste servers. Server-id&#39;s die niet overeenkomen met een van deze voorvoegsels of de standaard-id `central` worden nooit weerspiegeld door Cloud Manager.

Als dit bestand is geïnstalleerd, wordt vanuit een element `<repository>` en/of `<pluginRepository>` in het bestand `pom.xml` naar de server-id verwezen. Over het algemeen, zouden deze `<repository>` en/of `<pluginRepository>` elementen binnen a [ Cloud Manager-specifiek profiel ](#activating-maven-profiles-in-cloud-manager) bevat zijn, hoewel dat niet strikt noodzakelijk is.

Stel bijvoorbeeld dat de repository zich op `https://repository.myco.com/maven2` bevindt, dat de gebruikersnaam die Cloud Manager moet gebruiken `cloudmanager` is en dat het wachtwoord `secretword` is.

Plaats eerst het wachtwoord als geheim op de pijpleiding:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

Verwijs vervolgens vanuit het `.cloudmanager/maven/settings.xml` -bestand naar dit bestand:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

En ten slotte verwijs naar de server-id in het `pom.xml` -bestand:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Bronnen implementeren {#deploying-sources}

Het is een goede praktijk om de bronnen van Java samen met binair aan een Geweven bewaarplaats op te stellen.

Configureer de `maven-source-plugin` in uw project:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Projectbronnen implementeren {#deploying-project-sources}

Het is een goede praktijk om de volledige projectbron samen met binair aan een Geweven bewaarplaats op te stellen. Hierdoor kan het exacte artefact worden hersteld.

Configureer de `maven-assembly-plugin` in uw project:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Inhoudspakketten worden overgeslagen {#skipping-content-packages}

In Cloud Manager kunnen builds een willekeurig aantal inhoudspakketten produceren. Om diverse redenen kan het wenselijk zijn een inhoudspakket te maken, maar het niet te implementeren. Dit kan bijvoorbeeld handig zijn wanneer u inhoudspakketten maakt die alleen voor testen worden gebruikt of die door een andere stap in het constructieproces opnieuw worden verpakt, dat wil zeggen als een subpakket van een ander pakket.

Cloud Manager zoekt naar een eigenschap met de naam `cloudManagerTarget` in de eigenschappen van samengestelde inhoudspakketten om deze scenario&#39;s te kunnen gebruiken. Als deze eigenschap is ingesteld op `none` , wordt het pakket overgeslagen en niet geïmplementeerd. Het mechanisme om deze eigenschap in te stellen hangt af van de manier waarop de build het contentpakket produceert. Met de `filevault-maven-plugin` configureert u bijvoorbeeld de insteekmodule als volgt:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Met de lus `content-package-maven-plugin` is deze vergelijkbaar:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Artefacthergebruik maken {#build-artifact-reuse}

In veel gevallen, wordt de zelfde code opgesteld aan veelvoudige AEM milieu&#39;s. Waar mogelijk, zal Cloud Manager vermijden herbouwend de codebasis wanneer het ontdekt dat het zelfde gat begaan wordt gebruikt in veelvoudige full-stack pijpleidinguitvoeringen.

Wanneer een uitvoering is begonnen, begaat de huidige HEAD voor de takpijpleiding wordt gehaald. De commit hash is zichtbaar in UI en via API. Wanneer de bouwstijlstap met succes voltooit, worden de resulterende artefacten opgeslagen gebaseerd op die knoeiboel begaan en kunnen in verdere pijpleidingsuitvoeringen opnieuw worden gebruikt.

Pakketten worden opnieuw gebruikt via pijpleidingen als ze zich in hetzelfde programma bevinden. Wanneer u pakketten zoekt die opnieuw kunnen worden gebruikt, negeert AEM vertakkingen en hergebruikt artefacten tussen vertakkingen.

Wanneer een hergebruik voorkomt, worden de bouw en de stappen van de codekwaliteit effectief vervangen met de resultaten van de originele uitvoering. Het logboekdossier voor de bouwstijlstap zal van de artefacten en de uitvoeringsinformatie een lijst maken die werd gebruikt om hen oorspronkelijk te bouwen.

Hieronder ziet u een voorbeeld van een dergelijke loguitvoer.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Het logboek van de stap van de codekwaliteit zal gelijkaardige informatie bevatten.

### Voorbeelden {#example-reuse}

#### Voorbeeld 1 {#example-1}

Houd er rekening mee dat uw programma twee ontwikkelingspijplijnen heeft:

* Pijpleiding 1 op vertakking `foo`
* Pijpleiding 2 op vertakking `bar`

Beide vertakkingen zijn op zelfde verbind identiteitskaart

1. De lopende pijpleiding 1 zal eerst de pakketten normaal bouwen.
1. Dan die pijpleiding 2 loopt zal pakketten hergebruiken die door pijpleiding 1 worden gecreeerd.

#### Voorbeeld 2 {#example-2}

Houd er rekening mee dat uw programma twee vertakkingen heeft:

* Branch `foo`
* Branch `bar`

Beide vertakkingen hebben zelfde verbind identiteitskaart

1. Een ontwikkelingspijplijn bouwt en voert `foo` uit.
1. Vervolgens wordt een productiepijplijn gebouwd en uitgevoerd `bar` .

In dit geval wordt het artefact van `foo` opnieuw gebruikt voor de productiepijplijn aangezien dezelfde commit hash werd geïdentificeerd.

### Afmelden {#opting-out}

Indien gewenst, kan het hergebruikgedrag voor specifieke pijpleidingen worden onbruikbaar gemaakt door de pijpleidingsvariabele `CM_DISABLE_BUILD_REUSE` aan `true` te plaatsen. Als deze variabele wordt geplaatst, begaan hash nog wordt gehaald en de resulterende artefacten voor later gebruik zullen worden opgeslagen, maar om het even welke eerder opgeslagen artefacten zullen niet opnieuw worden gebruikt. Overweeg het volgende scenario om dit gedrag te begrijpen.

1. Er wordt een nieuwe pijpleiding gemaakt.
1. De pijpleiding wordt uitgevoerd (uitvoering #1) en de huidige HEAD begaan is `becdddb`. De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De variabele `CM_DISABLE_BUILD_REUSE` wordt ingesteld.
1. De pijpleiding wordt opnieuw uitgevoerd zonder code te veranderen. Hoewel er opgeslagen artefacten aan `becdddb` worden geassocieerd, worden zij niet opnieuw gebruikt toe te schrijven aan de `CM_DISABLE_BUILD_REUSE` variabele.
1. De code wordt veranderd en de pijpleiding wordt uitgevoerd. De HEAD commit is nu `f6ac5e6` . De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De variabele `CM_DISABLE_BUILD_REUSE` wordt verwijderd.
1. De pijpleiding wordt re-uitgevoerd zonder de code te veranderen. Aangezien er opgeslagen artefacten verbonden aan `f6ac5e6` zijn, worden die artefacten opnieuw gebruikt.

### Caveats {#caveats}

* Artefacten van de bouwstijl worden niet opnieuw gebruikt over verschillende programma&#39;s, ongeacht als de commit knoeiboel identiek is.
* De kunstmatigheden van de bouwstijl worden opnieuw gebruikt binnen het zelfde programma zelfs als de tak en/of de pijpleiding verschillend is.
* [ Gemaakt versie behandelend ](/help/managing-code/maven-project-version.md) vervangt de projectversie slechts in productiepijpleidingen. Daarom als het zelfde begaat op zowel ontwikkelt uitvoering als een uitvoering van de productiepijplijn en de ontwikkelings opstellen pijpleiding eerst wordt uitgevoerd, zullen de versies aan stadium en productie zonder worden veranderd worden opgesteld. In dit geval wordt echter nog steeds een tag gemaakt.
* Als de terugwinning van de opgeslagen artefacten niet succesvol is, zal de bouwstijlstap worden uitgevoerd alsof geen artefacten waren opgeslagen.
* Andere pijplijnvariabelen dan `CM_DISABLE_BUILD_REUSE` worden niet in aanmerking genomen wanneer Cloud Manager besluit eerder gemaakte constructieartefacten opnieuw te gebruiken.

## Ontwikkel uw Code die op Beste praktijken wordt gebaseerd {#develop-your-code-based-on-best-practices}

De Techniek van de Adobe en de Consulting teams hebben a [ uitvoerige reeks beste praktijken voor AEM ontwikkelaars ontwikkeld.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)
