---
title: Créer une fonction sur Linux à l’aide d’une image personnalisée (préversion) | Microsoft Docs
description: Découvrez comment créer une exécution d’Azure Functions sur une image Linux personnalisée.
services: functions
keywords: ''
author: ggailey777
ms.author: glenga
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: azure-functions
ms.custom: mvc
ms.devlang: azure-cli
manager: jeconnoc
ms.openlocfilehash: 7b7a239d6c96d1d5b257828ebd49c25c5bafc827
ms.sourcegitcommit: a65b424bdfa019a42f36f1ce7eee9844e493f293
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55700806"
---
# <a name="create-a-function-on-linux-using-a-custom-image-preview"></a>Créer une fonction sur Linux en utilisant une image personnalisée (préversion)

Azure Functions vous permet d’héberger vos fonctions sur Linux dans votre propre conteneur personnalisé. Vous pouvez également [héberger dans un conteneur Azure App Service par défaut](functions-create-first-azure-function-azure-cli-linux.md). Cette fonctionnalité est actuellement en préversion et requiert le [runtime Functions 2.0](functions-versions.md).

Dans ce didacticiel, vous apprenez à déployer vos fonctions vers Azure en tant qu’image personnalisée de Docker. Ce modèle est utile lorsque vous avez besoin de personnaliser l’image de conteneur intégrée d’App Service. Une image personnalisée peut vous être utile lorsque vos fonctions nécessitent une version de langue spécifique, une dépendance particulière ou une configuration qui n’est pas fournie dans l’image intégrée.

Ce didacticiel vous guide tout au long de l’utilisation d’Azure Functions Core Tools pour créer une fonction dans une image personnalisée Linux. Vous publiez cette image dans une application de fonction dans Azure, créée à l’aide d’Azure CLI.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Créer une application de fonction et un fichier Docker à l’aide de Core Tools.
> * Créer une image personnalisée à l’aide de Docker
> * Publier une image personnalisée dans un registre de conteneurs
> * Création d’un compte Azure Storage.
> * Créer un plan App Service Linux
> * Déployer une application de fonction à partir de Docker Hub
> * Ajouter des paramètres d’application à l’application de fonction

Les étapes suivantes sont prises en charge sur un ordinateur Mac, Windows ou Linux.  

## <a name="prerequisites"></a>Prérequis

Avant d’exécuter cet exemple, vous devez disposer des éléments suivants :

* Installez [Azure Core Tools version 2.x](functions-run-local.md#v2).

* Installez [Azure CLI]( /cli/azure/install-azure-cli). Cet article nécessite la version 2.0 ou ultérieure d’Azure CLI. Exécutez `az --version` pour trouver la version qui est à votre disposition.  
Vous pouvez également utiliser [Azure Cloud Shell](https://shell.azure.com/bash).

* Un abonnement Azure actif.

[!INCLUDE [quickstarts-free-trial-note](../../includes/quickstarts-free-trial-note.md)]

## <a name="create-the-local-function-app-project"></a>Créer le projet d’application de fonction local

Exécutez la commande suivante à partir de la ligne de commande pour créer un projet d’application de fonction dans le dossier `MyFunctionProj` du répertoire local actif.

```bash
func init MyFunctionProj --docker
```

Lorsque vous incluez l’option `--docker`, un fichier Docker est généré pour ce projet. Ce fichier est utilisé pour créer un conteneur personnalisé dans lequel exécuter le projet. L’image de base utilisée dépend du langage du worker runtime choisi.  

Lorsque vous y êtes invités, choisissez un worker runtime parmi les langages suivants :

* `dotnet` : crée un projet de bibliothèque de classes .NET (.csproj).
* `node` : créer un projet JavaScript.
* `python` : crée un projet Python.

Lorsque la commande s’exécute, une sortie similaire à la suivante s’affiche :

```output
Writing .gitignore
Writing host.json
Writing local.settings.json
Writing Dockerfile
```

Utilisez la commande suivante pour accéder au nouveau dossier du projet `MyFunctionProj`.

```bash
cd MyFunctionProj
```

[!INCLUDE [functions-create-function-core-tools](../../includes/functions-create-function-core-tools.md)]

[!INCLUDE [functions-update-function-code](../../includes/functions-update-function-code.md)]

[!INCLUDE [functions-run-function-test-local](../../includes/functions-run-function-test-local.md)]

## <a name="build-the-image-from-the-docker-file"></a>Créer l’image à partir du fichier Docker

Jetez un coup d’œil au _fichier Docker_ dans le dossier racine du projet. Ce fichier décrit l’environnement exigé pour exécuter l’application de fonction sur Linux. L’exemple suivant est un fichier Docker qui crée un conteneur exécutant une application de fonction sur le worker runtime JavaScript (Node.js) : 

```docker
FROM mcr.microsoft.com/azure-functions/node:2.0

ENV AzureWebJobsScriptRoot=/home/site/wwwroot
COPY . /home/site/wwwroot
```

> [!NOTE]
> Lors de l’hébergement d’une image dans un registre de conteneurs privé, vous devez ajouter les paramètres de connexion à l’application de fonction en utilisant les variables **ENV** dans le Dockerfile. Étant donné que ce didacticiel ne peut pas garantir que vous utilisez un registre privé, en tant que bonne pratique de sécurité, les paramètres de connexion sont [ajoutés après le déploiement par le biais d’Azure CLI](#configure-the-function-app).

### <a name="run-the-build-command"></a>Exécutez la commande `build`.
Dans le dossier racine, exécutez la commande [docker build](https://docs.docker.com/engine/reference/commandline/build/), puis indiquez un nom, `mydockerimage`, et une balise, `v1.0.0`. Remplacez `<docker-id>` par votre ID de compte Docker Hub. Cette commande génère l’image Docker pour le conteneur.

```bash
docker build --tag <docker-id>/mydockerimage:v1.0.0 .
```

Lorsque la commande s’exécute, une sortie similaire à la suivante s’affiche, qui est, dans ce cas, un worker runtime JavaScript :

```bash
Sending build context to Docker daemon  17.41kB
Step 1/3 : FROM mcr.microsoft.com/azure-functions/node:2.0
2.0: Pulling from azure-functions/node
802b00ed6f79: Pull complete
44580ea7a636: Pull complete
73eebe8d57f9: Pull complete
3d82a67477c2: Pull complete
8bd51cd50290: Pull complete
7bd755353966: Pull complete
Digest: sha256:480e969821e9befe7c61dda353f63298f2c4b109e13032df5518e92540ea1d08
Status: Downloaded newer image for mcr.microsoft.com/azure-functions/node:2.0
 ---> 7c71671b838f
Step 2/3 : ENV AzureWebJobsScriptRoot=/home/site/wwwroot
 ---> Running in ed1e5809f0b7
Removing intermediate container ed1e5809f0b7
 ---> 39d9c341368a
Step 3/3 : COPY . /home/site/wwwroot
 ---> 5e196215935a
Successfully built 5e196215935a
Successfully tagged <docker-id>/mydockerimage:v1.0.0
```

### <a name="test-the-image-locally"></a>Tester localement l’image
Vérifiez que l’image générée fonctionne en exécutant l’image Docker dans un conteneur local. Exécutez la commande [docker run](https://docs.docker.com/engine/reference/commandline/run/) puis passez le nom et la balise de l’image. Veillez à spécifier le port à l’aide de l’argument `-p`.

```bash
docker run -p 8080:80 -it <docker-ID>/mydockerimage:v1.0.0
```

Tandis que l’image personnalisée s’exécute dans un conteneur Docker local, vérifiez que l’application de fonction et le conteneur fonctionnent correctement en accédant à <http://localhost:8080>.

![Testez localement l’application de fonction.](./media/functions-create-function-linux-custom-image/run-image-local-success.png)

Vous pouvez tester votre fonction à nouveau, cette fois-ci dans le conteneur local avec l’URL suivante :

`http://localhost:8080/api/myhttptrigger?name=<yourname>`

Une fois que vous avez vérifié l’application de fonction dans le conteneur, arrêtez l’exécution. À présent, vous pouvez transmettre l’image personnalisée à votre compte Docker Hub.

## <a name="push-the-custom-image-to-docker-hub"></a>Envoyer (push) l’image personnalisée à Docker Hub

Un registre est une application qui héberge des images et fournit des services d’image et de conteneur. Pour partager votre image, vous devez la transférer vers un registre. Docker Hub est un registre d’images Docker qui vous permet d’héberger vos propres référentiels publics ou privés.

Avant de pousser une image, vous devez vous connecter à Docker Hub par le biais de la commande [docker login](https://docs.docker.com/engine/reference/commandline/login/). À l’invite de commandes dans la console, remplacez `<docker-id>` par votre nom de compte et tapez votre mot de passe. Pour les autres options de mot de passe Docker Hub, consultez la [documentation de la commande docker login](https://docs.docker.com/engine/reference/commandline/login/).

```bash
docker login --username <docker-id>
```

Un message « login succeeded » (connexion réussie) confirme que vous êtes connecté. Une fois connecté, vous pouvez transférer l’image à Docker Hub au moyen de la commande [docker push](https://docs.docker.com/engine/reference/commandline/push/).

```bash
docker push <docker-id>/mydockerimage:v1.0.0
```

Vérifiez que le transfert a réussi en consultant les résultats de la commande.

```bash
The push refers to a repository [docker.io/<docker-id>/mydockerimage:v1.0.0]
24d81eb139bf: Pushed
fd9e998161c9: Mounted from <docker-id>/mydockerimage
e7796c35add2: Mounted from <docker-id>/mydockerimage
ae9a05b85848: Mounted from <docker-id>/mydockerimage
45c86e20670d: Mounted from <docker-id>/mydockerimage
v1.0.0: digest: sha256:be080d80770df71234eb893fbe4d... size: 1796
```

Vous pouvez désormais utiliser cette image comme source de déploiement pour une nouvelle application de fonction dans Azure.

[!INCLUDE [functions-create-resource-group](../../includes/functions-create-resource-group.md)]

[!INCLUDE [functions-create-storage-account](../../includes/functions-create-storage-account.md)]

## <a name="create-a-linux-app-service-plan"></a>Créer un plan App Service Linux

L’hébergement Linux pour Functions n’est pas actuellement pris en charge dans les plans Consommation. Vous devez héberger des applications de conteneur Linux dans un plan App Service Linux. Pour en savoir plus sur l’hébergement, consultez [Comparaison des plans d’hébergement Azure Functions](functions-scale.md).

[!INCLUDE [app-service-plan-no-h](../../includes/app-service-web-create-app-service-plan-linux-no-h.md)]

## <a name="create-and-deploy-the-custom-image"></a>Créer et déployer l’image personnalisée

L’application de fonction héberge l’exécution de vos fonctions. Créez une application de fonction à partir de l’image Docker Hub à l’aide de la commande [az functionapp create](/cli/azure/functionapp#az-functionapp-create).

Dans la commande suivante, indiquez un nom d’application de fonction unique là où se trouve l’espace réservé `<app_name>`, et le nom du compte de stockage pour `<storage_name>`. La valeur `<app_name>` est utilisée en tant que domaine DNS par défaut pour la Function App. Pour cette raison, ce nom doit être unique sur l’ensemble des applications dans Azure. Comme précédemment, `<docker-id>` est le nom de votre compte Docker.

```azurecli-interactive
az functionapp create --name <app_name> --storage-account  <storage_name>  --resource-group myResourceGroup \
--plan myAppServicePlan --deployment-container-image-name <docker-id>/mydockerimage:v1.0.0
```

Une fois la Function App créée, Azure CLI affiche des informations semblables à celles de l’exemple suivant :

```json
{
  "availabilityState": "Normal",
  "clientAffinityEnabled": true,
  "clientCertEnabled": false,
  "containerSize": 1536,
  "dailyMemoryTimeQuota": 0,
  "defaultHostName": "quickstart.azurewebsites.net",
  "enabled": true,
  "enabledHostNames": [
    "quickstart.azurewebsites.net",
    "quickstart.scm.azurewebsites.net"
  ],
   ....
    // Remaining output has been truncated for readability.
}
```

Le paramètre _deployment-container-image-name_ indique l’image hébergée sur Docker Hub à utiliser pour créer l’application de fonction.

## <a name="configure-the-function-app"></a>Configurer l’application de fonction

La fonction a besoin que la chaîne de connexion se connecte au compte de stockage par défaut. Lorsque vous publiez votre image personnalisée sur un compte de conteneur privé, préférez plutôt définir ces paramètres d’application comme des variables d’environnement dans le Dockerfile au moyen de l’[instruction ENV](https://docs.docker.com/engine/reference/builder/#env), ou équivalent.

Dans ce cas, `<storage_account>` est le nom du compte de stockage Blob que vous avez créé. Pour afficher la chaîne de connexion, exécutez la commande [az storage account show-connection-string](/cli/azure/storage/account). Ajoutez ces paramètres d’application dans l’application de fonction à l’aide de la commande [az functionapp config appsettings set](/cli/azure/functionapp/config/appsettings#az-functionapp-config-appsettings-set).

```azurecli-interactive
storageConnectionString=$(az storage account show-connection-string \
--resource-group myResourceGroup --name <storage_account> \
--query connectionString --output tsv)

az functionapp config appsettings set --name <function_app> \
--resource-group myResourceGroup \
--settings AzureWebJobsDashboard=$storageConnectionString \
AzureWebJobsStorage=$storageConnectionString
```

> [!NOTE]
> Si votre conteneur est privé, vous devez également définir les paramètres d’application suivants :  
> - DOCKER_REGISTRY_SERVER_USERNAME  
> - DOCKER_REGISTRY_SERVER_PASSWORD  
>
> Vous devez arrêter puis redémarrer votre application de fonction pour que ces valeurs soient récupérées.

Vous pouvez désormais tester vos fonctions qui s’exécutent sur Linux dans Azure.

[!INCLUDE [functions-test-function-code](../../includes/functions-test-function-code.md)]

[!INCLUDE [functions-cleanup-resources](../../includes/functions-cleanup-resources.md)]

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à :

> [!div class="checklist"]
> * Créer une application de fonction et un fichier Docker à l’aide de Core Tools.
> * Créer une image personnalisée à l’aide de Docker
> * Publier une image personnalisée dans un registre de conteneurs
> * Création d’un compte Azure Storage.
> * Créer un plan App Service Linux
> * Déployer une application de fonction à partir de Docker Hub
> * Ajouter des paramètres d’application à l’application de fonction

Découvrez comment activer la fonctionnalité d’intégration continue intégrée au cœur de la plateforme App Service. Vous pouvez configurer votre application de fonction de telle sorte que le conteneur soit redéployé lorsque vous mettez à jour votre image dans Hub Docker.

> [!div class="nextstepaction"] 
> [Déploiement continu avec Web App pour conteneurs](../app-service/containers/app-service-linux-ci-cd.md)
