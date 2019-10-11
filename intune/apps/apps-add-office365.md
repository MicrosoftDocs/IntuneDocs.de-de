---
title: Zuweisen von Office 365-Apps an Windows 10-Geräte mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Microsoft Intune verwenden können, um Office 365-Apps auf Windows 10-Geräten zu installieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38cc8ebc7be09d6ca0322a916d71f1fc86d3e49b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725204"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Zu den verfügbaren [App-Typen](apps-add.md#app-types-in-microsoft-intune) gehören Office 365-Apps für Windows 10-Geräte. Wenn Sie den App-Typ in Intune auswählen, können Sie Office 365-Apps zuweisen und auf Geräten mit Windows 10 installieren. Sie können auch Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Online Plan 2 zuweisen und installieren, wenn Sie über die entsprechenden Lizenzen verfügen. Die verfügbaren Office 365-Apps werden in Azure in der Intune-Konsole als einzelne Einträge in der App-Liste angezeigt.

> [!NOTE]
> Sie müssen Office 365 ProPlus-Lizenzen verwenden, um Office 365 ProPlus-Apps zu aktivieren, die über Microsoft Intune bereitgestellt wurden. Die Office 365 Business-Edition wird nicht von Intune unterstützt.

## <a name="before-you-start"></a>Vorbereitung

> [!IMPORTANT]
> Wenn es auf dem Endbenutzergerät MSI-Office-Apps gibt, müssen Sie diese Apps mit dem Feature **MSI entfernen** sicher deinstallieren. Andernfalls schlägt die Installation der von Intune bereitgestellten Office 365-Apps fehl.

- Auf den Geräten, auf denen Sie diese Apps bereitstellen, muss das Windows 10 Creators Update oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps aus der Office 365-Suite.
- Falls Office-Apps geöffnet sind, wenn Intune die App-Suite installiert, kann bei der Installation ein Fehler auftreten, und Benutzer verlieren möglicherweise Daten aus nicht gespeicherten Dateien.
- Diese Installationsmethode wird auf Windows Home-, Windows Team-, Windows Holographic- oder Windows Holographic for Business-Geräten nicht unterstützt.
- Intune unterstützt nicht das Installieren von Office 365-Desktop-Apps aus dem Microsoft Store (sogenannte Office Centennial-Apps) auf einem Gerät, für das bereits Office 365-Apps mit Intune bereitgestellt wurden. Wenn Sie diese Konfiguration installieren, kann sie zu Datenverlusten oder -beschädigungen führen.
- Mehrere erforderliche oder verfügbare App-Zuweisungen sind nicht additiv. Eine spätere App-Zuweisung überschreibt bereits vorhandene installierte App-Zuweisungen. Wenn z.B. der erste Satz von Office-Apps Word enthält und der spätere nicht, wird Word deinstalliert. Diese Bedingung gilt nicht für Visio- oder Project-Anwendungen.
- Mehrere Office 365-Bereitstellungen werden derzeit nicht unterstützt. Es wird nur eine Bereitstellung an das Gerät übermittelt.
- **Office-Version:** Wählen Sie aus, ob Sie die 32-Bit- oder die 64-Bit-Version von Office zuweisen möchten. Sie können die 32-Bit-Version sowohl auf 32-Bit- als auch auf 64-Bit-Geräten installieren. Die 64-Bit-Version lässt sich jedoch nur auf 64-Bit-Geräten installieren.
- **Remove MSI from end-user devices** (MSI von Endbenutzergeräten entfernen): Wählen Sie aus, ob Sie vorhandene Office-MSI-Apps von Endbenutzergeräten entfernen möchten. Die Installation kann nicht erfolgreich durchgeführt werden, wenn bereits MSI-Apps auf den Endbenutzergeräten vorhanden sind. Die zu deinstallierenden Apps sind nicht auf die Apps beschränkt, die in **App-Suite konfigurieren** zur Installation ausgewählt wurden, sondern es werden sämtliche Office-(MSI)-Apps vom Endbenutzergerät entfernt. Weitere Informationen finden Sie unter [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus (Entfernen vorhandener MSI-Versionen von Office beim Upgrade auf Office 365 ProPlus)](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Wenn Intune Office auf den Computern Ihrer Endbenutzer neu installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen.

## <a name="get-started"></a>Erste Schritte

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus.
5. Wählen Sie **Hinzufügen** aus.
6. Wählen Sie im Bereich **Apps hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** die Option **Windows 10** aus.

## <a name="select-settings-format"></a>Auswählen von Einstellungsformaten

Sie können eine Methode zum Konfigurieren von App-Einstellungen auswählen, indem Sie auf **Einstellungsformat** klicken. Es stehen die folgenden Einstellungsformate zur Verfügung:
- Konfigurations-Designer
- Eingeben von XML-Daten

Wenn Sie auf **Konfigurations-Designer** klicken, ändert sich das Blatt **App hinzufügen**, und es werden zwei weitere Einstellungsoptionen angezeigt:
- App-Suite konfigurieren
- Einstellungen der App-Suite

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Wenn Sie auf **XML-Daten eingeben** klicken, wird das Blatt **App hinzufügen** mit der Option **XML-Daten eingeben** angezeigt. Klicken Sie auf diese Option, um das Blatt **Konfigurationsdatei** anzuzeigen. 

![Konfigurations-Designer für Office 365 hinzufügen](./media/apps-add-office365/apps-add-office365-01.png)
    
Weitere Informationen zur Option **XML-Daten eingeben** finden Sie weiter unten im Abschnitt [Eingeben von XML-Daten](apps-add-office365.md#enter-xml-format).

## <a name="configure-app-suite-information"></a>Konfigurieren von Informationen zur App-Suite

In diesem Schritt stellen Sie Informationen über die App-Suite bereit. Diese Informationen helfen Ihnen dabei, die App-Suite in Intune zu identifizieren. Außerdem können Benutzer sie im Unternehmensportal leichter finden.

1. Wählen Sie im Bereich **App hinzufügen** die Option **Informationen zur App-Suite** aus.
2. Gehen Sie im Bereich **Informationen zur App-Suite** folgendermaßen vor:
    - **Name der Suite**: Geben Sie den Namen der App-Suite so ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Suitenamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung der Suite**: Geben Sie eine Beschreibung der App-Suite ein. Sie können die Apps auflisten, die Sie einschließen möchten.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App-Suite im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Das Office 365-Logo wird gemeinsam mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wählen Sie **OK** aus.

## <a name="configure-app-suite"></a>Konfigurieren der App-Suite

Wenn Sie im Dropdownfeld **Setting format** (Einstellungsformat) die Option **Konfigurations-Designer** ausgewählt haben, wird die Option **App-Suite konfigurieren** auf dem Blatt **App hinzufügen** angezeigt. Wählen Sie die Office-Apps aus, die Sie den Geräten zuweisen möchten.

1. Wählen Sie auf dem Blatt **App hinzufügen** die Option **App-Suite konfigurieren** aus.
2. Wählen Sie auf dem Blatt **App-Suite konfigurieren** die Office-Standard-Apps aus, die Sie Geräten zuweisen möchten.  
    Sie können zusätzlich Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Online Plan 2 installieren, wenn Sie über die entsprechenden Lizenzen verfügen.
3. Wählen Sie **OK** aus.

## <a name="configure-app-suite-settings"></a>Konfigurieren der Einstellungen der App-Suite

Wenn Sie im Dropdownfeld **Setting format** (Einstellungsformat) die Option **Konfigurations-Designer** ausgewählt haben, wird die Option **Einstellungen der App-Suite** auf dem Blatt **App hinzufügen** angezeigt. In diesem Schritt konfigurieren Sie Installationsoptionen für die App-Sammlung. Die Einstellungen gelten für alle Apps, die Sie der Suite hinzugefügt haben.

1. Wählen Sie im Bereich **App hinzufügen** die Option **Einstellungen der App-Suite** aus.
2. Gehen Sie im Bereich **Einstellungen der App-Suite** folgendermaßen vor:
    - **Office-Version**: Wählen Sie aus, ob Sie die 32-Bit- oder die 64-Bit-Version von Office zuweisen möchten. Sie können die 32-Bit-Version sowohl auf 32-Bit- als auch auf 64-Bit-Geräten installieren. Die 64-Bit-Version lässt sich jedoch nur auf 64-Bit-Geräten installieren.
    - **Updatekanal**: Wählen Sie aus, wie Office auf Geräten aktualisiert wird. Informationen zu den unterschiedlichen Updatekanälen finden Sie in der [Übersicht der Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Es stehen die folgenden Optionen zur Auswahl:
        - **Monatlich**
        - **Monatlich (Ziel)**
        - **Halbjährlich**
        - **Halbjährlich (Ziel)**

        Nachdem Sie einen Kanal ausgewählt haben, können Sie danach **Specific** (Spezifisch) auswählen, um eine bestimmte Office-Version für den ausgewählten Kanal oder die Endbenutzergeräte zu installieren. Dann können Sie die **spezifische Version** von Office auswählen, die verwendet werden soll.
        
        Die verfügbaren Versionen werden im Laufe der Zeit geändert. Wenn Sie eine neue Bereitstellung erstellen, können deshalb die verfügbaren Versionen aktueller sein, und bestimmte ältere Versionen sind möglicherweise nicht mehr verfügbar. Für aktuelle Bereitstellungen sind weiterhin die älteren Versionen verfügbar, jedoch wird die Liste mit den Versionen nicht ständig pro Kanal aktualisiert.
        
        Der Berichtsstatus für Geräte, deren angeheftete Version (oder andere Eigenschaften) aktualisiert wurde und die als verfügbar bereitgestellt wurden, lautet „Installiert“, wenn die vorherige Version vor dem Check-In des Geräts installiert wurde. Wenn das Gerät eingecheckt wird, ändert sich der Status vorübergehend in „Unbekannt“. Dies wird dem Benutzer nicht angezeigt. Wenn der Benutzer die Installation der neuesten verfügbaren Version startet, wird der Status als „Installiert“ angezeigt.
        
        Weitere Informationen finden Sie unter [Übersicht über die Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **Remove MSI from end-user devices** (MSI von Endbenutzergeräten entfernen): Wählen Sie aus, ob Sie vorhandene Office-MSI-Apps von Endbenutzergeräten entfernen möchten. Die Installation kann nicht erfolgreich durchgeführt werden, wenn bereits MSI-Apps auf den Endbenutzergeräten vorhanden sind. Die zu deinstallierenden Apps sind nicht auf die Apps beschränkt, die in **App-Suite konfigurieren** zur Installation ausgewählt wurden, sondern es werden sämtliche Office-(MSI)-Apps vom Endbenutzergerät entfernt. Weitere Informationen finden Sie unter [Remove existing MSI versions of Office when upgrading to Office 365 ProPlus (Entfernen vorhandener MSI-Versionen von Office beim Upgrade auf Office 365 ProPlus)](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Wenn Intune Office auf den Computern Ihrer Endbenutzer neu installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen. 
    - **Microsoft-Software-Lizenzbedingungen automatisch akzeptieren**: Wählen Sie diese Option aus, wenn es nicht erforderlich ist, dass Endbenutzer die Lizenzvereinbarung akzeptieren. Intune akzeptiert daraufhin die automatisch die Vereinbarung.
    - **Aktivierung gemeinsam genutzter Computer verwenden**: Wählen Sie diese Option aus, wenn sich mehrere Benutzer einen Computer teilen. Weitere Informationen finden Sie in der [Übersicht über die Aktivierung gemeinsam genutzter Computer für Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Sprachen**: Office wird automatisch in allen unterstützen Sprachen installiert, die mit Windows auf Endbenutzergeräten installiert wurden. Wählen Sie diese Option, wen Sie zusätzliche Sprachen mit der App-Sammlung installieren möchten. <p></p>
    Sie können zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung von Sprachen in Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT).

1. Wählen Sie **Scope (Tags)**  > **Add** (Bereich (Markierungen) > Hinzufügen) aus.
2. Verwenden Sie das Feld **Auswählen**, um nach Bereichsmarkierungen zu suchen.
3. Aktivieren Sie das Kontrollkästchen neben den Bereichsmarkierungen, die Sie dieser App zuweisen möchten.
4. Klicken Sie auf **Auswählen** > **OK**.

## <a name="enter-xml-format"></a>Eingeben von XML-Daten

Wenn Sie im Dropdownfeld **Setting format** (Einstellungsformat) die Option **XML-Daten eingeben** ausgewählt haben, wird die Option **Enter XML format** (XML-Format eingeben) auf dem Blatt **App hinzufügen** angezeigt. Weitere Informationen finden Sie unter [Konfigurationsoptionen für das Office-Bereitstellungstool](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Fertig stellen

Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**. Die von Ihnen erstellte App wird in der Liste der Apps angezeigt.

## <a name="troubleshooting"></a>Problembehandlung
Intune verwendet das [Office-Bereitstellungstool](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) zum Herunterladen und Bereitstellen von Office 365 ProPlus auf Ihren Clientcomputern über das [Office 365-CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Sehen Sie sich die Best Practices in [Verwalten von Office 365-Endpunkten](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) an, um sicherzustellen, dass Ihre Netzwerkkonfiguration Clients den Zugriff auf das CDN erlaubt, anstatt den CDN-Datenverkehr über zentrale Proxys weiterzuleiten, um unnötige Latenzen zu vermeiden.

Führen Sie den [Microsoft Support- und Wiederherstellungs-Assistenten für Office 365](https://diagnostics.office.com) auf einem Zielgerät aus, falls Installations- oder Laufzeitprobleme auftreten.

## <a name="errors-during-installation-of-the-app-suite"></a>Fehler während der Installation der App-Suite

Informationen zum Anzeigen ausführlicher Installationsprotokolle finden Sie im Blogbeitrag [How to enable Office 365 ProPlus ULS logging](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) (Aktivieren der ULS-Protokollierung von Office 365 ProPlus).

In den nachstehenden Tabellen sind die häufigsten Fehlercodes aufgeführt, die auftreten können, sowie deren Bedeutung.

### <a name="status-for-office-csp"></a>Status für Office CSP

| Status | Phase | Beschreibung |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Herunterladen | Das Office-Bereitstellungstool konnte nicht heruntergeladen werden |
| 13 (ERROR_INVALID_DATA) | - | Die Signatur des heruntergeladenen Office-Bereitstellungstools konnte nicht überprüft werden. |
| Fehlercode aus CertVerifyCertificateChainPolicy | - | Fehlgeschlagene Zertifizierungsprüfung für das heruntergeladene Office-Bereitstellungstool. |
| 997 | WIP | Installation |
| 0 | Nach der Installation | Die Installation war erfolgreich |
| 1603 (ERROR_INSTALL_FAILURE) | - | Fehler bei Voraussetzungsprüfungen, z.B.:SxS (beim Installationsversuch war 2016 MSI installiert)Nicht übereinstimmende VersionSonstiges |
| 0x8000ffff (E_UNEXPECTED) | - | Beim Versuch, eine Deinstallation durchzuführen, war keine Klick-und-Los-Version von Office auf dem Computer vorhanden. |
| 17002 | - | Das Szenario (Installation) konnte nicht abgeschlossen werden. Mögliche Gründe:Installation durch Benutzer abgebrochen Installation durch andere Installation abgebrochen Fehlender Speicherplatz auf dem Datenträger während der Installation Unbekannte Sprach-ID |
| 17004 | - | Unbekannte SKUs |


### <a name="office-deployment-tool-error-codes"></a>Fehlercodes der Office-Bereitstellungstools

| Szenario | Rückgabecode | Benutzeroberfläche | Hinweis |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Deinstallationsaufwand, wenn keine aktive Klick-und-Los-Installation vorhanden ist | – 2147418113, 0x8000ffff oder 2147549183 | Fehlercode: 30088-1008Fehlercode: 30125-1011 (404) | Office-Bereitstellungstool |
| Installieren, wenn eine MSI-Version installiert wird | 1603 | - | Office-Bereitstellungstool |
| Die Installation wurde vom Benutzer oder einer anderen Installation abgebrochen | 17002 | - | Klick-und-Los |
| Versuch, eine 64-Bit-Version auf einem Gerät mit installierter 32-Bit-Version zu installieren | 1603 | - | Rückgabecode der Office-Bereitstellungstools |
| Versuch, eine unbekannte SKU zu installieren (kein zulässiger Anwendungsfall für Office CSP, da nur gültige SKUs übergeben werden sollen) | 17004 | - | Klick-und-Los |
| Nicht genügend Speicherplatz | 17002 | - | Klick-und-Los |
| Der Klick-und-Los-Client konnte nicht gestartet werden (unerwartet) | 17000 | - | Klick-und-Los |
| Der Klick-und-Los-Client konnte das Szenario nicht in die Warteschlange einreihen (unerwartet) | 17001 | - | Klick-und-Los |

## <a name="next-steps"></a>Nächste Schritte

- Wie Sie die Apps den von Ihnen ausgewählten Gruppen zuweisen können, erfahren Sie unter [Das Zuweisen von Apps zu Gruppen](/intune-azure/manage-apps/deploy-apps).