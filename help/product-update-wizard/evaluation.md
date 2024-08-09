---
title: Evaluatiefase
seo-title: Evaluation Phase
description: Leer hoe de de evaluatiefase van de Tovenaar van de Update van het Product de verbeteringsingewikkeldheid met de patroondetector beoordeelt.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Evaluatiefase {#evaluation}

De eerste fase in de wizard Productupdates is **[!UICONTROL Evaluation]** -fase, waarin de complexiteit van de upgrade wordt beoordeeld aan de hand van de patroondetector rechtstreeks in de wizard. Aan het einde van deze stap hebt u toegang tot een evaluatierapport.

Met het gegenereerde rapport kunt u controleren of de auteurinstantie geschikt is voor upgrades door patronen te detecteren die:

* Overtreed bepaalde regels betreffende gebieden die door de upgrade worden beïnvloed of overschreven.

* Gebruik een AEM 6.x-functie of een API die niet achterwaarts compatibel is met de nieuwe versie van AEM en die na de upgrade mogelijk kan worden onderbroken.

Het verslag dient als een beoordeling van de ontwikkelingsinspanningen die gepaard gaan met de opwaardering tot Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Om meer over patroondetector te leren, zie [ die de Complexiteit van de Verbetering met de Detector van het Patroon ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en) beoordelen.

## De evaluatie uitvoeren {#running}

De patroondetector kan in elke omgeving worden uitgevoerd. Nochtans, om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, zal Cloud Manager het op het opvoeren milieu van de auteursinstantie in werking stellen.

Voer de volgende stappen uit om het evaluatieverslag te genereren.

1. Begin de tovenaar zoals die in het document [ wordt beschreven tovenaar van de Update van het Product ](/help/product-update-wizard/overview.md).

1. Klik op **[!UICONTROL Run Evaluation]** .

   ![ evaluatie van de Looppas ](/help/assets/Run-Evaluation.png)

1. De wizard informeert u over de status van uw handeling. U zult **in uitvoering** of **voltooide** zoals toepasselijk merken wanneer het evaluatierapport wordt geproduceerd.

1. Nadat het rapport is gegenereerd, kunt u op **[!UICONTROL Download report]** klikken om een kopie op te slaan.

   ![ gecreeerd Rapport ](/help/assets/Evaluation-1.png)

De huidige versie van de tovenaar van de Update van het Product in Cloud Manager steunt de **slechts fase van de Evaluatie**. De andere vier fasen namelijk **Vergoeding**, **Uitvoering**, **Bevestiging**, en **Voltooiing** komen binnenkort.
