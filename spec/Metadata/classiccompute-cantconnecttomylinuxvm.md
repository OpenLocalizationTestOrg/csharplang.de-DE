---
ms.openlocfilehash: 32610e9ef1fce157dd3d9480867948d25feac2ce
ms.sourcegitcommit: 55811c551095ea9ab89baf1144ac0cf7fb1c5df8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57253845"
---
<properties
    pageTitle="Ich kann keine Verbindung mit meinem virtuellen Computer herstellen"
    description="Ich kann keine Verbindung mit meinem virtuellen Computer herstellen "
    service="microsoft.classiccompute"
    resource="virtualmachines"
    authors="ScottAzure"
    ms.author="scotro"
    displayOrder="2"
    selfHelpType="resource"
    supportTopicIds="32615531,32615526"
    resourceTags="linux,redhat,Ubuntu"
    productPesIds="16470,15797,15571,16454"
    cloudEnvironments="public"
    articleId="420298f8-b3fb-49f2-b359-f7cdf357901c"
    category="Konnektivität"
    searchTags="kann keine Verbindung herstellen, kann keine Verbindung herstellen, Vm, Rdp-Konnektivität"
 />

# <a name="i-cant-connect-to-my-vm"></a><span data-ttu-id="e93fa-105">Ich kann keine Verbindung mit meinem virtuellen Computer herstellen</span><span class="sxs-lookup"><span data-stu-id="e93fa-105">I can't connect to my VM</span></span>

<span data-ttu-id="e93fa-106">4 von 5 Kunden aufgelöst, ihre virtuellen Computer Netzwerkkonnektivität Problem mit der folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="e93fa-106">4 out of 5 customers resolved their VM connectivity issue using the below steps.</span></span><br>

## <a name="recommended-steps"></a><span data-ttu-id="e93fa-107">**Empfohlene Schritte**</span><span class="sxs-lookup"><span data-stu-id="e93fa-107">**Recommended Steps**</span></span>

<span data-ttu-id="e93fa-108">Um häufig auftretende Probleme zu beheben, versuchen Sie es mindestens eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="e93fa-108">To resolve common issues, try one or more of the following methods:</span></span><br>

1. <span data-ttu-id="e93fa-109">Überprüfen Sie, ob es sich bei Ihrem virtuellen Computer ausgeführt wird, anhand Ihres virtuellen Computers [Konsolenprotokoll oder den Screenshot](data-blade:Microsoft_Azure_Classic_Compute.VirtualMachineSerialConsoleLogBlade.id.$resourceId).</span><span class="sxs-lookup"><span data-stu-id="e93fa-109">Verify if your VM is running by viewing your VM's [console log or screenshot](data-blade:Microsoft_Azure_Classic_Compute.VirtualMachineSerialConsoleLogBlade.id.$resourceId).</span></span><br>

    * <span data-ttu-id="e93fa-110">Überprüfen Sie Fehler in Protokollen wie etwa FSTAB-(File Systems Table), FSCK (Konsistenz des Dateisystems) oder Netzwerkprotokollen.</span><span class="sxs-lookup"><span data-stu-id="e93fa-110">Review errors in logs such as FSTAB (file systems table), FSCK (file system consistency), or networking.</span></span><br>

2. <span data-ttu-id="e93fa-111">Klicken Sie auf [hier](data-blade:microsoft_azure_network.verifyipflowblade.vmId.$resourceId) um sicherzustellen, dass die Netzwerksicherheitsgruppe Datenverkehr zulässt.</span><span class="sxs-lookup"><span data-stu-id="e93fa-111">Click [here](data-blade:microsoft_azure_network.verifyipflowblade.vmId.$resourceId) to ensure that Network Security Group is allowing traffic.</span></span><br>
3. <span data-ttu-id="e93fa-112">Klicken Sie auf [hier](data-blade:microsoft_azure_network.NetworkWatcherConnectivityBlade.id.$resourceId) um Konnektivitätsprobleme zu beheben, wenn Sie versuchen, Azure SSH.</span><span class="sxs-lookup"><span data-stu-id="e93fa-112">Click [here](data-blade:microsoft_azure_network.NetworkWatcherConnectivityBlade.id.$resourceId) to troubleshoot connectivity issues when trying SSH from Azure.</span></span><br>
4. <span data-ttu-id="e93fa-113">[Zurücksetzen des Kennworts](data-blade:Microsoft_Azure_Classic_Compute.PasswordResetBlade.id.$resourceId) um Authentifizierungsfehler zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="e93fa-113">[Reset password](data-blade:Microsoft_Azure_Classic_Compute.PasswordResetBlade.id.$resourceId) to address authentication errors.</span></span><br>
5. <span data-ttu-id="e93fa-114">Starten Sie den virtuellen Computer beim Start aufgetretene Probleme durch Klicken auf "Neu starten", am oberen Rand dem Blatt der VM-Ressource neu.</span><span class="sxs-lookup"><span data-stu-id="e93fa-114">Restart the virtual machine to address startup issues by clicking 'Restart' at the top of the VM resource blade.</span></span><br>
6. <span data-ttu-id="e93fa-115">Ändern der Größe des virtuellen Computers, um hostprobleme zu beheben, indem Sie auf "Größe" auf dem Blatt "Einstellungen" der VM-Ressource.</span><span class="sxs-lookup"><span data-stu-id="e93fa-115">Resize the VM to fix host issues by clicking 'Size' in the Settings blade of the VM resource.</span></span><br>
7. <span data-ttu-id="e93fa-116">Zurücksetzen der SSH-Konfiguration zum Beheben von SSH-Problemen [mithilfe der CLI](https://docs.microsoft.com/azure/virtual-machines/linux/classic/reset-access-classic#sshconfigresetcli)</span><span class="sxs-lookup"><span data-stu-id="e93fa-116">Reset the SSH configuration to fix any SSH issues [using CLI](https://docs.microsoft.com/azure/virtual-machines/linux/classic/reset-access-classic#sshconfigresetcli)</span></span>

## <a name="recommended-documents"></a><span data-ttu-id="e93fa-117">**Empfohlene Dokumente**</span><span class="sxs-lookup"><span data-stu-id="e93fa-117">**Recommended Documents**</span></span>

* [<span data-ttu-id="e93fa-118">Detaillierte Problembehandlung für SSH-Fehler</span><span class="sxs-lookup"><span data-stu-id="e93fa-118">Detailed troubleshooting of SSH errors</span></span>](https://azure.microsoft.com/documentation/articles/virtual-machines-troubleshoot-ssh-connections/#detailed-troubleshooting-of-ssh-errors)<br>
* [<span data-ttu-id="e93fa-119">Automatisieren von Linux-VM-Anpassungsaufgaben mithilfe der benutzerdefinierten Skripterweiterung</span><span class="sxs-lookup"><span data-stu-id="e93fa-119">Automate Linux VM Customization Tasks using Custom Script Extension</span></span>](https://azure.microsoft.com/blog/automate-linux-vm-customization-tasks-using-customscript-extension)
