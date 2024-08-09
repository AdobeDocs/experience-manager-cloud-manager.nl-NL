---
title: Veelgestelde vragen over Cloud Manager
description: In dit document worden antwoorden gegeven op de meest gestelde vragen over Cloud Manager voor AMS-klanten.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

In dit document worden antwoorden gegeven op de meest gestelde vragen over Cloud Manager voor AMS-klanten.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11}

Ja. U moet de `maven-toolchains-plugin` met de juiste instellingen voor Java 11 toevoegen.

* Dit proces wordt gedocumenteerd [ hier ](/help/getting-started/using-the-wizard.md).
* Voor een voorbeeld, zie de [ code van het steekproefproject van de wint ](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mijn build mislukt met een fout over maven-scr-plugin na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#maven-src-plugin}

Het is mogelijk dat uw AEM Cloud Manager-build mislukt wanneer u probeert de build over te schakelen van Java 8 naar 11. Als de volgende fout optreedt, moet u `maven-scr-plugin` verwijderen en alle OSGi-annotaties omzetten in OSGi R6-annotaties.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Voor instructies op hoe te om deze stop te verwijderen, [ zie hier ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mijn build mislukt met een fout met betrekking tot RequireJavaVersion na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#requirejavaversion}

Voor Cloud Manager builds zal `maven-enforcer-plugin` mogelijk mislukken met deze fout

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Dit is een bekend probleem dat te wijten is aan het gebruik van een andere versie van Java voor het uitvoeren van de gemaven opdracht in plaats van het compileren van code. Laat `requireJavaVersion` gewoon weg van uw `maven-enforcer-plugin` configuraties.

## De kwaliteitscontrole van de code is mislukt en onze implementatie is vastgelopen. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Ja. Alle mislukkingen van de codekwaliteit behalve veiligheidsclassificaties zijn niet-kritieke metriek, zodat kunnen zij als deel van een plaatsingspijpleiding worden overgeslagen door de punten in resultatenUI uit te breiden.

Een gebruiker met [ Manager van de Plaatsing, de Manager van het Project, of de rol van de BedrijfsEigenaar ](/help/requirements/users-and-roles.md#role-definitions) kan de kwesties met voeten treden, in welk geval de pijpleiding te werk gaat of zij de kwesties kunnen goedkeuren, waarin de pijpleiding met een mislukking stopt.

Zie de documenten [ Drievoudige Gates terwijl het runnen van een Pijpleiding ](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) en [ Vormend niet-Productie Pijpleidingen ](/help/using/non-production-pipelines.md#understanding-the-flow) voor meer details.

## Cloud Manager-implementaties mislukken bij de teststap voor prestaties in Adobe Managed Services-omgevingen. Hoe zuiveren wij dit om de kritieke metriek over te gaan? {#debug-critical-metrics}

Er is geen enkel antwoord op deze vraag. Maar dit zijn enkele belangrijke punten met betrekking tot de teststap voor de prestaties die u in gedachten moet houden:

* Deze stap is een stap in de webprestaties, d.w.z. de tijd om de pagina met een webbrowser te laden.
* De URL&#39;s die in het CSV-bestand met resultaten worden vermeld, worden tijdens de test in een Chrome-browser in de Cloud Manager-infrastructuur geladen.
* Een gemeenschappelijke metrisch die ontbreekt is het foutentarief.
   * Een URL kan alleen worden doorgegeven als de hoofd-URL is geladen met de status `200` en binnen `20` seconden.
   * Paginaladen die langer zijn dan `20` seconden, worden gemarkeerd als `504` fouten.
* Als uw plaats gebruikersauthentificatie vereist, zie het document [ Uw Resultaten van de Test ](/help/using/code-quality-testing.md#authenticated-performance-testing) begrijpen voor het vormen van de test om aan uw plaats voor authentiek te verklaren.

Zie [ Begrijpend de Resultaten van de Test ](/help/using/code-quality-testing.md) voor meer informatie over kwaliteitscontroles.

## Kan ik SNAPSHOT voor de versie van het Maven project gebruiken? {#snapshot}

Ja. Voor ontwikkelaarsimplementaties moeten de `pom.xml` bestanden van de grijsvertakking `-SNAPSHOT` aan het einde van de `<version>` -waarde bevatten.

Dit laat verdere plaatsing toe om nog worden geïnstalleerd wanneer de versie niet veranderde. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

U kunt de versie ook instellen op `-SNAPSHOT` voor stadium- en productiebuilds of -implementaties. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in de it. Indien nodig kunt u later naar dit label verwijzen.

De verdere details over versie behandeling worden [ hier gedocumenteerd ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html).

## Hoe werkt het pakket en de bundelversioning voor het opvoeren en productieplaatsingen? {#staging-production}

In het opvoeren en productieplaatsingen, wordt een automatische versie geproduceerd [ zoals hier gedocumenteerd ](/help/managing-code/maven-project-version.md).

Stel voor aangepaste versies in werkgebied- en productieimplementaties een geschikte versie met drie delen in, zoals `1.0.0` . Verhoog de versie telkens wanneer u aan productie opstelt.

Cloud Manager voegt automatisch zijn versie aan stadium toe en de productie bouwt en leidt tot een git tak. Er is geen speciale configuratie vereist. Als u een bepaalde versie niet zoals eerder beschreven plaatst, zal de plaatsing nog slagen en een versie zal automatisch worden geplaatst.

## Mijn gefabriceerde build mislukt voor Cloud Manager-implementaties, maar het wordt lokaal zonder fouten gemaakt. Wat is er mis? {#maven-build-fail}

Zie dit [ git middel ](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer details.

## Ik kan geen variabele plaatsen gebruikend een bevel van de lucht. Wat kan ik doen? {#set-variable}

U kunt een fout van 403 zoals het volgende ontvangen wanneer het proberen om pijpleidingsvariabelen via `aio` bevelen te vermelden of te plaatsen.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In dit geval, moet de gebruiker die deze bevelen uitvoert aan de **rol van de Manager van de Plaatsing** in de Admin Console worden toegevoegd.

Zie [ API Toestemmingen ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) voor meer details.
