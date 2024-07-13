---
title: Ondersteuning voor Git-submodule
description: Leer hoe u Git-submodules kunt gebruiken om de inhoud van meerdere vertakkingen in git-opslagruimten tijdens het samenstellen samen te voegen.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Ondersteuning voor Git-submodule voor opslagplaatsen voor Adoben {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen tussen git-opslagruimten.

Wanneer het Cloud Manager-bouwproces wordt uitgevoerd, nadat de opslagplaats die voor de pijplijn is geconfigureerd, is gekloond en de geconfigureerde vertakking is uitgecheckt, wordt de opdracht uitgevoerd als de vertakking een `.gitmodules` -bestand in de hoofdmap bevat.

```
$ git submodule update --init
```

Dit zal elke submodule in de aangewezen folder uitchecken. Deze techniek is een potentieel alternatief aan [ werkend met veelvoudige opslagplaatsen van de bronGit ](/help/managing-code/multiple-git-repos.md) voor organisaties die met het gebruiken van git submodules vertrouwd zijn en geen extern het samenvoegen proces willen beheren.

Stel dat er drie opslagruimten zijn die elk één vertakking met de naam `main` bevatten. In de &quot;primaire&quot; opslagplaats, d.w.z. de opslagplaats die in de pijpleidingen is geconfigureerd, heeft de `main` -vertakking een `pom.xml` -bestand waarin de projecten in de andere twee opslagplaatsen worden gedeclareerd:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Vervolgens voegt u submodules toe voor de andere twee opslagruimten:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dit resulteert in een `.gitmodules` -bestand dat er als volgt uitziet:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Meer informatie over git submodules kan in het [ de verwijzingshandboek van de Git ](https://git-scm.com/book/en/v2/Git-Tools-Submodules) worden gevonden.

## Beperkingen {#limitations}

Houd rekening met het volgende wanneer u it-submodules gebruikt:

* De URL van de it moet exact in de hierboven beschreven syntaxis staan.
* Sluit om beveiligingsredenen geen referenties in deze URL&#39;s in.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* Git-submoduleverwijzingen worden opgeslagen naar specifieke it-opdrachten.
   * Als er wijzigingen worden aangebracht in de opslagplaats van de submodule, moet de verwijzing naar de submodule daarom worden bijgewerkt, bijvoorbeeld met behulp van `git submodule update --remote` .
* Tenzij anders nodig, wordt het ten zeerste aanbevolen &quot;oppervlakkige&quot; submodules te gebruiken.
   * Voer hiervoor `git config -f .gitmodules submodule.<submodule path>.shallow true` uit voor elke submodule.


## Ondersteuning voor Git-submodule voor privéopslagplaatsen {#private-repositories}

Steun voor git submodules wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md) is grotendeels het zelfde als wanneer het gebruiken van de bewaarplaatsen van de Adobe.

Nadat u het `pom.xml` -bestand hebt ingesteld en de `git submodule` -opdrachten hebt uitgevoerd, moet u echter een `.gitmodules` -bestand aan de hoofdmap van de aggregatoropslagplaats toevoegen, zodat Cloud Manager de installatie van de submodule kan detecteren.

![ .gitmodules, bestand ](assets/gitmodules.png)

![ Agregator ](assets/aggregator.png)

### Beperkingen en Recommendations {#limitations-recommendations-private-repos}

Houd rekening met de volgende beperkingen wanneer u git-submodules gebruikt met persoonlijke opslagruimten.

* De URL&#39;s van de it voor de submodules kunnen de HTTPS- of SSH-indeling hebben, maar ze moeten een koppeling naar een github.com-opslagplaats maken
   * Het toevoegen van een ondermodule van de opslagplaats van de Adobe aan een aggregatorbewaarplaats GitHub of vice versa zal niet werken.
* De ondermodules GitHub moeten voor de AdobeApp toegankelijk zijn GitHub.
* [ de beperkingen om git submodules met Adobe-geleide bewaarplaatsen ](#limitations-recommendations) te gebruiken zijn ook van toepassing.
