---
title: Evaluatiefase
seo-title: Evaluation Phase
description: Leer hoe de evaluatiefase van de wizard Productupdates de upgradecomplexiteit met de patroondetector beoordeelt.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Evaluatiefase {#evaluation}

De eerste fase in de wizard Productupdates is de **[!UICONTROL Evaluation]** -fase, die de complexiteit van de upgrade rechtstreeks met de patroondetector in de wizard evalueert. Aan het eind van deze stap, kunt u tot het evaluatierapport toegang hebben.

Met het gegenereerde rapport kunt u controleren of de auteur in aanmerking komt voor een upgrade door de volgende patronen te detecteren:

* Breek bepaalde regels betreffende gebieden die door de upgrade worden beïnvloed of overschreven.

* Gebruik een AEM 6.x-functie of een API die niet achterwaarts compatibel is met de nieuwe versie van AEM en die na een upgrade mogelijk kan worden onderbroken.

Het verslag dient als een beoordeling van de ontwikkelingsinspanningen die gepaard gaan met de opwaardering tot Adobe Experience Manager (AEM) 6.5.

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

De huidige versie van de tovenaar van de Update van het Product in Cloud Manager steunt de **slechts fase van de Evaluatie**. De andere vier fasen namelijk **Vergoeding**, **Uitvoering**, **Bevestiging**, en **Voltooiing** komen binnenkort.
