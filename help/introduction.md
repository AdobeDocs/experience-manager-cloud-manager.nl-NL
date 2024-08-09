---
title: Inleiding tot Cloud Manager voor AMS
description: Begin hier om Cloud Manager for Adobe Managed Services (AMS) te leren kennen en hoe organisaties Adobe Experience Manager in de cloud kunnen beheren.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 3%

---


# Inleiding tot [!UICONTROL Cloud Manager] voor AMS {#introduction-to-cloud-manager}

Begin hier om Cloud Manager for Adobe Manage Services (AMS) te leren kennen en hoe organisaties Adobe Experience Manager in de cloud kunnen beheren.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Inleiding tot Cloud Manager voor AMS"
>abstract="Laat organisaties toe om Adobe Experience Manager in de wolk zelf te beheren. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Programma&#39;s maken"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Omgevingen maken"

## Inleiding {#introduction}

[!UICONTROL Cloud Manager] voor Adobe Experience Manager biedt ontwikkelaars de mogelijkheid om effectieve klantervaringen te maken via gestroomlijnde workflows, op basis van Adobe Experience Manager best practices. CI/CD pijpleidingen die voor Adobe Experience Manager worden geoptimaliseerd staan u toe om ontwikkelingswerkschema&#39;s gemakkelijk samen te voegen door uw code eenvoudig te controleren die dan helemaal tot productie-klaar kan bewegen. Tijdens de bouwstijlfase, worden uw updates van de douanecode grondig getest tegen beste praktijken om betrouwbare toepassingen voor uw klanten te leveren. Cloud Manager maakt gebruik van een open API-benadering en biedt u de mogelijkheid om uw systemen te integreren zonder bestaande processen en gereedschappen te onderbreken.

>[!NOTE]
>
>In deze documentatie worden specifiek de functies en functies van Cloud Manager for Adobe Managed Services (AMS) beschreven.
>
>De gelijkwaardige documentatie voor AEM as a Cloud Service kan in de [ documentatie van AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html) worden gevonden.

Met Cloud Manager profiteert uw ontwikkelingsteam van de volgende functies:

* Doorlopende integratie/doorlopende levering (CI/CD) van code om de tijd tot de markt te beperken van maanden/weken tot dagen/uren

* Codeinspectie, prestatietests en beveiligingsvalidatie op basis van best practices voordat u naar de productie gaat om productieonderbrekingen tot een minimum te beperken

* API-connectiviteit als aanvulling op bestaande DevOps-processen

* Autoscaling die intelligent de behoefte aan verhoogde capaciteit ontdekt en automatisch extra Dispatcher/het publiceren segmenten online brengt

Deze afbeelding illustreert de verwerkingsstroom CI/CD die wordt gebruikt in [!UICONTROL Cloud Manager]:

![ CI/CD stroom ](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Belangrijke functies in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Hieronder volgt een dieper overzicht van de belangrijkste functies van Cloud Manager.

### Self-Service Interface {#self-service-interface}

Met de gebruikersinterface (UI) voor [!UICONTROL Cloud Manager] hebt u eenvoudig toegang tot en beheer van de cloudomgeving en de CI/CD-pijplijn voor uw Adobe Experience Manager-toepassingen.

U definieert toepassingsspecifieke prestatiekernindicatoren (KPI&#39;s) (zoals piekpaginaweergaven per minuut en verwachte responstijd voor een paginabelasting) die de basis vormen voor het meten van een geslaagde implementatie. Rollen en machtigingen voor verschillende teamleden kunnen eenvoudig worden gedefinieerd. De zelfbedieningsinterface plaatst controle in uw handen, maar het biedt ook verbindingen aan beste praktijkmiddelen en toegang tot deskundigen binnen Adobe aan die de noodzakelijke begeleiding kunnen verstrekken zoals nodig.

Om te onderzoeken en begonnen te worden met [!UICONTROL Cloud Manager]&#39;s UI, zie het document [ Eerste Login van de Tijd ](/help/getting-started/first-time-login.md).

### CI/CD Pipet {#ci-cd-pipeline}

Een van de belangrijkste mogelijkheden van [!UICONTROL Cloud Manager] is de mogelijkheid om een geoptimaliseerde CI/CD-pijpleiding uit te voeren om de levering van aangepaste code of updates te versnellen, zoals het toevoegen van nieuwe componenten op de website.

Via de interface van [!UICONTROL Cloud Manager] kunt u de I/CD-pijpleiding configureren en afschoppen. Als deel van deze pijpleiding, wordt een grondig codescannen uitgevoerd om ervoor te zorgen dat slechts de toepassingen van uitstekende kwaliteit door aan het productiemilieu overgaan.

Meer leren over het vormen van pijpleiding van [!UICONTROL Cloud Manager] UI, zie de documenten [ het Vormen de Pijpleidingen van de Productie ](/help/using/production-pipelines.md) en [ het Vormen niet-Productiepijpleidingen ](/help/using/non-production-pipelines.md).

### Flexibele implementatiemodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] biedt flexibele en configureerbare implementatiemodi, zodat u ervaringen kunt bieden op basis van veranderende bedrijfsbehoeften.

Met een automatische trekkerwijze, wordt de code automatisch opgesteld aan een milieu dat op specifieke gebeurtenissen zoals code wordt gebaseerd begaat. U kunt codeplaatsingen tijdens gespecificeerde tijdkaders, zelfs buiten kantooruren ook plannen.

Onafhankelijk van de plaatsingstrekker, worden de kwaliteitscontroles altijd uitgevoerd als deel van CI/CD pijpleiding uitvoering telkens als een plaatsing wordt teweeggebracht. De controles van de kwaliteit omvatten, code inspectie, veiligheidstests, en prestaties het testen, allen die uit de doos zonder inspanning worden geleverd van u of uw partners wordt vereist.

Meer leren over het opstellen van code en kwaliteitscontroles, zie het document [ Opstellend Code ](/help/using/code-deployment.md).

## Optionele functies in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager biedt extra, geavanceerde functies die gunstig kunnen zijn voor uw project, afhankelijk van de instellingen en behoeften van uw specifieke omgeving. Als deze functies u interesseren, kunt u contact opnemen met uw Customer Success Engineer (CSE) of Adobe vertegenwoordiger om verder te bespreken.

### Automatisch schalen {#autoscaling}

Wanneer de productieomgeving te maken heeft met een ongewoon hoge belasting, detecteert [!UICONTROL Cloud Manager] de behoefte aan extra capaciteit en wordt automatisch extra capaciteit online beschikbaar via de functie voor automatisch schalen.

In een dergelijke gebeurtenis activeert [!UICONTROL Cloud Manager] automatisch het inrichtingsproces voor automatisch schalen, wordt een melding van de gebeurtenis voor automatisch schalen verzonden en wordt binnen enkele minuten extra capaciteit online gezet. De extra capaciteit wordt geleverd in de productieomgeving, in dezelfde regio of regio&#39;s en overeenkomstig dezelfde systeemspecificaties als de lopende Dispatcher/publicatieknooppunten.

De functie voor automatisch schalen is alleen van toepassing op de Dispatcher-/publicatielaag en wordt uitgevoerd met een horizontale schaalmethode, met minimaal één extra segment van een Dispatcher-/publicatiepaar tot maximaal tien segmenten. Eventuele extra capaciteit die wordt geleverd, wordt handmatig geschaald binnen een periode van tien werkdagen, zoals bepaald door de CSE (Customer Success Engineer).

>[!NOTE]
>
>Neem contact op met uw CSE of Adobe als u wilt weten of autoscaling geschikt is voor uw toepassing.

### Blauwe/groene implementaties {#blue-green}

Blauwe/groene implementatie is een techniek die downtime en risico&#39;s vermindert door twee identieke productieomgevingen uit te voeren, die blauw en groen worden genoemd.

Op elk ogenblik, is slechts één van de milieu&#39;s levend, met het levende milieu dat al productieverkeer dient. Over het algemeen is blauw de huidige live omgeving en groen is inactief.

* Blauwe/groene implementatie is een invoegtoepassing voor Cloud Manager CI/CD-pijpleidingen waarin een tweede verzameling publicatie- en Dispatcher-instanties (groen) wordt gemaakt en gebruikt voor implementaties. De groene instanties worden vervolgens gekoppeld aan het taakverdelingsmechanisme voor de productie en de oude (blauwe) exemplaren worden verwijderd en beëindigd.
* Deze implementatie van blauw/groen behandelt instanties als transient en elke herhaling van een blauwe/groene pijpleiding zal tot een nieuwe reeks publiceren en Dispatcher servers leiden.
* Als onderdeel van de installatie wordt een groene taakverdelingsmechanisme gemaakt. Dit taakverdelingsmechanisme wordt nooit gewijzigd en verwijst naar de groene of &quot;test&quot;-URL.
* Tijdens een blauwe/groene implementatie wordt een exacte replica van de bestaande publiceer-/Dispatcher-lagen gemaakt.

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

Alle AMS-gebruikers die Cloud Manager gebruiken voor productieimplementaties, kunnen gebruikmaken van een blauwe/groene implementatie. Het gebruik van een blauw/groene implementatie vereist echter extra validatie van uw omgevingen en installatie door een Adobe-CSE.

Als u in blauwe/groene plaatsing geinteresseerd bent, overweeg de volgende vereisten en de beperkingen en contacteer uw CSE.

#### Eisen en beperkingen {#limitations}

* Blauw/groen is alleen beschikbaar voor publicatie/Dispatcher-paren.
* Voorvertoning van Dispatcher/publicatieparen maakt geen deel uit van blauw/groene implementaties.
* Elk Dispatcher/publicatiepaar is identiek aan elk ander Dispatcher/publicatiepaar.
* Blauw/groen is alleen beschikbaar in de productieomgeving.
* Blauw/groen is beschikbaar in AWS en Azure.
* Blauw/groen is niet alleen beschikbaar voor klanten van Assets.
