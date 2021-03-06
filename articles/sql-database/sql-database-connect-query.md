---
title: 'Démarrage rapide : se connecter à Azure SQL Database et interroger la base de données | Microsoft Docs'
description: Cet article de démarrage rapide sur Azure SQL Database explique comment se connecter à une base de données SQL Azure et l’interroger.
services: sql-database
ms.service: sql-database
ms.subservice: ''
ms.custom: ''
ms.devlang: ''
ms.topic: quickstart
author: CarlRabeler
ms.author: carlrab
ms.reviewer: ''
manager: craigg
ms.date: 11/01/2018
ms.openlocfilehash: 613b4cf2b08269259a4608a6960b815777cd0ae9
ms.sourcegitcommit: 4eeeb520acf8b2419bcc73d8fcc81a075b81663a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53608032"
---
# <a name="quickstarts-azure-sql-database-connect-and-query"></a>Guides de démarrage rapide : Connexion et interrogation d’Azure SQL Database

Le document suivant contient des liens vers des exemples Azure expliquant comment se connecter à une base de données SQL Azure et l’interroger. Il contient également des recommandations pour la sécurité de niveau transport.

## <a name="quickstarts"></a>Démarrages rapides

| |  |
|---|---|
|[SQL Server Management Studio](sql-database-connect-query-ssms.md)|Ce guide de démarrage rapide montre comment utiliser SSMS pour se connecter à une base de données SQL Azure, puis utiliser des instructions Transact-SQL pour interroger, insérer, mettre à jour et supprimer des données dans la base de données.|
|[Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/quickstart-sql-database?toc=/azure/sql-database/toc.json)|Ce guide de démarrage rapide explique comment utiliser Azure Data Studio pour se connecter à une base de données SQL Azure, puis recourir à des instructions T-SQL (Transact-SQL) pour créer le TutorialDB utilisé dans les tutoriels Azure Data Studio.|
|[Portail Azure](sql-database-connect-query-portal.md)|Ce guide de démarrage rapide indique comment utiliser l’éditeur de requête pour se connecter à une base de données SQL, puis utiliser les instructions Transact-SQL pour interroger, insérer, mettre à jour et supprimer des données dans la base de données.|
|[Visual Studio Code](sql-database-connect-query-vscode.md)|Ce guide de démarrage rapide explique comment utiliser Visual Studio Code pour se connecter à une base de données SQL Azure, puis utiliser des instructions Transact-SQL pour interroger, insérer, mettre à jour et supprimer des données dans la base de données.|
|[.NET avec Visual Studio](sql-database-connect-query-dotnet-visual-studio.md)|Ce démarrage rapide explique comment utiliser .NET Framework pour créer un programme C# avec Visual Studio en vue de se connecter à une base de données SQL Azure et recourir à des instructions Transact-SQL pour interroger des données.|
|[.NET Core](sql-database-connect-query-dotnet-core.md)|Ce démarrage rapide explique comment utiliser .NET Core sur Windows/Linux/macOS pour créer un programme C# en vue de se connecter à une base de données SQL Azure et recourir à des instructions Transact-SQL pour interroger des données.|
|[Go](sql-database-connect-query-go.md)|Ce démarrage rapide explique comment utiliser Go pour se connecter à une base de données SQL Azure. Les instructions Transact-SQL permettant d’interroger et de modifier des données sont également présentées.|
|[Java](sql-database-connect-query-java.md)|Ce démarrage rapide explique comment utiliser Java pour se connecter à une base de données SQL Azure et se servir d’instructions Transact-SQL pour interroger des données.|
|[Node.JS](sql-database-connect-query-nodejs.md)|Ce démarrage rapide explique comment utiliser Node.js pour créer un programme en vue de se connecter à une base de données SQL Azure et recourir à des instructions Transact-SQL pour interroger des données.|
|[PHP](sql-database-connect-query-php.md)|Ce démarrage rapide explique comment utiliser PHP pour créer un programme en vue de se connecter à une base de données SQL Azure et recourir à des instructions Transact-SQL pour interroger des données.|
|[Python](sql-database-connect-query-python.md)|Ce démarrage rapide explique comment utiliser Python pour se connecter à une base de données SQL Azure et se servir d’instructions Transact-SQL pour interroger des données. |
|[Ruby](sql-database-connect-query-ruby.md)|Ce démarrage rapide explique comment utiliser Ruby pour créer un programme en vue de se connecter à une base de données SQL Azure et recourir à des instructions Transact-SQL pour interroger des données.|
|||

## <a name="tls-considerations-for-sql-database-connectivity"></a>Considérations relatives au protocole TLS pour la connectivité de SQL Database
Le protocole TLS (Transport Layer Security) est utilisé par tous les pilotes fournis et pris en charge par Microsoft pour la connexion à Azure SQL Database. Aucune configuration spéciale n’est nécessaire. Pour l’ensemble des connexions à SQL Server ou à Azure SQL Database, nous recommandons que toutes les applications définissent les configurations suivantes ou leurs équivalents :

 - **Encrypt = On**
 - **TrustServerCertificate = Off**

Certains systèmes utilisent des mots clés différents, mais équivalents pour ces configurations. Ces configurations garantissent que le pilote du client vérifie l’identité du certificat TLS provenant du serveur.

Nous vous recommandons également de désactiver les protocoles TLS 1.1 et 1.0 sur le client si vous devez respecter la norme de sécurité des données de l’industrie des cartes de paiement (PCI - DSS).

Les pilotes autres que Microsoft peuvent ne pas utiliser le protocole TLS par défaut. Cela peut être un facteur à prendre en compte lors de la connexion à Azure SQL Database. Il se peut que les applications présentent des pilotes incorporés qui ne permettent pas de contrôler ces paramètres de connexion. Nous vous recommandons d’examiner la sécurité de ces pilotes et applications avant de les utiliser sur les systèmes qui interagissent avec des données sensibles.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’architecture de connectivité, consultez [Architecture de connectivité Azure SQL Database](sql-database-connectivity-architecture.md).