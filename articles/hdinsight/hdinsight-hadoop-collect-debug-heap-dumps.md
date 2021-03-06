---
title: Déboguer et analyser les services Apache Hadoop avec des dumps de tas – Azure
description: Collectez automatiquement les dumps de tas des services Apache Hadoop et placez-les dans le compte de stockage Blob Azure à des fins de débogage et d’analyse.
services: hdinsight
author: hrasheed-msft
ms.reviewer: jasonh
ms.service: hdinsight
ms.topic: conceptual
ms.date: 05/25/2017
ms.author: hrasheed
ROBOTS: NOINDEX
ms.openlocfilehash: 698806bdedd9994f2c9de53118cb42c9df1c36cd
ms.sourcegitcommit: 549070d281bb2b5bf282bc7d46f6feab337ef248
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53724400"
---
# <a name="collect-heap-dumps-in-blob-storage-to-debug-and-analyze-apache-hadoop-services"></a>Collecter les dumps de tas dans le Stockage Blob pour déboguer et analyser les services Apache Hadoop
[!INCLUDE [heapdump-selector](../../includes/hdinsight-selector-heap-dump.md)]

Les dumps de tas contiennent un instantané de la mémoire de l’application, y compris des valeurs des variables au moment de la création du dump. Ils sont donc utiles pour diagnostiquer les problèmes qui se produisent au moment de l’exécution. Il est possible de collecter automatiquement les dumps de tas des services [Apache Hadoop](https://hadoop.apache.org/) et de les placer dans le compte de stockage Blob Azure d’un utilisateur sous HDInsightHeapDumps/.

La collection des dumps de tas pour différents services doit être activée pour les services sur des clusters individuels. Par défaut, cette fonctionnalité est désactivée pour un cluster. Les dumps de tas pouvant être volumineux, nous vous recommandons de surveiller le compte de stockage d’objets blob dans lequel ils sont enregistrés une fois la collection activée.

> [!IMPORTANT]  
> Linux est le seul système d’exploitation utilisé sur HDInsight version 3.4 ou supérieure. Pour plus d’informations, consultez [Suppression de HDInsight sous Windows](hdinsight-component-versioning.md#hdinsight-windows-retirement). Les informations mentionnées dans cet article s’appliquent uniquement aux clusters HDInsight sur Windows. Pour plus d’informations au sujet de HDInsight sur Linux, consultez [Activer les dumps de tas pour les services Apache Hadoop sur HDInsight sur Linux](hdinsight-hadoop-collect-debug-heap-dump-linux.md).


## <a name="eligible-services-for-heap-dumps"></a>Services éligibles pour le vidage de tas
Vous pouvez activer des dumps de tas pour les services suivants :

* **Apache hcatalog** - tempelton
* **Apache hive** - hiveserver2, metastore, derbyserver
* **mapreduce** - jobhistoryserver
* **Apache yarn** - resourcemanager, nodemanager, timelineserver
* **Apache hdfs** - datanode, secondarynamenode, namenode

## <a name="configuration-elements-that-enable-heap-dumps"></a>Éléments de configuration permettant d’activer le vidage de tas
Pour activer des dumps de tas sur un service, vous devez définir les éléments de configuration appropriés dans la section de ce service, qui est spécifié par **service_name**.

    "javaargs.<service_name>.XX:+HeapDumpOnOutOfMemoryError" = "-XX:+HeapDumpOnOutOfMemoryError",
    "javaargs.<service_name>.XX:HeapDumpPath" = "-XX:HeapDumpPath=c:\Dumps\<service_name>_%date:~4,2%%date:~7,2%%date:~10,2%%time:~0,2%%time:~3,2%%time:~6,2%.hprof"

La valeur de **service_name** peut être l’un des services répertoriés ci-dessus : tempelton, hiveserver2, metastore, derbyserver, jobhistoryserver, resourcemanager, nodemanager, timelineserver, datanode, secondarynamenode ou namenode.

## <a name="enable-using-azure-powershell"></a>Activer à l’aide d’Azure PowerShell
Par exemple, pour activer les dumps de tas à l’aide d’Azure PowerShell pour jobhistoryserver, procédez comme suit :

[!INCLUDE [upgrade-powershell](../../includes/hdinsight-use-latest-powershell.md)]

    $MapRedConfigValues = new-object 'Microsoft.WindowsAzure.Management.HDInsight.Cmdlet.DataObjects.AzureHDInsightMapReduceConfiguration'

    $MapRedConfigValues.Configuration = @{ "javaargs.jobhistoryserver.XX:+HeapDumpOnOutOfMemoryError"="-XX:+HeapDumpOnOutOfMemoryError" ; "javaargs.jobhistoryserver.XX:HeapDumpPath" = "-XX:HeapDumpPath=c:\\Dumps\\jobhistoryserver_%date:~4,2%_%date:~7,2%_%date:~10,2%_%time:~0,2%_%time:~3,2%_%time:~6,2%.hprof" }

## <a name="enable-using-net-sdk"></a>Activer avec le kit de développement logiciel (SDK) .NET
Par exemple, pour activer les dumps de tas à l’aide du Kit de développement logiciel (SDK) Azure HDInsight .NET pour jobhistoryserver, procédez comme suit :

    clusterInfo.MapReduceConfiguration.ConfigurationCollection.Add(new KeyValuePair<string, string>("javaargs.jobhistoryserver.XX:+HeapDumpOnOutOfMemoryError", "-XX:+HeapDumpOnOutOfMemoryError"));

    clusterInfo.MapReduceConfiguration.ConfigurationCollection.Add(new KeyValuePair<string, string>("javaargs.jobhistoryserver.XX:HeapDumpPath", "-XX:HeapDumpPath=c:\\Dumps\\jobhistoryserver_%date:~4,2%_%date:~7,2%_%date:~10,2%_%time:~0,2%_%time:~3,2%_%time:~6,2%.hprof"));
