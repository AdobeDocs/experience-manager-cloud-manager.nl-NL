---
title: De Build-omgeving
description: Leer over de gespecialiseerde bouwstijlomgeving die de gebruikers van Cloud Manager om uw code te bouwen en te testen.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---


# De ontwikkelomgeving {#build-environment}

Leer over de gespecialiseerde bouwstijlomgeving die de gebruikers van Cloud Manager om uw code te bouwen en te testen.

## Omgevingsdetails {#details}

Cloud Manager-ontwikkelomgevingen hebben de volgende kenmerken.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 22.04.
* Apache Maven 3.9.4 is geïnstalleerd.
   * De Adobe adviseert gebruikers [ hun Geweven bewaarplaatsen bij te werken om HTTPS in plaats van HTTP ](#https-maven) te gebruiken.
* De geïnstalleerde Java-versies zijn Oracle JDK 8u401 en Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Standaard wordt de omgevingsvariabele `JAVA_HOME` ingesteld op `/usr/lib/jvm/jdk1.8.0_401` , die Oracle JDK 8u401 bevat. Zie de sectie [ Afwisselend Gemaakte Versie van JDK van de Uitvoering ](#alternate-maven) voor meer details.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere pakketten kunnen bij bouwstijltijd zoals die in de sectie [ wordt beschreven worden geïnstalleerd die de Extra Pakketten van het Systeem ](#installing-additional-system-packages) installeert.
* Elke build wordt uitgevoerd in een ongerepte omgeving. De bouwstijlcontainer houdt geen staat tussen uitvoeringen.
* Maven wordt altijd uitgevoerd met deze drie opdrachten:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wordt op systeemniveau geconfigureerd met een `settings.xml` -bestand dat automatisch de openbare gegevensopslagruimte voor Adoben bevat met een profiel met de naam `adobe-public` . Zie de [ openbaar Maven bewaarplaats van de Adobe ](https://repo1.maven.org/) voor meer details.
* Node.js 18 is beschikbaar voor [ front eindpijpleidingen ](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Hoewel Cloud Manager geen specifieke versie van de `jacoco-maven-plugin` definieert, moet de gebruikte versie ten minste `0.7.5.201505241946` zijn.

>[!TIP]
>
>Zie de volgende aanvullende bronnen voor informatie over het gebruik van Cloud Manager API&#39;s:
>
>* [ air-cli-stop-cloudmanager ](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [ Creërend een API Integratie ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [ API Toestemmingen ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Door HTTPS aangebrachte opslagruimten {#https-maven}

Cloud Manager [ 2023.10.0 ](/help/release-notes/2023/2023-10-0.md) begon een het rollen update aan het bouwstijlmilieu (die met versie 2023.12.0) voltooide, die een update aan Geweven 3.8.8 omvatte. Een belangrijke wijziging die werd aangebracht in Maven 3.8.1 was een verbetering van de beveiliging die bedoeld was om potentiële kwetsbaarheden te beperken. Specifiek, maven maakt nu alle onveilige `http://*` spiegels door gebrek onbruikbaar, zoals die in de [ Gemaakt versienota&#39;s ](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) worden geschetst.

Als gevolg van deze beveiligingsuitbreiding kunnen sommige gebruikers problemen ondervinden tijdens de constructiestap, met name wanneer ze artefacten downloaden van Geweven opslagplaatsen die onveilige HTTP-verbindingen gebruiken.

Om ervoor te zorgen dat de bijgewerkte versie probleemloos wordt uitgevoerd, raadt Adobe gebruikers aan hun Geweven opslagplaatsen bij te werken om HTTPS in plaats van HTTP te gebruiken. Deze aanpassing sluit aan op de groeiende verschuiving van de industrie naar veilige communicatieprotocollen en helpt een veilig en betrouwbaar bouwproces in stand te houden.

## Een specifieke Java-versie gebruiken {#using-java-version}

Door gebrek, maken de projecten die door Cloud Manager worden gebouwd Oracle 8 JDK. Klanten die een alternatieve JDK willen gebruiken, hebben twee opties.

* [ Gemaakt Toolketens ](#maven-toolchains)
* [Een alternatieve JDK-versie selecteren voor het volledige uitgevoerde Maven-proces](#alternate-maven)

### Maven Toolketins {#maven-toolchains}

De [ Gemaakt stop-in Toolketens ](https://maven.apache.org/plugins/maven-toolchains-plugin/) laat projecten een specifieke JDK (of toolchain) selecteren om in de context van toolketens-bewuste Gewenste stop-ins te gebruiken. Dit proces wordt uitgevoerd in het `pom.xml` dossier van het project door een verkoper en versiewaarde te specificeren. Een voorbeeldsectie in het bestand `pom.xml` is als volgt:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

Dit proces veroorzaakt alle toolketins-bewuste Geweven stop-ins om het Oracle JDK, versie 11 te gebruiken.

Wanneer u deze methode gebruikt, wordt Maven zelf nog steeds uitgevoerd met de standaard-JDK (Oracle 8) en wordt de omgevingsvariabele `JAVA_HOME` niet gewijzigd. Daarom het controleren van of het handhaven van de versie van Java door stop-ins zoals [ Apache Maven Plug-in van de Enforcer ](https://maven.apache.org/enforcer/maven-enforcer-plugin/) werkt niet en dergelijke stop-ins moet niet worden gebruikt.

De momenteel beschikbare combinaties leverancier/versie zijn:

| Leverancier | Versie |
|---|---|
| Oracle | 1,8 |
| Oracle | 1,11 |
| Oracle | 11 |
| Zon | 1,8 |
| Zon | 1,11 |
| Zon | 11 |

>[!NOTE]
>
>Vanaf april 2022 zal Oracle JDK de standaard JDK zijn voor de ontwikkeling en werking van AEM toepassingen. Cloud Manager bouwt proces automatisch aan het gebruiken van Oracle JDK over, zelfs als een alternatieve optie uitdrukkelijk in Maven toolchain wordt geselecteerd. Zie de [ versienota&#39;s van april ](/help/release-notes/2022/2022-4-0.md) voor meer details.

### Alternatieve JDK-versie voor uitvoering {#alternate-maven}

Het is ook mogelijk om Oracle 8 of Oracle 11 als JDK voor de volledige Geweven uitvoering te selecteren. In tegenstelling tot de opties van toolketins, verandert dit JDK die voor alle stop-ins wordt gebruikt tenzij de toolketenconfiguratie ook wordt geplaatst, in welk geval de toolketenconfiguratie nog wordt toegepast voor toolketens-bewuste Geweven stop-ins. Dientengevolge, controlerend en uitvoerend de versie van Java gebruikend de [ Apache Maven Plug-in van de Enforcer ](https://maven.apache.org/enforcer/maven-enforcer-plugin/) werken.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de vertakking Git-opslagruimte die door de pijplijn wordt gebruikt. Dit bestand kan de inhoud `11` of `8` hebben. Eventuele andere waarden worden genegeerd. Wanneer `11` wordt opgegeven, wordt Oracle 11 gebruikt en wordt de omgevingsvariabele `JAVA_HOME` ingesteld op `/usr/lib/jvm/jdk-11.0.22` . Wanneer `8` wordt opgegeven, wordt Oracle 8 gebruikt en wordt de `JAVA_HOME` omgevingsvariabele ingesteld op `/usr/lib/jvm/jdk1.8.0_401` .

## Omgevingsvariabelen {#environment-variables}

### Standaardomgevingsvariabelen {#standard-environ-variables}

In sommige gevallen, kunt u het noodzakelijk vinden om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als u bijvoorbeeld een gereedschap zoals gulp voor JavaScript-minificatie gebruikt, kunt u de voorkeur geven aan verschillende miniatuurniveaus voor ontwikkelings- en productieomgevingen.

Om dit te steunen, voegt Cloud Manager standaardmilieuvariabelen aan de bouwstijlcontainer voor elke uitvoering toe.

| Naam variabele | Beschrijving |
|---|---|
| `CM_BUILD` | Altijd ingesteld op `true` |
| `BRANCH` | De gevormde tak voor de uitvoering |
| `CM_PIPELINE_ID` | De numerieke identificatie van de pijplijn |
| `CM_PIPELINE_NAME` | De pijpleidingsnaam |
| `CM_PROGRAM_ID` | De numerieke programma-id |
| `CM_PROGRAM_NAME` | De programmenaam |
| `ARTIFACTS_VERSION` | Voor een afbouw- of productiepijplijn, de synthetische versie die door Cloud Manager wordt gegenereerd |

### Beschikbaarheid van standaardomgevingsvariabele {#availability}

Standaardomgevingsvariabelen kunnen op een aantal plaatsen worden gebruikt.

#### Auteur-, voorproef- en publicatieomgevingen {#author-preview-publish}

Zowel normale omgevingsvariabelen als geheimen kunnen worden gebruikt in de ontwerpomgeving, voorvertoningsomgeving en in de publicatieomgeving.

#### Dispatcher {#dispatcher}

Slechts kunnen de regelmatige milieuvariabelen met [ Dispatcher ](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/dispatcher) worden gebruikt. Geheimen kunnen niet worden gebruikt.

Omgevingsvariabelen kunnen echter niet worden gebruikt in `IfDefine` -instructies.

>[!TIP]
>
>Valideer uw gebruik van milieuvariabelen met [ Dispatcher plaatselijk ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) alvorens op te stellen.

#### OSGi-configuraties {#osgi}

Zowel kunnen de regelmatige milieuvariabelen als de geheimen in [ configuraties OSGi ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi) worden gebruikt.

### Pipetvariabelen {#pipeline-variables}

In sommige gevallen, kan uw bouwstijlproces van specifieke configuratievariabelen afhangen die om in de bewaarplaats van het Git ongepast zouden zijn te plaatsen of tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak.

Cloud Manager staat voor deze variabelen toe om door Cloud Manager API of Cloud Manager CLI op een per-pijpleidingsbasis worden gevormd. Variabelen kunnen worden opgeslagen als normale tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele, waarnaar vervolgens kan worden verwezen vanuit het `pom.xml` -bestand of andere constructiescripts.

Om een variabele te plaatsen die CLI gebruiken, stel een bevel in werking gelijkend op het volgende.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Huidige variabelen kunnen worden vermeld gebruikend een bevel gelijkend op het volgende.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variabelen moeten aan bepaalde beperkingen voldoen.

* Namen van variabelen mogen alleen alfanumerieke tekens en het onderstrepingsteken (`_`) bevatten.
   * Volgens de conventie moeten de namen allemaal in hoofdletters staan.
* Er is een grens van 200 variabelen per pijpleiding.
* Elke naam moet minder dan 100 tekens bevatten.
* Elke tekenreekswaarde moet uit minder dan 2048 tekens bestaan.
* Elke `secretString` -waarde moet uit minder dan 500 tekens bestaan.

Bij gebruik in een Maven `pom.xml` -bestand is het doorgaans handig om deze variabelen toe te wijzen aan Maven-eigenschappen met een syntaxis die lijkt op de volgende.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Extra systeempakketten installeren {#installing-additional-system-packages}

Om volledig te functioneren, vereisen sommige bouwstijlen extra systeempakketten worden geïnstalleerd. Een build kan bijvoorbeeld een Python- of Ruby-script aanroepen en moet daarom een geschikte taalinterpreter hebben geïnstalleerd. Dit scenario kan worden gedaan door [`exec-maven-plugin` ](https://www.mojohaus.org/exec-maven-plugin/) te roepen APT aan te halen. Deze uitvoering moet doorgaans worden opgenomen in een Cloud Manager-specifiek Maven-profiel. Als u bijvoorbeeld Python wilt installeren, kunt u het volgende doen:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Deze techniek kan ook worden gebruikt om taalspecifieke pakketten te installeren. Dat wil zeggen: gebruik `gem` voor RubyGems of `pip` voor Python Packages.

>[!NOTE]
>
>Als u een systeempakket op deze manier installeert, wordt dit niet geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.
