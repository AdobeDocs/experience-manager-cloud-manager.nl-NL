---
title: Maven Project Version Handling
description: Leer hoe Maven projectversioning in Cloud Manager afhandelt.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# Maven Project Version Handling {#project-version}

Leer hoe Maven projectversioning in Cloud Manager afhandelt.

## Hoe Maven projectversies afhandelt {#how-maven}

Cloud Manager genereert voor staging- en productieimplementaties een unieke, incrementele versie.

Deze versie wordt gezien op de pagina van de details van de pijpleidingsuitvoering en de activiteitenpagina. Wanneer een bouwstijl in werking wordt gesteld, wordt het Maven project bijgewerkt om deze versie te gebruiken en een markering wordt gecreeerd in de git bewaarplaats met die versie als zijn naam.

Als de oorspronkelijke projectversie aan bepaalde criteria voldoet, voegt de bijgewerkte versie van het Maven-project zowel de oorspronkelijke projectversie als de door Cloud Manager gegenereerde versie samen. De tag gebruikt echter altijd de gegenereerde versie. Deze samenvoeging vindt pas plaats wanneer de oorspronkelijke projectversie is samengesteld met precies drie versiesegmenten, bijvoorbeeld `1.0.0` of `1.2.3` , maar niet `1.0` of `1` , en de oorspronkelijke versie mag niet eindigen in `-SNAPSHOT` .

>[!NOTE]
>
>Deze oorspronkelijke waarde voor de projectversie moet statisch worden ingesteld in het `<version>` -element van het bestand op hoofdniveau `pom.xml` in de vertakking van de it-opslagplaats.

Als de originele versie aan deze criteria voldoet, zal de geproduceerde versie aan de originele versie als nieuw versiesegment worden toegevoegd. De gegenereerde versie wordt ook enigszins aangepast, zodat de versie correct wordt gesorteerd en verwerkt. Stel bijvoorbeeld dat u een gegenereerde versie van `2019.926.121356.0000020490` gebruikt:

| Versie | Versie in `pom.xml` | Opmerking |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Oorspronkelijke versie met de juiste indeling |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Opnameversie, overschreven |
| `1` | `2019.926.121356.0000020490` | Onvolledige versie, overschreven |

>[!NOTE]
>
>Ongeacht of de oorspronkelijke versie al dan niet is opgenomen in de Cloud Manager-geïnitialiseerde versie, is de oorspronkelijke versie beschikbaar als een Maven-eigenschap met de naam `cloudManagerOriginalVersion` .
