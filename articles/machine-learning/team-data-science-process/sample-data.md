---
title: Échantillonner données dans des emplacements de stockage Azure différents - Team Data Science Process
description: Échantillonnez des données dans des conteneurs d’objets blob Azure, SQL Server et des tables Hive pour une taille réduite, mais plus représentative et facile à gérer.
services: machine-learning
author: marktab
manager: cgronlun
editor: cgronlun
ms.service: machine-learning
ms.subservice: team-data-science-process
ms.topic: article
ms.date: 11/13/2017
ms.author: tdsp
ms.custom: seodec18, previous-author=deguhath, previous-ms.author=deguhath
ms.openlocfilehash: fc91aec80f74488125649cfe807757ba5ae49c9b
ms.sourcegitcommit: 698a3d3c7e0cc48f784a7e8f081928888712f34b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55466334"
---
# <a name="heading"></a>Échantillonner des données dans des conteneurs d'objets blob Azure, SQL Server et des tables Hive

Les articles suivants expliquent comment échantillonner les données stockées dans l’un des trois emplacements Azure :

* Les [**données de conteneurs d’objets blob Azure**](sample-data-blob.md) sont échantillonnées par le biais de leur téléchargement par programmation, puis de leur échantillonnage à l’aide d’un exemple de code Python.
* Les [**données SQL Server**](sample-data-sql-server.md) sont échantillonnées à l’aide de SQL et du langage de programmation Python. 
* Les [**données de tables Hive**](sample-data-hive.md) sont échantillonnées à l’aide de requêtes Hive.

Cette tâche d’échantillonnage est une étape du [processus TDSP (Team Data Science Process)](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/).

**Pourquoi échantillonner des données ?**

Si vous prévoyez d’analyser un jeu de données volumineux, il est généralement recommandé de sous-échantillonner les données afin de réduire leur taille sous une forme plus facilement exploitable, mais toujours représentative. Cette opération facilite la compréhension et l’exploration des données, ainsi que la conception de fonctionnalités. Son rôle dans le processus Cortana Analytics consiste à permettre le prototypage rapide des fonctions de traitement des données et des modèles d’apprentissage automatique.

