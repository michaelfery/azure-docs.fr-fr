---
title: Liste de compatibilité de fédération Azure AD
description: Cette page présente les fournisseurs d’identité non-Microsoft qui peuvent être utilisés pour mettre en œuvre l’authentification unique.
services: active-directory
documentationcenter: ''
author: billmath
manager: daveba
editor: curtand
ms.assetid: 22c8693e-8915-446d-b383-27e9587988ec
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 08/23/2018
ms.subservice: hybrid
ms.author: billmath
ms.openlocfilehash: 6ee772054a823ae0607672d41a17a38cd44b2fb8
ms.sourcegitcommit: 5978d82c619762ac05b19668379a37a40ba5755b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55494831"
---
# <a name="azure-ad-federation-compatibility-list"></a>Liste de compatibilité de fédération Azure AD
Azure Active Directory fournit l’authentification unique et une sécurité de l’accès aux applications améliorée pour Office 365 et d’autres ressources de Microsoft Online Services pour des implémentations hybrides et uniquement dans le cloud, sans nécessiter de solution tierce. À l’instar de la plupart des services Microsoft Online, Office 365 est intégré à Azure Active Directory pour les services de répertoire, l’authentification et l’autorisation. En outre, Azure Active Directory fournit l’authentification unique à des milliers d’applications SaaS et à des applications web locales. Consultez la [galerie d’applications](https://azuremarketplace.microsoft.com/marketplace/apps/category/azure-active-directory-apps) Azure Active Directory pour connaître les applications SaaS prises en charge. 

## <a name="idp-validation"></a>Validation IDP
Si votre organisation utilise une solution de fédération tierce, vous pouvez configurer l’authentification unique pour vos utilisateurs Active Directory locaux avec les services Microsoft Online, tels qu’Office 365, à condition que la solution de fédération tierce soit compatible avec Azure Active Directory.  Pour toute question concernant la compatibilité, contactez votre fournisseur d’identité.  Si vous souhaitez afficher la liste des fournisseurs d’identité dont la compatibilité avec Azure AD a déjà été testée par Microsoft, cliquez [ici](https://www.microsoft.com/download/details.aspx?id=56843). 

>[!NOTE]
>Microsoft ne propose plus de tests de validation de la compatibilité avec Azure Active Directory aux fournisseurs d’identité indépendants. Si vous souhaitez tester l’interopérabilité de votre produit, suivez ces [recommandations](https://www.microsoft.com/download/details.aspx?id=56843). 

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer vos répertoires locaux à Azure Active Directory](whatis-hybrid-identity.md)
- [Fédération avec Azure AD Connect](how-to-connect-fed-whatis.md)
