---
title: Senken von dienstkosten mithilfe Azure Advisor | Microsoft-Dokumentation
description: Verwenden Sie Azure Advisor, um die Kosten ihrer Azure-bereit Stellungen zu optimieren.
services: advisor
documentationcenter: NA
author: kasparks
ms.service: advisor
ms.topic: article
ms.date: 01/29/2019
ms.author: kasparks
ms.openlocfilehash: 34031883ec432fce4dcdcd3e825c99e453a6c6e3
ms.sourcegitcommit: 5aca2af2f2c521ae3f3e7fab640edda966edd007
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "6610198"
---
![Test1noicon](./image/Test1noicon.png)

# <a name="reduce-service-costs-using-azure-advisor"></a>Senken der dienstkosten mithilfe von Azure Advisor

Mit Advisor können Sie Ihre Gesamtausgaben für Azure optimieren und reduzieren, indem Sie im Leerlauf und unter ausgelastete Ressourcen ermitteln. Kosten Empfehlungen finden Sie auf dem Advisor-Dashboard auf der Registerkarte **Kosten** . Dies ist Test 123.

## <a name="optimize-virtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances"></a>Optimieren der Ausgaben von virtuellen Computern durch Ändern der Größe oder Herunterfahren von unter ausgelasteten Instanzen 

Obwohl bestimmte Anwendungsszenarien zu einer geringen Auslastung führen können, können Sie häufig Kosten sparen, indem Sie die Größe und die Anzahl ihrer virtuellen Computer verwalten. Advisor überwacht die Nutzung Ihrer virtuellen Computer 7 Tage lang und identifiziert dann virtuelle Computer mit geringer Auslastung. Virtuelle Computer gelten als geringe Auslastung, wenn die CPU-Auslastung maximal 5% beträgt und die Netzwerk Auslastung weniger als 2% beträgt oder wenn die aktuelle Arbeitsauslastung durch eine geringere Größe des virtuellen Computers untergebracht werden kann. Dies ist kein Loc-Test.

Der Ratgeber zeigt Ihnen die geschätzten Kosten für die Fortsetzung der virtuellen Maschine, sodass Sie Sie Herunterfahren oder deren Größe ändern können.

Wenn Sie unter ausgelastete virtuelle Computer leichter identifizieren möchten, können Sie die Regel für die durchschnittliche CPU-Auslastung auf Abonnement Basis anpassen.

## <a name="reduce-costs-by-eliminating-unprovisioned-expressroute-circuits"></a>Kosten senken, indem nicht bereitgestellte expressroute-Leitungen eliminiert werden

Advisor identifiziert expressroute-Verbindungen, die sich seit mehr als einem Monat im Anbieter Status " *nicht* bereitgestellt" befanden, und empfiehlt das Löschen der Verbindung, wenn Sie nicht beabsichtigen, die Verbindung mit Ihrem konnektivitätsanbieter bereitzustellen.

## <a name="reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways"></a>Senken Sie die Kosten, indem Sie virtuelle Netzwerk Gateways im Leerlauf löschen oder neu konfigurieren

Advisor identifiziert virtuelle netzwerkgates, die seit mehr als 90 Tagen im Leerlauf waren. Da diese Gateways stündlich abgerechnet werden, empfiehlt es sich, diese neu zu konfigurieren oder zu löschen, wenn Sie Sie nicht mehr verwenden möchten. 

## <a name="buy-reserved-virtual-machine-instances-to-save-money-over-pay-as-you-go-costs"></a>Erwerben Sie reservierte VM-Instanzen, um Kosten im Vergleich zu den Kosten für die Zahlungs basierte Bezahlung zu sparen.

Der Ratgeber überprüft die Auslastung Ihres virtuellen Computers in den letzten 30 Tagen und bestimmt, ob Sie Geld sparen können, indem Sie eine Azure-Reservierung erwerben. Advisor zeigt Ihnen die Regionen und Größen an, in denen Sie möglicherweise die meisten Einsparungen erzielen, und zeigt Ihnen die geschätzten Einsparungen beim Kauf von Reservierungen. Mit Azure-Reservierungen können Sie die Grundkosten für Ihre virtuellen Computer vorab erwerben. Rabatte gelten automatisch für neue oder vorhandene VMS mit derselben Größe und Region wie Ihre Reservierungen. [Erfahren Sie mehr über Azure reserved VM Instances.](https://azure.microsoft.com/pricing/reserved-vm-instances/)

Advisor benachrichtigt Sie auch über reservierte Instanzen, die in den nächsten 30 Tagen ablaufen. Es wird empfohlen, dass Sie neue reservierte Instanzen kaufen, um zu vermeiden, dass Sie die Preise für die Bezahlung bezahlen.

## <a name="delete-unassociated-public-ip-addresses-to-save-money"></a>Löschen Sie nicht zugeordnete öffentliche IP-Adressen, um Geld zu sparen

Advisor identifiziert öffentliche IP-Adressen, die derzeit nicht Azure-Ressourcen wie Lasten Ausgleichs Modulen oder VMS zugeordnet sind. Diese öffentlichen IP-Adressen verfügen über eine nominale Gebühr. Wenn Sie nicht beabsichtigen, Sie zu verwenden, kann das Löschen zu Kosteneinsparungen führen.

## <a name="how-to-access-cost-recommendations-in-azure-advisor"></a>Zugreifen auf Kosten Empfehlungen in Azure Advisor

:::image type="complex"  alt-text="Dies ist eine komplexe Funktion zum Testen von Images für LOC-scope1" loc-scope="Azure" source="./Test.png"::: 
Dies ist eine Protokoll Beschreibung für das Feature für komplexe Abbild Tests für LOC scope1 Dies ist mehrzeilige testing1 :::image-end:::

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an, und öffnen Sie [Advisor](https://aka.ms/azureadvisordashboard).
:::icon source="image\Test123.png":::Dies ist der Symbol Quell Test, wird die nächste Zeile getestet.

2.  Klicken Sie im Advisor-Dashboard auf die Registerkarte **Kosten** . Dies ist eine :::no-loc text="TEST for inline lock":::, um zu überprüfen, ob der "Test for Inline Loc" entfernt oder als Tag abgelegt wird.

:::image source="https://portal.azure.com" alt-text="Dies ist ein Image Quell Test.":::
Tlong-Beschreibung starten. Advisor identifiziert öffentliche IP-Adressen, die derzeit nicht Azure-Ressourcen wie Lasten Ausgleichs Modulen oder VMS zugeordnet sind. Diese öffentlichen IP-Adressen verfügen über eine nominale Gebühr. Wenn Sie nicht beabsichtigen, Sie zu verwenden, kann das Löschen zu Kosteneinsparungen führen.
Lange Beschreibung Ende :::image-end:::Dies ist das Bild Ende

::: image source= "./image/Test1noicon.png" alt-text="space teating":::

:::image type="complex" source="./image/Test1noicon.png" alt-text="Dies ist eine komplexe Funktion zum Testen von Images für LOC-scope2" loc-scope="Azure"::: 
Dies ist eine Protokoll Beschreibung für das Feature für komplexe Abbild Tests für LOC scope2 Dies ist mehrzeilige testing2 :::image-end:::

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Advisor-Empfehlungen finden Sie unter:
* [Einführung in Advisor](advisor-overview.md)
* [Einstieg](advisor-get-started.md)
* [Advisor-Empfehlungen zur Leistung](advisor-cost-recommendations.md)
* [Advisor-Empfehlungen für Hochverfügbarkeit](advisor-cost-recommendations.md)
* [Advisor-Sicherheitsempfehlungen](advisor-cost-recommendations.md)
