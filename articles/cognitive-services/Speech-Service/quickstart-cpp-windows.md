---
title: 'Démarrage rapide : Reconnaissance vocale, C++ (Windows) - Services de reconnaissance vocale'
titleSuffix: Azure Cognitive Services
description: Découvrez comment exécuter la reconnaissance vocale en C++ sur Windows Desktop à l’aide du kit SDK Service Speech
services: cognitive-services
author: wolfma61
manager: cgronlun
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: quickstart
ms.date: 12/13/2018
ms.author: wolfma
ms.openlocfilehash: 17bc5fb4ed059c0922e85e467cbafbd5a90299b0
ms.sourcegitcommit: 95822822bfe8da01ffb061fe229fbcc3ef7c2c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55221638"
---
# <a name="quickstart-recognize-speech-in-c-on-windows-by-using-the-speech-sdk"></a>Démarrage rapide : Reconnaissance vocale en C++ sur Windows à l’aide du kit SDK de reconnaissance vocale

[!INCLUDE [Selector](../../../includes/cognitive-services-speech-service-quickstart-selector.md)]

Dans cet article, vous créez une application console C++ pour Windows. Vous utilisez le [kit SDK Speech](speech-sdk.md) de Cognitive Services pour transcrire la reconnaissance vocale en temps réel à partir du microphone de votre PC. L’application est créée avec le [package NuGet du kit SDK Speech](https://aka.ms/csspeech/nuget) et Microsoft Visual Studio 2017 (toute édition).

## <a name="prerequisites"></a>Prérequis

Vous avez besoin d’une clé d’abonnement au service Speech pour suivre ce guide de démarrage rapide. Vous pouvez en obtenir une gratuitement. Consultez [Essayer le service Speech gratuitement](get-started.md) pour plus d’informations.

## <a name="create-a-visual-studio-project"></a>Créer un projet Visual Studio

[!INCLUDE [](../../../includes/cognitive-services-speech-service-quickstart-cpp-create-proj.md)]

## <a name="add-sample-code"></a>Ajouter un exemple de code

1. Ouvrez le fichier source *helloworld.cpp*. Remplacez tout le code sous l’instruction include initiale (`#include "stdafx.h"` ou `#include "pch.h"`) par le code suivant :

   [!code-cpp[Quickstart Code](~/samples-cognitive-services-speech-sdk/quickstart/cpp-windows/helloworld/helloworld.cpp#code)]

1. Dans le même fichier, remplacez la chaîne `YourSubscriptionKey` par votre clé d’abonnement.

1. Remplacez la chaîne `YourServiceRegion` par la [région](regions.md) associée à votre abonnement (par exemple, `westus` pour l’abonnement à un essai gratuit).

1. Enregistrez les modifications apportées au projet.

## <a name="build-and-run-the-app"></a>Générer et exécuter l’application

1. Générez l’application. Dans la barre de menus, choisissez **Générer** > **Générer la solution**. Le code doit se compiler sans erreur.

   ![Capture d’écran de l’application Visual Studio, avec l’option Générer la solution mise en surbrillance](media/sdk/qs-cpp-windows-06-build.png)

1. Lancez l’application. Dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage**, ou appuyez sur **F5**.

   ![Capture d’écran de l’application Visual Studio, avec l’option Démarrer le débogage mise en surbrillance](media/sdk/qs-cpp-windows-07-start-debugging.png)

1. Une fenêtre de console s’affiche vous invitant à dire quelque chose. Prononcez une phrase ou quelques mots en anglais. Votre production orale est transmise au service Speech, et transcrite en texte qui apparaît dans la même fenêtre.

   ![Capture d’écran de la sortie de la console après une reconnaissance réussie](media/sdk/qs-cpp-windows-08-console-output-release.png)

## <a name="next-steps"></a>Étapes suivantes

Des exemples supplémentaires, qui montrent notamment comment lire une entrée orale à partir d’un fichier audio, sont disponibles sur GitHub.

> [!div class="nextstepaction"]
> [Explorer des exemples C++ sur GitHub](https://aka.ms/csspeech/samples)

## <a name="see-also"></a>Voir aussi

- [Personnaliser les modèles acoustiques](how-to-customize-acoustic-models.md)
- [Personnaliser les modèles de langage](how-to-customize-language-model.md)
