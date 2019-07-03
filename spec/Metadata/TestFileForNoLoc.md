---
title: Verwenden von Azure Servicekosten reduzieren können Advisor | Microsoft-Dokumentation
description: Verwenden Sie Azure Advisor um die Kosten für Ihre Azure-Bereitstellungen zu optimieren.
services: advisor
documentationcenter: NA
author: kasparks
ms.service: advisor
ms.topic: article
ms.date: 01/29/2019
ms.author: kasparks
no-loc:
- Advisor
- virtual machines
- virtual machine
ms.openlocfilehash: 734f2a23565edfe472b9732f724501cdfbd44995
ms.sourcegitcommit: 9ff95935fb1f4654097b87b1105fd7358ac93a9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540134"
---
# <a name="reduce-service-costs-using-azure-opno-locadvisor"></a>Verwenden von Azure Servicekosten reduzieren Sie können Advisor

Advisor hilft, die Ihnen zu optimieren und reduzieren Ihre Gesamtausgaben für Azure, verbringen im Leerlauf bzw. zu gering ausgelastete Ressourcen identifiziert. Sie kostenempfehlungen finden Sie in der **Kosten** Registerkarte die Advisor Dashboard. Dies ist TEST 123.

## <a name="optimize-opno-locvirtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances"></a>Optimieren der virtual machine Kosten durch Ändern der Größe oder Herunterfahren von nicht ausgelasteten Instanzen 

Obwohl bestimmte Anwendungsszenarien geringe Auslastung bewirken, oft Geld sparen können durch die Verwaltung der Größe und Anzahl der Ihrem virtual machines. Advisor überwacht Ihre virtual machine Nutzung sieben Tage lang und mit geringer Auslastung ermittelt virtual machines. Mit geringer Auslastung ist die CPU-Auslastung 5 % oder weniger virtuelle Computer gelten und ihre Netzwerkauslastung ist weniger als 2 %, oder wenn die aktuelle arbeitsauslastung kann, indem Sie eine kleinere untergebracht werden virtual machine Größe. Dies ist keine Loc Test.

Advisor Erfahren Sie, die geschätzte Kosten für die Ausführung fortgesetzt wird Ihre virtual machine, sodass Sie sie Herunterfahren, oder passen Sie es auswählen können.

Wenn bei der Identifizierung von unterausgelastet aggressiver erfolgen sollen virtual machines, können Sie die Regel für durchschnittliche CPU-Auslastung auf Abonnementbasis anpassen.

## <a name="reduce-costs-by-eliminating-unprovisioned-expressroute-circuits"></a>Kostensenkung durch die Beseitigung nicht bereitgestellter ExpressRoute-Verbindungen

Advisor Bezeichnet die ExpressRoute-Verbindungen, die im Anbieterstatus wurden *Rolleninternen Cache* für mehr als einen Monat und empfiehlt, die die Verbindung löschen, wenn Sie nicht beabsichtigen, die Verbindung mit Ihrem konnektivitätsanbieter bereitzustellen.

## <a name="reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways"></a>Verringern der Kosten durch Löschen oder Neukonfigurieren von Gateways für virtuelle Netzwerke im Leerlauf

Advisor identifiziert die Gates für virtuelle Netzwerke, die mehr als 90 Tage lang im Leerlauf waren. Da diese Gateways pro Stunde in Rechnung gestellt werden, sollten Sie sie neu konfigurieren oder löschen, wenn Sie nicht mehr beabsichtigen, diese zu verwenden. 

## <a name="buy-reserved-opno-locvirtual-machine-instances-to-save-money-over-pay-as-you-go-costs"></a>Erwerben Sie reservierte virtual machine -Instanzen, die gegenüber der nutzungsbasierten Bezahlung Geld zu sparen.

Advisor Überprüfen Ihrer virtual machine Nutzung, die über den letzten 30 Tagen und zu bestimmen, ob Sie Geld sparen können, durch den Erwerb einer Azure-Reservierung. Advisor Zeigt die Regionen und die Größe, in denen Sie möglicherweise haben die meisten einsparungen und zeigt Ihnen die geschätzten einsparungen durch die Erwerb von Reservierungen. Mit Azure-Reservierungen, können Sie vorab erwerben die Basis Kosten für Ihre virtual machines. Rabatte gelten automatisch für neue oder vorhandene virtuelle Computer mit der gleichen Größe und Region wie Ihre Reservierungen. Weitere Informationen zu Azure Reserved Virtual Machine Instances finden Sie [hier](https://azure.microsoft.com/pricing/reserved-vm-instances/).

Advisor auch benachrichtigt der reservierten Instanzen, die Sie Sie, die in den nächsten 30 Tagen ablaufen. und empfiehlt Ihnen, neue reservierte Instanzen zu kaufen, damit Sie eine nutzungsbasierte Bezahlung vermeiden.

## <a name="delete-unassociated-public-ip-addresses-to-save-money"></a>Löschen nicht zugeordneter öffentlicher IP-Adressen zum Einsparen von Kosten

Advisor Gibt die öffentliche IP-Adressen, die nicht Azure-Ressourcen wie Lastenausgleich oder virtuelle Computer derzeit zugeordnet sind. Für diese öffentliche IP-Adressen fällt eine Schutzgebühr an. Wenn Sie nicht planen, sie zu verwenden, können Sie Kosten sparen, indem Sie sie löschen.

## <a name="how-to-access-cost-recommendations-in-azure-opno-locadvisor"></a>Zugreifen auf kostenempfehlungen in Azure Advisor

1. Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und öffnen Sie dann [ Advisor ](https://aka.ms/azureadvisordashboard).

2.  Auf der Advisor Dashboard, klicken Sie auf die **Kosten** Registerkarte. Dies ist eine :::no-loc text="TEST for inline lock"::: um festzustellen, ob es sich bei "TEST für Inline Loc" entfernt oder als ein Tag eingefügt werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Advisor Empfehlungen finden Sie unter:
* [Einführung in die Advisor](advisor-overview.md)
* [Erste Schritte](advisor-get-started.md)
* [Advisor Empfehlungen zur Leistung](advisor-cost-recommendations.md)
* [Advisor Empfehlungen für hochverfügbarkeit](advisor-cost-recommendations.md)
* [Advisor Empfehlungen zur Sicherheit](advisor-cost-recommendations.md)
