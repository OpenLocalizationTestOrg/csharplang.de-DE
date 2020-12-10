---
title: <specifiedPickupDirectory>Element (Netzwerkeinstellungen)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 0d9c68f887edd33d91c894a3caa47e37132dcd5c
ms.sourcegitcommit: 85b29db7d172293c141299aaae995c306bddfb83
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2020
ms.locfileid: "6612995"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a>\<SpecifiedPickupDirectory>-Element (Netzwerkeinstellungen)
Konfiguriert das lokale Verzeichnis für einen SMTP-Server (Simple Mail Transport Protocol).  
  
[**\<Konfigurations>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<SMTP->**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<SpecifiedPickupDirectory>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|Das Verzeichnis, in dem Anwendungen e-Mails zur späteren Verarbeitung durch den SMTP-Server speichern.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine.  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<SMTP->-Element (Netzwerkeinstellungen)](smtp-element-network-settings.md)|Konfiguriert die SMTP-e-Mail-Sendeoptionen (Simple Mail Transport Protocol).|  
  
## <a name="remarks"></a>Hinweise  
 Das `specifiedPickupDirectory` Attribut legt das Verzeichnis fest, in dem Anwendungen e-Mail-Nachrichten speichern, die vom SMTP-Server verarbeitet werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird c:\maildrop als e-Mail-Pickup-Verzeichnis angegeben.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [Netzwerk Einstellungs Schema](index.md)