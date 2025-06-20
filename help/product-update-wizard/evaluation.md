---
title: Evaluatiefase
seo-title: Evaluation Phase
description: Leer hoe de evaluatiefase van de wizard Productupdates de upgradecomplexiteit met de patroondetector beoordeelt.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Evaluatiefase {#evaluation}

De eerste fase van de wizard Productupdates is de **[!UICONTROL Evaluation]** -fase. Het stelt patroondetector in werking binnen de tovenaar om verbeteringsingewikkeldheid te beoordelen. Aan het eind van deze stap, kunt u het evaluatieverslag bekijken.

Het rapport controleert de auteurinstantie op verbeteringsbereidheid door patronen voor het volgende te ontdekken:

* Overtredingen van regels op gebieden die door de upgrade worden beïnvloed of overschreven.
* Er worden AEM 6.x-functies of API&#39;s gebruikt die niet compatibel zijn met oudere versies en die na de upgrade kunnen worden verbroken.

Dit rapport helpt de ontwikkelingsinspanningen te ramen die nodig zijn om te upgraden naar Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Om meer over de patroondetector te leren, zie [ die de Complexiteit van de Verbetering met de Detector van het Patroon ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector) beoordelen.

## Voer het evaluatierapport uit {#running}

De patroondetector kan in elke omgeving worden uitgevoerd. Nochtans, om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, stelt Cloud Manager het op het opvoeren milieu van de auteursinstantie in werking.

**om het evaluatierapport in werking te stellen:**

1. Begin de tovenaar zoals die in het document [ wordt beschreven tovenaar van de Update van het Product ](/help/product-update-wizard/overview.md).

1. Klik op **[!UICONTROL Run Evaluation]**.

   ![ evaluatie van de Looppas ](/help/assets/Run-Evaluation.png)

1. De wizard informeert u over de status van uw handeling. Bericht **lopend** of **voltooide** zoals toepasselijk wanneer het evaluatierapport wordt geproduceerd.

1. Nadat het rapport is gegenereerd, kunt u op **[!UICONTROL Download report]** klikken om een kopie op te slaan.

   ![ gecreeerd Rapport ](/help/assets/Evaluation-1.png)

De huidige tovenaar van de Update van het Product in Cloud Manager steunt de **slechts fase van de Evaluatie**. De andere vier fasen namelijk **Vergoeding**, **Uitvoering**, **Bevestiging**, en **Voltooiing** komen binnenkort.
