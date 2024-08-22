---
title: Maven Project Version Handling
description: Leer hoe Maven projectversioning in Cloud Manager afhandelt.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Afhandeling van gemaakte projectversie {#project-version}

Leer hoe Maven projectversioning in Cloud Manager afhandelt.

## Hoe Maven projectversies afhandelt {#how-maven}

Cloud Manager genereert voor staging- en productieimplementaties een unieke, incrementele versie.

Deze versie wordt gezien op de pagina van de details van de pijpleidingsuitvoering en de activiteitenpagina. Wanneer een bouwstijl in werking wordt gesteld, wordt het Maven project bijgewerkt om deze versie te gebruiken. Er wordt een tag gemaakt in de Git-opslagplaats met die versie als naam.

Als de oorspronkelijke projectversie aan bepaalde criteria voldoet, voegt de bijgewerkte versie van het Maven-project zowel de oorspronkelijke projectversie als de door Cloud Manager gegenereerde versie samen. De tag gebruikt echter altijd de gegenereerde versie. Deze samenvoeging vindt pas plaats wanneer de oorspronkelijke projectversie is samengesteld met precies drie versiesegmenten, bijvoorbeeld `1.0.0` of `1.2.3` , maar niet `1.0` of `1` , en de oorspronkelijke versie mag niet eindigen in `-SNAPSHOT` .

>[!NOTE]
>
>Deze oorspronkelijke versiewaarde van het project moet statisch worden ingesteld in het `<version>` -element van het `pom.xml` -bestand op hoofdniveau in de vertakking van de Git-opslagplaats.

Als de originele versie aan deze criteria voldoet, dan wordt de geproduceerde versie toegevoegd aan de originele versie als nieuw versiesegment. De gegenereerde versie is ook enigszins gewijzigd en bevat nu de juiste sortering en versiebeheer. Stel bijvoorbeeld dat u een gegenereerde versie van `2019.926.121356.0000020490` gebruikt:

| Versie | Versie in `pom.xml` | Opmerking |
| --- | --- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Oorspronkelijke versie met de juiste indeling |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Opnameversie, overschreven |
| `1` | `2019.926.121356.0000020490` | Onvolledige versie, overschreven |

>[!NOTE]
>
>Of de oorspronkelijke versie al dan niet is geïntegreerd in de Cloud Manager-geïnitialiseerde versie, deze is nog steeds toegankelijk als een Maven-eigenschap met de naam `cloudManagerOriginalVersion` .
