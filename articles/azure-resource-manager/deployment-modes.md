---
title: Modes de déploiement Azure Resource Manager | Microsoft Docs
description: Explique comment spécifier s’il faut utiliser un mode de déploiement complet ou incrémentiel avec Azure Resource Manager.
services: azure-resource-manager
documentationcenter: na
author: tfitzmac
ms.service: azure-resource-manager
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/24/2019
ms.author: tomfitz
ms.openlocfilehash: c0875861a90080c649596880804fe6538c04bc51
ms.sourcegitcommit: 5978d82c619762ac05b19668379a37a40ba5755b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55497608"
---
# <a name="azure-resource-manager-deployment-modes"></a>Modes de déploiement Azure Resource Manager

Lorsque vous déployez vos ressources, vous spécifiez que le déploiement est soit une mise à jour incrémentielle, soit une mise à jour complète.  La principale différence entre ces deux modes réside dans la manière dont le Gestionnaire des ressources gère les ressources existantes dans le groupe de ressources qui ne se trouvent pas dans le modèle. Le mode par défaut est incrémentiel.

[!INCLUDE [updated-for-az](../../includes/updated-for-az.md)]

## <a name="incremental-and-complete-deployments"></a>Déploiements incrémentiels et complets

Pour les deux modes, Resource Manager essaie de créer toutes les ressources spécifiées dans le modèle. Si la ressource existe déjà dans le groupe de ressources et que ses paramètres sont conservés, aucune opération n’est effectuée pour cette ressource. Si vous modifiez les valeurs de propriété d’une ressource, la ressource est mise à jour avec ces nouvelles valeurs. Si vous essayez de mettre à jour l’emplacement ou le type d’une ressource existante, le déploiement échoue avec une erreur. Vous devez dans ce cas déployer une nouvelle ressource avec l’emplacement ou le type dont vous avez besoin.

En mode complet, le Gestionnaire des ressources **supprime** les ressources qui existent dans le groupe de ressources, mais qui ne sont pas spécifiées dans le modèle. Les ressources qui sont spécifiées dans le modèle, mais qui ne sont pas déployées du fait qu’une [condition](resource-manager-templates-resources.md#condition) a la valeur false, ne sont pas supprimées.

En mode incrémentiel, le Gestionnaire des ressources **conserve telles quelles** les ressources qui existent dans le groupe de ressources, mais qui ne sont pas spécifiées dans le modèle. Lors du redéploiement d’une ressource en mode incrémentiel, spécifiez toutes les valeurs de propriété de la ressource, et pas seulement celles que vous mettez à jour. Si vous omettez de spécifier certaines propriétés, Resource Manager interprète la mise à jour comme un remplacement de ces valeurs.

## <a name="example-result"></a>Résultat de l’exemple

Pour illustrer la différence entre les modes incrémentiel et complet, examinez le scénario suivant.

Le **groupe de ressources** contient :

* Ressource A
* Ressource B
* Ressource C

Le **modèle** contient :

* Ressource A
* Ressource B
* Ressource D

Lors du déploiement en mode **incrémentiel**, le groupe de ressources contient :

* Ressource A
* Ressource B
* Ressource C
* Ressource D

Lors du déploiement en mode **complet**, la ressource C est supprimée. Le groupe de ressources contient :

* Ressource A
* Ressource B
* Ressource D

## <a name="set-deployment-mode"></a>Définir un mode de déploiement

Pour définir le mode de déploiement lors du déploiement avec PowerShell, utilisez le paramètre `Mode`.

```azurepowershell-interactive
New-AzResourceGroupDeployment `
  -Mode Complete `
  -Name ExampleDeployment `
  -ResourceGroupName ExampleResourceGroup `
  -TemplateFile c:\MyTemplates\storage.json
```

Pour définir le mode de déploiement lors du déploiement avec Azure CLI, utilisez le paramètre `mode`.

```azurecli-interactive
az group deployment create \
  --name ExampleDeployment \
  --mode Complete \
  --resource-group ExampleGroup \
  --template-file storage.json \
  --parameters storageAccountType=Standard_GRS
```

Lorsque vous utilisez un [modèle lié ou imbriqué](resource-group-linked-templates.md), vous devez définir la propriété `mode` sur `Incremental`. Seuls les modèles de niveau racine prennent en charge le mode de déploiement complet.

```json
"resources": [
  {
      "apiVersion": "2017-05-10",
      "name": "linkedTemplate",
      "type": "Microsoft.Resources/deployments",
      "properties": {
          "mode": "Incremental",
          <nested-template-or-external-template>
      }
  }
]
```

## <a name="next-steps"></a>Étapes suivantes

* Pour en savoir plus sur la création de modèles Resource Manager, consultez [Création de modèles Azure Resource Manager](resource-group-authoring-templates.md).
* Pour en savoir plus sur le déploiement de ressources, consultez [Déploiement d’une application avec un modèle Azure Resource Manager](resource-group-template-deploy.md).
* Pour afficher les opérations pour un fournisseur de ressources, consultez [API REST Azure](/rest/api/).
