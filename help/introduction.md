---
title: Inleiding tot Cloud Manager voor AMS
description: Begin hier om Cloud Manager for Adobe Managed Services (AMS) te leren kennen en hoe organisaties Adobe Experience Manager in de cloud kunnen beheren.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '1232'
ht-degree: 3%

---


# Inleiding tot [!UICONTROL Cloud Manager] voor AMS {#introduction-to-cloud-manager}

Begin hier om Cloud Manager for AMS (Adobe Managed Services) te leren kennen en hoe organisaties Adobe Experience Manager in de cloud kunnen beheren.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Inleiding tot Cloud Manager voor AMS"
>abstract="Laat organisaties toe om Adobe Experience Manager in de wolk zelf te beheren. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Programma&#39;s maken"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Omgevingen maken"

## Inleiding {#introduction}

[!UICONTROL Cloud Manager] voor Adobe Experience Manager biedt ontwikkelaars de mogelijkheid om effectieve klantervaringen te maken via gestroomlijnde workflows, op basis van Adobe Experience Manager best practices. Met CI-/CD-pijpleidingen die voor Adobe Experience Manager zijn geoptimaliseerd, kunt u ontwikkelworkflows eenvoudig samenvoegen door uw code eenvoudig in te checken. Deze kunnen dan volledig worden verplaatst naar productieklaar. Tijdens de bouwstijlfase, worden uw updates van de douanecode grondig getest tegen beste praktijken om betrouwbare toepassingen voor uw klanten te leveren. Cloud Manager maakt gebruik van een open API-benadering en biedt u de mogelijkheid om uw systemen te integreren zonder bestaande processen en gereedschappen te onderbreken.

>[!NOTE]
>
>In deze documentatie worden specifiek de functies en functies van Cloud Manager for Adobe Managed Services (AMS) beschreven.
>
>De gelijkwaardige documentatie voor AEM as a Cloud Service kan in de [ documentatie van AEM as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home) worden gevonden.

Met Cloud Manager profiteert uw ontwikkelingsteam van de volgende functies:

* Doorlopende integratie/doorlopende levering (CI/CD) van code om de tijd tot de markt te beperken van maanden/weken tot dagen/uren.

* Codeinspectie, prestatietests en beveiligingsvalidatie op basis van best practices voordat u naar de productie gaat om productieonderbrekingen tot een minimum te beperken.

* API-connectiviteit als aanvulling op bestaande DevOps-processen.

* Autoscaling die intelligent de behoefte aan verhoogde capaciteit ontdekt en automatisch extra Dispatcher/het publiceren segmenten online brengt.

![ CI/CD stroom ](/help/assets/screen_shot_2018-05-12at73843pm.png) de CI/CD processtroom die in [!UICONTROL Cloud Manager] wordt gebruikt.

## Belangrijke functies in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Hieronder volgt een dieper overzicht van de belangrijkste functies van Cloud Manager.

### Self-service interface {#self-service-interface}

Met de gebruikersinterface (UI) voor [!UICONTROL Cloud Manager] hebt u eenvoudig toegang tot de cloud-omgeving en kunt u de CI/CD-pijplijn eenvoudig beheren voor uw Adobe Experience Manager-toepassingen.

U definieert toepassingsspecifieke prestatie-indicatoren (KPI&#39;s), zoals piekpaginaweergaven per minuut of verwachte responstijd voor paginabelasting. Deze KPIs fungeert als de basis voor het meten van het succes van plaatsing. Rollen en machtigingen voor verschillende teamleden kunnen eenvoudig worden gedefinieerd. De zelfbediening interface geeft u volledige controle. Het biedt ook koppelingen naar middelen voor beste praktijken en toegang tot Adobe-experts als dat nodig is.

Om te onderzoeken en begonnen te worden met [!UICONTROL Cloud Manager]&#39;s UI, zie [ Eerste Login van de Tijd ](/help/getting-started/first-time-login.md).

### Cd-pijpleiding {#ci-cd-pipeline}

Een van de belangrijkste mogelijkheden van [!UICONTROL Cloud Manager] is de mogelijkheid om een geoptimaliseerde CI/CD-pijpleiding uit te voeren om de levering van aangepaste code of updates te versnellen, zoals het toevoegen van nieuwe componenten op de website.

Via de interface van [!UICONTROL Cloud Manager] kunt u de I/CD-pijpleiding configureren en afschoppen. Als deel van deze pijpleiding, wordt een grondig codescannen uitgevoerd om ervoor te zorgen dat slechts de toepassingen van uitstekende kwaliteit door aan het productiemilieu overgaan.

Meer leren over het vormen van pijpleiding van [!UICONTROL Cloud Manager] UI, zie [ het Vormen de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ het Vormen niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md).

### Flexibele implementatiemodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] biedt flexibele en configureerbare implementatiemodi, zodat u ervaringen kunt bieden op basis van veranderende bedrijfsbehoeften.

Met een automatische trekkerwijze, wordt de code automatisch opgesteld aan een milieu dat op specifieke gebeurtenissen zoals code wordt gebaseerd begaat. U kunt codeplaatsingen tijdens gespecificeerde tijdkaders, zelfs buiten kantooruren ook plannen.

Onafhankelijk van de plaatsingstrekker, worden de kwaliteitscontroles altijd uitgevoerd als deel van CI/CD pijpleiding uitvoering telkens als een plaatsing wordt teweeggebracht. De controles van de kwaliteit omvatten code inspectie, veiligheidstests, en prestaties het testen, allen die uit-van-de-doos zonder inspanning worden geleverd van u of uw partners wordt vereist.

Meer leren over het opstellen van code en kwaliteitscontroles, zie [ het Opstellen van Code ](/help/using/code-deployment.md).

## Optionele functies in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager biedt extra, geavanceerde functies die gunstig kunnen zijn voor uw project, afhankelijk van de instellingen en behoeften van uw specifieke omgeving. Als deze functies u interesseren, kunt u contact opnemen met uw Customer Success Engineer (CSE) of Adobe vertegenwoordiger om verder te bespreken.

### Automatisch schalen {#autoscaling}

Wanneer de productieomgeving te maken heeft met een ongewoon hoge belasting, detecteert [!UICONTROL Cloud Manager] de behoefte aan extra capaciteit en wordt automatisch extra capaciteit online beschikbaar via de functie voor automatisch schalen.

In een dergelijke gebeurtenis activeert [!UICONTROL Cloud Manager] automatisch het inrichtingsproces voor automatisch schalen, wordt een melding van de gebeurtenis voor automatisch schalen verzonden en wordt binnen enkele minuten extra capaciteit online gezet. De extra capaciteit wordt geleverd in de productieomgeving, in dezelfde regio&#39;s, en in overeenstemming met dezelfde systeemspecificaties als de lopende Dispatcher/publicatieknooppunten.

De functie voor automatisch schalen is van toepassing op de Dispatcher-/publicatielaag. Hierbij wordt horizontale schaling gebruikt om een tot tien segmenten van Dispatcher-/publicatieparen toe te voegen. Eventuele extra capaciteit die wordt geleverd, wordt handmatig geschaald binnen een periode van tien werkdagen, zoals bepaald door de CSE van de Adobe (Customer Success Engineer).

>[!NOTE]
>
>Neem contact op met uw CSE of Adobe als u wilt weten of autoscaling geschikt is voor uw toepassing.

### Blauwe/groene implementaties {#blue-green}

Blauwe/groene implementatie is een techniek die downtime en risico&#39;s vermindert door twee identieke productieomgevingen uit te voeren, die blauw en groen worden genoemd.

Op elk ogenblik, is slechts één van de milieu&#39;s levend, met het levende milieu dat al productieverkeer dient. Over het algemeen is blauw de huidige live omgeving en groen is inactief.

* Blauwe/groene implementatie is een invoegtoepassing voor Cloud Manager CI/CD-pijpleidingen waarin een tweede verzameling publicatie- en Dispatcher-instanties (groen) wordt gemaakt en gebruikt voor implementaties. De groene instanties worden vervolgens gekoppeld aan het taakverdelingsmechanisme voor productie en de oude (blauwe) instanties worden verwijderd en beëindigd.
* Deze implementatie van blauw/groen behandelt instanties als voorbijgaand en elke herhaling van een blauwe/groene pijpleiding leidt tot een nieuwe reeks publiceren en Dispatcher servers.
* Er wordt een groene taakverdelingsmechanisme gemaakt als onderdeel van de installatie. Dit taakverdelingsmechanisme verandert nooit en is wat u uw groene of &quot;test&quot;URL aan zou moeten richten.
* Tijdens een blauw/groene implementatie wordt een exacte replica van de bestaande Dispatcher/publicatieniveaus gemaakt.

#### Blauwe/groene implementatiestroom {#flow}

Wanneer de blauwe/groene plaatsing wordt toegelaten, verschilt de plaatsingsstroom van de standaard Cloud Service plaatsingsstroom.

| Stap | Blauwe/groene implementatie | Standaardimplementatie |
|---|---|---|
| 1 | Implementatie aan auteur | Implementatie aan auteur |
| 2 | Onderbreken voor testen | - |
| 3 | Groene infrastructuur wordt gemaakt | - |
| 4 | Implementatie in groene publicatie-/verzendingslagen | Implementatie aan uitgever |
| 5 | Onderbreken voor testen (maximaal 24 uur) | - |
| 6 | Groene infrastructuur wordt toegevoegd aan het taakverdelingsmechanisme voor productie | - |
| 7 | Blauwe infrastructuur wordt verwijderd uit het productietraagtaakverdelingsmechanisme- |
| 8 | Pauzeren voor afmelding (maximaal 24 uur) | - |
| 9 | Blauwe infrastructuur wordt automatisch beëindigd | - |
| 10 | Pipet voltooid | - |

#### Blauw/groen implementeren {#implementing}

Alle AMS-gebruikers die Cloud Manager gebruiken voor productieimplementaties, kunnen de blauw/groene implementatie gebruiken. Het gebruik van een blauw/groene implementatie vereist echter extra validatie van uw omgevingen en installatie door een Adobe-CSE.

Als u in blauwe/groene plaatsing geinteresseerd bent, overweeg de volgende vereisten en de beperkingen en contacteer uw CSE.

#### Vereisten en beperkingen {#limitations}

* Blauw/groen is alleen beschikbaar voor Dispatcher/uitgeversparen.
* Voorvertoning van Dispatcher/publicatieparen maakt geen deel uit van blauw/groene implementaties.
* Elk Dispatcher/publicatiepaar is identiek aan elk ander Dispatcher/uitgeverspaar.
* Blauw/groen is alleen beschikbaar in de productieomgeving.
* Blauw/groen is beschikbaar in AWS en Azure.
* Blauw/groen is niet beschikbaar voor klanten met alleen Assets.
