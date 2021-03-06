---
title: "Didacticiel : Intégration d'Azure Active Directory à LearnUpon | Microsoft Docs"
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et LearnUpon.
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.assetid: b11c6315-c79d-4f34-9610-bd17070ab7c7
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/23/2017
ms.author: jeedes
ms.openlocfilehash: a548f11b1f423fb738108d9314f2fc887ef02c52
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55176843"
---
# <a name="tutorial-azure-active-directory-integration-with-learnupon"></a>Tutoriel : Intégration d'Azure Active Directory à LearnUpon

Dans ce didacticiel, vous allez apprendre à intégrer LearnUpon à Azure Active Directory (Azure AD).

L’intégration de LearnUpon à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à LearnUpon.
- Vous pouvez autoriser vos utilisateurs à se connecter automatiquement à LearnUpon (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes à partir d’un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à LearnUpon, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement LearnUpon pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez obtenir un essai d’un mois [ici](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de LearnUpon à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-learnupon-from-the-gallery"></a>Ajout de LearnUpon à partir de la galerie
Pour configurer l’intégration de LearnUpon à Azure AD, vous devez ajouter LearnUpon de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter LearnUpon à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![APPLICATIONS][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![APPLICATIONS][3]

1. Dans la zone de recherche, saisissez **LearnUpon**.

    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/tutorial_learnupon_search.png)

1. Dans le panneau de résultats, sélectionnez **LearnUpon**, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/tutorial_learnupon_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuration et test de l’authentification unique Azure AD
Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec LearnUpon à l’aide d’un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur LearnUpon équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et l’utilisateur de LearnUpon associé doit être établie.

Dans LearnUpon, affectez la valeur du **nom d’utilisateur** dans Azure AD comme valeur du **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique avec Azure AD avec LearnUpon, vous devez compléter les blocs de construction suivants :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Création d’un utilisateur de test LearnUpon](#creating-a-learnupon-test-user)** pour avoir un équivalent de Britta Simon dans LearnUpon lié à la représentation Azure AD de l’utilisateur.
1. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Testing Single Sign-On](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application LearnUpon.

**Pour configurer l’authentification unique Azure AD avec LearnUpon, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **LearnUpon**, cliquez sur **Authentification unique**.

    ![Configurer l'authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_samlbase.png)

1. Dans la section **LearnUpon Domain and URLs** (Domaine et URL LearnUpon), procédez comme suit :

    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_url.png)

    Dans la zone de texte **URL de réponse** , tapez une URL au format suivant : `https://<companyname>.learnupon.com/saml/consumer`

    > [!NOTE] 
    > Notez qu’il ne s’agit pas de la valeur réelle. Vous devez mettre à jour cette valeur avec l’URL de réponse réelle. Pour l’obtenir, contactez [l’équipe de support technique LearnUpon](https://www.learnupon.com/features/support/).



1. Dans la section **Certificat de signature SAML**, recherchez l’élément **Empreinte numérique**. Celui-ci sera ajouté à vos paramètres SAML LearnUpon.

    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_general_400.png)

1. Dans la section **LearnUpon Configuration** (Configuration de LearnUpon), cliquez sur **Configure LearnUpon** (Configurer LearnUpon) pour ouvrir la fenêtre **Configurer l’authentification**. Copiez **l’URL de déconnexion, l’ID d’entité SAML et l’URL du service d’authentification unique SAML** à partir de la **section Référence rapide.**

    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_configure.png) 

1. Ouvrez une autre instance du navigateur et connectez-vous à LearnUpon avec un compte d’administrateur. 

1. Cliquez sur l’onglet **Paramètres** .
   
    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_06.png)

1. Cliquez sur **Authentification unique - SAML**, puis cliquez sur **Paramètres généraux** pour configurer les paramètres SAML.
   
    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_07.png) 

1. Dans la section **Paramètres généraux** procédez comme suit :
   
    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_08.png)  
  
    a. Sélectionnez **Enabled**.

    b. Sélectionnez **2.0** pour **Version**.

    c. Sélectionnez **Non** pour **Skip conditions** (Ignorer les conditions).

    d. Dans la zone de texte **SAML Token POST param name** (Nom de paramètre POST du jeton SAML), entrez le nom du paramètre de publication de demande correspondant à l’URL de consommateur SAML indiquée ci-dessus, qui contient l’assertion SAML à vérifier et à authentifier. Par exemple, **SAMLResponse**.

    e. Dans la zone de texte **Format de l’identificateur du nom**, entrez la valeur indiquant à quel emplacement dans votre assertion SAML réside l’identificateur de l’utilisateur (adresse e-mail), par exemple, **urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress**.
  
    f. Dans la zone de texte **Identify Provider Location** (Identifier l’emplacement du fournisseur), entrez la valeur indiquant l’emplacement vers lequel sont envoyés les utilisateurs lorsqu’ils cliquent sur l’icône de téléchargement à partir de l’écran de connexion au portail Azure.
  
    g. Dans la zone de texte **URL de déconnexion**, collez **l’URL de déconnexion** que vous avez copiée à partir du portail Azure.
    
    h. Cliquez sur **Manage finger prints**(Gérer les empreintes), puis téléchargez l’empreinte du certificat téléchargé.

1. Cliquez sur **Paramètres utilisateur**, puis procédez comme suit :
   
     ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_11.png)  
 
    a. Dans la zone de texte **First Name Identifier Format** (Format de l’identificateur du prénom), entrez la valeur indiquant à quel emplacement dans votre assertion SAML réside le prénom des utilisateurs, par exemple, **http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname**.
  
    b. Dans la zone de texte **Last Name Identifier Format** (Format de l’identificateur du nom), entrez la valeur indiquant à quel emplacement dans votre assertion SAML réside le nom des utilisateurs, par exemple, **http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname**.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Pour en savoir plus sur la fonctionnalité de documentation incorporée, accédez à : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD
L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

![Créer un utilisateur Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le panneau de navigation gauche du **portail Azure**, cliquez sur l’icône **Azure Active Directory**.

    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/create_aaduser_01.png) 

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.
    
    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/create_aaduser_02.png) 

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue.
 
    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/create_aaduser_03.png) 

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :
 
    ![Création d’un utilisateur de test Azure AD](./media/learnupon-tutorial/create_aaduser_04.png) 

    a. Dans la zone de texte **Nom**, entrez **BrittaSimon**.

    b. Dans la zone de texte **Nom d’utilisateur**, tapez **l’adresse e-mail** de Britta Simon.

    c. Sélectionnez **Afficher le mot de passe** et notez la valeur du **mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="creating-a-learnupon-test-user"></a>Création d’un utilisateur de test LearnUpon

L’objectif de cette section est de créer l’utilisateur Britta Simon dans LearnUpon. LearnUpon prend en charge l’approvisionnement juste-à-temps, qui est activé par défaut.

Vous n’avez aucune opération à effectuer dans cette section. Un utilisateur est créé au moment d’une tentative d’accès à LearnUpon s’il n’existe pas déjà. [Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-single-sign-on).

>[!NOTE]
>Si vous devez créer un utilisateur manuellement, contactez [l’équipe de support technique LearnUpon](https://www.learnupon.com/features/support/). 

### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à LearnUpon.

![Affecter des utilisateurs][200] 

**Pour affecter Britta Simon à LearnUpon, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **LearnUpon**.

    ![Configurer l'authentification unique](./media/learnupon-tutorial/tutorial_learnupon_app.png) 

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202] 

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="testing-single-sign-on"></a>Test de l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la vignette LearnUpon dans le volet d’accès, vous devez être connecté automatiquement à votre application LearnUpon.
Pour plus d’informations sur le volet d’accès, consultez [Présentation du volet d’accès](../user-help/active-directory-saas-access-panel-introduction.md).

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/learnupon-tutorial/tutorial_general_01.png
[2]: ./media/learnupon-tutorial/tutorial_general_02.png
[3]: ./media/learnupon-tutorial/tutorial_general_03.png
[4]: ./media/learnupon-tutorial/tutorial_general_04.png

[100]: ./media/learnupon-tutorial/tutorial_general_100.png

[200]: ./media/learnupon-tutorial/tutorial_general_200.png
[201]: ./media/learnupon-tutorial/tutorial_general_201.png
[202]: ./media/learnupon-tutorial/tutorial_general_202.png
[203]: ./media/learnupon-tutorial/tutorial_general_203.png

