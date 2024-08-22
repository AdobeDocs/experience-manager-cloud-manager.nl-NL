---
title: GitHub Check Configuration for Private Repositories
description: Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# GitHub-controleconfiguratie voor privéopslagruimten {#github-check-config}

Leer hoe u de pijpleidingen kunt beheren die automatisch worden gemaakt om elke pull-aanvraag naar een privéopslagplaats te valideren.

## Configuratie van GitHub-controles {#configuration}

Wanneer het gebruiken van [ privé bewaarplaatsen ](private-repositories.md#using), wordt de a [ volledige pijpleiding van de kwaliteit van de stapelcode ](/help/overview/ci-cd-pipelines.md) automatisch gecreeerd. Deze pijpleiding is begonnen bij elke update van het trekkingsverzoek.

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
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` of `false` | `false` | Of om slechts de laatste commentaar met de codeaftastenresultaten op dit GitHub trekkingsverzoek te houden of allen te houden. |
| `type` | `CI_CD` | nvt | Bepaalt het gedrag van een pijpleiding CI/CD. |
| `template.programID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt de [ pijpleidingsvariabelen ](/help/getting-started/build-environment.md#pipeline-variables) opnieuw gebruiken die op een bestaande pijpleiding worden geplaatst, die elke PR automatisch creeert. |
| `template.pipelineID` | Geheel | Er worden geen pijpleidingvariabelen opnieuw gebruikt | U kunt de [ pijpleidingsvariabelen ](/help/getting-started/build-environment.md#pipeline-variables) opnieuw gebruiken die op een bestaande pijpleiding worden geplaatst, die elke PR automatisch creeert. |
| `namePrefix` | String | `Full Stack Code Quality Pipeline for PR` | Gebruikt om de naam van de pijpleiding te plaatsen die automatisch wordt gecreeerd. |
| `importantMetricsFailureBehavior` | `CONTINUE` of `FAIL` of `PAUSE` | `CONTINUE` | Plaatst het belangrijke metrische gedrag van de pijpleiding <br>`CONTINUE` = als belangrijke metrische ontbreekt, de pijpleiding zich automatisch <br>`FAIL` verplaatst = de pijpleiding eindigt met een FAILED status als belangrijke metrische ontbreekt <br>`PAUSE` = de stap van het codescanningsmiddel ontvangt een WAITING status wanneer belangrijke metrisch ontbreekt en moet manueel worden hervat. |
