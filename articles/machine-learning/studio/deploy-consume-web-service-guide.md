---
title: Déploiement et consommation
titleSuffix: Azure Machine Learning Studio
description: Vous pouvez utiliser Azure Machine Learning pour déployer des flux de travail et des modèles de machine learning en tant que services web. Ces services web peuvent ensuite servir à appeler les modèles de machine learning à partir d’applications via Internet pour effectuer des prévisions en temps réel ou par lots.
services: machine-learning
ms.service: machine-learning
ms.subservice: studio
ms.topic: article
author: ericlicoding
ms.author: amlstudiodocs
ms.custom: seodec18
ms.date: 04/19/2017
ms.openlocfilehash: 64276047410280f8e818cf695f1fbb0c80fdd693
ms.sourcegitcommit: 5978d82c619762ac05b19668379a37a40ba5755b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55497670"
---
# <a name="azure-machine-learning-studio-web-services-deployment-and-consumption"></a>Services web Azure Machine Learning Studio : Déploiement et consommation
Vous pouvez utiliser Azure Machine Learning pour déployer des flux de travail et des modèles de machine learning en tant que services web. Ces services web peuvent ensuite servir à appeler les modèles de machine learning à partir d’applications via Internet pour effectuer des prévisions en temps réel ou par lots. Les services web, RESTful, peuvent être appelés avec divers langages et plateformes de programmation, notamment Java, .NET et des applications comme Excel.

Les sections suivantes fournissent des liens vers des procédures pas à pas, du code et de la documentation pour vous aider à démarrer.

## <a name="deploy-a-web-service"></a>Déployer un service web

### <a name="with-azure-machine-learning-studio"></a>Avec Azure Machine Learning Studio
Machine Learning Studio et le portail des services web Microsoft Azure Machine Learning vous permettent de déployer et de gérer un service web sans avoir à écrire du code.

Les liens suivants fournissent des informations générales sur le processus de déploiement d’un nouveau service web :

* Pour une vue d’ensemble du déploiement d’un nouveau service web basé sur Azure Resource Manager, consultez [Déployer un nouveau service web](publish-a-machine-learning-web-service.md).
* Pour une présentation du déploiement d’un service web, consultez [Déployer un service web Azure Machine Learning](publish-a-machine-learning-web-service.md).
* Pour une présentation complète de la création et du déploiement d’un service web, consultez [Étape 1 du didacticiel pas à pas : créer un espace de travail Machine Learning](walkthrough-1-create-ml-workspace.md).
* Pour des exemples spécifiques de déploiement d’un service web, consultez :

  * [Étape 5 du didacticiel pas à pas : déployer le service web Azure Machine Learning](walkthrough-5-publish-web-service.md)
  * [Comment déployer un service web dans plusieurs régions](how-to-deploy-to-multiple-regions.md)

### <a name="with-web-services-resource-provider-apis-azure-resource-manager-apis"></a>Avec les API du fournisseur de ressources des services web (API Azure Resource Manager)
Le fournisseur de ressources Azure Machine Learning pour les services web permet le déploiement et la gestion des services web au moyen d’appels d’API REST. Pour plus de détails, consultez la référence [Service web Machine Learning (REST)](/rest/api/machinelearning/index).

<!-- [Machine Learning Web Service (REST)](https://msdn.microsoft.com/library/azure/mt767538.aspx) reference. -->


### <a name="with-powershell-cmdlets"></a>Avec des applets de commande PowerShell
Le fournisseur de ressources Azure Machine Learning pour les services web permet le déploiement et la gestion des services web au moyen d’applets de commande PowerShell.

Pour utiliser les applets de commande, vous devez d’abord vous connecter à votre compte Azure à partir de l’environnement PowerShell à l’aide de l’applet de commande [Connect-AzureRmAccount](/powershell/module/azurerm.profile/connect-azurermaccount). Si vous ne savez pas comment appeler les commandes PowerShell basées sur Resource Manager, consultez [Utilisation d’Azure PowerShell avec Azure Resource Manager](../../azure-resource-manager/powershell-azure-resource-manager.md).

Pour exporter votre expérience prédictive, utilisez cet [exemple de code](https://github.com/ritwik20/AzureML-WebServices). Après avoir créé le fichier .exe à partir du code, vous pouvez taper :

    C:\<folder>\GetWSD <experiment-url> <workspace-auth-token>

L’exécution de l’application crée un modèle JSON de service web. Pour utiliser le modèle afin de déployer un service web, vous devez ajouter les informations suivantes :

* Nom et clé du compte de stockage

    Vous pouvez récupérer le nom et la clé du compte de stockage à partir du [portail Azure](https://portal.azure.com/).
* ID de plan d’engagement

    Vous pouvez récupérer l’ID du plan sur le portail des [services web Azure Machine Learning](https://services.azureml.net) en vous connectant et en cliquant sur le nom d’un plan.

Ajoutez-les au modèle JSON en tant qu’enfants du nœud *Propriétés* au même niveau que le nœud *MachineLearningWorkspace*.

Voici un exemple :

    "StorageAccount": {
            "name": "YourStorageAccountName",
            "key": "YourStorageAccountKey"
    },
    "CommitmentPlan": {
        "id": "subscriptions/YouSubscriptionID/resourceGroups/YourResourceGroupID/providers/Microsoft.MachineLearning/commitmentPlans/YourPlanName"
    }

Consultez les articles et les exemples de code suivants pour plus de détails :

* [Applets de commande Azure Machine Learning](https://docs.microsoft.com/powershell/module/azurerm.machinelearning) sur MSDN
* Exemple de [procédure pas à pas](https://github.com/raymondlaghaeian/azureml-webservices-arm-powershell/blob/master/sample-commands.txt) sur GitHub

## <a name="consume-the-web-services"></a>Utiliser des services web
### <a name="from-the-azure-machine-learning-web-services-ui-testing"></a>À partir de l’interface utilisateur des services web Azure Machine Learning (test)
Vous pouvez tester votre service web sur le portail de services web Azure Machine Learning. Cela comprend le test du service de requête-réponse (RRS) et des interfaces de service d’exécution de lots (BES).

* [Déployer comme un nouveau service web](publish-a-machine-learning-web-service.md)
* [Déploiement d’un service web Azure Machine Learning](publish-a-machine-learning-web-service.md)
* [Étape 5 du didacticiel pas à pas : déployer le service web Azure Machine Learning](walkthrough-5-publish-web-service.md)

### <a name="from-excel"></a>À partir d’Excel
Vous pouvez télécharger un modèle Excel qui consomme le service web :

* [Utilisation d’un service web Microsoft Azure Machine Learning à partir de Microsoft Excel.](consuming-from-excel.md)
* [Complément Excel de services web Azure Machine Learning](excel-add-in-for-web-services.md)

### <a name="from-a-rest-based-client"></a>À partir d’un client basé sur REST
Les services web Azure Machine Learning sont des API RESTful. Vous pouvez consommer ces API à partir de différentes plateformes, notamment .NET, Python, R, Java, etc. La page **Consommer** de votre service web sur le [portail des services web Microsoft Azure Machine Learning](https://services.azureml.net) contient des exemples de code susceptibles de vous aider à démarrer. Pour plus d’informations, consultez [Utilisation d’un service Web Microsoft Azure Machine Learning](consume-web-services.md).
