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

# <a name="i-cant-connect-to-my-vm"></a>Ich kann keine Verbindung mit meinem virtuellen Computer herstellen

4 von 5 Kunden aufgelöst, ihre virtuellen Computer Netzwerkkonnektivität Problem mit der folgenden Schritte aus.<br>

## <a name="recommended-steps"></a>**Empfohlene Schritte**

Um häufig auftretende Probleme zu beheben, versuchen Sie es mindestens eine der folgenden Methoden:<br>

1. Überprüfen Sie, ob es sich bei Ihrem virtuellen Computer ausgeführt wird, anhand Ihres virtuellen Computers [Konsolenprotokoll oder den Screenshot](data-blade:Microsoft_Azure_Classic_Compute.VirtualMachineSerialConsoleLogBlade.id.$resourceId).<br>

    * Überprüfen Sie Fehler in Protokollen wie etwa FSTAB-(File Systems Table), FSCK (Konsistenz des Dateisystems) oder Netzwerkprotokollen.<br>

2. Klicken Sie auf [hier](data-blade:microsoft_azure_network.verifyipflowblade.vmId.$resourceId) um sicherzustellen, dass die Netzwerksicherheitsgruppe Datenverkehr zulässt.<br>
3. Klicken Sie auf [hier](data-blade:microsoft_azure_network.NetworkWatcherConnectivityBlade.id.$resourceId) um Konnektivitätsprobleme zu beheben, wenn Sie versuchen, Azure SSH.<br>
4. [Zurücksetzen des Kennworts](data-blade:Microsoft_Azure_Classic_Compute.PasswordResetBlade.id.$resourceId) um Authentifizierungsfehler zu behandeln.<br>
5. Starten Sie den virtuellen Computer beim Start aufgetretene Probleme durch Klicken auf "Neu starten", am oberen Rand dem Blatt der VM-Ressource neu.<br>
6. Ändern der Größe des virtuellen Computers, um hostprobleme zu beheben, indem Sie auf "Größe" auf dem Blatt "Einstellungen" der VM-Ressource.<br>
7. Zurücksetzen der SSH-Konfiguration zum Beheben von SSH-Problemen [mithilfe der CLI](https://docs.microsoft.com/azure/virtual-machines/linux/classic/reset-access-classic#sshconfigresetcli)

## <a name="recommended-documents"></a>**Empfohlene Dokumente**

* [Detaillierte Problembehandlung für SSH-Fehler](https://azure.microsoft.com/documentation/articles/virtual-machines-troubleshoot-ssh-connections/#detailed-troubleshooting-of-ssh-errors)<br>
* [Automatisieren von Linux-VM-Anpassungsaufgaben mithilfe der benutzerdefinierten Skripterweiterung](https://azure.microsoft.com/blog/automate-linux-vm-customization-tasks-using-customscript-extension)
