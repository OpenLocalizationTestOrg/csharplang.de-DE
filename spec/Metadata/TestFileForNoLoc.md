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
# <a name="reduce-service-costs-using-azure-opno-locadvisor"></a><span data-ttu-id="9ac7b-103">Verwenden von Azure Servicekosten reduzieren Sie können Advisor</span><span class="sxs-lookup"><span data-stu-id="9ac7b-103">Reduce service costs using Azure Advisor</span></span>

Advisor<span data-ttu-id="9ac7b-104"> hilft, die Ihnen zu optimieren und reduzieren Ihre Gesamtausgaben für Azure, verbringen im Leerlauf bzw. zu gering ausgelastete Ressourcen identifiziert.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-104"> helps you optimize and reduce your overall Azure spend by identifying idle and underutilized resources.</span></span> <span data-ttu-id="9ac7b-105">Sie kostenempfehlungen finden Sie in der **Kosten** Registerkarte die Advisor Dashboard.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-105">You can get cost recommendations from the **Cost** tab on the Advisor dashboard.</span></span> <span data-ttu-id="9ac7b-106">Dies ist TEST 123.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-106">This is TEST 123.</span></span>

## <a name="optimize-virtual-machine-spend-by-resizing-or-shutting-down-underutilized-instances"></a><span data-ttu-id="9ac7b-107">Optimieren der Kosten für virtuelle Computer durch Ändern der Größe oder Herunterfahren von nicht ausgelasteten Instanzen</span><span class="sxs-lookup"><span data-stu-id="9ac7b-107">Optimize virtual machine spend by resizing or shutting down underutilized instances</span></span> 

<span data-ttu-id="9ac7b-108">Obwohl bestimmte Anwendungsszenarien geringe Auslastung bewirken, oft Geld sparen können durch die Verwaltung der Größe und Anzahl der Ihrem virtual machines.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-108">Although certain application scenarios can result in low utilization by design, you can often save money by managing the size and number of your virtual machines.</span></span> Advisor<span data-ttu-id="9ac7b-109"> überwacht die Verwendung Ihrer virtuellen Computer 7 Tage lang und mit geringer Auslastung ermittelt virtual machines.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-109"> monitors your virtual machine usage for 7 days and then identifies low-utilization virtual machines.</span></span> <span data-ttu-id="9ac7b-110">Virtuelle Computer mit geringer Auslastung ist die CPU-Auslastung 5 % oder weniger gelten und ihre Netzwerkauslastung weniger als 2 % ist, oder wenn die aktuelle arbeitsauslastung durch eine kleinere VM-Größe untergebracht werden kann. Dies ist keine Loc Test.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-110">Virtual machines are considered low-utilization if their CPU utilization is 5% or less and their network utilization is less than 2% or if the current workload can be accommodated by a smaller virtual machine size.This is no-loc test.</span></span>

Advisor<span data-ttu-id="9ac7b-111"> Erfahren Sie, die geschätzte Kosten der weiterhin den virtuellen Computer ausgeführt wird, damit Sie sie Herunterfahren, oder passen Sie es auswählen können.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-111"> shows you the estimated cost of continuing to run your virtual machine, so that you can choose to shut it down or resize it.</span></span>

<span data-ttu-id="9ac7b-112">Wenn bei der Identifizierung von unterausgelastet aggressiver erfolgen sollen virtual machines, können Sie die Regel für durchschnittliche CPU-Auslastung auf Abonnementbasis anpassen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-112">If you want to be more aggressive at identifying underutilized virtual machines, you can adjust the average CPU utilization rule on a per subscription basis.</span></span>

## <a name="reduce-costs-by-eliminating-unprovisioned-expressroute-circuits"></a><span data-ttu-id="9ac7b-113">Senkung Ihrer Kosten unterstützt Eliminierung nicht bereitgestellte ExpressRoute-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="9ac7b-113">Reduce costs by eliminating unprovisioned ExpressRoute circuits</span></span>

Advisor<span data-ttu-id="9ac7b-114"> Bezeichnet die ExpressRoute-Verbindungen, die im Anbieterstatus wurden *Rolleninternen Cache* für mehr als einen Monat und empfiehlt, die die Verbindung löschen, wenn Sie nicht beabsichtigen, die Verbindung mit Ihrem konnektivitätsanbieter bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-114"> identifies ExpressRoute circuits that have been in the provider status of *Not Provisioned* for more than one month, and recommends deleting the circuit if you aren't planning to provision the circuit with your connectivity provider.</span></span>

## <a name="reduce-costs-by-deleting-or-reconfiguring-idle-virtual-network-gateways"></a><span data-ttu-id="9ac7b-115">Kostensenkung durch Löschen oder Neukonfiguration im Leerlauf virtuellen Netzwerkgateways</span><span class="sxs-lookup"><span data-stu-id="9ac7b-115">Reduce costs by deleting or reconfiguring idle virtual network gateways</span></span>

Advisor<span data-ttu-id="9ac7b-116"> identifiziert die Gates für virtuelle Netzwerke, die mehr als 90 Tage lang im Leerlauf waren.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-116"> identifies virtual network gates that have been idle for over 90 days.</span></span> <span data-ttu-id="9ac7b-117">Da diese Gateways pro Stunde in Rechnung gestellt werden, sollten Sie neu konfigurieren oder zu löschen, wenn Sie nicht beabsichtigen, die sie nicht mehr verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-117">Since these gateways are billed hourly, you should consider reconfiguring or deleting them if you don't intend to use them anymore.</span></span> 

## <a name="buy-reserved-virtual-machine-instances-to-save-money-over-pay-as-you-go-costs"></a><span data-ttu-id="9ac7b-118">Erwerben Sie reservierte VM-Instanzen, um gegenüber der nutzungsbasierten Bezahlung Geld zu sparen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-118">Buy reserved virtual machine instances to save money over pay-as-you-go costs</span></span>

Advisor<span data-ttu-id="9ac7b-119"> Prüfen der Verwendung Ihrer virtuellen Computer in den letzten 30 Tagen und bestimmen, ob Sie Geld sparen können, durch den Erwerb einer Azure-Reservierung.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-119"> will review your virtual machine usage over the last 30 days and determine if you could save money by purchasing an Azure reservation.</span></span> Advisor<span data-ttu-id="9ac7b-120"> Zeigt die Regionen und die Größe, in denen Sie möglicherweise haben die meisten einsparungen und zeigt Ihnen die geschätzten einsparungen durch die Erwerb von Reservierungen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-120"> will show you the regions and sizes where you potentially have the most savings and will show you the estimated savings from purchasing reservations.</span></span> <span data-ttu-id="9ac7b-121">Mit Azure-Reservierungen, können Sie vorab erwerben die Basis Kosten für Ihre virtual machines.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-121">With Azure reservations, you can pre-purchase the base costs for your virtual machines.</span></span> <span data-ttu-id="9ac7b-122">Rabatte gelten automatisch mit neuen oder vorhandenen virtuellen Computern, die die gleiche Größe und Region als Ihre Reservierungen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-122">Discounts will automatically apply to new or existing VMs that have the same size and region as your reservations.</span></span> [<span data-ttu-id="9ac7b-123">Erfahren Sie mehr über reservierte Azure-VM-Instanzen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-123">Learn more about Azure Reserved VM Instances.</span></span>](https://azure.microsoft.com/pricing/reserved-vm-instances/)

Advisor<span data-ttu-id="9ac7b-124"> auch benachrichtigt der reservierten Instanzen, die Sie Sie, die in den nächsten 30 Tagen ablaufen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-124"> will also notify you of reserved instances that you have that will expire in the next 30 days.</span></span> <span data-ttu-id="9ac7b-125">Es empfiehlt, dass Sie die neue reservierte Instanzen, um zu vermeiden, Zahlen, nutzungsbasierte Bezahlung erwerben.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-125">It will recommend that you purchase new reserved instances to avoid paying pay-as-you-go pricing.</span></span>

## <a name="delete-unassociated-public-ip-addresses-to-save-money"></a><span data-ttu-id="9ac7b-126">Löschen Sie nicht zugeordnete öffentliche IP-Adressen, um Geld zu sparen</span><span class="sxs-lookup"><span data-stu-id="9ac7b-126">Delete unassociated public IP addresses to save money</span></span>

Advisor<span data-ttu-id="9ac7b-127"> Gibt die öffentliche IP-Adressen, die nicht Azure-Ressourcen wie Lastenausgleich oder virtuelle Computer derzeit zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-127"> identifies public IP addresses that are not currently associated to Azure resources such as Load Balancers or VMs.</span></span> <span data-ttu-id="9ac7b-128">Diese öffentlichen IP-Adressen zu verfügen, über eine Gebühr an.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-128">These public IP addresses come with a nominal charge.</span></span> <span data-ttu-id="9ac7b-129">Wenn Sie nicht beabsichtigen, ihre Verwendung kann löschen zu kosteneinsparungen führen.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-129">If you do not plan to use them, deleting them can result in cost savings.</span></span>

## <a name="how-to-access-cost-recommendations-in-azure-opno-locadvisor"></a><span data-ttu-id="9ac7b-130">Zugreifen auf kostenempfehlungen in Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="9ac7b-130">How to access Cost recommendations in Azure Advisor</span></span>

1. <span data-ttu-id="9ac7b-131">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com), und öffnen Sie dann [ Advisor ](https://aka.ms/azureadvisordashboard).</span><span class="sxs-lookup"><span data-stu-id="9ac7b-131">Sign in to the [Azure portal](https://portal.azure.com), and then open [Advisor](https://aka.ms/azureadvisordashboard).</span></span>

2.  <span data-ttu-id="9ac7b-132">Auf der Advisor Dashboard, klicken Sie auf die **Kosten** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="9ac7b-132">On the Advisor dashboard, click the **Cost** tab.</span></span>
:::no-loc Text="Test Review":::
:::no-loc Text="This is Test String"::: 
## <a name="next-steps"></a><span data-ttu-id="9ac7b-133">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9ac7b-133">Next steps</span></span>

<span data-ttu-id="9ac7b-134">Erfahren Sie mehr über Advisor Empfehlungen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="9ac7b-134">To learn more about Advisor recommendations, see:</span></span>
* <span data-ttu-id="9ac7b-135">[Einführung in die Advisor](advisor-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9ac7b-135">[Introduction to Advisor](advisor-overview.md)</span></span>
* [<span data-ttu-id="9ac7b-136">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="9ac7b-136">Get Started</span></span>](advisor-get-started.md)
* <span data-ttu-id="9ac7b-137">[Advisor Empfehlungen zur Leistung](advisor-cost-recommendations.md)</span><span class="sxs-lookup"><span data-stu-id="9ac7b-137">[Advisor Performance recommendations](advisor-cost-recommendations.md)</span></span>
* <span data-ttu-id="9ac7b-138">[Advisor Empfehlungen für hochverfügbarkeit](advisor-cost-recommendations.md)</span><span class="sxs-lookup"><span data-stu-id="9ac7b-138">[Advisor High Availability recommendations](advisor-cost-recommendations.md)</span></span>
* <span data-ttu-id="9ac7b-139">[Advisor Empfehlungen zur Sicherheit](advisor-cost-recommendations.md)</span><span class="sxs-lookup"><span data-stu-id="9ac7b-139">[Advisor Security recommendations](advisor-cost-recommendations.md)</span></span>
