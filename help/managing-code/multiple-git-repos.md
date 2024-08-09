---
title: Werken met Meerdere Git-opslagplaatsen
description: Leer hoe u met uw eigen git-opslagplaats of met meerdere git-opslagplaatsen kunt werken in plaats van rechtstreeks te werken met de Cloud Manager git-opslagplaats.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Werken met meerdere Source Git-opslagplaatsen {#working-with-multiple-source-git-repos}

Leer hoe u met uw eigen git-opslagplaats of met meerdere git-opslagplaatsen kunt werken in plaats van rechtstreeks te werken met de Cloud Manager git-opslagplaats.

## Door de klant beheerde Git-opslagruimten synchroniseren {#syncing-customer-managed-git-repositories}

Als u met uw eigen opslagplaats of opslagplaatsen wilt werken, moet een geautomatiseerd synchronisatieproces worden ingesteld om ervoor te zorgen dat de Cloud Manager git-opslagplaats altijd up-to-date wordt gehouden.

Afhankelijk van waar uw git bewaarplaats wordt ontvangen, zou een actie GitHub of een ononderbroken integratieoplossing zoals Jenkins aan opstelling de automatisering kunnen worden gebruikt. Met een automatisering op zijn plaats, kan elke duw aan uw eigen bewaarplaats automatisch door:sturen aan Cloud Manager git bewaarplaats.

Hoewel een dergelijke automatisering voor één enkele klant-eigendom git bewaarplaats ongecompliceerd is, vereist het vormen van dit omhoog voor veelvoudige bewaarplaatsen een meer geïmpliceerde aanvankelijke opstelling. De inhoud van meerdere opslagplaatsen voor it moet worden toegewezen aan verschillende directory&#39;s binnen één Cloud Manager git-opslagplaats. De Cloud Manager it-opslagplaats moet zijn voorzien van een hoofdmap Maven `pom.xml` , waarin de verschillende subprojecten worden vermeld in de sectie Modules

Hieronder ziet u een voorbeeld `pom.xml` voor twee in eigendom van de klant zijnde it-opslagruimten. Het eerste project wordt in de map met de naam `project-a` geplaatst. Het tweede project wordt in de map met de naam `project-b` geplaatst.

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

Zo&#39;n root `pom.xml` wordt doorgegeven aan een vertakking in de Cloud Manager Git-opslagplaats. Vervolgens moeten de twee projecten worden ingesteld om wijzigingen automatisch door te sturen naar de Cloud Manager git-opslagplaats.

Bijvoorbeeld, kan een actie GitHub door een duw aan een tak in project A worden teweeggebracht. Met de actie worden project A en de Cloud Manager git-opslagplaats uitgecheckt en wordt alle inhoud van project A naar de directory `project-a` in de Cloud Manager git-opslagplaats gekopieerd en vervolgens wordt de wijziging doorgevoerd.

Een wijziging in de `main` -vertakking in project A wordt bijvoorbeeld automatisch doorgestuurd naar de `main` -vertakking in de Cloud Manager Git-opslagplaats. Natuurlijk kan er een toewijzing tussen vertakkingen zijn, zoals een duw naar een vertakking genoemd `dev` in project A wordt geduwd naar een vertakking genoemd `development` in Cloud Manager git repository. Vergelijkbare stappen zijn vereist voor project B.

Afhankelijk van de vertakkingsstrategie en workflows kan de synchronisatie worden geconfigureerd voor verschillende vertakkingen. Als de gebruikte gokbewaarplaats geen concept gelijkend op acties GitHub verstrekt, is een integratie via (of gelijkaardig) Jenkins ook mogelijk. In dit geval activeert een webhaak een Jenkins-taak die het werk doet.

Voer de onderstaande stappen uit om een nieuwe (derde) bron of opslagplaats toe te voegen:

1. Voeg een nieuwe actie GitHub aan de nieuwe bewaarplaats toe die veranderingen van die bewaarplaats aan Cloud Manager git bewaarplaats duwt.
1. Voer die actie minstens eenmaal uit om ervoor te zorgen dat de projectcode in Cloud Manager git repository is.
1. Voeg een verwijzing naar de nieuwe map toe in de hoofdmap Maven `pom.xml` in de Cloud Manager Git-opslagplaats.

## Voorbeeld van GitHub-actie {#sample-github-action}

Dit is een voorbeeld van een GitHub-actie die wordt geactiveerd door een push naar de `main` -vertakking en die vervolgens in een submap van de Cloud Manager Git-opslagplaats wordt doorgedrukt. De GitHub-acties moeten worden voorzien van twee geheimen, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en druk op de Cloud Manager-git-opslagplaats.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Zoals hierboven getoond, is het gebruiken van een actie GitHub zeer flexibel. Elke toewijzing tussen vertakkingen van de it-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke it-projecten aan de mappenindeling van het hoofdproject.

>[!NOTE]
>
>In het bovenstaande script wordt `git add` gebruikt om de gegevensopslagruimte bij te werken, waarbij ervan wordt uitgegaan dat verwijderingen worden opgenomen. Afhankelijk van de standaardconfiguratie van de it moet deze mogelijk worden vervangen door `git add --all` .

## Sample Jenkins Job {#sample-jenkins-job}

Dit is een voorbeeldscript dat kan worden gebruikt in een Jenkins-taak of vergelijkbaar. Het wordt geactiveerd door een wijziging in een git-opslagplaats. De baan Jenkins controleert uit de recentste staat van dat project of tak en dan brengt dit manuscript in werking.

Dit script controleert op zijn beurt de Cloud Manager git-opslagplaats en legt de projectcode vast aan een subdirectory.

Voor de Jenkins-taak moeten twee geheimen worden opgegeven, `MAIN_USER` en `MAIN_PASSWORD` , om verbinding te kunnen maken met en te kunnen drukken op de Cloud Manager Git-opslagplaats.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Zoals hierboven is weergegeven, is het gebruik van een Jenkins-baan erg flexibel. Elke toewijzing tussen vertakkingen van de it-opslagplaatsen kan worden uitgevoerd en elke toewijzing van de afzonderlijke it-projecten aan de mappenindeling van het hoofdproject.

>[!NOTE]
>
>In het bovenstaande script wordt `git add` gebruikt om de gegevensopslagruimte bij te werken, waarbij ervan wordt uitgegaan dat verwijderingen zijn opgenomen. Afhankelijk van de standaardconfiguratie van it moet deze mogelijk worden vervangen door `git add --all` .
