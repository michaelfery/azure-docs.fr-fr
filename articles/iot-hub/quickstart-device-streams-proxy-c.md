---
title: Démarrage rapide C sur les flux d’appareil Azure IoT Hub pour SSH/RDP (préversion) | Microsoft Docs
description: Dans ce guide de démarrage rapide, vous allez exécuter un exemple d’application C qui joue le rôle d’un proxy pour activer des scénarios SSH/RDP sur des flux d’appareil IoT Hub.
author: rezasherafat
manager: briz
ms.service: iot-hub
services: iot-hub
ms.devlang: c
ms.topic: quickstart
ms.custom: mvc
ms.date: 01/15/2019
ms.author: rezas
ms.openlocfilehash: d0fc8d68b3412c2c43a88e3a9484dab3a150b811
ms.sourcegitcommit: b4755b3262c5b7d546e598c0a034a7c0d1e261ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54886269"
---
# <a name="quickstart-sshrdp-over-iot-hub-device-streams-using-c-proxy-application-preview"></a>Démarrage rapide : SSH/RDP sur des flux d’appareil IoT Hub à l’aide d’une application proxy C (préversion)

[!INCLUDE [iot-hub-quickstarts-4-selector](../../includes/iot-hub-quickstarts-4-selector.md)]

Les [flux d’appareil IoT Hub](./iot-hub-device-streams-overview.md) permettent aux applications de service et d’appareil de communiquer de manière sécurisée à travers des pare-feux. Consultez [cette page](./iot-hub-device-streams-overview.md#local-proxy-sample-for-ssh-or-rdp) pour obtenir une vue d’ensemble de la configuration.

Le présent document décrit la configuration du tunneling du trafic SSH (qui utilise le port 22) par le biais de flux d’appareil. La configuration pour le trafic RDP est similaire et nécessite une simple modification. Étant donné que les flux d’appareil ne dépendent pas des applications et des protocoles, vous pouvez modifier le présent guide de démarrage rapide (en modifiant les ports de communication) pour prendre en charge d’autres types de trafic d’application.

## <a name="how-it-works"></a>Fonctionnement
La figure ci-dessous illustre la manière dont la configuration des programmes de proxys locaux d’appareil (et de service) active une connectivité de bout en bout entre le client SSH et les processus de démon SSH. Dans la préversion publique, le SDK C prend uniquement en charge les flux d’appareil côté appareil. Ainsi, le présent guide de démarrage rapide aborde uniquement les instructions permettant d’exécuter l’application proxy locale de l’appareil. Vous devez exécuter une application proxy locale de service complémentaire, disponible dans les guides de [démarrage rapide C#](./quickstart-device-streams-proxy-csharp.md) ou de [démarrage rapide Node.js](./quickstart-device-streams-proxy-nodejs.md).

![Texte de remplacement](./media/quickstart-device-streams-proxy-csharp/device-stream-proxy-diagram.svg "Configuration de proxy local")


1. Le proxy local de service se connecte au hub IoT et lance un flux d’appareil sur l’appareil cible.

2. Le proxy local d’appareil termine la négociation du lancement du flux et établit un tunnel de streaming de bout en bout par le biais du point de terminaison de streaming IoT Hub côté service.

3. Le proxy local d’appareil se connecte au démon SSH (SSHD) qui écoute le port 22 de l’appareil (ce dernier est configurable, comme décrit [ci-dessous](#run-the device-local-proxy-application)).

4. Le proxy local de service attend de nouvelles connexions SSH de l’utilisateur en écoutant un port désigné, dans cet exemple, le port 2222 (celui-ci est également configurable, comme décrit [ci-dessous](#run-the-device-local-proxy-application)). Quand l’utilisateur se connecte par le biais d’un client SSH, le tunnel permet au trafic d’application SSH d’être transféré entre les programmes client et serveur SSH.

> [!NOTE]
> Le trafic SSH envoyé sur un flux d’appareil est traité par tunnel par le biais d’un point de terminaison de streaming IoT Hub, plutôt que directement entre le service et l’appareil. Ce processus offre [ces avantages](./iot-hub-device-streams-overview.md#benefits). De plus, la figure illustre le démon SSH en cours d’exécution sur le même appareil (ou ordinateur) en tant que proxy local de l’appareil. Dans ce guide de démarrage rapide, le fait de fournir l’adresse IP du démon SSH permet au proxy local de l’appareil et au démon de s’exécuter également sur des ordinateurs différents.

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.

## <a name="prerequisites"></a>Prérequis

* Installez [Visual Studio 2017](https://www.visualstudio.com/vs/) avec la charge de travail [« Développement Desktop en C++ »](https://www.visualstudio.com/vs/support/selecting-workloads-visual-studio-2017/) activée.
* Installez la dernière version de [Git](https://git-scm.com/download/).

## <a name="prepare-the-development-environment"></a>Préparer l’environnement de développement

Pour ce guide de démarrage rapide, vous devez utiliser le [kit SDK Azure IoT device SDK for C](iot-hub-device-sdk-c-intro.md). Vous allez préparer un environnement de développement pour cloner et générer le [SDK C Azure IoT](https://github.com/Azure/azure-iot-sdk-c) à partir de GitHub. Le kit SDK sur GitHub comprend l’exemple de code utilisé dans ce guide de démarrage rapide. 


1. Téléchargez la version 3.11.4 du [système de génération de CMake](https://cmake.org/download/). Vérifiez le binaire téléchargé à l’aide de la valeur de hachage de chiffrement correspondante. L’exemple suivant utilise Windows PowerShell pour vérifier le hachage de chiffrement pour la version 3.11.4 de la distribution MSI x64 :

    ```PowerShell
    PS C:\Downloads> $hash = get-filehash .\cmake-3.11.4-win64-x64.msi
    PS C:\Downloads> $hash.Hash -eq "56e3605b8e49cd446f3487da88fcc38cb9c3e9e99a20f5d4bd63e54b7a35f869"
    True
    ```
    
    Les valeurs de hachage suivantes pour la version 3.11.4 étaient celles indiquées sur le site de CMake au moment de la rédaction de cet article :

    ```
    6dab016a6b82082b8bcd0f4d1e53418d6372015dd983d29367b9153f1a376435  cmake-3.11.4-Linux-x86_64.tar.gz
    72b3b82b6d2c2f3a375c0d2799c01819df8669dc55694c8b8daaf6232e873725  cmake-3.11.4-win32-x86.msi
    56e3605b8e49cd446f3487da88fcc38cb9c3e9e99a20f5d4bd63e54b7a35f869  cmake-3.11.4-win64-x64.msi
    ```

    Il est important que les composants requis Visual Studio (Visual Studio et la charge de travail « Développement Desktop en C++ ») soient installés sur votre machine, **avant** de commencer l’installation de l’élément `CMake`. Une fois les composants requis en place et le téléchargement effectué, installez le système de génération de CMake.

2. Ouvrez une invite de commandes ou l’interpréteur de commandes Git Bash. Exécutez la commande suivante pour cloner le référentiel GitHub du [Kit de développement logiciel (SDK) Azure IoT pour C](https://github.com/Azure/azure-iot-sdk-c) :
    
    ```
    git clone https://github.com/Azure/azure-iot-sdk-c.git --recursive
    ```
    Pour le moment, ce référentiel a une taille d’environ 220 Mo. Attendez-vous à ce que cette opération prenne plusieurs minutes.


3. Créez un sous-répertoire `cmake` dans le répertoire racine du référentiel Git et accédez à ce dossier. 

    ```
    cd azure-iot-sdk-c
    git checkout public-preview
    mkdir cmake
    cd cmake
    ```

4. Exécutez la commande suivante qui génère une version du kit SDK propre à votre plateforme cliente de développement. Sur Windows, une solution Visual Studio pour l’appareil simulé est générée dans le répertoire `cmake`. 

```
    # In Linux
    cmake ..
    make -j
```

Sur Windows, exécutez les commandes suivantes à l’invite de commandes développeur Visual Studio 2015 ou 2017 :

```
    # In Windows
    # For VS2015
    $ cmake .. -G "Visual Studio 15 2015"
    
    # Or for VS2017
    $ cmake .. -G "Visual Studio 15 2017

    # Then build the project
    cmake --build . -- /m /p:Configuration=Release
```
    

## <a name="create-an-iot-hub"></a>Créer un hub IoT

[!INCLUDE [iot-hub-include-create-hub](../../includes/iot-hub-include-create-hub-device-streams.md)]

## <a name="register-a-device"></a>Inscrire un appareil

Un appareil doit être inscrit dans votre hub IoT pour pouvoir se connecter. Dans cette section, vous allez utiliser Azure Cloud Shell avec l’[extension IoT](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot?view=azure-cli-latest) pour inscrire un appareil simulé.

1. Exécutez les commandes suivantes dans Azure Cloud Shell pour ajouter l’extension CLI IoT Hub et créer l’identité d’appareil. 

   **YourIoTHubName** : Remplacez l’espace réservé ci-dessous par le nom que vous avez choisi pour votre hub IoT.

   **MyDevice** : il s’agit du nom donné à l’appareil inscrit. Utilisez MyDevice comme indiqué. Si vous choisissez un autre nom pour votre appareil, vous devez également utiliser ce nom pour l’ensemble de cet article et mettre à jour le nom de l’appareil dans les exemples d’application avant de les exécuter.

    ```azurecli-interactive
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name YourIoTHubName --device-id MyDevice
    ```

2. Exécutez les commandes suivantes dans Azure Cloud Shell pour obtenir la _chaîne de connexion d’appareil_ pour celui que vous venez d’inscrire :

   **YourIoTHubName** : Remplacez l’espace réservé ci-dessous par le nom que vous avez choisi pour votre hub IoT.

    ```azurecli-interactive
    az iot hub device-identity show-connection-string --hub-name YourIoTHubName --device-id MyDevice --output table
    ```

    Notez la chaîne de connexion de l’appareil, qui ressemble à l’exemple suivant :

   `HostName={YourIoTHubName}.azure-devices.net;DeviceId=MyDevice;SharedAccessKey={YourSharedAccessKey}`

    Vous utiliserez cette valeur plus loin dans ce démarrage rapide.


## <a name="ssh-to-a-device-via-device-streams"></a>Liaison SSH à un appareil par le biais de flux d’appareil

### <a name="run-the-device-local-proxy-application"></a>Exécuter l’application proxy locale de l’appareil

- Modifiez le fichier source `iothub_client/samples/iothub_client_c2d_streaming_proxy_sample/iothub_client_c2d_streaming_proxy_sample.c` et indiquez la chaîne de connexion de votre appareil, l’adresse IP/le nom d’hôte de l’appareil cible, ainsi que le port RDP 22 :
```C
  /* Paste in the your iothub connection string  */
  static const char* connectionString = "[Connection string of IoT Hub]";
  static const char* localHost = "[IP/Host of your target machine]"; // Address of the local server to connect to.
  static const size_t localPort = 22; // Port of the local server to connect to.
```

- Compilez l’exemple comme suit :

```
    # In Linux
    # Go to the sample's folder cmake/iothub_client/samples/iothub_client_c2d_streaming_proxy_sample
    $ make -j


    # In Windows
    # Go to cmake at root of repository
    cmake --build . -- /m /p:Configuration=Release
```

- Exécutez le programme compilé sur l’appareil :
```
    # In Linux
    # Go to sample's folder cmake/iothub_client/samples/iothub_client_c2d_streaming_proxy_sample
    $ ./iothub_client_c2d_streaming_proxy_sample

    # In Windows
    # Go to sample's release folder cmake\iothub_client\samples\iothub_client_c2d_streaming_proxy_sample\Release
    iothub_client_c2d_streaming_proxy_sample.exe
```

### <a name="run-the-service-local-proxy-application"></a>Exécuter l’application proxy locale du service

Comme indiqué [ci-dessus](#how-it-works), l’établissement d’un flux de bout en bout pour traiter par tunnel le trafic SSH nécessite un proxy local à chaque extrémité (c.-à-d., le service et l’appareil). Mais, dans la préversion publique, le SDK C IoT Hub prend uniquement en charge les flux d’appareil côté appareil. Pour le proxy local de service, reportez-vous plutôt aux guides complémentaires de [démarrage rapide C#](./quickstart-device-streams-proxy-csharp.md) ou de [démarrage rapide Node.js](./quickstart-device-streams-proxy-nodejs.md).


### <a name="establish-an-ssh-session"></a>Établir une session SSH

Si nous supposons que les proxys locaux de l’appareil et du service sont tous les deux en cours d’exécution, utilisez à présent votre programme client SSH et connectez-vous au proxy local du service sur le port 2222 (au lieu du démon SSH directement). 

```
ssh <username>@localhost -p 2222
```

À ce stade, l’invite de connexion SSH s’affiche pour vous permettre d’entrer vos informations d’identification.


Sortie de console sur le proxy local de l’appareil qui se connecte au démon SSH à l’adresse `IP_address:22` : ![Texte de remplacement](./media/quickstart-device-streams-proxy-c/device-console-output.PNG "Sortie du proxy local d’appareil")

Sortie de console du programme client SSH (le client SSH communique avec le démon SSH en se connectant au port 22 où le proxy local du service est à l’écoute) : ![Texte de remplacement](./media/quickstart-device-streams-proxy-csharp/ssh-console-output.png "Sortie du client SSH")

## <a name="clean-up-resources"></a>Supprimer des ressources

[!INCLUDE [iot-hub-quickstarts-clean-up-resources](../../includes/iot-hub-quickstarts-clean-up-resources-device-streams.md)]

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez configuré un hub IoT, inscrit un appareil, déployé un programme proxy local d’appareil (et de service) pour établir un flux d’appareil par le biais d’IoT Hub, puis vous avez utilisé les proxys pour traiter par tunnel le trafic SSH.

Utilisez les liens ci-dessous pour en savoir plus sur les flux d’appareil :

> [!div class="nextstepaction"]
> [Vue d’ensemble des flux d’appareil](./iot-hub-device-streams-overview.md)
