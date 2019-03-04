---
ms.openlocfilehash: 132dd1bb13c54b49e54f946e46106ff942a84d0f
ms.sourcegitcommit: fed965b15069147176339f9d0d33ff38f0b95f6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
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

# <a name="my-vm-is-slow"></a>Mein virtueller Computer ist langsam.

Wiederholen Sie die folgenden Schritte aus, um zu diagnostizieren und zu Leistungsprobleme virtueller Computer aus.<br>

## <a name="recommended-steps"></a>**Empfohlene Schritte**

1. **Wussten Sie, dass PerfInsights Problemanalyse im Windows-Gast-VM können?**  
    [Installieren der Azure-Diagnose-VM-Erweiterung](https://docs.microsoft.com/azure/virtual-machines/troubleshooting/performance-diagnostics-vm-extension) direkt aus Azure-Portal. Sie können außerdem [Herunterladen von PerfInsights](https://www.microsoft.com/download/details.aspx?id=54915&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) , und führen Sie auf dem virtuellen Computer. Um eine schnelle Behebung zu gewährleisten, bieten Sie uns die PerfInsights-Protokolle, wenn Sie eine Supportanfrage erstellen. [Weitere Informationen](https://docs.microsoft.com/azure/virtual-machines/troubleshooting/how-to-use-perfInsights)

2. Überprüfen Sie die Anwendungsfehlerprotokolle, ablaufverfolgungen und Metriken, um zu ermitteln, ob Engpässe Anwendung Leistungsprobleme verursachen. Eine schnelle Möglichkeit zum Beheben Einmaliger Probleme Neustart der Anwendung und die virtuellen Computer.

3. Überprüfen Sie auf Betriebssystem-Metriken wie CPU, speicherauslastung, e/a- und Netzwerk, um festzustellen, ob eine Ressource durchgängig hochgradig ausgelastet ist.<br>

    Auf **Windows**, verwenden Sie die [Perfmon](https://docs.microsoft.com/windows-server/administration/windows-commands/perfmon) Tool<br>
    Auf **Linux**, verwenden Sie Befehle wie oben "," VmStat "," lsof ", und" Tcpdump<br>

4. Verwendung [VM und der Speicherdiagnose](http://aka.ms/azurevmperf) im Azure-Portal um festzustellen, ob bei Ressourcen überausgelastet sind oder gedrosselt. Sie können dann Diagnose und Überwachung zum Behandeln von Problemen mit Azure-VMs und Speicher ermöglichen.

5. Starten Sie den virtuellen Computer, VM-Betriebssystemprobleme zu beheben, indem Sie auf "Neu starten", am oberen Rand dem Blatt der VM-Ressource neu.<br>
6. Skalieren Sie den virtuellen Computer auf eine andere VM-Typ oder eine Reihe zur Verbesserung der Leistung durch Klicken auf "Größe" auf dem Blatt "Einstellungen" der VM-Ressource.<br>
7. Erwägen Sie die Verwendung [Storage Premium für Azure-VM-Workloads](https://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/).<br>

## <a name="recommended-documents"></a>**Empfohlene Dokumente**

* [Detaillierte Problembehandlung für Azure Storage](https://azure.microsoft.com/documentation/articles/storage-monitoring-diagnosing-troubleshooting/)
