---
title: Configurer les informations de sécurité pour utiliser l’e-mail - Azure Active Directory | Microsoft Docs
description: Configurez vos informations de sécurité pour vérifier votre identité au moyen de votre adresse e-mail professionnelle ou scolaire.
services: active-directory
author: eross-msft
manager: daveba
ms.reviewer: sahenry
ms.service: active-directory
ms.workload: identity
ms.subservice: user-help
ms.topic: conceptual
ms.date: 07/30/2018
ms.author: lizross
ms.openlocfilehash: 62b6f7306cb2492d4232b3b42021db721a0b374c
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55189287"
---
# <a name="set-up-security-info-to-use-email-preview"></a>Configurer les informations de sécurité pour utiliser l’e-mail (préversion)

[!INCLUDE [preview-notice](../../../includes/active-directory-end-user-preview-notice-security-info.md)]

Pour configurer vos informations de sécurité, vous devez vous connecter à votre compte professionnel ou scolaire et suivre la procédure d’inscription. Si vous n’avez jamais configuré vos informations de sécurité, vous êtes amené à le faire maintenant.

## <a name="set-up-email"></a>Configurer la messagerie

En fonction des paramètres de votre organisation, vous pouvez être invité à ajouter une adresse e-mail à vos informations de sécurité lorsque vous vous connectez. La configuration d’une adresse e-mail dans les informations de sécurité peut sinon s’effectuer en suivant les étapes dans [Gérer vos informations de sécurité](security-info-manage-settings.md).

>[!Note]
>Nous vous recommandons d’utiliser un compte de messagerie dont l’accès n’exige pas votre mot de passe réseau.<br>Si vous ne voyez pas l’option d’e-mail, il est possible que votre organisation ne vous autorise pas à utiliser un e-mail à des fins de vérification. Si tel est le cas, vous devez choisir une autre méthode, ou contacter votre administrateur pour obtenir de l’aide.

### <a name="to-use-your-email-address"></a>Pour utiliser votre adresse e-mail

1. Sélectionnez l’option **E-mail**, puis tapez votre adresse e-mail dans la zone. Cette adresse e-mail ne peut pas être votre e-mail professionnel ou scolaire.

     ![Page d’informations de sécurité, avec la zone d’entrée de l’e-mail](media/security-info/security-info-keep-secure-setup-email.png)

2. Vérifiez l’arrivée d’un e-mail provenant de Microsoft et adressé à votre organisation, tapez le code de vérification qu’il contient dans la zone **Vérifier votre adresse e-mail**, puis sélectionnez **Terminé**.

     ![Page d’informations de sécurité, avec la zone d’entrée du code de vérification de l’e-mail](media/security-info/security-info-verify-email.png)

    >[!Note]
    >Si vous ne voyez aucun e-mail de Microsoft pour votre organisation, assurez-vous d’avoir correctement tapé votre adresse e-mail, puis vérifiez vos dossiers de courrier indésirable ou de spam.

3. Dans la page **Protéger votre compte**, sélectionnez **Terminé**.

    Vos informations de sécurité sont mises à jour pour utiliser votre adresse e-mail à des fins de contrôle de votre identité lors de la réinitialisation de mot de passe.

## <a name="additional-security-info-options"></a>Options d’informations de sécurité supplémentaires

Vous avez la possibilité de choisir la façon d’être contacté par votre organisation pour la vérification de votre identité, en fonction de ce que vous essayez de faire. Ces options sont les suivantes :

- **Application d’authentification.** Téléchargez et utilisez une application d’authentification pour obtenir une notification d’approbation ou un code d’approbation généré de manière aléatoire pour la réinitialisation du mot de passe ou la vérification en deux étapes. Pour obtenir des instructions détaillées sur la configuration et l’utilisation de l’application Microsoft Authenticator, consultez [Configurer les informations de sécurité pour utiliser une application d’authentification](security-info-setup-auth-app.md).

- **SMS sur appareil mobile.** Entrez votre numéro de téléphone mobile et recevez un code par SMS, à utiliser pour la vérification en deux étapes ou la réinitialisation de mot de passe. Pour obtenir des instructions détaillées sur la vérification de votre identité par SMS, consultez [Configurer les informations de sécurité pour utiliser la messagerie texte (SMS)](security-info-setup-text-msg.md).

- **Appel sur téléphone mobile ou téléphone professionnel.** Entrez votre numéro de téléphone mobile et recevez un appel pour la réinitialisation de mot de passe ou la vérification en deux étapes. Pour obtenir des instructions détaillées sur la vérification de votre identité au moyen d’un numéro de téléphone, consultez [Configurer les informations de sécurité pour utiliser un appel téléphonique](security-info-setup-phone-number.md).

- **Questions de sécurité.** Répondez à certaines questions de sécurité créées par votre administrateur pour votre organisation. Cette option est uniquement disponible pour la réinitialisation du mot de passe et non pour la vérification en deux étapes. Pour des instructions pas à pas sur la façon de configurer vos questions de sécurité, consultez l’article [Configurer les informations de sécurité pour utiliser les questions de sécurité](security-info-setup-questions.md).
    
    >[!Note]
    >Si certaines de ces options ne sont pas disponibles, il est très probable que votre organisation n’autorise pas ces méthodes. Si tel est le cas, vous devez choisir une autre méthode ou contacter votre administrateur pour obtenir de l’aide.

## <a name="next-steps"></a>Étapes suivantes

- Si vous devez mettre à jour vos informations de sécurité, suivez les instructions dans l’article [Manage your security info](security-info-manage-settings.md) (Gérer vos informations de sécurité).

- Si vous avez perdu ou oublié votre mot de passe, réinitialisez-le à partir du [portail de réinitialisation de mot de passe](https://passwordreset.microsoftonline.com/), ou suivez les étapes de l’article [Réinitialiser votre mot de passe professionnel ou scolaire](user-help-reset-password.md).

- Obtenez des conseils de dépannage et de l’aide pour les problèmes de connexion en consultant l’article [Quand vous ne pouvez pas vous connecter à votre compte Microsoft](https://support.microsoft.com/help/12429/microsoft-account-sign-in-cant).
