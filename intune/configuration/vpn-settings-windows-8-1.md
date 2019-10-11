---
title: VPN-Einstellungen für Windows 8.1-Geräte in Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über die Intune-Einstellungen, die Sie zum Konfigurieren von VPN-Verbindungen auf Windows 8.1-Geräten verwenden können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd48b6f75d68f8078eaa01508f01d13e8490da2a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734114"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Konfigurieren von VPN-Einstellungen für Windows 8.1-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf Windows 8.1-Geräten zu konfigurieren.

Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen


- **Alle Einstellungen nur auf Windows 8.1 anwenden:** Diese Einstellung können Sie im klassischen Intune-Portal konfigurieren. Im Azure-Portal kann diese Einstellung nicht geändert werden. Wenn hierfür **Konfiguriert** festgelegt ist, werden sämtliche Einstellungen nur auf Windows 8.1-Geräte angewendet. Wenn **Nicht konfiguriert** festgelegt wird, gelten diese Einstellungen auch für Windows 10-Geräte.
- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Server:** Fügen Sie einen oder mehrere VPN-Server hinzu, mit denen Geräte eine Verbindung herstellen.
  - **Hinzufügen:** Öffnet die Seite **Zeile hinzufügen**, auf der Sie die folgenden Informationen angeben können:
    - **Beschreibung:** Geben Sie einen beschreibenden Namen für den Server ein, z.B. **Contoso-VPN-Server**.
    - **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
    - **Standardserver:** Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Achten Sie darauf, nur einen Server als Standard festzulegen.
  - **Importieren:** Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Wählen Sie **OK** aus, um diese in die Liste **Server** zu importieren.
  - **Exportieren:** exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp in der folgenden Liste von Anbietern aus:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Anmeldegruppe oder -domäne** (nur SonicWall Mobile Connect): Geben Sie den Namen der Anmeldegruppe oder -domäne an, mit der Sie eine Verbindung herstellen möchten.

- **Rolle** (nur Pulse Secure): Geben Sie den Namen der Benutzerrolle an, die Zugriff auf diese Verbindung hat. Eine Benutzerrolle definiert persönliche Einstellungen und Optionen und aktiviert oder deaktiviert bestimmte Zugriffsfeatures.

- **Bereich** (nur Pulse Secure): Geben Sie den Namen des gewünschten Authentifizierungsbereichs an. Ein Authentifizierungsbereich ist eine Gruppe von Authentifizierungsressourcen, die vom Verbindungstyp „Pulse Secure“ verwendet werden.


- **Benutzerdefiniertes XML:** Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung an.

**Beispiel für Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Beispiel für CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Beispiel für SonicWall Mobile Connect:**

```xml
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Beispiel für F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des jeweiligen Herstellers.


## <a name="proxy-settings"></a>Proxyeinstellungen

- **Proxyeinstellungen automatisch erkennen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, geben Sie an, ob Geräte die Verbindungseinstellungen automatisch erkennen können sollen. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
- **Automatisches Konfigurationsskript:** Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält. Geben Sie beispielsweise `http://proxy.contoso.com` ein.
- **Proxyserver verwenden:** Aktivieren Sie diese Option, wenn Sie die Proxyeinstellungen für den Server manuell eingeben möchten.
  - **Adresse:** Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
  - **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
- **Proxy für lokale Adressen umgehen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, wenn der Proxyserver für von Ihnen angegebene lokale Adressen nicht verwendet werden soll. Weitere Informationen finden Sie in der Windows Server-Dokumentation.