---
title: Anwendungs Typen, die in Azure Active Directory B2C verwendet werden können
description: Erfahren Sie mehr über die Arten von Anwendungen, die Sie mit Azure Active Directory B2C verwenden können.
services: active-directory-b2c
author: mmacy
manager: celestedg
ms.service: active-directory
ms.workload: identity
ms.topic: conceptual
ms.date: 07/24/2019
ms.author: marsma
ms.subservice: B2C
ms.openlocfilehash: ed75116801a0a8f7af23bf879383cc6b4d7a59ea
ms.sourcegitcommit: 036e4e16d0416fabfc6b4439fdd726b68e3f7373
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "6609447"
---
# <a name="application-types-that-can-be-used-in-active-directory-b2c"></a>Anwendungs Typen, die in Active Directory B2C verwendet werden können

Azure Active Directory B2C (Azure AD B2C) unterstützt die Authentifizierung für eine Vielzahl von modernen Anwendungsarchitekturen. Alle basieren auf den branchenüblichen Protokollen [OAuth 2,0](active-directory-b2c-reference-protocols.md) oder [OpenID Connect](active-directory-b2c-reference-protocols.md). In diesem Artikel werden die Anwendungs Typen beschrieben, die Sie unabhängig von der bevorzugten Sprache oder Plattform erstellen können. Außerdem hilft es Ihnen, die Szenarien auf hoher Ebene zu verstehen, bevor Sie mit dem Entwickeln von Anwendungen beginnen.

Jede Anwendung, die Azure AD B2C verwendet, muss mithilfe des [Azure-Portal](https://portal.azure.com/)in Ihrem [Azure AD B2C](active-directory-b2c-get-started.md) -Mandanten registriert werden. Beim Anwendungs Registrierungsprozess werden Werte erfasst und zugewiesen, wie z. b.:

* Eine **Anwendungs-ID** , die Ihre Anwendung eindeutig identifiziert.
* Eine **Antwort-URL** , die verwendet werden kann, um Antworten zurück an Ihre Anwendung zu leiten.

Jede Anforderung, die an Azure AD B2C gesendet wird, gibt einen **benutzerflow** (eine integrierte Richtlinie) oder eine **benutzerdefinierte Richtlinie** an, mit der das Verhalten Azure AD B2C gesteuert wird. Beide Richtlinien Typen ermöglichen es Ihnen, einen hochgradig anpassbaren Satz von Benutzeroberflächen zu erstellen.

Die Interaktion jeder Anwendung folgt einem ähnlichen Muster:

1. Die Anwendung leitet den Benutzer zum v 2.0-Endpunkt, um eine [Richtlinie](active-directory-b2c-reference-policies.md)auszuführen.
2. Der Benutzer schließt die Richtlinie gemäß der Richtlinien Definition ab.
3. Die Anwendung empfängt ein Sicherheits Token vom v 2.0-Endpunkt.
4. Die Anwendung verwendet das-Sicherheits Token für den Zugriff auf geschützte Informationen oder eine geschützte Ressource.
5. Der Ressourcen Server überprüft das Sicherheits Token, um zu überprüfen, ob der Zugriff gewährt werden kann.
6. Die Anwendung aktualisiert das Sicherheits Token in regelmäßigen Abständen.

Diese Schritte können sich je nach Art der Anwendung, die Sie entwickeln, geringfügig unterscheiden.

## <a name="web-applications"></a>Webanwendungen

Für Webanwendungen (einschließlich .net, PHP, Java, Ruby, Python und Node. js), die auf einem Server gehostet werden und auf die über einen Browser zugegriffen wird, unterstützt Azure AD B2C [OpenID Connect](active-directory-b2c-reference-protocols.md) für alle Benutzeroberflächen. In der Azure AD B2C-Implementierung von OpenID Connect initiiert Ihre Webanwendung die Benutzeroberfläche, indem Authentifizierungsanforderungen an Azure AD ausgegeben werden. Das Ergebnis der Anforderung ist eine `id_token`. Dieses Sicherheits Token stellt die Identität des Benutzers dar. Außerdem werden Informationen über den Benutzer in Form von Ansprüchen bereitstellen:

```json
// Partial raw id_token
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6ImtyaU1QZG1Cd...

// Partial content of a decoded id_token
{
    "name": "John Smith",
    "email": "john.smith@gmail.com",
    "oid": "d9674823-dffc-4e3f-a6eb-62fe4bd48a58"
    ...
}
```

Weitere Informationen zu den Typen von Token und Ansprüchen, die für eine Anwendung verfügbar sind, finden Sie in der [Azure AD B2C tokenreferenz](active-directory-b2c-reference-tokens.md).

In einer Webanwendung führt jede Ausführung einer [Richtlinie](active-directory-b2c-reference-policies.md) die folgenden wichtigen Schritte aus:

1. Der Benutzer sucht nach der Webanwendung.
2. Die Webanwendung leitet den Benutzer an Azure AD B2C um, der die auszuführende Richtlinie angibt.
3. Der Benutzer schließt die Richtlinie ab.
4. Azure AD B2C gibt `id_token` an den Browser zurück.
5. Der `id_token` wird an den Umleitungs-URI gesendet.
6. Der `id_token` wird überprüft, und ein Sitzungs Cookie wird festgelegt.
7. Eine sichere Seite wird an den Benutzer zurückgegeben.

Die Überprüfung des `id_token` mit einem öffentlichen Signatur Schlüssel, der von Azure AD empfangen wird, reicht aus, um die Identität des Benutzers zu überprüfen. Bei diesem Vorgang wird auch ein Sitzungs Cookie festgelegt, das zum Identifizieren des Benutzers bei nachfolgenden Seiten Anforderungen verwendet werden kann.

Um dieses Szenario in Aktion zu sehen, testen Sie eines der Codebeispiele für die Webanwendung für die Anmeldung im [Abschnitt "Getting Started](active-directory-b2c-overview.md)".

Zusätzlich zur Vereinfachung der einfachen Anmeldung muss eine Webserver Anwendung möglicherweise auch auf einen Back-End-Webdienst zugreifen. In diesem Fall kann die Webanwendung einen etwas anderen [OpenID Connect-Flow](active-directory-b2c-reference-oidc.md) ausführen und Token mithilfe von Autorisierungscodes und Aktualisierungs Token abrufen. Dieses Szenario wird im folgenden Web- [APIs-Abschnitt](#web-apis)dargestellt.

## <a name="web-apis"></a>Web-APIs

Sie können Azure AD B2C zum Sichern von Webdiensten verwenden, wie z. b. die Rest-Web-API Ihrer Anwendung. Web-APIs können OAuth 2,0 verwenden, um Ihre Daten zu schützen, indem eingehende HTTP-Anforderungen mithilfe von Token authentifiziert werden. Der Aufrufer einer Web-API fügt ein Token im Autorisierungs Header einer HTTP-Anforderung an:

```
GET /api/items HTTP/1.1
Host: www.mywebapi.com
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6...
Accept: application/json
...
```

Die Web-API kann dann das Token verwenden, um die Identität des API-Aufrufers zu überprüfen und Informationen über den Aufrufer aus Ansprüchen zu extrahieren, die im Token codiert sind. Weitere Informationen zu den Typen von Token und Ansprüchen, die für eine app verfügbar sind, finden Sie in der [Azure AD B2C tokenreferenz](active-directory-b2c-reference-tokens.md).

Eine Web-API kann Token von vielen Arten von Clients empfangen, z. b. Webanwendungen, Desktop-und Mobile Anwendungen, Single-Page-Anwendungen, serverseitige Daemons und andere Web-APIs. Im folgenden finden Sie ein Beispiel für den gesamten Flow für eine Webanwendung, die eine Web-API aufruft:

1. Die Webanwendung führt eine Richtlinie aus, und der Benutzer schließt die Benutzerfunktion ab.
2. Azure AD B2C gibt eine (OpenID Connect)-`id_token` und einen Autorisierungs Code an den Browser zurück.
3. Der Browser sendet den `id_token`-und Autorisierungs Code an den Umleitungs-URI.
4. Der Webserver überprüft den `id_token` und legt ein Sitzungs Cookie fest.
5. Der Webserver fragt Azure AD B2C nach einer `access_token` ab, indem er den Autorisierungs Code, die Anwendungs Client-ID und die Client Anmelde Informationen bereitstellt.
6. Die `access_token` und `refresh_token` werden an den Webserver zurückgegeben.
7. Die Web-API wird mit dem `access_token` in einem Autorisierungs Header aufgerufen.
8. Die Web-API überprüft das Token.
9. Sichere Daten werden an die Webanwendung zurückgegeben.

Weitere Informationen zu Autorisierungscodes, Aktualisierungs Token und den Schritten zum erhalten von Token finden Sie unter [OAuth 2,0-Protokoll](active-directory-b2c-reference-oauth-code.md).

Um zu erfahren, wie Sie eine Web-API mithilfe von Azure AD B2C sichern, sehen Sie sich die Web-API-Tutorials im [Abschnitt "Getting Started](active-directory-b2c-overview.md)" an.

## <a name="mobile-and-native-applications"></a>Mobile und native Anwendungen

Anwendungen, die auf Geräten installiert werden, z. b. Mobile Anwendungen und Desktop Anwendungen, müssen häufig auf Back-End-Dienste oder Web-APIs im Namen von Benutzern zugreifen. Sie können ihren systemeigenen Anwendungen angepasste Benutzeroberflächen zur Identitätsverwaltung hinzufügen und Back-End-Dienste sicher mithilfe von Azure AD B2C und dem [Autorisierungs Code Fluss von OAuth 2,0](active-directory-b2c-reference-oauth-code.md)abrufen.

In diesem Flow führt die Anwendung [Richtlinien](active-directory-b2c-reference-policies.md) aus und empfängt eine `authorization_code` von Azure AD, nachdem der Benutzer die Richtlinie abgeschlossen hat. Der `authorization_code` stellt die Berechtigung der Anwendung für den Rückruf von Back-End-Diensten im Namen des aktuell angemeldeten Benutzers dar. Die Anwendung kann dann die `authorization_code` im Hintergrund für einen `access_token` und einen `refresh_token` austauschen.  Die Anwendung kann die `access_token` verwenden, um sich bei einer Back-End-Web-API in HTTP-Anforderungen zu authentifizieren. Die `refresh_token` kann auch verwendet werden, um eine neue `access_token` zu erhalten, wenn eine ältere abgelaufen ist.

## <a name="current-limitations"></a>Aktuelle Einschränkungen

### <a name="unsupported-application-types"></a>Nicht unterstützte Anwendungs Typen

#### <a name="daemonsserver-side-applications"></a>Daemons/serverseitige Anwendungen

Anwendungen, die Prozesse mit langer Ausführungsdauer oder ohne Anwesenheit eines Benutzers betreiben, benötigen auch eine Möglichkeit, auf gesicherte Ressourcen wie Web-APIs zuzugreifen. Diese Anwendungen können Token mithilfe der Anwendungs Identität (anstelle der Delegierten Identität eines Benutzers) und mithilfe des OAuth 2,0-Client Anmelde Informationsflusses authentifizieren und erhalten. Der Ablauf der Client Anmelde Informationen ist nicht identisch mit dem "im Auftrag"-Fluss, und "im Auftrag" sollte nicht für die Server-zu-Server-Authentifizierung verwendet werden.

Obwohl der Client Anmelde Informationsfluss derzeit nicht von Azure AD B2C unterstützt wird, können Sie den Client Anmelde Informationsfluss mithilfe Azure AD einrichten. Ein Azure AD B2C-Mandant nutzt Azure AD Unternehmens Mandanten einige Funktionen.  Der Ablauf der Client Anmelde Informationen wird mithilfe der Azure AD Funktionen des Azure AD B2C-Mandanten unterstützt.

Informationen zum Einrichten des Client Anmelde Informationsflusses finden Sie unter [Azure Active Directory v 2.0 und im OAuth 2,0-Client Anmelde Informationsfluss](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds). Eine erfolgreiche Authentifizierung führt zum Empfang eines Tokens, das so formatiert wurde, dass es von Azure AD verwendet werden kann, wie in [Azure AD tokenreferenz](https://docs.microsoft.com/azure/active-directory/develop/active-directory-token-and-claims)beschrieben.

#### <a name="web-api-chains-on-behalf-of-flow"></a>Web-API-Ketten (im-Auftrag-von-Ablauf)

Viele Architekturen umfassen eine Web-API, die eine andere Downstream-Web-API aufgerufen werden muss, wobei beide durch Azure AD B2C gesichert werden. Dieses Szenario kommt häufig bei nativen Clients mit Web-API-Back-End vor und Ruft einen Microsoft-Onlinedienst wie die Azure AD Graph-API auf.

Dieses Szenario der verketteten Web-API kann mithilfe der Berechtigung für den OAuth 2,0 JWT-Träger Anmelde Informationsdienst (auch als "im Auftrag von" bezeichnet) unterstützt werden.  Der "im Auftrag von"-Ablauf ist jedoch zurzeit nicht in der Azure AD B2C implementiert.

### <a name="faulted-apps"></a>Fehlerhafte apps

Bearbeiten Sie Azure AD B2C Anwendungen nicht auf folgende Weise:

- In anderen Anwendungs Verwaltungs Portalen, z. b. im [Anwendungs Registrierungs Portal](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).
- Mithilfe von Graph-API oder PowerShell.

Wenn Sie die Azure AD B2C Anwendung außerhalb des Azure-Portal bearbeiten, wird Sie zu einer fehlerhaften Anwendung und kann nicht mehr mit Azure AD B2C verwendet werden. Löschen Sie die Anwendung, und erstellen Sie Sie erneut.

Wechseln Sie zum [Anwendungs Registrierungs Portal](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) , und löschen Sie die Anwendung dort, um die Anwendung zu löschen. Damit die Anwendung sichtbar ist, müssen Sie der Besitzer der Anwendung sein (und nicht nur ein Administrator des Mandanten).

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die integrierten Richtlinien, die von [benutzerflows in Azure Active Directory B2C](active-directory-b2c-reference-policies.md)bereitgestellt werden.
