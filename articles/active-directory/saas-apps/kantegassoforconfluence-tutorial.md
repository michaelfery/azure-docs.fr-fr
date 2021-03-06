---
title: 'Tutoriel : Intégration d’Azure Active Directory avec Kantega SSO pour Confluence | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Kantega SSO pour Confluence.
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.assetid: d0d99c14-a6ca-45f2-bb84-633126095e7a
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/12/2017
ms.author: jeedes
ms.openlocfilehash: 92df4ea39b4d94b78c528cb7c49d409cdfd6cfbe
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55174004"
---
# <a name="tutorial-azure-active-directory-integration-with-kantega-sso-for-confluence"></a>Tutoriel : Intégration d’Azure Active Directory avec Kantega SSO pour Confluence

Dans ce didacticiel, vous allez apprendre à intégrer Kantega SSO pour Confluence avec Azure Active Directory (Azure AD).

L’intégration de Kantega SSO pour Confluence avec Azure AD offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Kantega SSO pour Confluence.
- Vous pouvez autoriser vos utilisateurs à s’authentifier automatiquement auprès de Kantega SSO pour Confluence (authentification unique) avec leurs comptes Azure AD.
- Vous pouvez gérer vos comptes à partir d’un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD avec Kantega SSO pour Confluence, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement Kantega SSO pour Confluence pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez obtenir un essai d’un mois [ici](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Kantega SSO pour Confluence à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-kantega-sso-for-confluence-from-the-gallery"></a>Ajout de Kantega SSO pour Confluence à partir de la galerie
Pour configurer l’intégration de Kantega SSO pour Confluence dans Azure AD, vous devez ajouter Kantega SSO pour Confluence à partir de la galerie à la liste des applications SaaS managées.

**Pour ajouter Kantega SSO pour Confluence à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![APPLICATIONS][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![APPLICATIONS][3]

1. Dans la zone de recherche, tapez **Kantega SSO pour Confluence**.

    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_search.png)

1. Dans le volet de résultats, sélectionnez **Kantega SSO pour Confluence**, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuration et test de l’authentification unique Azure AD
Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Kantega SSO pour Confluence sur un utilisateur de test nommé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur équivalent à l’utilisateur Azure AD dans Kantega SSO pour Confluence. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur Kantega SSO pour Confluence associé doit être établie.

Dans Kantega SSO pour Confluence, affectez la valeur du **nom d’utilisateur** dans Azure AD comme valeur du **Username** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec Kantega SSO pour Confluence, vous devez suivre les indications des sections suivantes :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Création d’un utilisateur de test Kantega SSO pour Confluence](#creating-a-kantega-sso-for-confluence-test-user)** pour avoir un équivalent de Britta Simon dans Kantega SSO pour Confluence qui soit lié à la représentation Azure AD associée.
1. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Testing Single Sign-On](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Kantega SSO pour Confluence.

**Pour configurer l’authentification unique Azure AD avec Kantega SSO pour Confluence, procédez comme suit :**

1. Sur le portail Azure, dans la page d’intégration de l’application **Kantega SSO pour Confluence**, cliquez sur **Authentification unique**.

    ![Configurer l'authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_samlbase.png)

1. En mode initié **IDP**, dans la section **Domaine et URL Kantega SSO pour Confluence**, procédez comme suit :

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_url1.png)

    a. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`

    b. Dans la zone de texte **URL de réponse** , tapez une URL au format suivant : `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`

1. En mode initié **SP**, activez **Afficher les paramètres d’URL avancés**, puis procédez comme suit :

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_url2.png)

    Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://<server-base-url>/plugins/servlet/no.kantega.saml/sp/<uniqueid>/login`

    > [!NOTE] 
    > Il ne s’agit pas de valeurs réelles. Mettez à jour ces valeurs avec l’identificateur, l’URL de réponse et l’URL de connexion réels. Ces valeurs sont reçues durant la configuration du plug-in Confluence qui est décrite plus loin dans le didacticiel.

1. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier de métadonnées sur votre ordinateur.

    ![Configure Single Sign-On](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/tutorial_general_400.png)
    
1. Dans une autre fenêtre de navigateur web, connectez-vous à votre **portail d’administration Confluence** en tant qu’administrateur.

1. Pointez sur le roue dentée, puis cliquez sur **Modules complémentaires**.
    
    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon1.png)

1. Sous **ATLASSIAN MARKETPLACE**, cliquez sur **Find new add-ons** (Trouver de nouveaux modules complémentaires). 

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon.png)

1. Recherchez **Kerberos SAML Kantega SSO pour Confluence**, puis cliquez sur le bouton **Installer** pour installer le nouveau plug-in SAML.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon2.png)

1. L’installation du plug-in démarre.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon3.png)

1. Une fois l’installation terminée. Cliquez sur **Fermer**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon33.png)

1.  Cliquez sur **Gérer**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon34.png)
    
1. Cliquez sur **Configurer** pour configurer le nouveau plug-in.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon35.png)

1. Ce nouveau plug-in figure également sous l’onglet **UTILISATEURS ET SÉCURITÉ**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon36.png)
    
1. Dans la section **SAML**. Dans le menu déroulant **Ajouter le fournisseur d’identité**, sélectionnez **Azure Active Directory (Azure AD)**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon4.png)

1. Sélectionnez le niveau d’abonnement **De base**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon5.png)     

1. Dans la section **Propriétés de l’application**, procédez comme suit : 

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon6.png)

    a. Copiez la valeur **URI ID d’application** et utilisez-la en tant que **Identifier, Reply URL, and Sign-On URL** (Identificateur, URL de réponse et URL de connexion) dans la section **Domaine et URL Kantega SSO pour Confluence** du portail Azure.

    b. Cliquez sur **Suivant**.

1. Dans la section **Metadata import** (Importation des métadonnées), procédez comme suit : 

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon7.png)

    a. Sélectionnez **Metadata file on my computer** (Fichier de métadonnées sur mon ordinateur), puis chargez le fichier de métadonnées que vous avez téléchargé à partir du portail Azure.

    b. Cliquez sur **Suivant**.

1. Dans la section **Name and SSO location** (Nom et emplacement de l’authentification unique), procédez comme suit :

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon8.png)
    
    a. Ajoutez le nom du fournisseur d’identité dans la zone de texte **Identity provider name** (Nom du fournisseur d’identité) (par exemple, Azure AD).

    b. Cliquez sur **Suivant**.

1. Vérifiez le certificat de signature, puis cliquez sur **Suivant**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon9.png)

1. Dans la section **Confluence user accounts** (Comptes d’utilisateur Confluence), procédez comme suit :

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon10.png)

    a. Sélectionnez **Create users in Confluence’s internal Directory if needed** (Créer des utilisateurs dans l’annuaire interne de Confluence si nécessaire) et entrez le nom de groupe approprié pour les utilisateurs (il peut s’agir de plusieurs groupes séparés par des virgules).

    b. Cliquez sur **Suivant**.

1. Cliquez sur **Terminer**.    

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon11.png)

1. Dans la section **Known domains for Azure AD** (Domaines connus pour Azure AD), procédez comme suit : 

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/addon12.png)

    a. Sélectionnez **Known domains** (Domaines connus) dans le volet gauche de la page.

    b. Entrez le nom de domaine dans la zone de texte **Known domains** (Domaines connus).

    c. Cliquez sur **Enregistrer**. 

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Pour en savoir plus sur la fonctionnalité de documentation incorporée, accédez à : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD
L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

![Créer un utilisateur Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le panneau de navigation gauche du **portail Azure**, cliquez sur l’icône **Azure Active Directory**.

    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/create_aaduser_01.png) 

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.
    
    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/create_aaduser_02.png) 

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue.
 
    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/create_aaduser_03.png) 

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :
 
    ![Création d’un utilisateur de test Azure AD](./media/kantegassoforconfluence-tutorial/create_aaduser_04.png) 

    a. Dans la zone de texte **Nom**, entrez **BrittaSimon**.

    b. Dans la zone de texte **Nom d’utilisateur**, tapez **l’adresse e-mail** de Britta Simon.

    c. Sélectionnez **Afficher le mot de passe** et notez la valeur du **mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="creating-a-kantega-sso-for-confluence-test-user"></a>Création d’un utilisateur de test Kantega SSO pour Confluence

Pour permettre aux utilisateurs Azure AD de se connecter à Confluence, vous devez les approvisionner dans Confluence. Dans le cas de Kantega SSO pour Confluence, cet approvisionnement est une tâche manuelle.

**Pour approvisionner un compte d’utilisateur, procédez comme suit :**

1. Connectez-vous à votre site d’entreprise Kantega SSO pour Confluence en tant qu’administrateur.

1. Pointez sur la roue dentée, puis cliquez sur **Gestion des utilisateurs**.

    ![Ajouter un employé](./media/kantegassoforconfluence-tutorial/user1.png) 

1. Dans la section Utilisateurs, cliquez sur l’onglet **Add users** (Ajouter des utilisateurs). Dans la page de boîte de dialogue **Add a User** (Ajouter un utilisateur), procédez comme suit :

    ![Ajouter un employé](./media/kantegassoforconfluence-tutorial/user2.png) 

    a. Dans la zone de texte **Username** (Nom d’utilisateur), tapez l’e-mail d’un utilisateur, par exemple, Brittasimon@contoso.com.

    b. Dans la zone de texte **Full Name** (Nom complet), tapez le nom complet d’un utilisateur, par exemple, Britta Simon.

    c. Dans la zone de texte **Email** (E-mail), tapez l’adresse e-mail d’un utilisateur, par exemple, Brittasimon@contoso.com.

    d. Dans la zone de texte **Password** (Mot de passe), tapez le mot de passe de l’utilisateur.

    e. Cliquez sur **Confirm Password** (Confirmer le mot de passe), puis entrez de nouveau le mot de passe.
    
    f. Cliquez sur le bouton **Ajouter**.

### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous permettez à Britta Simon d’utiliser l’authentification unique Azure en lui accordant l’accès à Kantega SSO pour Confluence.

![Affecter des utilisateurs][200] 

**Pour affecter Britta Simon à Kantega SSO pour Confluence, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Kantega SSO pour Confluence**.

    ![Configurer l'authentification unique](./media/kantegassoforconfluence-tutorial/tutorial_kantegassoforconfluence_app.png) 

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202] 

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="testing-single-sign-on"></a>Test de l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette Kantega SSO pour Confluence dans le volet d’accès, vous devez être automatiquement connecté à votre application Kantega SSO pour Confluence.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/kantegassoforconfluence-tutorial/tutorial_general_01.png
[2]: ./media/kantegassoforconfluence-tutorial/tutorial_general_02.png
[3]: ./media/kantegassoforconfluence-tutorial/tutorial_general_03.png
[4]: ./media/kantegassoforconfluence-tutorial/tutorial_general_04.png

[100]: ./media/kantegassoforconfluence-tutorial/tutorial_general_100.png

[200]: ./media/kantegassoforconfluence-tutorial/tutorial_general_200.png
[201]: ./media/kantegassoforconfluence-tutorial/tutorial_general_201.png
[202]: ./media/kantegassoforconfluence-tutorial/tutorial_general_202.png
[203]: ./media/kantegassoforconfluence-tutorial/tutorial_general_203.png

