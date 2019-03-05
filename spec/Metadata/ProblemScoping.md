---
ms.openlocfilehash: 9e09fea1b050d4c81afa91b6d3345847f0496805
ms.sourcegitcommit: 55811c551095ea9ab89baf1144ac0cf7fb1c5df8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57253857"
---
<properties
articleId="problemscopingques-ssl"
pageTitle="SSL"
description="SSL"
supportTopicIds="32630470"
authors="khaled-zayed"
ms.author="khzayed"
selfHelpType="problemScopingQuestions"
productPesIds="16072"
cloudEnvironments="public"
schemaVersion="1"
/>
# <a name="ssl"></a><span data-ttu-id="f2c28-103">SSL</span><span class="sxs-lookup"><span data-stu-id="f2c28-103">SSL</span></span>
---
{
    "resourceRequired": false,
    "title": "SSL",
    "fileAttachmentHint": "Fügen Sie alle relevanten Protokolle/screenshots",
    "formElements": [
        {
            "id": "problem_start_time",
            "order": 1,
            "controlType": "datetimepicker",
            "displayLabel": "Zeit des Vorfalls",
            "required": true
        },
        {
            "id": "2",
            "order": 2,
            "controlType": "dropdown",
            "displayLabel": "Verwenden Sie ein App Service-Zertifikat (das über das Azure-Portal erworben wurden) oder ein externes Zertifikat, das (von einer Partei 3. gekauft)?",
            "watermarkText": "Wählen Sie eine option",
            "dropdownOptions": [
                {
                    "value": "App Service Certificate",
                    "text": "App Service-Zertifikat"
                },
                {
                    "value": "External certificate",
                    "text": "Externes Zertifikat"
                }
            ],
            "required": false
        },
        {
            "id": "3",
            "order": 3,
            "controlType": "textbox",
            "displayLabel": "Welche Domäne ist das SSL-Zertifikat ausgestellt?",
            "watermarkText": "...",
            "required": false
        },
        {
            "id": "4",
            "order": 4,
            "controlType": "textbox",
            "displayLabel": "Welcher Fehler wird angezeigt, und wann werden er angezeigt?",
            "watermarkText": "...",
            "required": false
        },
        {
            "id": "problem_description",
            "order": 5,
            "controlType": "multilinetextbox",
            "displayLabel": "Details",
            "watermarkText": "Geben Sie zusätzlichen Informationen zu Ihrem Problem an, einschließlich Fehlermeldungen, dass Sie angezeigt werden.",
            "required": true,
            "useAsAdditionalDetails": true
        }
    ]
}
---
