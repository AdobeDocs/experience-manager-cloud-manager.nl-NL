---
title: Branches configureren
description: Leer hoe te opstelling uw eerste tak in git en hoe het door de pijpleiding CI/CD wordt gebruikt om uw toepassingscode op te stellen.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Branches configureren {#configuring-branches}

Leer hoe te opstelling uw eerste tak in git en hoe het door de pijpleiding CI/CD wordt gebruikt om uw toepassingscode op te stellen.

## De eerste vertakking instellen in Git {#setting-up-your-first-branch-in-git}

Één enkele, aanvankelijk lege, git bewaarplaats [ wordt provisioned ](/help/requirements/environment-provisioning.md) voor elk programma op boord gebracht in Cloud Manager. Deze opslagplaats kan zo vele takken bevatten aangezien uw ontwikkelingsproces vereist, maar er moet minstens één tak zijn die door de pijpleiding CI/CD wordt gebruikt om toepassingscode aan stadium en productie op te stellen. U kunt `main` het beste gebruiken als de naam van deze vertakking. Dit is handig het standaardgedrag van it-clients wanneer u nieuwe projecten instelt.

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
>Het is geen vereiste om de bevel-lijn cliënt te gebruiken. Er zijn een verscheidenheid van grafische git cliënten beschikbaar of als standalone toepassingen of als deel van een geïntegreerde ontwikkelomgeving (winde) zoals Eclipse of IntelliJ. Zolang de clienttoepassing het gebruik van HTTPS ondersteunt, moet deze compatibel zijn met [!UICONTROL Cloud Manager] .

## De eerste vertakking duwen {#pushing-your-first-branch}

Nadat u ten minste één revisie hebt toegewezen, kunt u de [!UICONTROL Cloud Manager] -opslagplaats als een externe opslagplaats toevoegen en vervolgens uw verplichtingen erop toepassen.

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
>De specifieke URL, samen met uw referenties, wordt tijdens [!UICONTROL Cloud Manager] on-boarding door de Success Engineering van de Klant aan uw computer verstrekt.

## Aanvullende vertakkingen {#additional-branches}

Een enkele `main` -vertakking kan voldoende zijn voor zeer eenvoudige projecten, maar in de meeste gevallen is een complexere vertakkingsstrategie vereist. Veel klanten volgen een proces waarbij de ontwikkelingsactiviteiten van dag tot dag worden uitgevoerd op een vertakking die `develop` wordt genoemd en de ontwikkeltak in de `main` tak wordt samengevoegd wanneer het tijd voor een plaatsing is.

>[!TIP]
>
>Om gemeenschappelijke git bevelen te bekijken, zie het [ Punt van de Controle van de Git ](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
