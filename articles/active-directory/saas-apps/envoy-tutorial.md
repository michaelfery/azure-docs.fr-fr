---
title: "Tutoriel : Intégration d'Azure Active Directory à Envoy | Microsoft Docs"
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Envoy.
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.reviewer: joflore
ms.assetid: 71f7afcc-1033-4098-9b7e-4f9f2b26f734
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/08/2017
ms.author: jeedes
ms.openlocfilehash: ecc17e6836c7da1193e164cf48a737de82b60039
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55181348"
---
# <a name="tutorial-azure-active-directory-integration-with-envoy"></a>Tutoriel : Intégration d'Azure Active Directory à Envoy

Dans ce didacticiel, vous allez apprendre à intégrer Envoy à Azure Active Directory (Azure AD).

L’intégration d’Envoy à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Envoy.
- Vous pouvez autoriser vos utilisateurs à se connecter automatiquement à Envoy (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à Envoy, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement Envoy pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout d’Envoy à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-envoy-from-the-gallery"></a>Ajout d’Envoy à partir de la galerie
Pour configurer l’intégration d’Envoy à Azure AD, vous devez ajouter Envoy, disponible dans la galerie, à votre liste d’applications SaaS managées.

**Pour ajouter Envoy à partir de la galerie, effectuez les étapes suivantes :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **Envoy**, sélectionnez **Envoy** dans le panneau de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Envoy dans la liste des résultats](./media/envoy-tutorial/tutorial_envoy_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Envoy, avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Envoy équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur Envoy associé doit être établie.

Dans Envoy, affectez la valeur du **nom d’utilisateur** dans Azure AD comme valeur du **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec Envoy, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Créer un utilisateur de test Envoy](#create-an-envoy-test-user)** pour avoir un équivalent de Britta Simon dans Envoy, associé à sa représentation dans Azure AD.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous activez l’authentification unique Azure AD dans le portail Azure et configurez l’authentification unique dans votre application Envoy.

**Pour configurer l’authentification unique Azure AD avec Envoy, effectuez les étapes suivantes :**

1. Dans le portail Azure, dans la page d’intégration de l’application **Envoy**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/envoy-tutorial/tutorial_envoy_samlbase.png)

1. Dans la section **Domaine et URL Envoy**, effectuez les étapes suivantes :

    ![Informations d’authentification unique dans Domaine et URL Envoy](./media/envoy-tutorial/tutorial_envoy_url.png)

    Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://app.envoy.com/a/saml/auth/<company-ID-from-Envoy>`
    
    > [!NOTE] 
    > Cette valeur n’est pas la valeur réelle. Mettez à jour cette valeur avec l’URL d’authentification réelle. Pour obtenir cette valeur, contactez [l’équipe du support Envoy](https://envoy.com/contact/).

1. Dans la section **Certificat de signature SAML**, copiez la valeur **THUMBPRINT** du certificat.

    ![Lien Téléchargement de certificat](./media/envoy-tutorial/tutorial_envoy_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/envoy-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de Envoy**, cliquez sur **Configurer Envoy** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez l **’URL du service d’authentification unique SAML** à partir de la **section Référence rapide.**

    ![Configuration d’Envoy](./media/envoy-tutorial/tutorial_envoy_configure.png)

1. Dans une autre fenêtre de navigateur web, connectez-vous au site de votre entreprise Envoy en tant qu’administrateur.

1. Dans la barre d’outils située en haut, cliquez sur **Settings**.

    ![Envoy](./media/envoy-tutorial/ic776782.png "Envoy")

1. Cliquez sur **Company**.

    ![Company](./media/envoy-tutorial/ic776783.png "Company")

1. Cliquez sur **SAML**.

    ![SAML](./media/envoy-tutorial/ic776784.png "SAML")

1. Dans la section de configuration **SAML Authentication** , procédez comme suit :

    ![SAML authentication](./media/envoy-tutorial/ic776785.png "SAML authentication")
    
    >[!NOTE]
    >La valeur de l’ID d’emplacement du siège est générée automatiquement par l’application.
    
    a. Dans la zone de texte **Fingerprint** (Empreinte digitale), collez la valeur du certificat **Empreinte** que vous avez copiée à partir du portail Azure.
    
    b. Collez la valeur **URL du service d’authentification unique SAML** copiée dans le portail Azure dans la zone de texte **IDENTITY PROVIDER HTTP SAML URL** (URL HTTP SAML du fournisseur d’identité).
    
    c. Cliquez sur **Save changes**.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Pour en savoir plus sur la fonctionnalité de documentation incorporée, accédez à : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/envoy-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/envoy-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/envoy-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/envoy-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-an-envoy-test-user"></a>Créer un utilisateur de test Envoy

Aucun élément d'action ne vous permet de configurer l’approvisionnement des utilisateurs dans Envoy. Lorsqu’un utilisateur tente de se connecter à Envoy à l’aide du panneau d’accès, Envoy vérifie si cet utilisateur existe. Si aucun compte d'utilisateur n’est disponible, Envoy le crée automatiquement.

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Envoy.

![Attribuer le rôle utilisateur][200] 

**Pour attribuer Britta Simon à Envoy, effectuez les étapes suivantes :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Envoy**.

    ![Lien Envoy dans la liste des applications](./media/envoy-tutorial/tutorial_envoy_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette Envoy dans le volet d’accès, vous devez être connecté automatiquement à votre application Envoy.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/envoy-tutorial/tutorial_general_01.png
[2]: ./media/envoy-tutorial/tutorial_general_02.png
[3]: ./media/envoy-tutorial/tutorial_general_03.png
[4]: ./media/envoy-tutorial/tutorial_general_04.png

[100]: ./media/envoy-tutorial/tutorial_general_100.png

[200]: ./media/envoy-tutorial/tutorial_general_200.png
[201]: ./media/envoy-tutorial/tutorial_general_201.png
[202]: ./media/envoy-tutorial/tutorial_general_202.png
[203]: ./media/envoy-tutorial/tutorial_general_203.png

