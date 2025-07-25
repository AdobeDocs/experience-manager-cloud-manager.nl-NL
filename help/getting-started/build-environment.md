---
title: De Build-omgeving
description: Leer over de gespecialiseerde bouwstijlomgeving die de gebruikers van Cloud Manager om uw code te bouwen en te testen.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: e9f3ac70735a95a15b1f63cf40496672162de777
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---


# De ontwikkelomgeving {#build-environment}

Leer over de gespecialiseerde bouwstijlomgeving die de gebruikers van Cloud Manager om uw code te bouwen en te testen.

## Omgevingsdetails {#details}

Cloud Manager-ontwikkelomgevingen hebben de volgende kenmerken.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 22.04.
* Apache Maven 3.9.4 is geïnstalleerd.
   * Adobe adviseert gebruikers [ hun Geweven bewaarplaatsen bij te werken om HTTPS in plaats van HTTP ](#https-maven) te gebruiken.
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
* Maven wordt uitgevoerd met deze drie opdrachten:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wordt geconfigureerd op systeemniveau met een `settings.xml` -bestand. Dit bestand bevat automatisch de openbare Adobe-gegevensopslagruimte met een profiel met de naam `adobe-public` . Zie [ Adobe openbare Gemaakt bewaarplaats ](https://repo1.maven.org/) voor meer details.
* Node.js 18 is beschikbaar voor [ front eindpijpleidingen ](/help/overview/ci-cd-pipelines.md).

>[!IMPORTANT]
>De ondersteuning voor Maven-toolketens is verwijderd vanaf Cloud Manager 2025.06.0. JDK-selectie wordt nu alleen ondersteund via `.cloudmanager/java-version` . Voor meer informatie, zie [ Gebruikend een specifieke versie van Java ](#using-java-version).

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

Voor een vlotte ervaring met de bijgewerkte versie raadt Adobe gebruikers aan hun Geweven opslagplaatsen bij te werken om HTTPS in plaats van HTTP te gebruiken. Deze aanpassing sluit aan op de groeiende verschuiving van de industrie naar veilige communicatieprotocollen en helpt een veilig en betrouwbaar bouwproces in stand te houden.

## Een specifieke Java-versie gebruiken {#using-java-version}

Standaard wordt voor projecten die door de Cloud Manager worden gemaakt, gebruikgemaakt van de Oracle 8 JDK. Klanten die een alternatieve JDK willen gebruiken, kunnen een alternatieve JDK-versie selecteren voor het volledige uitgevoerde Maven-proces.

>[!IMPORTANT]
>
>Maven Toolketins worden niet meer ondersteund in Cloud Manager 2025.06.0. Houd er rekening mee dat pijpleidingen met een configuratie met een maven-toolketins-plug-in niet werken met `Cannot find matching toolchain definitions.` Gebruik het bestand `.cloudmanager/java-version` om JDK 11, 17 of 21 te selecteren.
>
>**begeleiding van de Migratie:**
>
>1. Verwijder toolketens door om het even welke `org.apache.maven.plugins:maven-toolchains-plugin` ingang en om het even welke `toolchains.xml` te schrappen geëngageerd aan uw broncontrole.
>1. Kies een JDK met `.cloudmanager/java-version` (21, 17, of 11) zoals die in [ wordt beschreven Afwisselend Gemaakt uitvoeringJDK versie ](#alternate-maven).
>1. Adobe raadt aan de Cloud Manager-constructiecache te wissen of een nieuwe pijpleidingrun te starten.
>

<!--DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

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

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details. -->

### Alternatieve JDK-versie voor uitvoering {#alternate-maven}

Het is mogelijk om Oracle 8 of Oracle 11 te selecteren als JDK voor de volledige uitgevoerde Maven. Deze benadering verandert JDK die voor alle stop-ins wordt gebruikt. Dientengevolge, controlerend en uitvoerend de versie van Java gebruikend de [ Apache Maven Plug-in van de Enforcer ](https://maven.apache.org/enforcer/maven-enforcer-plugin/) werken.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de vertakking Git-opslagruimte die door de pijplijn wordt gebruikt. Dit bestand kan de inhoud `11` of `8` hebben. Eventuele andere waarden worden genegeerd. Als `11` is opgegeven, gebruikt het systeem Oracle 11 en stelt de `JAVA_HOME` omgevingsvariabele in op `/usr/lib/jvm/jdk-11.0.22` . Als `8` is opgegeven, gebruikt het systeem Oracle 8 en stelt de `JAVA_HOME` omgevingsvariabele in op `/usr/lib/jvm/jdk1.8.0_401` .

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
>Als u een systeempakket op deze manier installeert, wordt dit niet geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Neem contact op met uw Adobe-vertegenwoordiger als u een systeempakket op de AEM-omgeving wilt installeren.
