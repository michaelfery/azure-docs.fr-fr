---
title: Déployer Kubernetes sur Azure Stack | Microsoft Docs
description: Découvrez comment déployer Kubernetes sur Azure Stack.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
editor: ''
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/16/2019
ms.author: mabrigg
ms.reviewer: waltero
ms.lastreviewed: 01/16/2019
ms.openlocfilehash: 9d542f7c2cdeb20806a2db98005ffc03cf72144c
ms.sourcegitcommit: 898b2936e3d6d3a8366cfcccc0fccfdb0fc781b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55238014"
---
# <a name="deploy-kubernetes-to-azure-stack"></a>Déployer Kubernetes sur Azure Stack

*S’applique à : systèmes intégrés Azure Stack et Kit de développement Azure Stack*

> [!Note]  
> Kubernetes sur Azure Stack est en préversion.

Vous pouvez suivre les étapes de cet article pour déployer et configurer les ressources pour Kubernetes en une seule opération coordonnée. Les étapes utilisent un modèle Azure Resource Manager. Vous devez collecter les informations nécessaires sur votre installation d’Azure Stack, générer le modèle, puis le déployer sur votre cloud. Le modèle Azure Stack n’utilise pas le service AKS managé qui est offert dans Azure mondial.

## <a name="kubernetes-and-containers"></a>Kubernetes et conteneurs

Vous pouvez installer Kubernetes à l’aide de modèles Azure Resource Manager générés par le moteur ACS (Azure Container Services) sur Azure Stack. Un [Kubernetes](https://kubernetes.io) est un système open source permettant d’automatiser le déploiement, la mise à l’échelle et la gestion d’applications dans des conteneurs. Un [conteneur](https://www.docker.com/what-container) se trouve dans une image. L’image de conteneur est similaire à une machine virtuelle, avec cette différence que le conteneur inclut seulement les ressources nécessaires pour exécuter une application, comme le code, un runtime pour exécuter le code, des bibliothèques spécifiques et des paramètres.

Vous pouvez utiliser Kubernetes pour ce qui suit :

- Développer des applications hautement évolutives et extensibles, qui peuvent être déployées en quelques secondes. 
- Simplifier la conception de vos applications et améliorer leur fiabilité à l’aide de différentes applications Helm. [Helm](https://github.com/kubernetes/helm) est un outil d’empaquetage open source qui vous aide à installer et à gérer le cycle de vie d’applications Kubernetes.
- Surveiller et diagnostiquer facilement l’intégrité de vos applications grâce à des fonctionnalités de mise à l’échelle et de mise à niveau.

Vous êtes facturé seulement pour l’utilisation des ressources de calcul qui est nécessaire aux nœuds où se trouve votre cluster. Pour plus d’informations, consultez [Utilisation et facturation dans Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-billing-and-chargeback).

## <a name="deploy-kubernetes"></a>Déployer Kubernetes

Les étapes pour déployer un cluster Kubernetes sur Azure Stack dépendent de votre service de gestion des identités. Vérifiez la solution de gestion des identités utilisée par votre installation d’Azure Stack. Contactez votre administrateur Azure Stack pour vérifier votre service de gestion des identités.

- **Azure Active Directory (Azure AD)**  
Pour obtenir des instructions sur l’installation du cluster lors de l’utilisation d’Azure AD, consultez [Déployer Kubernetes sur Azure Stack à l’aide d’Azure Active Directory (Azure AD)](azure-stack-solution-template-kubernetes-azuread.md).

- **Active Directory Federation Services (AD FS)**  
Pour obtenir des instructions sur l’installation du cluster lors de l’utilisation d’AD FS, consultez [Déployer Kubernetes sur Azure Stack à l’aide d’Active Directory Federation Services (AD FS)](azure-stack-solution-template-kubernetes-adfs.md).

## <a name="connect-to-your-cluster"></a>Se connecter au cluster

Vous êtes maintenant prêt à vous connecter à votre cluster. Le maître se trouve dans votre groupe de ressources de cluster et est nommé `k8s-master-<sequence-of-numbers>`. Utilisez un client SSH pour vous connecter au maître. Sur le maître, vous pouvez utiliser **kubectl**, client de ligne de commande Kubernetes, pour gérer le cluster. Pour obtenir des instructions, consultez [Kubernetes.io](https://kubernetes.io/docs/reference/kubectl/overview).

Le gestionnaire de package **Helm** peut également s’avérer utile pour installer et déployer des applications sur votre cluster. Pour obtenir des instructions sur l’installation et l’utilisation de Helm avec votre cluster, consultez [helm.sh](https://helm.sh/).

## <a name="next-steps"></a>Étapes suivantes

[Ajouter un cluster Kubernetes à la Place de marché (pour l’opérateur Azure Stack)](../azure-stack-solution-template-kubernetes-cluster-add.md)

[Déployer Kubernetes sur Azure Stack à l’aide d’Azure Active Directory (Azure AD)](azure-stack-solution-template-kubernetes-azuread.md)

[Déployer Kubernetes sur Azure Stack à l’aide d’Active Directory Federation Services (AD FS)](azure-stack-solution-template-kubernetes-adfs.md)

[Kubernetes sur Azure](https://docs.microsoft.com/azure/container-service/kubernetes/container-service-kubernetes-walkthrough)
