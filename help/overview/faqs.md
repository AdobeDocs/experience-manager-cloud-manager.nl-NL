---
title: Veelgestelde vragen over Cloud Manager
description: Leer meer over antwoorden op de vaakst gestelde vragen over Cloud Manager voor AMS-klanten.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---


# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

In dit document worden antwoorden gegeven op de meest gestelde vragen over Cloud Manager voor AMS-klanten.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11}

Ja. U moet `maven-toolchains-plugin` met de correcte montages voor Java 11 toevoegen.

* Dit proces wordt gedocumenteerd [ hier ](/help/getting-started/using-the-wizard.md).
* Voor een voorbeeld, zie de [ WKND code van het steekproefproject ](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mijn build mislukt met een fout over maven-scr-plugin na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#maven-src-plugin}

Het is mogelijk dat uw AEM Cloud Manager-build mislukt wanneer u probeert de build over te schakelen van Java 8 naar 11. Als de volgende fout optreedt, moet u `maven-scr-plugin` verwijderen en alle OSGi-annotaties omzetten in OSGi R6-annotaties.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Voor instructies op hoe te om deze stop-binnen te verwijderen, [ zie hier ](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mijn build mislukt met een fout met betrekking tot RequireJavaVersion na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#requirejavaversion}

Voor Cloud Manager builds zal `maven-enforcer-plugin` mogelijk mislukken met deze fout

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Dit bekende probleem is te wijten aan het feit dat Cloud Manager een andere versie van Java gebruikt om de Maven-opdracht uit te voeren in plaats van code te compileren. Laat `requireJavaVersion` weg van uw `maven-enforcer-plugin` configuraties.

## De kwaliteitscontrole van de code is mislukt en de implementatie is nu vastgelopen. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Ja. Alle fouten in de codekwaliteit, behalve beveiligingsbeoordelingen, zijn niet-kritieke metingen. Als dusdanig, kunnen zij als deel van een plaatsingspijpleiding worden overgeslagen door de punten in resultatenUI uit te breiden.

Een gebruiker met de [ Manager van de Plaatsing, de Manager van het Project, of de rol Bedrijfs van de Eigenaar ](/help/requirements/users-and-roles.md#role-definitions) kan de kwesties met voeten treden. In dat geval gaat de pijpleiding door. Of, kunnen zij de kwesties goedkeuren, waarbij de pijpleiding met een mislukking stopt.

Zie de documenten [ Drievoudige Gates terwijl het runnen van een Pijpleiding ](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) en [ Vormend niet-Productie Pijpleidingen ](/help/using/non-production-pipelines.md#understanding-the-flow) voor meer details.

## Cloud Manager-implementaties mislukken bij de teststap voor prestaties in Adobe Managed Services-omgevingen. Hoe kan deze kwestie worden gezuiverd om de kritieke metriek over te gaan? {#debug-critical-metrics}

Er is geen enkel antwoord op deze vraag. De volgende punten over de stap voor het testen van de prestaties kunnen echter nuttig zijn:

* Deze stap is een stap in de webprestaties. Het is dus bijna tijd om de pagina te laden met een webbrowser.
* De URL&#39;s die in het CSV-bestand met resultaten worden vermeld, worden tijdens de test in een Chrome-browser in de Cloud Manager-infrastructuur geladen.
* Een gemeenschappelijke metrisch die ontbreekt is het foutentarief. Een URL kan dus alleen worden doorgegeven als de hoofd-URL met de status `200` en in minder dan `20` seconden wordt geladen. Wanneer een pagina langer dan `20` seconden wordt geladen, wordt deze gemarkeerd als een `504` -fout.
* Als uw plaats gebruikersauthentificatie vereist, zie [ Uw Resultaten van de Test ](/help/using/code-quality-testing.md#authenticated-performance-testing) begrijpen voor het vormen van de test zodat kunt u aan uw plaats voor authentiek verklaren.

Zie [ Begrijpend de Resultaten van de Test ](/help/using/code-quality-testing.md) voor meer informatie over kwaliteitscontroles.

## Kan ik SNAPSHOT voor de versie van het Maven project gebruiken? {#snapshot}

Ja. Voor ontwikkelaarsimplementaties moeten de Git-vertakkingsbestanden `pom.xml` aan het einde van de `-SNAPSHOT` -waarde bevatten.`<version>`

Dit laat verdere plaatsingen nog worden geïnstalleerd wanneer de versie niet veranderde. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

U kunt de versie ook instellen op `-SNAPSHOT` voor stadium- en productiebuilds of -implementaties. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in Git. Indien nodig kunt u later naar dit label verwijzen.

De verdere details over versie behandeling worden [ hier gedocumenteerd ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Hoe werkt het pakket en de bundelversioning voor het opvoeren en productieplaatsingen? {#staging-production}

In het opvoeren en productieplaatsingen, wordt een automatische versie geproduceerd [ zoals hier gedocumenteerd ](/help/managing-code/maven-project-version.md).

Stel voor aangepaste versies in werkgebied- en productieimplementaties een geschikte versie met drie delen in, zoals `1.0.0` . Verhoog de versie telkens wanneer u aan productie opstelt.

Cloud Manager voegt automatisch zijn versie aan stadium toe en de productie bouwt en leidt tot een tak van de Git. Er is geen speciale configuratie vereist. Als u een bepaalde versie niet zoals eerder beschreven plaatst, slaagt de plaatsing nog en een versie wordt automatisch geplaatst.

## Mijn gefabriceerde build mislukt voor Cloud Manager-implementaties, maar het wordt lokaal zonder fouten gemaakt. Wat is er mis? {#maven-build-fail}

Zie dit [ middel van de Git ](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer details.

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
