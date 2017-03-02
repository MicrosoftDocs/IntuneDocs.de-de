---
title: "Vollständiges oder selektives Zurücksetzen auf Geräten mit Intune | Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie, wie Sie eine selektive Zurücksetzung von Unternehmensdaten auf einem Gerät oder eine vollständige Zurücksetzung des Geräts auf Werkseinstellungen durchführen."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 9188f4bb4ea526227ccd9f2029fc9b44cbd4a334


---

# <a name="use-full-or-selective-wipe"></a>Verwenden des vollständigen oder selektiven Zurücksetzens 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Sie können Apps und Daten von Intune-verwalteten Geräten zurücksetzen, die nicht mehr benötigt werden, einem neuen Zweck zugeführt werden oder verloren gegangen sind. Zu diesem Zweck enthält Intune Funktionen zum vollständigen oder selektiven Zurücksetzen. Für private Geräte, die in Intune registriert sind, können die Benutzer über die Intune-Unternehmensportal-App einen Remotebefehl zum Zurücksetzen des Geräts erteilen.

  > [!NOTE]
  > In diesem Thema wird nur das Zurücksetzen von Geräten behandelt, die von der Verwaltung mobiler Geräte für Intune verwaltet werden. Sie können auch das [Azure-Portal](https://portal.azure.com) zum [Entfernen von Unternehmensdaten aus Apps](https://docs.microsoft.com/intune/deploy-use/wipe-managed-company-app-data-with-microsoft-intune) verwenden. Außerdem können Sie [mit der Intune-Clientsoftware verwaltete Computer abkoppeln](https://docs.microsoft.com/intune/deploy-use/retire-a-windows-pc-with-microsoft-intune).

## <a name="full-wipe"></a>Vollständiges Zurücksetzen

**Vollständiges Zurücksetzen** setzt ein Gerät auf die werkseitigen Standardeinstellungen zurück, wobei alle Unternehmens- und Benutzerdaten und -einstellungen entfernt werden. Das Gerät wird aus Intune entfernt. Das vollständige Zurücksetzen ist hilfreich, wenn Sie ein Gerät vor der Übergabe an einen neuen Benutzer zurücksetzen möchten oder wenn ein Gerät verloren oder gestohlen wurde.  **Überlegen Sie sich genau, ob Sie ein Gerät wirklich vollständig zurücksetzen möchten. Die Daten auf dem Gerät können anschließend nicht wiederhergestellt werden.**


> [!Warning]
> Nach dem Zurücksetzen ist der Zugriff auf Windows 10 RTM-Geräte (Geräte vor Windows 10, Version 1511) mit weniger als 4 GB RAM vielleicht nicht möglich. Um auf ein Windows 10-Gerät zuzugreifen, das nicht mehr reagiert hat, können Sie das Gerät von einem USB-Laufwerk aus starten.


**So führen Sie eine vollständige Zurücksetzung (Werkseinstellungen) eines Geräts durch**

1.  Wählen Sie auf dem Blatt **Geräte und Gruppen** die Option **Alle Geräte** aus.

2.  Wählen Sie den Namen des Geräts aus, das Sie zurücksetzen möchten.

3.  Wählen Sie auf dem Blatt mit dem Namen des Geräts **Zurücksetzung auf Werkseinstellungen** und dann zur Bestätigung des Zurücksetzens **Ja** aus.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis ein Befehl zum Zurücksetzen an alle Gerätetypen weitergegeben wurde.

### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>So löschen Sie Geräte im Azure Active Directory-Portal

1.  Navigieren Sie zu [http://aka.ms/accessaad](http://aka.ms/accessaad), oder klicken Sie unter [https://portal.office.com](https://portal.office.com) auf **Verwaltung** &gt; **Azure AD**.

2.  Melden Sie sich mit Ihrer Organisations-ID über den Link im linken Bereich der Seite an.

3.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren** ).

4.  Wählen Sie zuerst **Active Directory** und dann Ihre Organisation aus.

5.  Wählen Sie die Registerkarte **Benutzer** aus.

6.  Wählen Sie den Benutzer aus, dessen Geräte Sie löschen möchten.

7.  Klicken Sie auf **Geräte**.

8.  Entfernen Sie Geräte nach Bedarf, z. B. solche, die nicht mehr verwendet werden oder fehlerhafte Definitionen haben.


## <a name="selective-wipe"></a>Selektives Zurücksetzen

Beim **selektiven Zurücksetzen** werden die Unternehmensdaten und bei Bedarf auch die Daten für die Verwaltung mobiler Apps (MAM, Mobile App Management) vom Gerät entfernt. Außerdem werden Einstellungen und E-Mail-Profile entfernt. Die persönlichen Daten des Benutzers bleiben beim selektiven Zurücksetzen auf dem Gerät erhalten. Das Gerät wird aus Intune entfernt. Die folgende Tabelle beschreibt, welche Daten bei einem selektiven Zurücksetzen entfernt werden und mit welchen Auswirkungen auf die auf dem Gerät verbleibenden Daten zu rechnen ist. (Diese Tabellen sind nach Plattform sortiert.)

**iOS**

|Datentyp|iOS|
|-------------|-------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.<br /><br />App-Daten aus Microsoft-Anwendungen, die die Verwaltung von mobilen Anwendungen verwenden, werden entfernt. Die App wird nicht entfernt.|
|Einstellungen|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate werden entfernt und gesperrt.|
|Verwaltungs-Agent|Das Verwaltungsprofil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht. Wenn Microsoft Exchange lokal gehostet wird, werden E-Mail-Profile und zwischengespeicherte E-Mails nicht entfernt.|
|Outlook|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt.</br>Ausnahme: Wenn Exchange lokal gehostet wird, werden E-Mails nicht entfernt.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|AAD-Datensatz wird entfernt.|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

**Android**

|Datentyp|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Weblinks|Entfernt.|Entfernt.|
|Nicht verwaltete Google Play-Apps|Apps und Daten bleiben installiert.|Apps und Daten bleiben installiert.|
|Nicht verwaltete Geschäftssparten-Apps|Apps und Daten bleiben installiert.|Apps werden deinstalliert, und daher werden auch lokal für die App gespeicherte Daten entfernt. Daten außerhalb der App (z.B. auf einer SD-Karte) werden nicht entfernt.|
|Verwaltete Google Play-Apps|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt, werden aber nicht entfernt.|
|Verwaltete Geschäftssparten-Apps|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Daten, die von der MAM-Verschlüsselung außerhalb der App (z.B. auf einer SD-Karte) geschützt sind, bleiben verschlüsselt und unbrauchbar, werden aber nicht entfernt.|
|Einstellungen|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate gesperrt, aber nicht entfernt.|Zertifikate wurden entfernt und gesperrt.|
|Verwaltungs-Agent|Die Berechtigung „Geräteadministrator“ wird gesperrt.|Die Berechtigung „Geräteadministrator“ wird gesperrt.|
|E-Mail|E-Mails, die über die Microsoft Outlook-App für Android empfangen wurden, werden entfernt.|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|
|Outlook|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt.</br>Ausnahme: Wenn Exchange lokal gehostet wird, werden E-Mails nicht entfernt.|E-Mails, die über die Microsoft Outlook-App für iOS empfangen wurden, werden entfernt.</br>Ausnahme: Wenn Exchange lokal gehostet wird, werden E-Mails nicht entfernt.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|AAD-Datensatz wird entfernt.|AAD-Datensatz wird entfernt.|
|Kontakte | Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.|Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt.  Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. <br /> <br />Derzeit wird nur die Outlook-App unterstützt.

**Windows**

|Datentyp|Windows 8.1 (MDM) und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Von Intune installierte Unternehmens-Apps und zugehörige Daten|Bei Dateien, die durch ein EFS geschützt sind, wird der Schlüssel gesperrt, und der Benutzer kann die Dateien nicht mehr öffnen.|Unternehmensanwendungen werden nicht entfernt.|Ursprünglich über das Unternehmensportal installierte Anwendungen werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.|Anwendungen werden deinstalliert, und Sideload-Schlüssel werden entfernt.|
|Einstellungen|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Intune-Richtlinie festgelegt wurden, werden nicht mehr erzwungen, und Benutzer können die Einstellungen ändern.|
|Einstellungen für WLAN- und VPN-Profil|Entfernt.|Entfernt.|Nicht unterstützt.|Entfernt.|
|Zertifikatprofil-Einstellungen|Zertifikate wurden entfernt und gesperrt.|Zertifikate wurden entfernt und gesperrt.|Nicht unterstützt.|Zertifikate wurden entfernt und gesperrt.|
|E-Mail|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen.|Nicht unterstützt.|E-Mail-Profile, die über Intune bereitgestellt wurden, werden entfernt und zwischengespeicherte E-Mails auf dem Gerät gelöscht.|Entfernt EFS-aktivierte E-Mails, darunter die E-Mail-App für Windows-E-Mails und -Anlagen. Entfernt E-Mail-Konten, die von Intune bereitgestellt wurden.</br>**Ausnahme**: Wenn Microsoft Exchange lokal gehostet wird, werden E-Mail-Konten nicht entfernt.|
|Azure Active Directory (AAD)-Verbindung aufgehoben|Nein.|Nein.|AAD-Datensatz wird entfernt.|Nicht zutreffend. Windows 10 unterstützt kein selektives Zurücksetzen für Geräte, die in Azure Active Directory eingebunden wurden.|

**So führen Sie eine selektive Zurücksetzung durch**

1.  Wählen Sie auf dem Blatt **Geräte und Gruppen** die Option **Alle Geräte** aus.

2.  Wählen Sie den Namen des Geräts aus, das Sie zurücksetzen möchten.

3.  Wählen Sie auf dem Blatt mit dem Namen des Geräts **Unternehmensdaten entfernen** und dann zur Bestätigung des Zurücksetzens **Ja** aus.

Wenn das Gerät eingeschaltet und verbunden ist, dauert es weniger als 15 Minuten, bis ein Befehl zum Zurücksetzen an alle Gerätetypen weitergegeben wurde.



<!--HONumber=Feb17_HO1-->

