---
title: Dienst senken mithilfe von Azure Advisor | Microsoft-Dokumentation
description: Verwenden Sie Azure Advisor, um die Kosten für Ihre Azure-Bereitstellungen zu optimieren.
services: advisor
documentationcenter: NA
author: kasparks
ms.service: advisor
ms.topic: article
ms.date: 01/29/2019
ms.author: kasparks
ms.openlocfilehash: 0753d6123bd95fc0fb4820e85bab717603dfa163
ms.sourcegitcommit: afdb017b6e7925572904f2d85d86352f95e336ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "6606365"
---
# <a name="reduce-service-costs-using-azure-advisor"></a>Reduzieren Sie die Servicekosten, die mithilfe von Azure Advisor

Advisor hilft Ihnen dabei, die zu optimieren und reduzieren Ihre Gesamtausgaben für Azure, verbringen im Leerlauf bzw. zu gering ausgelastete Ressourcen identifiziert. Sie kostenempfehlungen finden Sie in der **Kosten** auf dem Advisor-Dashboard auf die Registerkarte. Dies ist TEST 123.

## <a name="optimize-virtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances"></a>Optimieren der Kosten für virtuelle Computer durch Ändern der Größe oder Herunterfahren von nicht ausgelasteten Instanzen 

Obwohl bestimmte Anwendungsszenarien geringe Auslastung bewirken, können Sie häufig Kosten sparen, durch die Verwaltung der Größe und Anzahl der virtuellen Computer. Advisor überwacht die Verwendung Ihrer virtuellen Computer 7 Tage lang und ermittelt virtuelle Computer mit geringer Auslastung. Virtuelle Computer mit geringer Auslastung ist die CPU-Auslastung 5 % oder weniger gelten und ihre Netzwerkauslastung weniger als 2 % ist, oder wenn die aktuelle arbeitsauslastung durch eine kleinere VM-Größe untergebracht werden kann. Dies ist keine Loc Test.

Advisor zeigt Sie die geschätzte Kosten der weiterhin den virtuellen Computer ausgeführt wird, damit Sie sie Herunterfahren, oder passen Sie es auswählen können.

Wenn Sie konsequenter zu gering ausgelastete virtuelle Computer identifiziert werden möchten, können Sie die Regel für durchschnittliche CPU-Auslastung auf Abonnementbasis anpassen.

## <a name="reduce-costs-by-eliminating-unprovisioned-expressroute-circuits"></a>Senkung Ihrer Kosten unterstützt Eliminierung nicht bereitgestellte ExpressRoute-Verbindungen

Der Advisor identifiziert ExpressRoute-Verbindungen, die im Anbieterstatus wurden *Rolleninternen Cache* für mehr als einen Monat und empfiehlt, die die Verbindung löschen, wenn Sie nicht beabsichtigen, die Verbindung mit Ihrer Konnektivität bereitzustellen. Anbieter.

## <a name="reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways"></a>Kostensenkung durch Löschen oder Neukonfiguration im Leerlauf virtuellen Netzwerkgateways

Der Advisor identifiziert virtuelle Netzwerk-Gates, die mehr als 90 Tage lang im Leerlauf waren. Da diese Gateways pro Stunde in Rechnung gestellt werden, sollten Sie neu konfigurieren oder zu löschen, wenn Sie nicht beabsichtigen, die sie nicht mehr verwenden. 

## <a name="buy-reserved-virtual-machine-instances-to-save-money-over-pay-as-you-go-costs"></a>Erwerben Sie reservierte VM-Instanzen, um gegenüber der nutzungsbasierten Bezahlung Geld zu sparen.

Advisor Verwendung Ihrer virtuellen Computer in den letzten 30 Tagen prüfen und bestimmen, ob Sie Geld sparen können, durch den Erwerb einer Azure-Reservierung. Advisor zeigt Ihnen, die Regionen und die Größe, in denen Sie möglicherweise haben die meisten einsparungen und zeigt Ihnen die geschätzten einsparungen durch die Erwerb von Reservierungen. Mit Azure-Reservierungen können Sie die Basis-Kosten für Ihre virtuellen Computer vorab erwerben. Rabatte gelten automatisch mit neuen oder vorhandenen virtuellen Computern, die die gleiche Größe und Region als Ihre Reservierungen aufweisen. [Erfahren Sie mehr über reservierte Azure-VM-Instanzen.](https://azure.microsoft.com/pricing/reserved-vm-instances/)

Advisor auch benachrichtigt der reservierten Instanzen, die Sie Sie, die in den nächsten 30 Tagen ablaufen. Es empfiehlt, dass Sie die neue reservierte Instanzen, um zu vermeiden, Zahlen, nutzungsbasierte Bezahlung erwerben.

## <a name="delete-unassociated-public-ip-addresses-to-save-money"></a>Löschen Sie nicht zugeordnete öffentliche IP-Adressen, um Geld zu sparen

Advisor ermittelt die öffentliche IP-Adressen, die nicht Azure-Ressourcen wie Lastenausgleich oder virtuelle Computer derzeit zugeordnet sind. Diese öffentlichen IP-Adressen zu verfügen, über eine Gebühr an. Wenn Sie nicht beabsichtigen, ihre Verwendung kann löschen zu kosteneinsparungen führen.

## <a name="how-to-access-cost-recommendations-in-azure-advisor"></a>Zugreifen auf kostenempfehlungen im Azure Advisor

1. Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und öffnen Sie dann [Advisor](https://aka.ms/azureadvisordashboard).
:::icon source="image\Test123.png":::Dies ist die Datenquelle testen Symbol Dies ist Test für die nächste Zeile

2.  Klicken Sie auf dem Advisor-Dashboard auf die **Kosten** Registerkarte. Dies ist eine :::no-loc text="TEST for inline lock"::: um festzustellen, ob es sich bei "TEST für Inline Loc" entfernt oder als ein Tag eingefügt werden.

:::image source="https://portal.azure.com" alt-text="Dies ist die Bildquelle Test":::
Starten Sie TLong Beschreibung. Advisor ermittelt die öffentliche IP-Adressen, die nicht Azure-Ressourcen wie Lastenausgleich oder virtuelle Computer derzeit zugeordnet sind. Diese öffentlichen IP-Adressen zu verfügen, über eine Gebühr an. Wenn Sie nicht beabsichtigen, ihre Verwendung kann löschen zu kosteneinsparungen führen.
Lange Beschreibung End :::image-end:::Dies ist die Image-Ende

::: image source= "./Test.png" alt-test="space teating":::
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Advisor-Empfehlungen finden Sie unter:
* [Einführung in Advisor](advisor-overview.md)
* [Erste Schritte](advisor-get-started.md)
* [Advisor-Empfehlungen zur Leistung](advisor-cost-recommendations.md)
* [Advisor-Empfehlungen für Hochverfügbarkeit](advisor-cost-recommendations.md)
* [Security-ratgeberempfehlungen](advisor-cost-recommendations.md)
