---
title: Gérer les disques de machine virtuelle dans Azure Stack | Microsoft Docs
description: Créez des disques pour des machines virtuelles dans Azure Stack.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
editor: ''
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 01/18/2019
ms.author: mabrigg
ms.reviewer: jiahan
ms.lastreviewed: 01/18/2019
ms.openlocfilehash: 022dd937ae0557ca848a329039703f3b94ad0885
ms.sourcegitcommit: 898b2936e3d6d3a8366cfcccc0fccfdb0fc781b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55245352"
---
# <a name="create-virtual-machine-disk-storage-in-azure-stack"></a>Créer un stockage sur disque pour machines virtuelles dans Azure Stack

*S’applique à : systèmes intégrés Azure Stack et Kit de développement Azure Stack*

Cet article explique comment créer un stockage sur disque pour machines virtuelles avec le portail Azure Stack ou PowerShell.

## <a name="overview"></a>Vue d’ensemble

À compter de la version 1808, Azure Stack prend en charge l’utilisation de disques managés et non managés sur les machines virtuelles, à la fois comme disque de système d’exploitation et comme disque de données. Dans les versions antérieures à la version 1808, seuls les disques non managés sont pris en charge. 

Les **[disques managés](https://docs.microsoft.com/azure/virtual-machines/windows/about-disks-and-vhds#managed-disks)** simplifient la gestion des disques des machines virtuelles Azure IaaS, en gérant les comptes de stockage associés aux disques de machines virtuelles. Vous spécifiez simplement la taille du disque dont vous avez besoin, et Azure Stack crée et gère le disque pour vous.

Les **[disques non managés](https://docs.microsoft.com/azure/virtual-machines/windows/about-disks-and-vhds#unmanaged-disks)** nécessitent la création d’un [compte de stockage](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account) pour stocker les disques. Les disques que vous créez sont appelés « disques de machine virtuelle » et sont stockés dans des conteneurs, dans le compte de stockage.

### <a name="best-practice-guidelines"></a>Conseils de bonnes pratiques

Pour améliorer les performances et réduire les coûts globaux, nous vous recommandons de placer chaque disque de machine virtuelle dans un conteneur distinct. Un conteneur doit contenir un disque du système d’exploitation ou un disque de données, mais pas les deux en même temps. (Rien ne vous empêche cependant de placer les deux types de disque dans le même conteneur.)

Si vous ajoutez un ou plusieurs disques de données à une machine virtuelle, utilisez des conteneurs supplémentaires comme emplacement de stockage de ces disques. Le disque du système d’exploitation pour des machines virtuelles supplémentaires doit également se trouver dans son propre conteneur distinct.

Quand vous créez des machines virtuelles, vous pouvez réutiliser le même compte de stockage pour chaque nouvelle machine virtuelle. Seuls les conteneurs que vous créez doivent être uniques.

### <a name="adding-new-disks"></a>Ajout de nouveaux disques

Le tableau suivant est un récapitulatif de la façon d’ajouter des disques avec le portail et avec PowerShell.

| Méthode | Options
|-|-|
|[Portail de l’utilisateur](#use-the-portal-to-add-additional-disks-to-a-vm)|- Ajouter de nouveaux disques de données à une machine virtuelle existante. Les nouveaux disques sont créés par Azure Stack. </br> </br>- Ajouter un fichier disque (.vhd) existant à une machine virtuelle déjà créée. Pour cela, vous devez d’abord préparer le .vhd, puis charger le fichier sur Azure Stack. |
|[PowerShell](#use-powershell-to-add-multiple-unmanaged-disks-to-a-vm) | - Créez une machine virtuelle en utilisant un disque de système d’exploitation, et ajoutez parallèlement un ou plusieurs disques de données à cette machine virtuelle. |

## <a name="use-the-portal-to-add-disks-to-a-vm"></a>Utiliser le portail pour ajouter des disques à une machine virtuelle

Par défaut, quand vous utilisez le portail pour créer une machine virtuelle pour la plupart des éléments de la Place de marché, seul le disque du système d’exploitation est créé.

Après avoir créé une machine virtuelle, vous pouvez utiliser le portail pour :
* Créer un disque de données et l’attacher à la machine virtuelle.
* Charger un disque de données existant et l’attacher à la machine virtuelle.

Chaque disque non managé que vous ajoutez doit être placé dans un conteneur distinct.

>[!NOTE]  
>Les disques créés et gérés par Azure sont appelés [disques managés](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview).

### <a name="use-the-portal-to-create-and-attach-a-new-data-disk"></a>Utiliser le portail pour créer et attacher un disque de données

1.  Dans le portail, choisissez **Tous les services** > **Machines virtuelles**.    
    ![Exemple : tableau de bord de machine virtuelle](media/azure-stack-manage-vm-disks/vm-dashboard.png)

2.  Sélectionnez une machine virtuelle qui a déjà été créée.   
    ![Exemple : sélectionner une machine virtuelle dans le tableau de bord](media/azure-stack-manage-vm-disks/select-a-vm.png)

3.  Pour la machine virtuelle, sélectionnez **Disques** > **Ajouter un disque de données**.       
    ![Exemple : attacher un nouveau disque à la machine virtuelle](media/azure-stack-manage-vm-disks/Attach-disks.png)    

4.  Pour le disque de données :
    -  Entrez le **LUN** (numéro d’unité logique). Le numéro d’unité logique doit être un nombre valide.
    -  Sélectionnez **Créer un disque**.
    ![Exemple : attacher un nouveau disque à la machine virtuelle](media/azure-stack-manage-vm-disks/add-a-data-disk-create-disk.png)

5.  Dans le panneau Créer un disque géré :
    -  Entrez le **Nom** du disque.
    -  Créez un **Groupe de ressources** ou sélectionnez-en un.
    -  Sélectionnez un **Emplacement**. Par défaut, l’emplacement est défini sur le conteneur qui renferme le disque du système d’exploitation.
    -  Sélectionnez le **Type de compte**. 
        ![Exemple : attacher un nouveau disque à la machine virtuelle](media/azure-stack-manage-vm-disks/create-manage-disk.png)

        **SSD Premium**  
        Les disques Premium (SSD) sont associés à des disques SSD afin d’offrir des performances constantes et une faible latence. Ils proposent le meilleur rapport prix/performances et conviennent parfaitement aux applications d’E/S intensives et aux charges de travail de production.
       
        **HDD Standard**  
        Les disques standard (HDD) sont associés à des lecteurs magnétiques et conviennent davantage aux applications dont les données sont rarement utilisées. Les disques redondants interzones sont associés à un stockage redondant interzone (ZRS) qui réplique vos données sur plusieurs zones, et restent disponibles même si une zone n’est pas disponible. 

    -  Sélectionnez le **Type de source**.

       Créez un disque à partir d’un instantané d’un autre disque ou d’un objet blob d’un compte de stockage, ou créez un disque vide.

        **Instantané**  
        Sélectionnez un instantané, si disponible. L’instantané doit être disponible dans l’abonnement et l’emplacement de la machine virtuelle.

        **Objet blob de stockage**  
        - Ajoutez l’URI de l’objet blob de stockage qui contient l’image disque.  
        - Sélectionnez **Parcourir** pour ouvrir le panneau Comptes de stockage. Pour obtenir des instructions, consultez [Ajouter un disque de données à partir d’un compte de stockage](#add-a-data-disk-from-a-storage-account).
        - Sélectionnez le type du système d’exploitation de l’image : **Windows**, **Linux** ou **Aucun (disque de données)**.

        **Aucun (disque vide)**

    -  Sélectionnez la **Taille (Gio)**.

       Le coût d’un disque standard augmente avec sa taille. Le coût et les performances d’un disque Premium augmentent avec sa taille. Pour plus d’informations, consultez [Tarification Managed Disks](https://go.microsoft.com/fwlink/?linkid=843142).

    -  Sélectionnez **Créer**. Azure Stack crée et valide le disque managé.

5.  Après qu’Azure Stack a créé le disque et l’a attaché à la machine virtuelle, le nouveau disque est répertorié dans les paramètres de disque de la machine virtuelle sous **DISQUES DE DONNÉES**.   

    ![Exemple : Afficher le disque](media/azure-stack-manage-vm-disks/view-data-disk.png)

### <a name="add-a-data-disk-from-a-storage-account"></a>Ajouter un disque de données à partir d’un compte de stockage

Pour plus d’informations sur l’utilisation des comptes de stockage dans Azure Stack, consultez [Présentation du stockage Azure Stack](azure-stack-storage-overview.md).

1. Sélectionnez le **compte de stockage** à utiliser.
2. Sélectionnez le **Conteneur** dans lequel vous souhaitez placer le disque de données. Si vous le souhaitez, vous pouvez créer un conteneur dans le panneau **Conteneurs**. Vous pouvez ensuite modifier l’emplacement du nouveau disque et le définir sur son propre conteneur. Si vous utilisez un conteneur distinct pour chaque disque, vous répartissez le positionnement du disque de données, ce qui peut améliorer les performances.
3. Pour enregistrer la sélection, choisissez **Sélectionner**.

    ![Exemple : Sélectionner un conteneur](media/azure-stack-manage-vm-disks/select-container.png)

## <a name="attach-an-existing-data-disk-to-a-vm"></a>Ajouter un disque de données existant à une machine virtuelle

1.  [Préparez un fichier .vhd](https://docs.microsoft.com/azure/virtual-machines/windows/classic/createupload-vhd) à utiliser comme disque de données pour une machine virtuelle. Chargez ce fichier .vhd vers un compte de stockage que vous utilisez avec la machine virtuelle à laquelle vous souhaitez attacher le fichier .vhd.

    Pour stocker le fichier .vhd, pensez à utiliser un conteneur autre que le conteneur du disque du système d’exploitation.   
    ![Exemple : Télécharger un fichier VHD](media/azure-stack-manage-vm-disks/upload-vhd.png)

2.  Une fois que le fichier .vhd est chargé, vous êtes prêt à attacher le disque dur virtuel (VHD) à une machine virtuelle. Dans le menu de gauche, sélectionnez **Machines virtuelles**.  
 ![Exemple : sélectionner une machine virtuelle dans le tableau de bord](media/azure-stack-manage-vm-disks/vm-dashboard.png)

3.  Choisissez la machine virtuelle dans la liste.

    ![Exemple : sélectionner une machine virtuelle dans le tableau de bord](media/azure-stack-manage-vm-disks/select-a-vm.png)

4.  Dans la page correspondant à la machine virtuelle, sélectionnez **Disques** > **Attacher un disque existant**.   

    ![Exemple : Association d'un disque existant](media/azure-stack-manage-vm-disks/attach-disks2.png)

5.  Dans la page **Attacher un disque existant**, sélectionnez **Fichier VHD**. La page **Comptes de stockage** s’ouvre.    

    ![Exemple : Sélectionner un fichier VHD](media/azure-stack-manage-vm-disks/select-vhd.png)

6.  Sous **Comptes de stockage**, sélectionnez le compte à utiliser, puis choisissez un conteneur qui contient le fichier .vhd que vous avez précédemment chargé. Sélectionnez le fichier .vhd, puis choisissez **Sélectionner** pour enregistrer la sélection.    

    ![Exemple : Sélectionner un conteneur](media/azure-stack-manage-vm-disks/select-container2.png)

7.  Sous **Attacher un disque existant**, le fichier que vous avez sélectionné est répertorié sous **Fichier VHD**. Mettez à jour le paramètre **Mise en cache de l’hôte** du disque, puis sélectionnez **OK** pour enregistrer la configuration du nouveau disque de la machine virtuelle.    

    ![Exemple : Attacher le fichier VHD](media/azure-stack-manage-vm-disks/attach-vhd.png)

8.  Après qu’Azure Stack a créé le disque et l’a attaché à la machine virtuelle, le nouveau disque est répertorié dans les paramètres de disque de la machine virtuelle sous **Disques de données**.   

    ![Exemple : Procéder à l’attachement du disque](media/azure-stack-manage-vm-disks/complete-disk-attach.png)

## <a name="use-powershell-to-add-multiple-unmanaged-disks-to-a-vm"></a>Utiliser PowerShell pour ajouter plusieurs disques non gérés à une machine virtuelle

Vous pouvez utiliser PowerShell pour approvisionner une machine virtuelle et ajouter un nouveau disque de données, ou attacher un fichier **.vhd** préexistant en tant que disque de données.

La cmdlet **Add-AzureRmVMDataDisk** ajoute un disque de données à une machine virtuelle. Vous pouvez ajouter un disque de données lorsque vous créez une machine virtuelle. Vous pouvez également ajouter un disque de données à une machine virtuelle existante. Spécifiez le paramètre **VhdUri** pour distribuer les disques vers différents conteneurs.

### <a name="add-data-disks-to-a-new-virtual-machine"></a>Ajouter des disques de données à une nouvelle machine virtuelle
Les exemples suivants utilisent des commandes PowerShell pour créer une machine virtuelle comportant trois disques de données, chacun étant placé dans un conteneur différent.

La première commande crée un objet machine virtuelle avant de le stocker dans la variable *$VirtualMachine*. La commande attribue un nom et une taille à la machine virtuelle.

```powershell
$VirtualMachine = New-AzureRmVMConfig -VMName "VirtualMachine" `
                                    -VMSize "Standard_A2"
```

Les trois commandes suivantes attribuent les chemins d’accès de trois disques de données aux variables *$DataDiskVhdUri01*, *$DataDiskVhdUri02* et *$DataDiskVhdUri03*. Définissez un nom de chemin d’accès différent dans l’URL pour répartir les disques dans différents conteneurs.

```powershell
$DataDiskVhdUri01 = "https://contoso.blob.local.azurestack.external/test1/data1.vhd"
```

```powershell
$DataDiskVhdUri02 = "https://contoso.blob.local.azurestack.external/test2/data2.vhd"
```

```powershell
$DataDiskVhdUri03 = "https://contoso.blob.local.azurestack.external/test3/data3.vhd"
```

Les trois commandes finales ajoutent des disques de données à la machine virtuelle stockée dans *$VirtualMachine*. Chaque commande spécifie le nom, l’emplacement et des propriétés supplémentaires du disque. L’URI de chaque disque est stocké dans *$DataDiskVhdUri01*, *$DataDiskVhdUri02* et *$DataDiskVhdUri03*.

```powershell
$VirtualMachine = Add-AzureRmVMDataDisk -VM $VirtualMachine -Name 'DataDisk1' `
                -Caching 'ReadOnly' -DiskSizeInGB 10 -Lun 0 `
                -VhdUri $DataDiskVhdUri01 -CreateOption Empty
```

```powershell
$VirtualMachine = Add-AzureRmVMDataDisk -VM $VirtualMachine -Name 'DataDisk2' `
                -Caching 'ReadOnly' -DiskSizeInGB 11 -Lun 1 `
                -VhdUri $DataDiskVhdUri02 -CreateOption Empty
```

```powershell
$VirtualMachine = Add-AzureRmVMDataDisk -VM $VirtualMachine -Name 'DataDisk3' `
                -Caching 'ReadOnly' -DiskSizeInGB 12 -Lun 2 `
                -VhdUri $DataDiskVhdUri03 -CreateOption Empty
```

Les commandes PowerShell suivantes permettent d’ajouter la configuration du réseau et du disque du système d’exploitation à la machine virtuelle, puis de démarrer la nouvelle machine virtuelle.

```powershell
#set variables
$rgName = "myResourceGroup"
$location = "local"
#Set OS Disk
$osDiskUri = "https://contoso.blob.local.azurestack.external/vhds/osDisk.vhd"
$osDiskName = "osDisk"

$VirtualMachine = Set-AzureRmVMOSDisk -VM $VirtualMachine -Name $osDiskName -VhdUri $osDiskUri `
    -CreateOption FromImage -Windows

# Create a subnet configuration
$subnetName = "mySubNet"
$singleSubnet = New-AzureRmVirtualNetworkSubnetConfig -Name $subnetName -AddressPrefix 10.0.0.0/24

# Create a vnet configuration
$vnetName = "myVnetName"
$vnet = New-AzureRmVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $location `
    -AddressPrefix 10.0.0.0/16 -Subnet $singleSubnet

# Create a public IP
$ipName = "myIP"
$pip = New-AzureRmPublicIpAddress -Name $ipName -ResourceGroupName $rgName -Location $location `
    -AllocationMethod Dynamic

# Create a network security group configuration
$nsgName = "myNsg"
$rdpRule = New-AzureRmNetworkSecurityRuleConfig -Name myRdpRule -Description "Allow RDP" `
    -Access Allow -Protocol Tcp -Direction Inbound -Priority 110 `
    -SourceAddressPrefix Internet -SourcePortRange * `
    -DestinationAddressPrefix * -DestinationPortRange 3389
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $rgName -Location $location `
    -Name $nsgName -SecurityRules $rdpRule

# Create a NIC configuration
$nicName = "myNicName"
$nic = New-AzureRmNetworkInterface -Name $nicName -ResourceGroupName $rgName `
-Location $location -SubnetId $vnet.Subnets[0].Id -NetworkSecurityGroupId $nsg.Id -PublicIpAddressId $pip.Id

#Create the new VM
$VirtualMachine = Set-AzureRmVMOperatingSystem -VM $VirtualMachine -Windows -ComputerName VirtualMachine | `
    Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer `
    -Skus 2016-Datacenter -Version latest | Add-AzureRmVMNetworkInterface -Id $nic.Id
New-AzureRmVM -ResourceGroupName $rgName -Location $location -VM $VirtualMachine
```

### <a name="add-data-disks-to-an-existing-virtual-machine"></a>Ajouter des disques de données à une machine virtuelle existante

Les exemples suivants utilisent des commandes PowerShell pour ajouter trois disques de données à une machine virtuelle existante.
La première commande récupère la machine virtuelle nommée VirtualMachine à l’aide de la cmdlet **Get-AzureRmVM**. La commande stocke la machine virtuelle dans la variable *$VirtualMachine* .

```powershell
$VirtualMachine = Get-AzureRmVM -ResourceGroupName "myResourceGroup" `
                                -Name "VirtualMachine"
```
Les trois commandes suivantes attribuent les chemins d’accès de trois disques de données aux variables $DataDiskVhdUri01, $DataDiskVhdUri02 et $DataDiskVhdUri03.  Les différents noms de chemin d’accès dans le paramètre vhduri indiquent différents conteneurs pour le placement des disques.
```powershell
$DataDiskVhdUri01 = "https://contoso.blob.local.azurestack.external/test1/data1.vhd"
```
```powershell
$DataDiskVhdUri02 = "https://contoso.blob.local.azurestack.external/test2/data2.vhd"
```
```powershell
$DataDiskVhdUri03 = "https://contoso.blob.local.azurestack.external/test3/data3.vhd"
```


Les trois commandes suivantes ajoutent les disques de données à la machine virtuelle stockée dans la variable *$VirtualMachine*. Chaque commande spécifie le nom, l’emplacement et des propriétés supplémentaires du disque. L’URI de chaque disque est stocké dans *$DataDiskVhdUri01*, *$DataDiskVhdUri02* et *$DataDiskVhdUri03*.

```powershell
Add-AzureRmVMDataDisk -VM $VirtualMachine -Name "disk1" `
                      -VhdUri $DataDiskVhdUri01 -LUN 0 `
                      -Caching ReadOnly -DiskSizeinGB 10 -CreateOption Empty
```

```powershell
Add-AzureRmVMDataDisk -VM $VirtualMachine -Name "disk2" `
                      -VhdUri $DataDiskVhdUri02 -LUN 1 `
                      -Caching ReadOnly -DiskSizeinGB 11 -CreateOption Empty
```

```powershell
Add-AzureRmVMDataDisk -VM $VirtualMachine -Name "disk3" `
                      -VhdUri $DataDiskVhdUri03 -LUN 2 `
                      -Caching ReadOnly -DiskSizeinGB 12 -CreateOption Empty
```

La commande finale met à jour l’état de la machine virtuelle stockée dans *$VirtualMachine* dans -*ResourceGroupName*.

```powershell
Update-AzureRmVM -ResourceGroupName "myResourceGroup" -VM $VirtualMachine
```

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les machines virtuelles Azure Stack, consultez [Considérations relatives aux machines virtuelles dans Azure Stack](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-vm-considerations).
