---
title: Privéopslagplaatsen toevoegen in Cloud Manager
description: Leer hoe te opstelling Cloud Manager om met uw eigen privé bewaarplaatsen te werken GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 58cdebf819f2737be5d8e129ff5b9783888f3c21
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Persoonlijke opslagruimten toevoegen in Cloud Manager {#private-repositories}

Leer hoe te opstelling Cloud Manager om met uw eigen privé bewaarplaatsen te werken GitHub.

## Overzicht {#overview}

Het vormen van Cloud Manager met uw privé bewaarplaatsen GitHub laat u code direct binnen GitHub bevestigen, die de behoefte om met de bewaarplaats van Adobe regelmatig elimineert te synchroniseren.

>[!NOTE]
>
>Deze eigenschap is exclusief aan openbare GitHub. De steun voor zelf-ontvangen GitHub is niet beschikbaar.

## Configuratie {#configuration}

De configuratie bestaat uit twee hoofdstappen:

1. [Opslagplaats toevoegen](#add-repo)
1. [Eigendom van privéopslagplaats valideren](#validate-ownership)



### Een opslagplaats toevoegen {#add-repo}

1. In Cloud Manager, van de **pagina van het Overzicht van het Programma**, klik het **lusje van Bewaarplaatsen** om aan de **pagina van Bewaarplaatsen** te schakelen en **te klikken voeg Bewaarplaats** toe.

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, uitgezochte **Privé Bewaarplaats** als bewaarplaatstype.

1. Geef de gegevens van uw opslagplaats op

   * **Naam van de Bewaarplaats** - een expressieve naam
   * **Repository URL** - URL van de bewaarplaats, die in `.git` moet beëindigen
   * **Beschrijving** (facultatief) - een langere beschrijving van de bewaarplaats zonodig

   ![ voeg eigen bewaarplaats ](/help/assets/repositories/add-own-github.png) toe

1. Klik **sparen**.

>[!TIP]
>
>Voor details over het beheren van bewaarplaatsen in Cloud Manager, zie [ Bewaarplaatsen van Cloud Manager ](/help/managing-code/managing-repositories.md).



### Eigendom van een privéopslagplaats valideren {#validate-ownership}

Cloud Manager weet nu van uw bewaarplaats GitHub, maar het heeft nog toegang tot het nodig. Om toegang te verlenen, moet u de toepassing van Adobe GitHub installeren en verifiëren dat u de gespecificeerde bewaarplaats bezit.

1. Na het toevoegen van uw eigen bewaarplaats, wordt het **dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé getoond.**

   ![ Persoonlijke Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats ](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager gebruikt een GitHub-app om veilig met uw opslagplaats te communiceren.

   Een eigenaar van uw GitHub-organisatie moet de toepassing in `https://github.com/apps/cloud-manager-for-aem` installeren en toegang verlenen tot de opslagplaats. Zie de documentatie van GitHub voor details.

1. Om de beveiliging te verbeteren, maakt u een geheim bestand in de standaardvertakking van de repository. Klik **produceren**.

1. Bevestig de generatie van het geheime dossier door **te klikken bevestigt**.

   ![ bevestigt geheime generatie ](/help/assets/repositories/confirm-generation.png)

1. Terug in de **dialoogdoos van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé, heeft Cloud Manager de inhoud op het** Geheime 3} gebied van de dossierinhoud {geproduceerd. **** Kopieer de inhoud van dat veld.

   De inhoud van het geheime bestand wordt slechts eenmaal weergegeven. Als u de inhoud niet kopieert voordat u dit venster sluit, moet u het geheim opnieuw genereren.

   ![ het geheime dossierinhoud van het Exemplaar ](/help/assets/repositories/new-secret.png)

1. Maak een nieuw bestand in de standaardvertakking van uw GitHub-repo met de naam `.well-known/adobe/cloud-manager-challenge` en plak de geheime bestandsinhoud in dat bestand en sla dit op.

1. Nadat app wordt geïnstalleerd en het geheime dossier in de bewaarplaats bestaat, kunt u **klikken bevestigt** in de **Privé dialoog van de Bevestiging van de Eigendom van de Bewaarplaats van de Bewaarplaats**.

De toepassing kan worden geïnstalleerd en u kunt een geheim dossier in om het even welke orde produceren. Beide stappen moeten echter zijn voltooid voordat u de validatie kunt uitvoeren.

Tot de validatie wordt de repository weergegeven met een rood pictogram dat aangeeft dat deze nog niet is gevalideerd en nog niet kan worden gebruikt.

![ Unvalidate repo ](/help/assets/repositories/unvalidated-repo.png)

Merk op dat de **kolom van het Type** gemakkelijk Adobe-Verstrekte bewaarplaatsen (**Adobe**) en uw eigen bewaarplaatsen GitHub (**GitHub**) identificeert.

Om aan de bewaarplaats later terug te keren en de bevestiging te voltooien, ga naar de **pagina van Bewaarplaatsen**. Klik ![ Meer pictogram, ellips ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast de bewaarplaats GitHub die u toevoegde, dan klik de Bevestiging van de Eigendom ****.


## Persoonlijke opslagruimten gebruiken met Cloud Manager {#using}

Nadat de bewaarplaats GitHub in Cloud Manager wordt bevestigd, wordt de integratie voltooid en u kunt de bewaarplaats met Cloud Manager gebruiken.

**om privé bewaarplaatsen met Cloud Manager te gebruiken:**

1. Wanneer u een trekkingsverzoek creeert, begint een controle GitHub automatisch.

   ![ controles GitHub ](/help/assets/repositories/github-checks.png)

1. Voor elk trekkingsverzoek, wordt de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/using/managing-pipelines.md) automatisch gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

1. De controle GitHub blijft in een lopende staat tot de controles van de codekwaliteit worden voltooid. De resultaten van de codekwaliteit worden dan verspreid aan de controle GitHub.

   ![ GitHub de controles van de codekwaliteit ](/help/assets/repositories/github-code-quality.png)

Wanneer het trekkingsverzoek wordt gesloten of samengevoegd, wordt de volledige pijpleiding van de kwaliteit van de stapelcode gecreeerd automatisch geschrapt.

>[!TIP]
>
>Zie de Annotaties van de Controle van het document [ GitHub ](github-annotations.md) voor details over de informatie die via GitHub wordt verstrekt wanneer de controles van het trekkingsverzoek in werking worden gesteld.

>[!TIP]
>
>U kunt de pijpleidingen controleren die automatisch worden gecreeerd om elk trekkingsverzoek aan een privé bewaarplaats te bevestigen. Zie {de Configuratie van de Controle van 0} GitHub voor Privé Opslagplaatsen ](github-check-config.md) voor meer informatie.[



## Particuliere opslagplaatsen koppelen aan pijpleidingen {#pipelines}

Gevalideerde privé bewaarplaatsen kunnen met [ volledig-stapel en frontend pijpleidingen ](/help/overview/ci-cd-pipelines.md) worden geassocieerd.



## Beperkingen {#limitations}

Bij het gebruik van persoonlijke opslagruimten met Cloud Manager gelden bepaalde beperkingen.

* De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen.
* Er wordt geen tag Git gemaakt en geduwd wanneer u privéopslagruimten gebruikt bij de productie van volledige stapelleidingen.
* Als de Adobe GitHub-toepassing uit uw GitHb-organisatie wordt verwijderd, verwijdert deze actie de functie voor het valideren van pull-aanvragen voor alle repositories.
* De pijpleidingen die privé bewaarplaatsen gebruiken en de aanzetmachine op-verbind zijn niet automatisch begonnen wanneer nieuw verbindt in de geselecteerde tak wordt geduwd.
* [ functionaliteit van het Hergebruik van Artefact ](/help/getting-started/project-setup.md#build-artifact-reuse) is niet op privé bewaarplaatsen van toepassing.
* U kunt niet de bevestiging van het trekkingsverzoek pauzeren gebruikend de controle GitHub van Cloud Manager. Als de bewaarplaats GitHub in Cloud Manager wordt bevestigd, probeert Cloud Manager om de trekkingsverzoeken te bevestigen die voor die bewaarplaats worden gecreeerd.
