---
title: 'Didacticiel : Intégration d’Azure Active Directory à GaggleAMP | Microsoft Docs'
description: Découvrez comment configurer l'authentification unique entre Azure Active Directory et GaggleAMP.
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.assetid: 9cc1a4b7-964b-406b-9e0c-05cb1a7c9856
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/06/2018
ms.author: jeedes
ms.openlocfilehash: ccb2e6be481c27661543ff0dc19e5b60b2aa8d8a
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55178255"
---
# <a name="tutorial-azure-active-directory-integration-with-gaggleamp"></a>Tutoriel : Intégration d’Azure AD à GaggleAMP

Dans ce didacticiel, vous allez apprendre à intégrer GaggleAMP à Azure Active Directory (Azure AD).

L’intégration de GaggleAMP dans Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à GaggleAMP.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à GaggleAMP (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes à partir d’un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à GaggleAMP, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement GaggleAMP pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de GaggleAMP à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-gaggleamp-from-the-gallery"></a>Ajout de GaggleAMP à partir de la galerie
Pour configurer l’intégration de GaggleAMP à Azure AD, vous devez ajouter GaggleAMP à partir de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter GaggleAMP à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![APPLICATIONS][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![APPLICATIONS][3]

1. Dans la zone de recherche, entrez **GaggleAMP**.

    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/tutorial_gaggleamp_search.png)

1. Dans le volet de résultats, sélectionnez **GaggleAMP**, puis cliquez sur **Ajouter** pour ajouter l’application.

    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/tutorial_gaggleamp_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuration et test de l’authentification unique Azure AD
Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec GaggleAMP, avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur GaggleAMP correspondant dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur GaggleAMP associé doit être établie.

Dans GaggleAMP, assignez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec GaggleAMP, vous devez suivre les indications des sections suivantes :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Création d’un utilisateur de test GaggleAMP](#creating-a-gaggleamp-test-user)** pour avoir un équivalent de Britta Simon dans GaggleAMP lié à la représentation Azure AD associée.
1. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Testing Single Sign-On](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application GaggleAMP.

**Pour configurer l’authentification unique Azure AD avec GaggleAMP, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **GaggleAMP**, cliquez sur **Authentification unique**.

    ![Configurer l'authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_gaggleamp_samlbase.png)

1. Dans la section **GaggleAMP Domain and URLs** (Domaine et URL GaggleAMP), suivez les étapes ci-dessous si vous souhaitez configurer l’application en mode initié par **IDP** :

    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_gaggleamp_url.png)

     Dans la zone de texte **Identificateur**, tapez l’URL : `https://accounts.gaggleamp.com/auth/saml/callback`

1. Si vous souhaitez configurer l’application en **mode démarré par le fournisseur de service**, cochez **Afficher les paramètres d’URL avancés**, puis effectuez les étapes suivantes :

    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_gaggleamp_url1.png)

     Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://gaggleamp.com/i/<customerid>`

    > [!NOTE]
    > La valeur de l’URL de connexion n’est pas réelle. Mettez à jour la valeur avec l’URL de connexion réelle. Pour obtenir cette valeur, contactez [l’équipe du support technique de GaggleAMP](mailto:sales@gaggleamp.com).
 
1. Dans la section **Certificat de signature SAML**, cliquez sur **Téléchargez le certificat (Base64)** puis enregistrez le fichier du certificat sur votre ordinateur.

    ![Configure Single Sign-On](./media/gaggleamp-tutorial/tutorial_gaggleamp_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de GaggleAMP**, cliquez sur **Configurer GaggleAMP** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez l’**ID d’entité SAML et l’URL du service d’authentification unique SAML** à partir de la **section Référence rapide.**

    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_gaggleamp_configure.png) 

1. Dans une autre instance de navigateur, accédez à la page d’authentification unique SML que l’équipe du support technique Gaggle aura créée pour vous (par exemple : *https://accounts.gaggleamp.com/saml_configurations/oXH8sQcP79dOzgFPqrMTyw/edit*).

1. Sur la page **SAML SSO** (Authentification unique SAML), procédez comme suit :  
   
    ![Authentification unique GaggleAMP](./media/gaggleamp-tutorial/tutorial_gaggleamp_06.png)

    a. Sélectionnez **Autres** dans le menu déroulant **Fournisseur d’identité**.
    
    b. Dans la zone de texte **Émetteur du fournisseur d’identité**, collez la valeur de **l’URL de l’émetteur** copiée à partir du portail Azure.
    
    c. Dans la zone de texte **URL d’authentification unique du fournisseur d’identité**, collez la valeur **URL du service d’authentification unique** que vous avez copiée à partir du portail Azure.
    
    d. Ouvrez dans le Bloc-notes votre fichier **Certificate(Base64)** téléchargé, copiez son contenu dans le Presse-papiers, puis collez-le dans la zone de texte **Certificat X.509**.
    
    e. Cliquez sur **Enregistrer**.

### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD
L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

![Créer un utilisateur Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le panneau de navigation gauche du **portail Azure**, cliquez sur l’icône **Azure Active Directory**.

    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/create_aaduser_01.png) 

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.
    
    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/create_aaduser_02.png) 

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue.
 
    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/create_aaduser_03.png) 

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :
 
    ![Création d’un utilisateur de test Azure AD](./media/gaggleamp-tutorial/create_aaduser_04.png) 

    a. Dans la zone de texte **Nom**, entrez **BrittaSimon**.

    b. Dans la zone de texte **Nom d’utilisateur**, tapez **l’adresse e-mail** de Britta Simon.

    c. Sélectionnez **Afficher le mot de passe** et notez la valeur du **mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="creating-a-gaggleamp-test-user"></a>Création d’un utilisateur de test GaggleAMP

L'objectif de cette section est de créer un utilisateur appelé Britta Simon dans GaggleAMP. GaggleAMP prend en charge l'approvisionnement juste-à-temps, option activée par défaut.

Vous n’avez aucune opération à effectuer dans cette section. Un utilisateur est créé lors d’une tentative d’accès à GaggleAMP s’il n’existe pas déjà. 

### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à GaggleAMP.

![Affecter des utilisateurs][200] 

**Pour affecter Britta Simon à GaggleAMP, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **GaggleAMP**.

    ![Configurer l'authentification unique](./media/gaggleamp-tutorial/tutorial_gaggleamp_app.png) 

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202] 

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="testing-single-sign-on"></a>Test de l’authentification unique

L’objectif de cette section est de tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la vignette GaggleAMP dans le volet d’accès, vous devez être connecté automatiquement à votre application GaggleAMP.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/gaggleamp-tutorial/tutorial_general_01.png
[2]: ./media/gaggleamp-tutorial/tutorial_general_02.png
[3]: ./media/gaggleamp-tutorial/tutorial_general_03.png
[4]: ./media/gaggleamp-tutorial/tutorial_general_04.png

[100]: ./media/gaggleamp-tutorial/tutorial_general_100.png

[200]: ./media/gaggleamp-tutorial/tutorial_general_200.png
[201]: ./media/gaggleamp-tutorial/tutorial_general_201.png
[202]: ./media/gaggleamp-tutorial/tutorial_general_202.png
[203]: ./media/gaggleamp-tutorial/tutorial_general_203.png
