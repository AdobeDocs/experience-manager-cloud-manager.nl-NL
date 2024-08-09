---
title: GitHub Check Configuration for Private Repositories
description: Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# GitHub Check Configuration for Private Repositories {#github-check-config}

Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.

## Configuratie van GitHub-controles {#configuration}

Wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md#using), zal de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/overview/ci-cd-pipelines.md) automatisch worden gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

U kunt deze controles besturen door een `.cloudmanager/pr_pipelines.yml` -bestand te maken in de standaardvertakking van de privéopslagruimte.

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
| `template.programID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | Kan worden gebruikt om de [ pijpleidingsvariabelen ](/help/getting-started/build-environment.md#pipeline-variables) opnieuw te gebruiken die op één van de bestaande pijpleidingen worden geplaatst die automatisch door elke PR worden gecreeerd. |
| `template.pipelineID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | Kan worden gebruikt om de [ pijpleidingsvariabelen ](/help/getting-started/build-environment.md#pipeline-variables) opnieuw te gebruiken die op één van de bestaande pijpleidingen worden geplaatst die automatisch door elke PR worden gecreeerd. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Gebruikt om de naam van de pijpleiding te plaatsen die automatisch wordt gecreeerd |
| `importantMetricsFailureBehavior` | `CONTINUE` of `FAIL` of `PAUSE` | `CONTINUE` | Plaatst het belangrijke metrische gedrag van de pijpleiding <br>`CONTINUE` = Als belangrijke metrische ontbreekt, zal de pijpleiding zich automatisch <br>`FAIL` = de pijpleiding met een FAILED status beëindigen als belangrijke metrische ontbreekt <br>`PAUSE` = de stap van het codescannen een WAITING status zal ontvangen wanneer belangrijke metrisch ontbreekt en moet manueel worden hervat |
