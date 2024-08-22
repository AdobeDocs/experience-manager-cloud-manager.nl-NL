---
title: Ondersteuning voor Git-submodule
description: Leer hoe u Git-submodules kunt gebruiken om de inhoud van meerdere vertakkingen in Git-opslagruimten tijdens het samenstellen samen te voegen.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Ondersteuning voor Git-submodule voor opslagruimten voor Adoben {#git-submodule-support}

Git-submodules kunnen worden gebruikt om de inhoud van meerdere vertakkingen tijdens het samenstellen samen te voegen via Git-opslagruimten.

Wanneer Cloud Manager bouwt proces looppas, klonen het eerst de bewaarplaats van de pijpleiding en controleert de gevormde tak. Als de vertakking een `.gitmodules` dossier in de wortelfolder bevat, wordt het bevel dan uitgevoerd.

```
$ git submodule update --init
```

Dit proces controleert elke submodule in de aangewezen folder. Deze techniek is een potentieel alternatief aan [ werkend met veelvoudige opslagplaatsen van de bronGit ](/help/managing-code/multiple-git-repos.md) voor organisaties die comfortabel het gebruiken van submodules van het Git zijn en geen extern het samenvoegen proces willen beheren.

Stel dat er drie opslagruimten zijn die elk één vertakking met de naam `main` bevatten. In de &quot;primaire&quot; opslagplaats, dat wil zeggen de opslagplaats die in de pijpleidingen is geconfigureerd, heeft de `main` -vertakking een `pom.xml` -bestand waarmee de projecten in de andere twee opslagplaatsen worden gedeclareerd:

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

De resultaten in het `.gitmodules` -bestand zien er als volgt uit:

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

Zie het [ referentiehandboek van de Git ](https://git-scm.com/book/en/v2/Git-Tools-Submodules) voor meer informatie over submodules van het Git.

## Beperkingen {#limitations}

Houd rekening met het volgende wanneer u Git-submodules gebruikt:

* De URL van de it moet exact in de hierboven beschreven syntaxis staan.
* Sluit om beveiligingsredenen geen referenties in deze URL&#39;s in.
* Alleen submodules in de hoofdmap van de vertakking worden ondersteund.
* De verwijzingen van de submodule van de Git worden opgeslagen aan specifieke Git begaat. Dientengevolge, wanneer veranderingen in de submodule bewaarplaats worden aangebracht, begaat referenced moet worden bijgewerkt. Bijvoorbeeld met `git submodule update --remote` .
* Tenzij anders nodig, adviseert de Adobe dat u &quot;oppervlakkige&quot;submodules door `git config -f .gitmodules submodule.<submodule path>.shallow true` voor elke submodule in werking te stellen gebruikt.


## Ondersteuning voor Git-submodule voor privéopslagruimten {#private-repositories}

De steun voor submodules van het Git wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md) is grotendeels het zelfde als wanneer het gebruiken van de bewaarplaatsen van de Adobe.

Nadat u het `pom.xml` -bestand hebt ingesteld en de `git submodule` -opdrachten hebt uitgevoerd, moet u echter een `.gitmodules` -bestand aan de hoofdmap van de aggregatoropslagplaats toevoegen, zodat Cloud Manager de installatie van de submodule kan detecteren.

![ .gitmodules, bestand ](assets/gitmodules.png)

![ Agregator ](assets/aggregator.png)

### Beperkingen en aanbevelingen {#limitations-recommendations-private-repos}

Houd rekening met de volgende beperkingen wanneer u Git-submodules gebruikt met persoonlijke opslagruimten.

* De URL&#39;s van de Git voor de submodules kunnen de HTTPS- of SSH-indeling hebben, maar ze moeten een koppeling naar een Github.com-opslagplaats maken. Het toevoegen van een submodule van de opslagplaats van de Adobe aan een aggregatorbewaarplaats GitHub of vice versa werkt niet.
* De ondermodules GitHub moeten voor de AdobeApp toegankelijk zijn GitHub.
* [ de beperkingen van het gebruiken van submodules van het Git met Adobe-beheerde bewaarplaatsen ](#limitations-recommendations) zijn ook van toepassing.
