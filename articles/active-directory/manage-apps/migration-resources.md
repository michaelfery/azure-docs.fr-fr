---
title: Ressources pour la migration d’application vers Azure Active Directory | Microsoft Docs
description: Ressources pour vous aider à migrer l’accès et l’authentification d’applications vers Azure Active Directory (Azure AD).
services: active-directory
author: barbkess
manager: daveba
ms.service: active-directory
ms.subservice: app-mgmt
ms.topic: conceptual
ms.workload: identity
ms.date: 09/19/2018
ms.author: barbkess
ms.reviewer: baselden
ms.openlocfilehash: 40e9a6a7a8693f710fdb41e1c6738ecc70e5a0b7
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55189542"
---
# <a name="resources-for-migrating-applications-to-azure-active-directory"></a>Ressources pour la migration d’applications vers Azure Active Directory

Ressources pour vous aider à migrer l’accès et l’authentification d’applications vers Azure Active Directory (Azure AD). Répondez à cette courte enquête (https://aka.ms/AppsMigrationFeedback) pour nous fournir vos commentaires sur votre expérience de la migration d’applications vers Azure AD (y compris les freins à la migration, les besoins d’outils et/ou de conseils, ou les raisons de votre choix de conserver votre IDP local). 

| Ressource  | Description  |
|:-----------|:-------------|
|[Migration de vos applications vers Azure AD](https://aka.ms/migrateapps/whitepaper) | Ce livre blanc présente les avantages de la migration et explique comment la planifier en quatre phases clairement expliquées : la découverte, la classification, la migration et la gestion continue. Vous serez guidé pour savoir comment penser avec ce processus et diviser votre projet en éléments faciles à utiliser. Le document contient des liens vers des ressources importantes qui vous aideront tout au long du processus. |
|[Guide de solution : Migration d'applications des services de fédération Active Directory (AD FS) vers Azure AD](https://aka.ms/migrateapps/adfssolutionguide) | Ce guide de solution vous guide tout au long des quatre mêmes phases de planification et d’exécution d’un projet de migration d’applications décrit à un niveau supérieur dans le livre blanc sur la migration. Dans ce guide, vous allez apprendre à appliquer ces phases à l’objectif spécifique de déplacement d’une application à partir d’Azure Directory Federated Services (AD FS) vers Azure AD.|
| [Outil : script de préparation de la migration des services de fédération Active Directory (AD FS)](https://aka.ms/migrateapps/adfstools) | Il s’agit d’un script que vous pouvez exécuter sur votre serveur Active Directory Federation Services (ADFS) local pour déterminer l’état de préparation des applications pour la migration vers Azure AD.|
| [Plan de déploiement : migration d'AD FS vers la synchronisation de hachage de mot de passe](https://aka.ms/ADFSTOPHSDPDownload) | Avec la synchronisation de hachage de mot de passe, les hachages des mots de passe utilisateur sont synchronisés de votre annuaire Active Directory local vers Azure AD. Cela permet à Azure AD d’authentifier les utilisateurs sans interagir avec l’Active Directory en local.| 
| [Plan de déploiement : migration d'AD FS vers l'authentification directe](https://aka.ms/ADFSTOPTADPDownload)|L’authentification directe Azure AD permet à vos utilisateurs de se connecter aux applications locales et aux applications cloud à l’aide du même mot de passe. Cette fonctionnalité offre une meilleure expérience aux utilisateurs, car ils n’ont besoin de se souvenir que d’un seul mot de passe. Elle réduit également les coûts du support technique informatique, car les utilisateurs sont moins susceptibles d’oublier comment se connecter lorsqu’ils ne doivent mémoriser qu’un seul mot de passe. Lorsque les utilisateurs se connectent à l’aide d’Azure AD, cette fonctionnalité valide leurs mots de passe directement à partir de l’installation Active Directory locale.|
| [Plan de déploiement : activation de l'authentification unique sur une application SaaS avec Azure AD](https://aka.ms/SSODPDownload) | Avec l’authentification unique (SSO), vous pouvez accéder à toutes les applications et ressources dont vous avez besoin pour travailler, et ce, en vous connectant une seule fois avec un seul compte d’utilisateur. Par exemple, une fois qu’un utilisateur est connecté, il peut passer de Microsoft Office à SalesForce ou à Box sans devoir se soumettre à une nouvelle authentification (par exemple, taper un mot de passe). 
| [Plan de déploiement : étendre des applications à Azure AD avec le proxy d'application](https://aka.ms/AppProxyDPDownload)| La fourniture d’un accès aux applications locales pour les ordinateurs portables et d’autres appareils appartenant à des employés implique généralement le recours à des réseaux privés virtuels (VPN) ou à des zones démilitarisées (DMZ). Non seulement ces solutions sont complexes et difficiles à sécuriser, mais leur configuration et leur gestion ont un coût élevé. Le proxy d’application Azure AD facilite l’accès aux applications locales. |
| [Plans de déploiement](../fundamentals/active-directory-deployment-plans.md) | Trouvez d’autres plans de déploiement pour le déploiement de fonctionnalités tels que l’authentification multifacteur, l’accès conditionnel, l’approvisionnement des utilisateurs, l’authentification unique transparente, la réinitialisation de mot de passe en libre-service et bien plus encore ! |


