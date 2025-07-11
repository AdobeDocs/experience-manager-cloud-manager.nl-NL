---
title: Toegangstokens beheren in Cloud Manager
description: Leer hoe u de toegangstokens die worden gebruikt voor 'Create Your Own Git' in Cloud Manager op Adobe Managed Services, kunt weergeven, bewerken en verwijderen.
badge: label="Private bèta" type="Positive" url="/help/release-notes/current.md#access-tokens"
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
source-git-commit: 254ad0ac77e793657292e34ae4a6bf3baecea8d5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Toegangstokens beheren voor externe opslagruimten {#manage-access-tokens}

Cloud Manager gebruikt toegangstokens om opslagruimten te beheren die op externe Git-platforms worden gehost. Eerder, als een teken verliep, moest de bijbehorende bewaarplaats opnieuw worden geregistreerd om operationeel te blijven.

Nu, laat **de Tokens van de Toegang beheren** eigenschap u tokens efficiënter beheren. U kunt tokens bekijken, anders noemen of verwijderen die aan gesteunde externe leveranciers van de it, met inbegrip van de Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps worden aangesloten.

Zie ook [ Externe Bewaarplaatsen in Cloud Manager ](/help/managing-code/external-repositories.md) toevoegen.

>[!NOTE]
>
>De functies die in dit artikel worden beschreven, zijn alleen beschikbaar via het persoonlijke bètaprogramma. Voor meer details en om omhoog voor privé bèta te ondertekenen, zie [ de Tokens van de Toegang beheren ](/help/release-notes/current.md#access-tokens).

## Toegangstokens weergeven {#view-access-tokens}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.
1. Op de **[Mijn console van Programma&#39;s](/help/getting-started/navigation.md#my-programs-console)**, selecteer het programma waarvan uw eigen toegangstoken van het Git brengt u wilt beheren.
1. In het zijmenu, onder **Programma**, klik ![ het overzichtspictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Bewaarplaatsen**.
1. Vlak de hoger-juiste hoek van de pagina, klik **beheert de Tokens van de Toegang**.

   De **beheert de Tokens van de Toegang** knoop is slechts zichtbaar als uw programma uw eigen eigenschap van de it gebruikt.

   ![ beheert de dialoogdoos die van de Tokens van de Toegang één teken dat actief is en één teken dat inactief is ](/help/managing-code/assets/access-tokens-manage.png)

1. In **beheert de Tokens van de Toegang** dialoogdoos:
   * Alle toegangstokens worden vermeld.
   * U kunt **uitgeven** om het even welk teken.
   * U kunt **schrappen** slechts die tokens die *niet momenteel in gebruik* zijn. Als een teken in gebruik is, is de ![ knoop van het het overzichtspictogram van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) gehandicapt.

## Een toegangstoken bewerken {#edit-access-tokens}

1. In **beheert de Tokens van de Toegang** dialoogdoos, rechts van een symbolische naam, klik ![ uitgeven pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. In **geef Token van de Toegang** dialoogdoos uit, werk de **Symbolische Naam**, of de **Symbolische waarde van de Toegang**, of allebei bij.

   ![ geef de Token van de Toegang dialoogdoos uit ](/help/managing-code/assets/access-tokens-edit.png)

1. Als het **Token van de Toegang** momenteel in gebruik is, verschijnt een bericht waarschuwend u dat alle bijbehorende bewaarplaatsen automatisch na de update worden opnieuw bevestigd.

1. Klik **Update** om de veranderingen te bewaren.

## Een toegangstoken verwijderen {#delete-access-token}

1. In **beheer de Tokens van de Toegang** dialoogdoos, rechts van een symbolische naam, klik ![ pictogram van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   Het pictogram is gehandicapt (![ schrap overzichtspictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) voor tokens die momenteel in gebruik zijn.

1. In het **Symbolische de dialoogvakje van de Toegang van de Schrapping**, klik **Schrapping** om het teken permanent te verwijderen.
