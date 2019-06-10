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
ms.openlocfilehash: 0db56c3b5257b5a662aa40b79b1c5353cb882613
ms.sourcegitcommit: 36bce7b2d33dec748fe380b3308db90082881fe3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66757868"
---
# <a name="reduce-service-costs-using-azure-opno-locadvisor"></a>Verwenden von Azure Servicekosten reduzieren Sie können Advisor

Advisor hilft, die Ihnen zu optimieren und reduzieren Ihre Gesamtausgaben für Azure, verbringen im Leerlauf bzw. zu gering ausgelastete Ressourcen identifiziert. Sie kostenempfehlungen finden Sie in der **Kosten** Registerkarte die Advisor Dashboard. Dies ist TEST 123.

## <a name="optimize-virtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances"></a>Optimieren der Kosten für virtuelle Computer durch Ändern der Größe oder Herunterfahren von nicht ausgelasteten Instanzen 

Obwohl bestimmte Anwendungsszenarien geringe Auslastung bewirken, oft Geld sparen können durch die Verwaltung der Größe und Anzahl der Ihrem virtual machines. Advisor überwacht die Verwendung Ihrer virtuellen Computer 7 Tage lang und mit geringer Auslastung ermittelt virtual machines. Virtuelle Computer mit geringer Auslastung ist die CPU-Auslastung 5 % oder weniger gelten und ihre Netzwerkauslastung weniger als 2 % ist, oder wenn die aktuelle arbeitsauslastung durch eine kleinere VM-Größe untergebracht werden kann. Dies ist keine Loc Test.

Advisor Erfahren Sie, die geschätzte Kosten der weiterhin den virtuellen Computer ausgeführt wird, damit Sie sie Herunterfahren, oder passen Sie es auswählen können.

Wenn bei der Identifizierung von unterausgelastet aggressiver erfolgen sollen virtual machines, können Sie die Regel für durchschnittliche CPU-Auslastung auf Abonnementbasis anpassen.

## <a name="reduce-costs-by-eliminating-unprovisioned-expressroute-circuits"></a>Senkung Ihrer Kosten unterstützt Eliminierung nicht bereitgestellte ExpressRoute-Verbindungen

Advisor Bezeichnet die ExpressRoute-Verbindungen, die im Anbieterstatus wurden *Rolleninternen Cache* für mehr als einen Monat und empfiehlt, die die Verbindung löschen, wenn Sie nicht beabsichtigen, die Verbindung mit Ihrem konnektivitätsanbieter bereitzustellen.

## <a name="reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways"></a>Kostensenkung durch Löschen oder Neukonfiguration im Leerlauf virtuellen Netzwerkgateways

Advisor identifiziert die Gates für virtuelle Netzwerke, die mehr als 90 Tage lang im Leerlauf waren. Da diese Gateways pro Stunde in Rechnung gestellt werden, sollten Sie neu konfigurieren oder zu löschen, wenn Sie nicht beabsichtigen, die sie nicht mehr verwenden. 

## <a name="buy-reserved-virtual-machine-instances-to-save-money-over-pay-as-you-go-costs"></a>Erwerben Sie reservierte VM-Instanzen, um gegenüber der nutzungsbasierten Bezahlung Geld zu sparen.

Advisor Prüfen der Verwendung Ihrer virtuellen Computer in den letzten 30 Tagen und bestimmen, ob Sie Geld sparen können, durch den Erwerb einer Azure-Reservierung. Advisor Zeigt die Regionen und die Größe, in denen Sie möglicherweise haben die meisten einsparungen und zeigt Ihnen die geschätzten einsparungen durch die Erwerb von Reservierungen. Mit Azure-Reservierungen, können Sie vorab erwerben die Basis Kosten für Ihre virtual machines. Rabatte gelten automatisch mit neuen oder vorhandenen virtuellen Computern, die die gleiche Größe und Region als Ihre Reservierungen aufweisen. [Erfahren Sie mehr über reservierte Azure-VM-Instanzen.](https://azure.microsoft.com/pricing/reserved-vm-instances/)

Advisor auch benachrichtigt der reservierten Instanzen, die Sie Sie, die in den nächsten 30 Tagen ablaufen. Es empfiehlt, dass Sie die neue reservierte Instanzen, um zu vermeiden, Zahlen, nutzungsbasierte Bezahlung erwerben.

## <a name="delete-unassociated-public-ip-addresses-to-save-money"></a>Löschen Sie nicht zugeordnete öffentliche IP-Adressen, um Geld zu sparen

Advisor Gibt die öffentliche IP-Adressen, die nicht Azure-Ressourcen wie Lastenausgleich oder virtuelle Computer derzeit zugeordnet sind. Diese öffentlichen IP-Adressen zu verfügen, über eine Gebühr an. Wenn Sie nicht beabsichtigen, ihre Verwendung kann löschen zu kosteneinsparungen führen.

## <a name="how-to-access-cost-recommendations-in-azure-opno-locadvisor"></a>Zugreifen auf kostenempfehlungen in Azure Advisor

1. Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und öffnen Sie dann [ Advisor ](https://aka.ms/azureadvisordashboard).

2.  Auf der Advisor Dashboard, klicken Sie auf die **Kosten** Registerkarte.
:::no-loc Text="Test Review":::
:::no-loc Text="This is Test String"::: 
## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Advisor Empfehlungen finden Sie unter:
* [Einführung in die Advisor](advisor-overview.md)
* [Erste Schritte](advisor-get-started.md)
* [Advisor Empfehlungen zur Leistung](advisor-cost-recommendations.md)
* [Advisor Empfehlungen für hochverfügbarkeit](advisor-cost-recommendations.md)
* [Advisor Empfehlungen zur Sicherheit](advisor-cost-recommendations.md)
