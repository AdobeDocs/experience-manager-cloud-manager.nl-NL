---
title: Een productiepijpleiding toevoegen
description: Leer hoe u Cloud Manager kunt gebruiken om productiepijpleidingen te maken en te configureren om uw code te implementeren.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 0%

---


# Een productiepijplijn toevoegen {#configuring-production-pipelines}

Leer hoe u Cloud Manager kunt gebruiken om productiepijpleidingen te maken en te configureren om uw code te implementeren. Als u eerst een meer conceptueel overzicht van zou houden hoe de pijpleidingen in Cloud Manager werken, zie [ CI/CD Pijpleidingen ](/help/overview/ci-cd-pipelines.md).

## Overzicht {#overview}

Gebruikend de **tegel van de Montages van de Pijpleiding** {in [!UICONTROL Cloud Manager] kunt u twee verschillende soorten pijpleidingen tot stand brengen.

* **de Pijpleidingen van de Productie** - De productiepijpleidingen van A zijn een doelgerichte pijpleiding die van een reeks georkestreerde stappen wordt gemaakt om broncode van uw bewaarplaats van het Git helemaal in productie te nemen.
* **niet-Productiepijpleidingen** - een niet productiepijplijn dient hoofdzakelijk code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

Dit document richt zich op productiepijpleidingen. Voor details op hoe te om niet-productiepijpleidingen te vormen zie het document [ Vormend niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md).

De **rol van de Manager van de Plaatsing** is verantwoordelijk voor vestiging de pijpleiding. Configuratie van pijpleidingen bestaat uit:

1. Het bepalen van de trekker die de pijpleiding begint.
1. De parameters definiëren die de productieimplementatie bepalen.
1. De testparameters voor prestaties configureren.

>[!NOTE]
>
>Een pijpleiding kan niet opstelling zijn tot zijn bijbehorende bewaarplaats van het Git minstens één tak heeft en [ programmaopstelling ](/help/getting-started/program-setup.md) is volledig.

## Een nieuwe productiepijplijn toevoegen {#adding-production-pipeline}

Nadat u de gebruikersinterface van [!UICONTROL Cloud Manager] hebt gebruikt om uw programma in te stellen en minstens één omgeving hebt, kunt u een productiepijplijn toevoegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma**.

1. Klik **+ toevoegen**, dan uitgezocht **voeg de Pijpleiding van de Productie** toe.

   ![ voeg een productiepijpleiding ](/help/assets/configure-pipelines/add-prod1.png) toe

1. **voeg de dialoogdoos van de Pijpleiding van de Productie toe** aan het **3} lusje van de Configuratie {opent waar een aantal opties voor uw pijpleiding moet worden bepaald.** Deze opties zijn gegroepeerd in inklapbare secties en worden in de volgende stappen beschreven.

   1. Verstrek een beschrijvende naam voor uw pijpleiding op het **gebied van de Naam van de Pijpleiding**.

   1. Onder de **sectie van de Code van Source**, bepaalt u waar de pijpleiding de code terugwint het verwerkt.

      * **Bewaarplaats** - bepaalt welke repo van het Git de pijpleiding de code zou moeten terugwinnen.

      >[!TIP]
      >
      >Zie het document [ Opstelling van het Programma ](/help/getting-started/program-setup.md) leren hoe te om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

      * **Tak van het Git** - bepaalt waarvan de tak in de geselecteerde pijpleiding de code zou moeten terugwinnen.
      * **Plaats van de Code** - bepaalt de weg in de tak van de geselecteerde repo waarvan de pijpleiding de code zou moeten terugwinnen.

      ![ bepalen repos voor de pijpleiding ](/help/assets/configure-pipelines/add-prod2.png)

   1. Onder de **sectie van Milieu&#39;s**, bepaalt u wat een plaatsing teweegbrengt en hoe het per milieu zou moeten worden uitgerold.

      1. In de **sectie van het STADIUM**, kunt u bepalen hoe de pijpleiding uit aan uw het opvoeren milieu rolt.

         * **Trigger van de Plaatsing** - u hebt de volgende opties om de plaatsingstrekkers te bepalen om de pijpleiding te beginnen.

            * **Handboek** - Begin manueel de pijpleiding gebruikend Cloud Manager UI.
            * **op de Veranderingen van het Git** - Begin de pijpleiding CI/CD wanneer de bedenkingen aan de gevormde tak van het Git worden toegevoegd. Met deze optie, kunt u de pijpleiding nog manueel zoals vereist beginnen.

         * **Belangrijk Metrisch Gedrag van Mislukt** - tijdens pijpleidingsopstelling of geef uit, heeft de Manager van de Plaatsing de optie om het gedrag van de pijpleiding te bepalen wanneer een belangrijke mislukking in om het even welke kwaliteitspoorten wordt ontmoet. De beschikbare opties zijn:

            * **vraag telkens** - het gebrek dat en vereist handinterventie op om het even welke belangrijke mislukking plaatst.
            * **onmiddellijk het Eindigen** - de pijpleiding wordt geannuleerd wanneer een belangrijke mislukking voorkomt. Het emuleert een gebruiker handmatig elke fout af.
            * **gaat onmiddellijk** voort - de pijpleiding gaat automatisch wanneer een belangrijke mislukking voorkomt. Het emuleert een gebruiker handmatig die elke fout goedkeurt.

         ![ trekker van de Plaatsing ](/help/assets/configure-pipelines/add-prod3.png)

         * **Opties van de Plaatsing** - u kunt bepaalde plaatsingstaken versnellen.

            * **keur na de Plaatsing van het Stadium** goed - Deze goedkeuring komt na plaatsing aan het opvoeren milieu voor alvorens om het even welk testen wordt gedaan. Anders vindt goedkeuring plaats voordat de productie wordt geïmplementeerd, wat gebeurt nadat alle tests zijn voltooid.

            * **overslaan de veranderingen van de Balancer van de Lading** - de veranderingen van het balanceerhulpmiddel van de Lading worden niet aangebracht.

         ![ het Staging plaatsingsopties ](/help/assets/configure-pipelines/add-prod4.png)

         * **de Configuratie van Dispatcher** - de **rol van de Manager van de Plaatsing** kan een reeks inhoudspaden vormen die of ongeldig of uit het geheime voorgeheugen van AEM Dispatcher worden gespoeld wanneer een pijpleiding in werking wordt gesteld. Deze geheim voorgeheugenacties worden uitgevoerd als deel van de stap van de plaatsingspijpleiding, enkel nadat om het even welke inhoudspakketten worden opgesteld. Bij deze instellingen wordt standaard AEM Dispatcher-gedrag gebruikt. Voer de volgende handelingen uit om te configureren:

            1. Onder **PAD** verstrekt een inhoudspad.
            1. Onder **TYPE**, selecteer de actie die op die weg moet worden genomen.

               * **Flush** - voer een geheim voorgeheugenschrapping uit.
               * **ongeldig maakt** ongeldig - voer een geheim voorgeheugenbevestiging uit, gelijkend op wanneer de inhoud van een auteursinstantie aan een het publiceren instantie wordt geactiveerd.

            1. Klik **toevoegen Weg** om uw gespecificeerde weg toe te voegen. U kunt maximaal 100 paden per omgeving toevoegen.

         ![ de configuratie van Dispatcher ](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Over het algemeen verdient het de voorkeur de actie voor invalideren te gebruiken, maar er kunnen zich gevallen voordoen waarin flushing vereist is, met name bij gebruik van AEM Client Libraries voor HTML.

      1. In de **sectie van de PRODUCTIE**, kunt u bepalen hoe de pijpleiding uit aan uw productiemilieu voortkomt.

         * **Opties van de Plaatsing** - u kunt de parameters bepalen die de productieleiding controleren.

            * **het Gebruik gaat Levende Goedkeuring** - een gebruiker met **BedrijfsEigenaar**, **de Manager van het Project**, of **de rol van de Manager van de Plaatsing** als [!UICONTROL Cloud Manager] UI moet manueel een plaatsing goedkeuren.
            * **Gepland** - Stopt de pijpleiding vóór productieleiding om het toe te laten om worden gepland. Als deze optie wordt geselecteerd, stopt de pijpleiding na plaatsing aan het opvoeren milieu en vraagt de gebruiker op de te nemen actie.
               * **`Now`** - Implementeert onmiddellijk en voltooit de pijplijn.
               * **Datum** - laat het gebruikersprogramma een tijd wanneer de plaatsing zou moeten worden voltooid.
               * **Uitvoering van het Einde** - borst plaatsing aan productie.

           >[!TIP]
           >
           >Zie ](/help/using/code-deployment.md) de Plaatsing van de Code van 0} om te leren hoe te om het plaatsingsprogramma te plaatsen of de pijpleiding onmiddellijk uit te voeren.[

            * **Het Toezicht CSE van het Gebruik** - als deze optie wordt geselecteerd, is een CSE (de Ingenieur van het Succes van de Klant) betrokken om de daadwerkelijke plaatsing te beginnen. Wanneer het creëren van of het uitgeven van een pijpleiding wanneer deze optie wordt toegelaten, heeft de **rol van de Manager van de Plaatsing** de volgende opties.

               * **Om het even welke CSE** - staat om het even welke beschikbare CSE toe om de plaatsing te beginnen.
               * **Mijn CSE** - staat slechts specifieke CSE toe die aan de klant wordt toegewezen om de plaatsing te beginnen. Deze optie is ook van toepassing voor de aangewezen steun van CSE als toegewezen CSE niet beschikbaar is.

           ![ de plaatsingsopties van de Productie ](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuratie van Dispatcher** - bepaal de configuratie van Dispatcher voor uw productiemilieu. De opties zijn hetzelfde als de opties voor de testomgeving.

1. Klik **verdergaan** aan het **Testen van het Stadium** lusje vooruit waar u het Testen van Prestaties van AEM Sites en van AEM Assets kunt vormen, afhankelijk van welke producten u vergunning hebt gegeven.

   >[!TIP]
   >
   >Zie [ het Testen van de Kwaliteit van de Code ](/help/using/code-quality-testing.md#performance-testing) voor meer details over de opties beschikbaar op het **Testen van het Stadium** tabel.

   1. In de **sectie van het Gewicht van de Inhoudslevering van Plaatsen/Verspreid van de Lading**, vormt u het Testen van de plaatsPrestaties die op de weging van paginaverzoeken onder drie paginasets wordt gebaseerd. U kunt de paginasets desgewenst in- of uitschakelen.

      * **Populaire Levende Pagina&#39;s**
      * **Andere Levende Pagina&#39;s**
      * **Nieuwe Pagina&#39;s**

      ![ het ladingsgewicht van Plaatsen ](/help/assets/configure-pipelines/add-prod5.png)

   1. Onder de **het Testen van Prestaties van Assets** sectie, bepaalt u de testdistributie van beelden en PDF en bepaalt uw eigen testactiva.

      * **Beelden** - pas de schuif aan om de testspleet tussen beelden en PDF aan te passen.
      * **PDF** - pas de schuif aan om de testspleet tussen beelden en PDF aan te passen.

      * Definieer uw eigen aangepaste elementen door deze te uploaden.

         1. **FORMAAT** - verkies of uw douanemiddel een PDF van een beeld is.
         1. **BESTANDSNAAM** - gebruik de knoop van dossierbrowser om een beeld van uw lokale machine te selecteren.
         1. **voeg het Dossier van de Test** toe - klik om uw geselecteerde activa te uploaden.

      ![ Assets testende distributie ](/help/assets/configure-pipelines/add-prod6.png)

1. Klik **sparen** om het toevoegen van uw productiepijplijn te voltooien.

## De volgende stappen {#the-next-steps}

Nadat u de pijpleiding hebt gevormd, stelt u uw code op. Zie [ Plaatsing van de Code ](/help/using/code-deployment.md) voor meer details.

## Videozelfstudie {#video-tutorial-one}

Deze video biedt een overzicht van het proces voor het maken van pijpleidingen, dat in dit document wordt beschreven.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
