---
title: Programma instellen
description: Na het instappen, moet de bedrijfseigenaar één of andere aanvankelijke opstelling van het programma doen.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# Programmainstelling {#program-setup}

Na het instappen, plaatst de bedrijfseigenaar opstelling het programma door een beschrijving toe te voegen en zeer belangrijke prestatiesindicatoren (KPIs) te bepalen. Deze KPI&#39;s worden vervolgens gebruikt voor het testen van de prestaties.

## Programmainstelling met [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Voer de volgende stappen uit om het programma in te stellen en KPI&#39;s te definiëren.

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com) en selecteer de juiste organisatie.

1. Klik **Programma van de Opstelling** om het opstellingsproces te beginnen.

   ![ programma van de Opstelling ](/help/assets/set-up-program/setup1.png)

1. In het **de dialoogvakje van het Programma van de Opstelling**, kunt u programmainformatie over drie lusjes ingaan:

   * **Algemeen**
   * **KPI**
   * **Levering**

1. Op het **Algemene** lusje, voeg een beschrijving voor uw programma toe en upload naar keuze een duimnagel door op **de Foto van de Verandering** te klikken.

   ![ Algemene tabel ](/help/assets/Setup_Program-General.png)

1. Voor **KPI** lusje, bepaal uw KPIs. In dit voorbeeld, wordt afzonderlijke KPIs bepaald voor **AEM Sites** en **AEM Assets**. Specificeer KPIs voor de producten die u vergunning hebt gegeven.

   Zie sectie [ KPIs ](#kpis) voor meer details over hoe KPIs in Cloud Manager wordt gemeten.

   ![ het bepalen KPIs ](/help/assets/Setup_Program-KPIs.png)

1. Op het **lusje van de Levering**, kunt u de het schrapen op bestelling opties voor uw milieu&#39;s bepalen als autoscaling voor uw programma wordt toegelaten.

   Autoscaling is alleen van toepassing op de productieomgeving en is mogelijk niet voor alle programma&#39;s van de klant beschikbaar.

   ![ de opties van de Levering ](/help/assets/Setup_Program-Provisioning.png)

1. Klik **sparen**.

Uw programma is gemaakt. Het kan enige minuten duren voordat de bronnen zijn ingericht voordat het programma klaar is voor gebruik.

## Een programma bewerken {#editing-program}

U kunt programma&#39;s bewerken nadat u ze hebt ingesteld. Voer de volgende stappen uit om een programma te bewerken.

1. Meld u aan bij Cloud Manager op [`https://my.cloudmanager.adobe.com` ](https://my.cloudmanager.adobe.com) en selecteer de juiste organisatie.

1. Navigeer naar het programma vanuit het Cloud Manager-beginscherm.

1. Klik **uitgeven programma** om uw programma van de **pagina van het Overzicht** bij te werken of te wijzigen.

   ![ geef programmaoptie ](/help/assets/set-up-program/edit-program1.png) uit

1. De **geeft de vertoningen van de de dialoog van het Programma** uit, toestaand u om uw programma bij te werken. Zie de sectie [ Opstelling van het Programma met Cloud Manager ](#program-setup-cloud-manager) voor details op de beschikbare gebieden.

   ![ geef programmadialoog ](/help/assets/set-up-program/edit-program-general.png) uit

1. Klik **Update** om uw veranderingen te bewaren.

De wijzigingen worden direct in Cloud Manager opgeslagen, maar worden pas in uw omgeving doorgevoerd wanneer de volgende pijpleiding wordt uitgevoerd.

Als u nog geen pijpleiding hebt gecreeerd, zie [ het Vormen de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ het Vormen niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md).

## Schakelen tussen programma&#39;s {#swithing-programs}

Wanneer u aan een programma werkt, kunt u snel overschakelen naar een ander programma zonder terug te keren naar de overzichtspagina van Cloud Manager.

Gebruik de actiebalk om naar een ander programma te schakelen, het huidige programma te bewerken of een nieuw programma toe te voegen.

![ de schakelaar van het Programma ](/help/assets/set-up-program/setup2.png)

## KPI&#39;s {#kpis}

De plaatsen KPIs wordt gemeten op tests die in het opvoeren milieu worden in werking gesteld. Doorgaans worden deze KPI&#39;s verkleind om ze aan te passen aan de mogelijkheden van de testomgeving.

Bijvoorbeeld, zou een gebruiker die een gemiddelde van 1000 paginameningen per minuut in hun productiemilieu verwacht, en vier Dispatcher/het publiceren servers in productie heeft, dit scenario aan 250 paginameningen per minuut moeten schrapen. In dit scenario wordt ervan uitgegaan dat hun testomgeving uit slechts één Dispatcher/publish-serverpaar bestaat.

Bij het testen van Assets-prestaties worden elementen gedurende 30 minuten herhaaldelijk geüpload. De verwerkingstijd voor elk element en de verschillende metingen op systeemniveau worden gedurende de hele test gemeten.

U kunt een netwerk van de inhoudslevering (CDN) zoals Akamai of CloudFront vóór uw productiemilieu hebben. Omdat [!UICONTROL Cloud Manager] tests tegen het het opvoeren milieu direct, KPI slechts op het verkeer zou moeten wijzen dat door CDN wordt verwacht over te gaan. Dat wil zeggen dat de cache ontbreekt. Deze ervaring is doorgaans een relatief kleine ondergroep van het totale productieverkeer.

## Video-overzicht {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
