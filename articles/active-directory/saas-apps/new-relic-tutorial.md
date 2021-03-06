---
title: 'Tutoriel : Intégration d’Azure Active Directory à New Relic | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et New Relic.
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.reviewer: joflore
ms.assetid: 3186b9a8-f4d8-45e2-ad82-6275f95e7aa6
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/31/2017
ms.author: jeedes
ms.openlocfilehash: a60360d8268d43d920ad878d372014fa6d9cc875
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55176860"
---
# <a name="tutorial-azure-active-directory-integration-with-new-relic"></a>Didacticiel : Intégration d’Azure Active Directory à New Relic

Dans ce didacticiel, vous allez apprendre à intégrer New Relic à Azure Active Directory (Azure AD).

L’intégration de New Relic dans Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à New Relic.
- Vous pouvez autoriser vos utilisateurs à se connecter automatiquement à New Relic (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à New Relic, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement New Relic pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de New Relic depuis la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-new-relic-from-the-gallery"></a>Ajout de New Relic depuis la galerie
Pour configurer l’intégration de New Relic à Azure AD, vous devez ajouter New Relic à votre liste d’applications SaaS gérées, à partir de la galerie.

**Pour ajouter New Relic à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **New Relic**, sélectionnez **New Relic** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![New Relic dans la liste des résultats](./media/new-relic-tutorial/tutorial_new-relic_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec New Relic, avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur New Relic correspondant dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur New Relic associé doit être établie.

Dans New Relic, affectez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec New Relic, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Créer un utilisateur de test New Relic](#create-a-new-relic-test-user)** pour obtenir un équivalent de Britta Simon dans New Relic lié à la représentation Azure AD de l’utilisateur.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application New Relic.

**Pour configurer l’authentification unique Azure AD avec New Relic, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **New Relic**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/new-relic-tutorial/tutorial_new-relic_samlbase.png)

1. Dans la section **Domaine et URL New Relic**, procédez comme suit :

    ![Informations d’authentification unique dans Domaine et URL New Relic](./media/new-relic-tutorial/tutorial_new-relic_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://rpm.newrelic.com/accounts/{acc_id}/sso/saml/login`. Veillez à remplacer par votre propre ID de nouveau compte Relic.

    b. Dans la zone de texte **Identificateur**, entrez la valeur : `rpm.newrelic.com`

1. Dans la section **Certificat de signature SAML**, cliquez sur **Téléchargez le certificat (Base64)** puis enregistrez le fichier du certificat sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/new-relic-tutorial/tutorial_new-relic_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/new-relic-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de New Relic**, cliquez sur **Configurer New Relic** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez **l’URL de déconnexion et l’URL du service d’authentification unique SAML** à partir de la **section Référence rapide**.

    ![Configuration de New Relic](./media/new-relic-tutorial/tutorial_new-relic_configure.png) 

1. Dans une autre fenêtre de navigateur web, connectez-vous au site de votre entreprise **New Relic** en tant qu’administrateur.

1. Dans le menu situé en haut, cliquez sur **Account Settings**.
   
    ![Paramètres de compte](./media/new-relic-tutorial/ic797036.png "Paramètres de compte")

1. Cliquez sur l’onglet **Security and authentication**, puis sur l’onglet **Single sign on**.
   
    ![Authentification unique](./media/new-relic-tutorial/ic797037.png "Authentification unique")

1. Dans la page de boîte de dialogue SAML, procédez comme suit :
   
    ![SAML](./media/new-relic-tutorial/ic797038.png "SAML")
   
   a. Pour charger le certificat Azure Active Directory téléchargé, cliquez sur **Choose File** .

   b. Dans la zone de texte **URL de connexion à distance**, collez la valeur de **URL du service d’authentification unique SAML** que vous avez copiée à partir du portail Azure.
   
   c. Dans la zone de texte **URL de la page de déconnexion**, collez la valeur de **URL de déconnexion** que vous avez copiée à partir du portail Azure.

   d. Cliquez sur **Save my changes**.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Pour en savoir plus sur la fonctionnalité de documentation incorporée, accédez à : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/new-relic-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/new-relic-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/new-relic-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/new-relic-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-a-new-relic-test-user"></a>Créer un utilisateur de test New Relic

Pour se connecter à New Relic, les utilisateurs d’Azure Active Directory doivent être configurés dans New Relic. Dans le cas de New Relic, l’approvisionnement est une tâche manuelle.

**Pour approvisionner un compte d’utilisateur dans New Relic, procédez comme suit :**

1. Connectez-vous à votre site d’entreprise **New Relic** en tant qu’administrateur.

1. Dans le menu situé en haut, cliquez sur **Account Settings**.
   
    ![Paramètres de compte](./media/new-relic-tutorial/ic797040.png "Paramètres de compte")

1. Dans le volet **Account** situé sur le côté gauche, cliquez sur **Summary**, puis sur **Add user**.
   
    ![Paramètres de compte](./media/new-relic-tutorial/ic797041.png "Paramètres de compte")

1. Dans la boîte de dialogue **Active users** , procédez comme suit :
   
    ![Utilisateurs actifs](./media/new-relic-tutorial/ic797042.png "Utilisateurs actifs")
   
    a. Dans la zone de texte **Email** , tapez l’adresse de messagerie d’un utilisateur Azure Active Directory valide à approvisionner.

    b. Pour **Role**, sélectionnez **User**.

    c. Cliquez sur **Add this user**.

>[!NOTE]
>Vous pouvez utiliser n’importe quel outil ou API de création de compte d’utilisateur, fourni par New Relic, pour approvisionner des comptes utilisateur AAD.
> 

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à New Relic.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à New Relic, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **New Relic**.

    ![Lien New Relic dans la liste des applications](./media/new-relic-tutorial/tutorial_new-relic_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette New Relic dans le panneau d’accès, vous êtes automatiquement connecté à votre application New Relic.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/new-relic-tutorial/tutorial_general_01.png
[2]: ./media/new-relic-tutorial/tutorial_general_02.png
[3]: ./media/new-relic-tutorial/tutorial_general_03.png
[4]: ./media/new-relic-tutorial/tutorial_general_04.png

[100]: ./media/new-relic-tutorial/tutorial_general_100.png

[200]: ./media/new-relic-tutorial/tutorial_general_200.png
[201]: ./media/new-relic-tutorial/tutorial_general_201.png
[202]: ./media/new-relic-tutorial/tutorial_general_202.png
[203]: ./media/new-relic-tutorial/tutorial_general_203.png

