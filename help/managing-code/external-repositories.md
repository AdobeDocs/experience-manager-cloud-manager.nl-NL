---
title: Externe opslagplaatsen toevoegen in Cloud Manager
description: Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub Enterprise-, GitLab- en Bitbucket-opslagruimten.
badge: label="Private bèta" type="Positive" url="/help/release-notes/current.md#gitlab-bitbucket"
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: bacb4b6e79519e4fef4cf01e04154d492cc888e2
workflow-type: tm+mt
source-wordcount: '2035'
ht-degree: 0%

---

# Externe opslagruimten toevoegen in Cloud Manager {#external-repositories}

Leer hoe u een externe opslagplaats aan Cloud Manager kunt toevoegen. Cloud Manager ondersteunt integratie met GitHub Enterprise-, GitLab- en Bitbucket-opslagruimten.

>[!NOTE]
>
>De functies die in dit artikel worden beschreven, zijn alleen beschikbaar via het persoonlijke bètaprogramma. Voor meer details en om omhoog voor privé bèta te ondertekenen, zie [ Uw Eigen Git ](/help/release-notes/current.md#gitlab-bitbucket) brengen.

## Een externe opslagplaats configureren

De configuratie van een externe opslagplaats in Cloud Manager bestaat uit drie stappen:

1. [ voeg een externe bewaarplaats ](#add-external-repo) aan een geselecteerd programma toe.
1. [ Verbinding een gevalideerde externe bewaarplaats aan een pijpleiding ](#validate-ext-repo).
<!-- 1. Provide an access token to the external repository.
1. Validate ownership of the private GitHub repository. -->
1. [ vorm een webhaak ](#configure-webhook) aan een externe bewaarplaats.


## Een externe opslagplaats toevoegen {#add-ext-repo}

>[!NOTE]
>
>Externe opslagplaatsen kunnen niet worden gekoppeld aan configuratiepijpleidingen.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/getting-started/navigation.md#my-programs-console)**, selecteer het programma waaraan u een externe bewaarplaats wilt verbinden.

1. In het zijmenu, onder **Programma**, klik ![ het overzichtspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.

   ![ de pagina van Bewaarplaatsen ](/help/managing-code/assets/repositories-tab.png)

1. Vlak de hoger-juiste hoek van de **pagina van Bewaarplaatsen**, klik **toevoegen Bewaarplaats**.

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, selecteer **Privé Bewaarplaats** om een externe bewaarplaats van de Bewaarplaats van de Bewaarplaats aan uw programma te verbinden.

   ![ voeg eigen bewaarplaats ](/help/managing-code/assets/repository-add-private-dialogbox2.png) toe

1. Geef in elk veld de volgende gegevens over uw opslagplaats op:

   | Veld | Beschrijving |
   | --- | --- |
   | **Naam van de Bewaarplaats** | Vereist. Een expressieve naam voor uw nieuwe opslagplaats. |
   | **Repository URL** | Vereist. De URL van de gegevensopslagruimte.<br><br> als u een GitHub-ontvangen bewaarplaats gebruikt, moet de weg in `.git` beëindigen.<br> bijvoorbeeld, *`https://github.com/org-name/repo-name.git`* (De weg URL is slechts voor illustratie).<br><br> als u een externe bewaarplaats gebruikt, moet het het volgende URL wegformaat gebruiken:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> of <br>`https://self-hosted-domain/org-name/repo-name.git`<br> en past uw verkoper van het Git aan. |
   | **Uitgezochte Type van Bewaarplaats** | Vereist. Selecteer het type opslagplaats dat u gebruikt:<ul><li>**GitHub** (Onderneming GitHub en de zelf-ontvangen versie van GitHub)</li><li>**GitLab** (zowel `gitlab.com` als de zelf-ontvangen versie van GitLab) </li><li>**Bitbucket** (slechts `bitbucket.org` (wolkenversie) wordt gesteund. De zelfgehoste versie van Bitbucket is vanaf 15 februari 2024 vervangen.)</li></ul>Als het URL-pad van de repository hierboven de naam van de Git-leverancier bevat, zoals GitLab of Bitbucket, is het repository type al vooraf geselecteerd voor u. |
   | **Beschrijving** | Optioneel. Een gedetailleerde beschrijving van de gegevensopslagruimte. |

1. Selecteer **sparen** om de bewaarplaats toe te voegen.

   Geef nu een toegangstoken om de eigendom van de externe opslagplaats te valideren.

1. In het **dialoogvakje van de Bevestiging van de Eigendom van de Bewaarplaats 0} Privé, verstrek een toegangstoken om eigendom van de externe bewaarplaats te bevestigen zodat kunt u tot het toegang hebben, dan klik** Valideren **.**

   ![ Selecterend een bestaand toegangstoken voor een bewaarplaats ](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Selecterend een bestaand toegangstoken voor een bewaarplaats Bitbucket (voor illustratie slechts).*

>[!BEGINTABS]

>[!TAB  Onderneming GitHub ]

| Type token | Beschrijving |
| --- | --- |
| **het Bestaande Token van de Toegang van het Gebruik** | Als u al een toegangstoken voor de opslagplaats hebt opgegeven voor uw organisatie en toegang hebt tot meerdere opslagplaatsen, kunt u een bestaand token selecteren. Gebruik de **Symbolische Naam** drop-down lijst om het teken te kiezen u op de bewaarplaats wilt toepassen. Anders, voeg een nieuw toegangstoken toe. |
| **voeg nieuw Token van de Toegang toe** | <ul><li> Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een persoonlijk toegangstoken door de instructies in de [ documentatie GitHub ](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) te volgen.<li>De vereiste toestemmingen voor het Token van de Toegang van de Onderneming GitHub Persoonlijke (KLOPJE) <br> Deze toestemmingen verzekeren dat Cloud Manager trekverzoeken kan bevestigen, statuscontroles, en toegangsnoodzakelijke repo details beheren.<br> wanneer u het KLOPJE in de Onderneming GitHub produceert, zorg ervoor het de volgende bewaarplaatstoestemmingen omvat:<ul><li>Pull request (lezen en schrijven)<li>Statussen vastleggen (lezen en schrijven)<li>Metagegevens opslagplaats (alleen-lezen)</li></li></ul></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |

Na bevestiging, is de externe bewaarplaats klaar om aan een pijpleiding te gebruiken en te verbinden.

Zie ook [ de Tokens van de Toegang beheren ](/help/managing-code/manage-access-tokens.md).

>[!TAB  GitLab ]

| Type token | Beschrijving |
| --- | --- |
| **het Bestaande Token van de Toegang van het Gebruik** | Als u al een toegangstoken voor de opslagplaats hebt opgegeven voor uw organisatie en toegang hebt tot meerdere opslagplaatsen, kunt u een bestaand token selecteren. Gebruik de **Symbolische Naam** drop-down lijst om het teken te kiezen u op de bewaarplaats wilt toepassen. Anders, voeg een nieuw toegangstoken toe. |
| **voeg nieuw Token van de Toegang toe** | <ul><li>Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een persoonlijk toegangstoken door de instructie in de [ documentatie GitLab ](https://docs.gitlab.com/user/profile/personal_access_tokens/) te volgen.<li>Vereiste toestemmingen voor het Token van de Toegang van GitLab Persoonlijke (KLOPJE) <br> Deze werkingsgebieden staan Cloud Manager toe om tot gegevens van de gegevensopslagplaats en gebruikersinformatie zoals nodig voor bevestiging en WebHaakintegratie toegang te hebben.<br> wanneer u het KLOPJE in GitLab produceert, zorg ervoor het het volgende symbolische werkingsgebied omvat:<ul><li>api<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |

Na bevestiging, is de externe bewaarplaats klaar om aan een pijpleiding te gebruiken en te verbinden.

Zie ook [ de Tokens van de Toegang beheren ](/help/managing-code/manage-access-tokens.md).


>[!TAB  Bitbucket ]

| Type token | Beschrijving |
| --- | --- |
| **het Bestaande Token van de Toegang van het Gebruik** | Als u al een toegangstoken voor de opslagplaats hebt opgegeven voor uw organisatie en toegang hebt tot meerdere opslagplaatsen, kunt u een bestaand token selecteren. Gebruik de **Symbolische Naam** drop-down lijst om het teken te kiezen u op de bewaarplaats wilt toepassen. Anders, voeg een nieuw toegangstoken toe. |
| **voeg nieuw Token van de Toegang toe** | <ul><li>Op het **Symbolische de tekstgebied van de Naam**, typ een naam voor het toegangstoken u creeert.<li>Creeer een toegangstoken van de bewaarplaats gebruikend de [ documentatie Bitbucket ](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>De vereiste toestemmingen voor het Symbolische Symbolische Token van de Toegang van de Bitmap Persoonlijke (KLOPJE) <br> Deze toestemmingen staan Cloud Manager toe om tot inhoud van de opslagplaats toegang te hebben, trekkingsverzoeken te beheren, en te vormen of op Web-haakgebeurtenissen te reageren.<br> wanneer u het toepassingswachtwoord in Bitbucket creeert, zorg ervoor het de volgende vereiste toestemmingen van het toepassingswachtwoord omvat:<ul><li>Opslagplaats (alleen-lezen)<li>Pull-aanvragen (lezen en schrijven)<li>Webhaken (lezen en schrijven)</li></li></ul></li></li></ul></ul></ul><ul><li>Op het **Symbolische gebied van de Toegang**, kleef het teken u enkel creeerde. |

Na bevestiging, is de externe bewaarplaats klaar om aan een pijpleiding te gebruiken en te verbinden.

Zie ook [ de Tokens van de Toegang beheren ](/help/managing-code/manage-access-tokens.md).

>[!ENDTABS]


## Koppel een gevalideerde externe opslagruimte aan een pijpleiding {#validate-ext-repo}

1. Een pijplijn toevoegen of bewerken:
   * [Een productiepijplijn toevoegen](/help/using/production-pipelines.md#adding-production-pipeline)
   * [Niet-productiepijpleidingen toevoegen](/help/using/non-production-pipelines.md#add-non-production-pipeline)
   * [Een pijplijn bewerken](/help/using/managing-pipelines.md#editing-pipelines)

   {de bron van de 0} Opslag van de code van de Pijpleiding en tak van het Git ](/help/managing-code/assets/pipeline-repo-gitbranch.png)![
   *voeg de dialoogdoos van de Pijpleiding van de Niet-Productie met geselecteerde bewaarplaats en de tak van het Git toe,*

1. Wanneer het toevoegen van of het uitgeven van een pijpleiding, om de **plaats van de Code van Source** voor uw nieuwe of bestaande pijpleiding te specificeren, verkies de externe bewaarplaats u van de **drop-down lijst van de Bewaarplaats** wilt gebruiken.

1. In de **drop-down lijst van de Tak van 0} Git, selecteer de tak als bron voor de pijpleiding.**

1. Klik **sparen**.


>[!TIP]
>
>Voor details over het beheren van bewaarplaatsen in Cloud Manager, zie [ Bewaarplaatsen van Cloud Manager ](/help/managing-code/managing-repositories.md).


## Een webhaak configureren voor een externe gegevensopslagruimte {#configure-webhook}

Met Cloud Manager kunt u webhaken configureren voor externe Git-opslagruimten die u hebt toegevoegd. Zie [ een externe bewaarplaats ](#add-ext-repo) toevoegen. Met deze websites kan Cloud Manager gebeurtenissen ontvangen die gerelateerd zijn aan verschillende acties binnen uw Git-leveranciersoplossing.

Met websites kan Cloud Manager bijvoorbeeld acties activeren op basis van gebeurtenissen zoals de volgende:

* Creatie van het volledige verzoek (PR) - initieert de functionaliteit voor PR-validatie.
* Push events - Start pijpleidingen wanneer de trigger &quot;On Git Commit&quot; is ingeschakeld (ingeschakeld).
* Toekomstige op opmerkingen gebaseerde acties - Hiermee worden workflows mogelijk, zoals directe implementatie van een PR, naar een Rapid Development Environment (RDE).

Webhaconfiguratie is niet vereist voor opslagruimten die op `GitHub.com` worden gehost, omdat Cloud Manager rechtstreeks via de GitHub-app integreert.

Voor alle andere externe bewaarplaatsen die met een toegangstoken, zoals Onderneming GitHub, GitLab, en Bitbucket worden bezet, is de webhaakconfiguratie beschikbaar en moet opstelling manueel.

**om een webhaak voor een externe bewaarplaats te vormen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/getting-started/navigation.md#my-programs-console)**, selecteer het programma waaraan u een webhaak voor een externe bewaarplaats van het Git wilt vormen.

1. In de upper-left hoek van de pagina, klik ![ tonen menupictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het linkerzijmenu te openbaren.

1. In het linkerzijmenu, onder de **rubriek van het Programma**, klik ![ het overzichtspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.

1. Op de **pagina van Bewaarplaatsen**, die de **kolom van het Type** gebruikt om u in uw selectie te begeleiden, van de bewaarplaats de plaats bepalen u wilt, dan klik ![ Ellipse - Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) naast het.

   ![ de optie Webhaak van Config op drop-down menu voor een geselecteerde bewaarplaats ](/help/managing-code/assets/repository-config-webhook.png)

1. Van het drop-down menu, klik **Config Webhaak**.

   ![ vorm de dialoogdoos van Webhaak ](/help/managing-code/assets/config-webhook.png)

1. In het **de dialoogvakje van WebHaak van Config**, doe het volgende:

   1. Naast het **gebied van URL van de Webhaak**, klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Plak de URL in een tekstbestand zonder opmaak. De gekopieerde URL is vereist voor de WebHaak-instellingen van uw Git-leverancier.
   1. Naast het **Geheime 1} teken/zeer belangrijke gebied van Webhaak {, klik** **produceren, dan klik ![ pictogram van het Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).**
Plak het geheim in een tekstbestand zonder opmaak. Het gekopieerde geheim wordt vereist voor de montages Webhaak van uw verkoper van het Git.
1. Klik **dicht**.
1. Navigeer naar uw Git-leveranciersoplossing (GitHub Enterprise, GitLab of Bitbucket).

   Alle details op de webshconfiguratie en de gebeurtenissen die voor elke verkoper worden vereist zijn beschikbaar in [ een externe bewaarplaats ](#add-ext-repo) toevoegen. Zie de tabel met tabbladen onder stap 8.

1. Bepaal de plaats van de sectie van de Montages van Webhaak **** van de oplossing.
1. Plak de URL van de Webhaak die u eerder hebt gekopieerd in het URL-tekstveld.
   1. Vervang de query-parameter `api_key` in de URL van de Webhaak door uw eigen echte API-sleutel.

      Als u een API-sleutel wilt genereren, moet u een integratieproject maken in Adobe Developer Console. Zie [ Creërend een Project van de Integratie API ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) voor volledige details.

1. Plak het Geheim WebHaak dat u vroeger in het **Geheime** (of **Geheime sleutel**, of **Geheime teken**) tekstgebied kopieerde.
1. Configureer de webhaak om de gebeurtenissen te verzenden die Cloud Manager nodig heeft. Gebruik de volgende lijst om de correcte gebeurtenissen voor uw leverancier van het Git te bepalen.

>[!BEGINTABS]

>[!TAB  Onderneming GitHub ]

    | Vereiste gebeurtenissen van de webhaak |
    | — |
    | Deze gebeurtenissen staan Cloud Manager toe om aan activiteit te antwoorden GitHub, zoals trekverzoekbevestiging, op duw-gebaseerde trekkers voor pijpleidingen, of de codesynchronisatie van Edge Delivery Services.&lt;br>Controleer of de webhaak is ingesteld om de volgende vereiste webhgebeurtenissen te activeren:&lt;ul>&lt;li>Pull-verzoeken&lt;li>Pushes&lt;li>Issues comments&lt;/li>&lt;/li>&lt;/li>&lt;/ul>&lt;/ul>&lt;/ul>&lt;/ul>&lt;/ul> |

>[!TAB  GitLab ]

    | Vereiste gebeurtenissen van de webhaak |
    | — |
    | Met deze webhaakgebeurtenissen kan Cloud Manager pijpleidingen activeren wanneer code wordt geduwd of een samenvoegaanvraag wordt ingediend. Zij volgen ook commentaren met betrekking tot trekverzoekbevestiging (door nota gebeurtenissen).&lt;br>Zorg ervoor dat de webhaak is ingesteld om de volgende vereiste webhaakgebeurtenissen te activeren&lt;ul>&lt;li>Push events&lt;li>Merge request events&lt;li>Notitie events&lt;/li>&lt;/li>&lt;/li>&lt;/ul>&lt;/ul>&lt;/ul>&lt;/ul>&lt;/ul> |

>[!TAB  Bitbucket ]

    | Vereiste gebeurtenissen van de webhaak |
    | — |
    | Deze gebeurtenissen zorgen ervoor dat Cloud Manager aantrekverzoeken kan bevestigen, op codeduwen kan antwoorden, en met commentaren voor pijpleidingscoördinatie in wisselwerking staat.&lt;br>Controleer of de webhaak is ingesteld om de volgende vereiste webhgebeurtenissen te activeren&lt;ul>&lt;li>Pull-verzoek: Gemaakt&lt;li>Pull-verzoek: Bijgewerkt&lt;li>Pull-verzoeken: Samengevoegd&lt;li>Pull-verzoek: Opmerking&lt;li>Repository: Push&lt;/li>&lt;/li>&lt;/li>&lt;/ul>&lt;/ul>&lt;/ul> |

>[!ENDTABS]


### Validatie van trekkingsverzoeken met webhaken

Nadat websites correct zijn geconfigureerd, activeert Cloud Manager automatisch het uitvoeren van pijpleidingen of het valideren van aanvragen (PR) voor uw opslagplaats.

Het gedrag is afhankelijk van de Git-provider die u gebruikt, zoals hieronder wordt beschreven.


>[!BEGINTABS]

>[!TAB  Onderneming GitHub ]

Wanneer de controle is gemaakt, lijkt deze op de onderstaande schermafbeelding. Het belangrijkste verschil van `GitHub.com` is dat `GitHub.com` controle-looppas gebruikt, terwijl de Onderneming GitHub (die persoonlijke toegangstokens gebruikt) een begaat status produceert:

![ verbindt status toe om PR validatieproces op Onderneming GitHub ](/help/managing-code/assets/repository-webhook-github-pr-validation.png) te wijzen

>[!TAB  GitLab ]

GitLab-interacties zijn uitsluitend gebaseerd op opmerkingen. Wanneer de validatie begint, wordt een opmerking toegevoegd. Wanneer de validatie is voltooid (of deze is gelukt of mislukt), wordt de eerste opmerking verwijderd en vervangen door een nieuwe opmerking met validatieresultaten of foutdetails.

Wanneer de validatie van de codekwaliteit wordt uitgevoerd:

![ wanneer de bevestiging van de codekwaliteit ](/help/managing-code/assets/repository-webhook-gitlab1.png) loopt

Wanneer validatie van koude kwaliteit is voltooid:

![ wanneer de koude kwaliteitsbevestiging ](/help/managing-code/assets/repository-webhook-gitlab2.png) wordt gebeëindigd

Wanneer validatie van de codekwaliteit mislukt vanwege een fout:

![ wanneer de bevestiging van de codekwaliteit met een fout ](/help/managing-code/assets/repository-webhook-gitlab3.png) ontbreekt

Wanneer de validatie van de codekwaliteit mislukt als gevolg van problemen met de klant:

![ wanneer de bevestiging van de codekwaliteit wegens klantenkwesties ](/help/managing-code/assets/repository-webhook-gitlab4.png) ontbreekt

>[!TAB  Bitbucket ]

Wanneer de validatie van de codekwaliteit wordt uitgevoerd:

![ Status terwijl de bevestiging van de codekwaliteit ](/help/managing-code/assets/repository-webhook-bitbucket1.png) loopt

Gebruikt de status commit voor het volgen van voortgang van PR-validatie. In het volgende geval, toont het het schermschot wat gebeurt wanneer een bevestiging van de codekwaliteit wegens een klantenkwestie ontbreekt. Er wordt een opmerking toegevoegd met gedetailleerde foutinformatie en er wordt een commit check gemaakt, die de fout weergeeft (rechts zichtbaar):

![ Trek de status van de verzoekbevestiging voor Bitbucket ](/help/managing-code/assets/repository-webhook-bitbucket2.png)

>[!ENDTABS]

## Problemen met webhaken oplossen

* Zorg ervoor dat de Webhaak-URL een geldige API-sleutel bevat.
* Controleer of webhaakgebeurtenissen correct zijn geconfigureerd in de instellingen van uw Git-leverancier.
* Als de bevestiging van PR of pijpleidingstrekkers niet werken, verifieer dat het Geheime Geheime Web in zowel Cloud Manager als uw verkoper van het Git bijgewerkt is.