---
ms.openlocfilehash: 97f4a97a674e17870f1d24e35258c4f79c559eb2
ms.sourcegitcommit: 55811c551095ea9ab89baf1144ac0cf7fb1c5df8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57253860"
---
<properties
pageTitle="Top-Problemen für die Berechnung"
description="Menü basierend Workflowdokuments für Top-Compute-Probleme"        
service="microsoft.compute"
resource="virtualmachines"
authors="gamore"
displayOrder=""
articleId="7bd33a4a-8d59-4f16-a965-f1ac9deb730e"
selfHelpType="diagnoseandsolvev2"
resourceTags="linux"
productPesId="15571"
cloudEnvironments="public"
/>
---
{
    "$schema": "SelfHelpContent",
    "commonProblems": [
        {
            "title": "Ich kann keine Verbindung mit meinem virtuellen Computer herstellen",
            "description": "Ermitteln Sie Probleme, die Konnektivität mit Ihrem virtuellen Computer entweder plattformproblem oder VM-Problem u. u. betreffen",
            "category": "Konnektivität",
            "searchTags": "Rdp-Konnektivität",
            "supportTopicId": "4354354565",
            "symptomId": "cannotrdpazureportalinsight"
        },
        {
            "title": "Ich kann nicht Neustart/mein virtueller Computer neu starten",
            "description": "Ermitteln Sie Probleme, die Konnektivität mit Ihrem virtuellen Computer entweder plattformproblem oder VM-Problem u. u. betreffen",
            "category": "Konnektivität",
            "searchTags": "neu starten, neu starten",
            "supportTopicId": "4354354567"
        },
        {
            "title": "Mein virtueller Computer ist langsam ausgeführt.",
            "description": "Ermitteln Sie Probleme, die Konnektivität mit Ihrem virtuellen Computer entweder plattformproblem oder VM-Problem u. u. betreffen",
            "category": "Leistung",
            "searchTags": "Leistung, virtuelle Computer",
            "supportTopicId": "4354354565"
        },
        {
            "title": "Wie setze ich das Kennwort für mein virtueller Computer zurück?",
            "description": "Ermitteln Sie Probleme, die Konnektivität mit Ihrem virtuellen Computer entweder plattformproblem oder VM-Problem u. u. betreffen",
            "category": "Zurücksetzen",
            "supportTopicId": "4354354565"
        }
    ],
    "troubleshootingTools": [
        {
            "title": "Erneutes Bereitstellen des virtuellen Computers",
            "description": "Migrieren Sie diese virtuelle Maschine auf einen anderen Host aus, um Konnektivitätsprobleme zu beheben.",
            "newTagExpiryDate": "4/14/2019",
            "category": "Konnektivität",
            "searchTags": "Rdp-Bereitstellung",
            "type": "tool",
            "bladeLink": {
                "extensionName": "Microsoft_Azure_Compute",
                "bladeName": "VirtualMachineRedeployViewModel",
                "parameters": [
                    {
                        "name": "id",
                        "value": "$resourceId"
                    }
                ]
            }
        },
        {
            "title": "Kann keine Verbindung zum virtuellen Computer hergestellt werden.",
            "description": "Ermitteln Sie Probleme, die Konnektivität mit Ihrem virtuellen Computer entweder plattformproblem oder VM-Problem u. u. betreffen",
            "newTagExpiryDate": "",
            "type": "insight",
            "searchTags": "sporadischen, Rdp-Verbindungen",
            "category": "Konnektivität",
            "supportTopicId": "4354354565",
            "symptomId": "cannotrdpazureportalinsight"
        }
    ]
}
---
