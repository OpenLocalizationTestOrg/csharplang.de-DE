---
ms.openlocfilehash: 132dd1bb13c54b49e54f946e46106ff942a84d0f
ms.sourcegitcommit: 55811c551095ea9ab89baf1144ac0cf7fb1c5df8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57253851"
---
<properties
    pageTitle="Mein virtueller Computer ist langsam."
    description="Mein virtueller Computer ist langsam. "
    service="microsoft.classiccompute"
    resource="virtualmachines"
    authors="ScottAzure"
    ms.author="scotro"
    displayOrder="7"
    selfHelpType="resource"
    supportTopicIds="32628264,32628261,32628277,32628254,32628275,32628268,32628281,32628270"
    resourceTags="windows, linux, windowsSQL, redhat"
    productPesIds="14749,15571,15797,16454"
    cloudEnvironments="public"
    articleId="5b164da5-bc96-47b3-8bd9-74cfcf4db851"
    category="Leistung"
    searchTags="Leistungseinbußen, virtuelle Computer"
/>

# <a name="my-vm-is-slow"></a><span data-ttu-id="ef70e-105">Mein virtueller Computer ist langsam.</span><span class="sxs-lookup"><span data-stu-id="ef70e-105">My VM is slow</span></span>

<span data-ttu-id="ef70e-106">Wiederholen Sie die folgenden Schritte aus, um zu diagnostizieren und zu Leistungsprobleme virtueller Computer aus.</span><span class="sxs-lookup"><span data-stu-id="ef70e-106">Try the following steps to diagnose and mitigate VM performance issues.</span></span><br>

## <a name="recommended-steps"></a><span data-ttu-id="ef70e-107">**Empfohlene Schritte**</span><span class="sxs-lookup"><span data-stu-id="ef70e-107">**Recommended steps**</span></span>

1. <span data-ttu-id="ef70e-108">**Wussten Sie, dass PerfInsights Problemanalyse im Windows-Gast-VM können?**</span><span class="sxs-lookup"><span data-stu-id="ef70e-108">**Did you know PerfInsights can help you analyze Windows guest VM issues?**</span></span>  
    <span data-ttu-id="ef70e-109">[Installieren der Azure-Diagnose-VM-Erweiterung](https://docs.microsoft.com/azure/virtual-machines/troubleshooting/performance-diagnostics-vm-extension) direkt aus Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="ef70e-109">[Install Azure Performance Diagnostics VM Extension](https://docs.microsoft.com/azure/virtual-machines/troubleshooting/performance-diagnostics-vm-extension) directly from Azure portal.</span></span> <span data-ttu-id="ef70e-110">Sie können außerdem [Herunterladen von PerfInsights](https://www.microsoft.com/download/details.aspx?id=54915&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) , und führen Sie auf dem virtuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="ef70e-110">You may also [download PerfInsights](https://www.microsoft.com/download/details.aspx?id=54915&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) and run on the VM.</span></span> <span data-ttu-id="ef70e-111">Um eine schnelle Behebung zu gewährleisten, bieten Sie uns die PerfInsights-Protokolle, wenn Sie eine Supportanfrage erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef70e-111">To ensure a speedy resolution, provide us the PerfInsights logs if you create a support case.</span></span> [<span data-ttu-id="ef70e-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ef70e-112">Learn more</span></span>](https://docs.microsoft.com/azure/virtual-machines/troubleshooting/how-to-use-perfInsights)

2. <span data-ttu-id="ef70e-113">Überprüfen Sie die Anwendungsfehlerprotokolle, ablaufverfolgungen und Metriken, um zu ermitteln, ob Engpässe Anwendung Leistungsprobleme verursachen.</span><span class="sxs-lookup"><span data-stu-id="ef70e-113">Review your application error logs, traces, and metrics to determine if there are any application bottlenecks causing performance issues.</span></span> <span data-ttu-id="ef70e-114">Eine schnelle Möglichkeit zum Beheben Einmaliger Probleme Neustart der Anwendung und die virtuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="ef70e-114">As a quick way to recover from one-time issues, restart your application and virtual machine.</span></span>

3. <span data-ttu-id="ef70e-115">Überprüfen Sie auf Betriebssystem-Metriken wie CPU, speicherauslastung, e/a- und Netzwerk, um festzustellen, ob eine Ressource durchgängig hochgradig ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="ef70e-115">Review operating system level metrics such as CPU, memory usage, IO, and network to see if any resource has consistently high utilization.</span></span><br>

    <span data-ttu-id="ef70e-116">Auf **Windows**, verwenden Sie die [Perfmon](https://docs.microsoft.com/windows-server/administration/windows-commands/perfmon) Tool</span><span class="sxs-lookup"><span data-stu-id="ef70e-116">On **Windows**, use the [Perfmon](https://docs.microsoft.com/windows-server/administration/windows-commands/perfmon) tool</span></span><br>
    <span data-ttu-id="ef70e-117">Auf **Linux**, verwenden Sie Befehle wie oben "," VmStat "," lsof ", und" Tcpdump</span><span class="sxs-lookup"><span data-stu-id="ef70e-117">On **Linux**, use commands such as Top, VmStat, Lsof, and Tcpdump</span></span><br>

4. <span data-ttu-id="ef70e-118">Verwendung [VM und der Speicherdiagnose](http://aka.ms/azurevmperf) im Azure-Portal um festzustellen, ob bei Ressourcen überausgelastet sind oder gedrosselt.</span><span class="sxs-lookup"><span data-stu-id="ef70e-118">Use [VM and Storage Diagnostics](http://aka.ms/azurevmperf) in the Azure portal to identify if any resource is being overutilized or throttled.</span></span> <span data-ttu-id="ef70e-119">Sie können dann Diagnose und Überwachung zum Behandeln von Problemen mit Azure-VMs und Speicher ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ef70e-119">You can then enable diagnostics and monitoring to troubleshoot issues with Azure VMs and Storage.</span></span>

5. <span data-ttu-id="ef70e-120">Starten Sie den virtuellen Computer, VM-Betriebssystemprobleme zu beheben, indem Sie auf "Neu starten", am oberen Rand dem Blatt der VM-Ressource neu.</span><span class="sxs-lookup"><span data-stu-id="ef70e-120">Restart the VM to address any VM operating system issues by clicking 'Restart' at the top of the VM resource blade.</span></span><br>
6. <span data-ttu-id="ef70e-121">Skalieren Sie den virtuellen Computer auf eine andere VM-Typ oder eine Reihe zur Verbesserung der Leistung durch Klicken auf "Größe" auf dem Blatt "Einstellungen" der VM-Ressource.</span><span class="sxs-lookup"><span data-stu-id="ef70e-121">Scale up the virtual machine to a different VM type or series for increased performance by clicking 'Size' in the Settings blade of the VM resource.</span></span><br>
7. <span data-ttu-id="ef70e-122">Erwägen Sie die Verwendung [Storage Premium für Azure-VM-Workloads](https://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/).</span><span class="sxs-lookup"><span data-stu-id="ef70e-122">Consider using [Premium Storage for Azure Virtual Machine Workloads](https://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/).</span></span><br>

## <a name="recommended-documents"></a><span data-ttu-id="ef70e-123">**Empfohlene Dokumente**</span><span class="sxs-lookup"><span data-stu-id="ef70e-123">**Recommended documents**</span></span>

* [<span data-ttu-id="ef70e-124">Detaillierte Problembehandlung für Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ef70e-124">Detailed troubleshooting of Azure Storage</span></span>](https://azure.microsoft.com/documentation/articles/storage-monitoring-diagnosing-troubleshooting/)
