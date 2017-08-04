---
title: "Installieren von Office 365 ProPlus-Apps auf Windows 10-Geräten mithilfe von Intune"
titleSuffix: Intune on Azure
description: "Erfahren Sie, wie Sie Intune verwenden können, um Office 365-Apps einfacher auf Windows 10-Geräten erstellen zu können."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0f6a3cdc2b5d95f57f1ffc1f68b6748b357f2ef4
ms.sourcegitcommit: 21a9db380956a50031dbea360b4c76664cbc2768
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>So weisen Sie Office 365 ProPlus 2016-Apps Windows 10-Geräten mit Microsoft Intune hinzu

Diese App erleichtert Ihnen die Zuweisung von Office 365 ProPlus 2016-Apps zu Geräten, die Sie verwalten und die Windows 10 ausführen. Sie können zusätzlich Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen. Die Apps, die als eine App in der Liste der Apps in der Intune-Konsole erscheinen sollen.


## <a name="before-you-start"></a>Vorbereitung

>[!IMPORTANT]
>Diese Installationsmethode für Office wird nicht unterstützt, wenn keine anderen Versionen von Microsoft Office auf dem Gerät installiert sind.

- Auf den Geräten, auf denen Sie diese Apps bereitstellen, muss das Windows 10 Creators Update oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps aus der Sammlung von Office 365 ProPlus 2016.
- Wenn Office-Apps geöffnet sind, wenn Intune die App-Sammlung erstellt, verlieren Endbenutzer möglicherweise Daten aus nicht gespeicherten Dateien.
- Wenn Sie Office auf einem Gerät installieren, auf dem bereits Office installiert ist, lesen Sie die folgenden Überlegungen durch:
    - Unabhängig von der Office-Version, die Sie verwenden, können Sie keine 32-Bit- und 64-Bit-Office-Produkte auf dem gleichen Gerät installieren.
    - Sie können nicht die gleichen Klick-und-Los- und MSI-Versionen von Office auf demselben Gerät ausführen, jedoch können Sie unterschiedliche Hauptversionen erstellen.
    - Wenn Sie bereits eine frühere Version von Office besitzen, die Sie mithilfe von Klick-und-Los installiert haben, müssen Sie alle Apps entfernen, die Sie mit der neueren Version ersetzen möchten. Wenn Sie z.B. über eine neuere Version von World auf dem Gerät verfügen, und Sie die neueste Version zuweisen möchten, müssen Sie zuerst die alte Version entfernen.
    - Wenn auf einem Gerät bereits Office 365 installiert ist, kann es bedeuten, dass Sie bei der Zuweisung der Office 365 ProPlus 2016-Sammlung auf das Gerät möglicherweise Ihre Office-Abonnementebene ändern müssen.


## <a name="get-started"></a>Erste Schritte

1.  Melden Sie sich beim Azure-Portal an.
2.  Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3.  Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4.  Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5.  Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6.  Wählen Sie auf dem Blatt **App hinzufügen** **Office 365 ProPlus-Suite (Windows 10)** aus.

## <a name="configure-the-app-suite"></a>Konfigurieren der App-Sammlung

In diesem Schritt wählen Sie die Office-Apps aus, die Sie den Geräten zuweisen möchten.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **Configure App Suite** (App-Sammlung konfigurieren) aus.
2.  Wählen Sie auf dem Blatt **Configure App Suite** die Office-Standard-Apps, die Sie Geräten zuweisen möchten. Sie können zusätzlich Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen.
3.  Klicken Sie abschließend auf **OK**.

>[!IMPORTANT]
> Nachdem Sie die App-Sammlung erstellt haben, können Sie diese Eigenschaften bearbeiten. Um unterschiedliche Eigenschaften zu konfigurieren, löschen Sie die App-Sammlung, und erstellen Sie eine neue.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

Stellen Sie in diesem Schritt Informationen über die App-Sammlung bereit. Diese Informationen helfen Ihnen, die Sammlung in der Intune-Konsole zu identifizieren, und Endbenutzer können sie in der Unternehmensportal-App finden.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **App Suite Information** (Informationen über die App-Sammlung) aus.
2.  Geben Sie auf dem Blatt **App Suite Information** die folgenden Informationen an: 
    - **Sammlungsname:** Geben Sie den Namen der App-Sammlung ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Sammlungsnamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Sammlungsbeschreibung:** Geben Sie eine Beschreibung für die Sammlung ein. Sie können die Apps auflisten, die Sie einschließen möchten.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Kategorie:** Wählen Sie optional eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch wird es für Benutzer leichter, die App-Sammlung im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App-Sammlung auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Symbol hochladen:** Laden Sie ein Symbol hoch, das gemeinsam mit der App angezeigt wird, wenn die Benutzer das Unternehmensportal durchsuchen.
3.  Klicken Sie abschließend auf **OK**.

## <a name="configure-app-settings"></a>App-Einstellungen konfigurieren

In diesem Schritt konfigurieren Sie Installationsoptionen für die App-Sammlung. Die Einstellungen gelten für alle Apps, die Sie zur Sammlung hinzugefügt haben.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **App Suite Settings** (Einstellungen für die App-Sammlung) aus.
2.  Geben Sie auf dem Blatt **App Suite Settings** die folgenden Informationen an: 
    - **Office-Version:** Wählen Sie aus, ob Sie die 32-Bit- oder die 64-Bit-Version von Office zuweisen möchten. Sie können die 32-Bit-Version auf jeweils 32-Bit- und 64-Bit-Geräten installieren, jedoch können Sie die 64-Bit-Version nur auf 64-Bit-Geräten installieren.
    - **Updatekanal:** Wählen Sie aus, wie Office auf Geräten aktualisiert wird. Informationen zu den unterschiedlichen Updatekanälen finden Sie in der Übersicht der Updatekanäle für Office 365 ProPlus. Wählen Sie aus: 
        - **Aktuell**
        - **Verzögert**
        - **First Release für aktuellen Kanal**
        - **First Release für verzögerten Kanal**
    - **Automatically accept the app end user license agreement** (Die Endbenutzer-Lizenzvereinbarung der App automatisch akzeptieren): Wählen Sie diese Option aus, wenn Endbenutzer die Lizenzvereinbarung nicht akzeptieren müssen. Intune akzeptiert daraufhin die automatisch die Vereinbarung.
    - **Aktivierung gemeinsam genutzter Computer:** Die Aktivierung gemeinsam genutzter Computer wird verwendet, wenn sich mehrere Benutzer einen Computer teilen. Weitere Informationen finden Sie im Überblick über die Aktivierung gemeinsam genutzter Computer für Office 365 ProPlus.
    - **Sprachen:** Office installiert automatisch alle unterstützen Sprachen, die mit Windows auf Endbenutzergeräten installiert werden. Wählen Sie diese Option, wen Sie zusätzliche Sprachen mit der App-Sammlung installieren möchten.

>[!IMPORTANT]
> Nachdem Sie die App-Sammlung erstellt haben, können Sie diese Eigenschaften bearbeiten. Um unterschiedliche Eigenschaften zu konfigurieren, löschen Sie die App-Sammlung, und erstellen Sie eine neue.

## <a name="finish-up"></a>Fertig stellen

Wenn Sie fertig sind, wählen Sie auf dem Blatt **App hinzufügen** die Option **Speichern** aus. Die von Ihnen erstellte App wird in der Liste der Apps angezeigt.

## <a name="error-codes-when-installing-the-app-suite"></a>Fehlercodes beim Installieren der App-Sammlung

In der nachstehenden Tabelle sind die häufigsten Fehlercodes, die auftreten können, sowie deren Bedeutung aufgeführt.

### <a name="status-for-office-csp"></a>Status für Office CSP: 

||||
|-|-|-|
|Status|Phase|Beschreibung|
|1460 (ERROR_TIMEOUT)|Herunterladen|Das Office-Bereitstellungstool konnte nicht heruntergeladen werden|    
|13 (ERROR_INVALID_DATA)|-|Die Signatur des heruntergeladenen Office-Bereitstellungstools konnte nicht überprüft werden.| 
|Fehlercode aus CertVerifyCertificateChainPolicy|-|Fehlgeschlagene Zertifizierungsprüfung für das heruntergeladene Office-Bereitstellungstool.|    
|997|WIP|Installation| 
|0|Nach der Installation|Die Installation war erfolgreich|    
|1603 (ERROR_INSTALL_FAILURE)|-|Alle Voraussetzungsüberprüfungen sind fehlgeschlagen, z.B.:<br>– SxS (Installation wurde versucht, während 2016 MSI installiert wird)<br>– Versionskonflikt<br>usw.|     
|0x8000ffff (E_UNEXPECTED)|-|Es wurde versucht, eine Deinstallation durchzuführen, wenn keine Klick-und-Los-Office-Version auf dem Computer vorhanden ist.|    
|17002|-|Das Szenario (Installation) konnte nicht abgeschlossen werden. Mögliche Gründe:<br>– Die Installation wurde vom Benutzer abgebrochen<br>– Die Installation wurde von einer anderen Installation abgebrochen<br>– Fehlender Speicherplatz auf dem Datenträger während der Installation<br>– Unbekannte Sprach-ID| 
|17004|-|Unbekannte SKUs|   


### <a name="office-deployment-tool-error-codes"></a>Fehlercodes der Office-Bereitstellungstools

|||||
|-|-|-|-|
|Szenario|Rückgabecode|Benutzeroberfläche|Hinweis| 
|Deinstallationsaufwand, wenn es keine aktive Klick-und-Los-Installation gibt|– 2147418113, 0x8000ffff oder 2147549183|Fehlercode: 30088-1008<br>Fehlercode: 30125-1011 (404)|Office-Bereitstellungstool| 
|Installieren, wenn eine MSI-Version installiert wird|1603|-|Office-Bereitstellungstool| 
|Die Installation wurde vom Benutzer oder einer anderen Installation abgebrochen|17002|-|Klick-und-Los| 
|Versuch, eine 64-Bit-Version auf einem Gerät mit installierter 32-Bit-Version zu installieren|1603|-|Rückgabecode der Office-Bereitstellungstools| 
|Versuch, eine unbekannte SKU zu installieren (kein zulässiger Anwendungsfall für Office CSP, da nur gültige SKUs übergeben werden sollen)|17004|-|Klick-und-Los| 
|Nicht genügend Speicherplatz|17002|-|Klick-und-Los| 
|Der Klick-und-Los-Client konnte nicht gestartet werden (unerwartet)|17000|-|Klick-und-Los| 
|Der Klick-und-Los-Client konnte das Szenario nicht in die Warteschlange einreihen (unerwartet)|17001|-|Klick-und-Los| 

## <a name="next-steps"></a>Nächste Schritte

Sie können die Apps jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](/intune-azure/manage-apps/deploy-apps).

             

