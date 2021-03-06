---
title: Migrer une stratégie classique nécessitant l’authentification multifacteur dans le portail Azure | Microsoft Docs
description: Cet article montre comment migrer une stratégie classique qui nécessite l’authentification multifacteur dans le portail Azure.
services: active-directory
keywords: accès conditionnel aux applications, accès conditionnel à Azure AD, accès sécurisé aux ressources d’entreprise, stratégies d’accès conditionnel
documentationcenter: ''
author: MarkusVi
manager: daveba
editor: ''
ms.assetid: 8c1d978f-e80b-420e-853a-8bbddc4bcdad
ms.service: active-directory
ms.subservice: conditional-access
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 06/13/2018
ms.author: markvi
ms.reviewer: nigu
ms.openlocfilehash: 82d53b4eb81f6b7ca6f43d73a8968dbcbd158d43
ms.sourcegitcommit: 58dc0d48ab4403eb64201ff231af3ddfa8412331
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55081158"
---
# <a name="migrate-a-classic-policy-that-requires-multi-factor-authentication-in-the-azure-portal"></a>Migrer une stratégie classique nécessitant l’authentification multifacteur dans le portail Azure 

Cet article montre comment migrer une stratégie classique qui nécessite l’**authentification multifacteur** pour une application cloud. Bien qu’il ne s’agisse pas d’une prérequis, nous vous recommandons de lire [Migrer les stratégies classiques dans le portail Azure](policy-migration.md) avant d’effectuer la migration de vos stratégies classiques.


 
## <a name="overview"></a>Vue d’ensemble 

Le scénario de cet article montre comment migrer une stratégie classique qui nécessite l’**authentification multifacteur** pour une application cloud. 

![Azure Active Directory](./media/policy-migration/33.png)


Le processus de migration est constitué des étapes suivantes :

1. [Ouvrez la stratégie classique](#open-a-classic-policy) pour obtenir les paramètres de configuration.
2. Créez une nouvelle stratégie d’accès conditionnel Azure AD afin de remplacer votre stratégie classique. 
3. Désactivez la stratégie classique.



## <a name="open-a-classic-policy"></a>Ouvrir une stratégie classique

1. Dans la barre de navigation gauche du [portail Azure](https://portal.azure.com), cliquez sur **Azure Active Directory**.

    ![Azure Active Directory](./media/policy-migration-mfa/01.png)

2. Dans la page **Azure Active Directory**, dans la section **Gérer**, cliquez sur **Accès conditionnel**.

    ![Accès conditionnel](./media/policy-migration-mfa/02.png)

3. Dans la section **Gérer**, cliquez sur **Stratégies classiques (préversion)**.

    ![Stratégies classiques](./media/policy-migration-mfa/12.png)

4. Dans la liste de stratégies classiques, cliquez sur celle qui nécessite l’**authentification multifacteur** pour une application cloud.

    ![Stratégies classiques](./media/policy-migration-mfa/13.png)


## <a name="create-a-new-conditional-access-policy"></a>Créer une nouvelle stratégie d’accès conditionnel


1. Dans la barre de navigation gauche du [portail Azure](https://portal.azure.com), cliquez sur **Azure Active Directory**.

    ![Azure Active Directory](./media/policy-migration/01.png)

2. Dans la page **Azure Active Directory**, dans la section **Gérer**, cliquez sur **Accès conditionnel**.

    ![Accès conditionnel](./media/policy-migration/02.png)



3. Dans la page **Accès conditionnel**, pour ouvrir la page **Nouveau**, cliquez sur **Ajouter** dans la barre d’outils située en haut.

    ![Accès conditionnel](./media/policy-migration/03.png)

4. Dans la page **Nom** du panneau **Nouveau**, indiquez le nom de votre stratégie.

    ![Accès conditionnel](./media/policy-migration/29.png)

5. Dans la section **Affectations**, cliquez sur **Utilisateurs et groupes**.

    ![Accès conditionnel](./media/policy-migration/05.png)

    a. Si vous avez tous les utilisateurs sélectionnés dans votre stratégie classique, cliquez sur **Tous les utilisateurs**. 

    ![Accès conditionnel](./media/policy-migration/35.png)

    b. Si vous avez des groupes sélectionnés dans votre stratégie classique, cliquez sur **Sélectionner des utilisateurs et des groupes**, puis sélectionnez les groupes et utilisateurs requis.

    ![Accès conditionnel](./media/policy-migration/36.png)

    c. Si vous avez des groupes exclus, cliquez sur l’onglet **Exclure** et sélectionnez les groupes et utilisateurs requis. 

    ![Accès conditionnel](./media/policy-migration/37.png)

6. Dans la page **Nouveau**, pour ouvrir la page **Applications cloud**, cliquez sur **Applications cloud** dans la section **Affectation**.

8. Dans la page **Applications cloud**, procédez comme suit :

    ![Accès conditionnel](./media/policy-migration/08.png)

    a. Cliquez sur **Sélectionner les applications**.

    b. Cliquez sur **Sélectionner**.

    c. Dans la page **Sélectionner**, sélectionnez votre application cloud, puis cliquez sur **Sélectionner**.

    d. Dans la page **Applications cloud**, cliquez sur **Terminé**.



9. Si vous avez sélectionné **Imposer l’authentification multifacteur** :

    ![Accès conditionnel](./media/policy-migration/26.png)

    a. Dans la section **Contrôles d’accès**, cliquez sur **Accorder**.

    ![Accès conditionnel](./media/policy-migration/27.png)

    b. Sur la page **Accorder**, cliquez sur **Accorder l’accès**, puis cliquez sur **Imposer l’authentification multifacteur**.

    c. Cliquez sur **Sélectionner**.


10. Cliquez sur **Activé** pour activer votre stratégie.

    ![Accès conditionnel](./media/policy-migration/30.png)



## <a name="disable-the-classic-policy"></a>Désactiver la stratégie classique

Pour désactiver votre stratégie classique, cliquez sur **Désactiver** dans la vue **Détails**.

![Stratégies classiques](./media/policy-migration-mfa/14.png)



## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur la migration des stratégies classiques, consultez [Migrer les stratégies classiques dans le portail Azure](policy-migration.md).


- Pour savoir comment configurer une stratégie d’accès conditionnel, consultez [Exiger une authentification multifacteur (MFA) pour des applications spécifiques disposant d’un accès conditionnel Azure Active Directory](app-based-mfa.md).

- Si vous êtes prêt à configurer des stratégies d’accès conditionnel pour votre environnement, consultez les [Meilleures pratiques pour l’accès conditionnel dans Azure Active Directory](best-practices.md). 
