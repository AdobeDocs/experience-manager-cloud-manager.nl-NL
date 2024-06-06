---
title: GitHub Check Configuration for Private Repositories
description: Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# GitHub Check Configuration for Private Repositories {#github-check-config}

Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.

## Configuratie van GitHub-controles {#configuration}

Wanneer u [privéopslagplaatsen;](private-repositories.md#using) a [volledige stackcodekwaliteitpijplijn](/help/overview/ci-cd-pipelines.md) wordt automatisch gemaakt. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

U kunt deze controles controleren door een `.cloudmanager/pr_pipelines.yml` in de standaardvertakking van de privéopslagplaats.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mogelijke waarden | Standaard | Beschrijving |
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` of `false` | `false` | Of om slechts de laatste commentaar met de codeaftastenresultaten op dit GitHub trekkingsverzoek te houden of alles te houden |
| `type` | `CI_CD` | nvt | Bepaalt gedrag van een pijpleiding CI/CD |
| `template.programID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | Kan worden gebruikt om het [pijplijnvariabelen](/help/getting-started/build-environment.md#pipeline-variables) die op een van de bestaande pijpleidingen zijn aangebracht die automatisch door elke PR worden aangelegd. |
| `template.pipelineID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | Kan worden gebruikt om het [pijplijnvariabelen](/help/getting-started/build-environment.md#pipeline-variables) die op een van de bestaande pijpleidingen zijn aangebracht die automatisch door elke PR worden aangelegd. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Gebruikt om de naam van de pijpleiding te plaatsen die automatisch wordt gecreeerd |
| `importantMetricsFailureBehavior` | `CONTINUE` of `FAIL` of `PAUSE` | `CONTINUE` | Plaatst het belangrijke metrische gedrag van de pijpleiding<br>`CONTINUE` = Als belangrijke metrisch ontbreekt, zal de pijpleiding zich automatisch vooruit bewegen<br>`FAIL` = de pijpleiding zal met een FAILED status beëindigen als belangrijke metrisch ontbreekt<br>`PAUSE` = De stap van het codescannen zal een WAITING status ontvangen wanneer belangrijke metrisch ontbreekt en moet manueel worden hervat |
