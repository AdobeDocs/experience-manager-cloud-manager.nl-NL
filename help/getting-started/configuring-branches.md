---
title: Branches configureren
description: Leer hoe te opstelling uw eerste tak in Git en hoe het door de pijpleiding CI/CD wordt gebruikt om uw toepassingscode op te stellen.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Vertakkingen configureren {#configuring-branches}

Leer hoe te opstelling uw eerste tak in Git en hoe het door de pijpleiding CI/CD wordt gebruikt om uw toepassingscode op te stellen.

## De eerste vertakking in Git instellen {#setting-up-your-first-branch-in-git}

Één enkele, aanvankelijk lege, git bewaarplaats [ wordt provisioned ](/help/requirements/environment-provisioning.md) voor elk programma op boord gebracht in Cloud Manager. Deze opslagplaats kan zo vele takken bevatten aangezien uw ontwikkelingsproces vereist, maar er moet minstens één tak zijn die door de pijpleiding CI/CD wordt gebruikt om toepassingscode aan stadium en productie op te stellen. U kunt `main` het beste gebruiken als de naam van deze vertakking. Deze benadering is handig het standaardgedrag van Git-clients bij het opzetten van nieuwe projecten.

Wanneer u bijvoorbeeld een nieuw project instelt, voert u een set opdrachten uit die vergelijkbaar zijn met de volgende:

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Het is geen vereiste om de bevel-lijn cliënt te gebruiken. Er zijn een verscheidenheid van grafische cliënten van Git beschikbaar of als standalone toepassingen of als deel van een geïntegreerde ontwikkelomgeving (winde) zoals Eclipse of IntelliJ. Zolang de clienttoepassing het gebruik van HTTPS ondersteunt, moet deze compatibel zijn met [!UICONTROL Cloud Manager] .

## De eerste vertakking duwen {#pushing-your-first-branch}

Wanneer u minstens één revisie hebt toegewezen, kunt u de [!UICONTROL Cloud Manager] opslagplaats als ver toevoegen, en dan uw toezeggingen aan het duwen.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>De specifieke URL, samen met uw gegevens, wordt tijdens het instappen door uw Adobe-CSE (Customer Success Engineer) verstrekt.[!UICONTROL Cloud Manager]

## Aanvullende vertakkingen {#additional-branches}

Een enkele `main` -vertakking kan voldoende zijn voor zeer eenvoudige projecten, maar in de meeste gevallen is een complexere vertakkingsstrategie vereist. Veel klanten volgen een proces waarbij de ontwikkelingsactiviteiten van dag tot dag worden uitgevoerd op een vertakking met de naam `develop` . De ontwikkeltak wordt dan samengevoegd in de `main` tak wanneer het tijd voor een plaatsing is.

>[!TIP]
>
>Om gemeenschappelijke bevelen van het Git te bekijken, zie het [ Vondst van de Git ](https://training.github.com/downloads/github-git-cheat-sheet).
