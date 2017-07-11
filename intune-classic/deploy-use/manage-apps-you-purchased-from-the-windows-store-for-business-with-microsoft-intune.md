---
title: "Verwalten von Windows Store für Unternehmen-Apps"
description: "Stellen Sie eine Verbindung zwischen Microsoft Intune und dem Windows Store für Unternehmen her, wenn Sie über ein Volumenprogramm erworbene Apps über die Intune-Konsole verwalten und bereitstellen möchten."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 888d825fb9955e97b49e54a0c36ab882055076d8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2017
---
# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Verwalten von Apps, die im Windows Store für Unternehmen erworben wurden, mit Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Im [Windows Store für Unternehmen](https://www.microsoft.com/business-store) können Sie Apps für Ihre Organisation suchen und einzeln oder im Rahmen eines Volumenprogramms erwerben. Indem Sie den Store mit Microsoft Intune verbinden, können Sie im Rahmen von Volumenprogrammen erworbene Apps über die Intune-Konsole verwalten. Beispiel:
* Sie können die Liste der Apps, die Sie im Speicher erworben haben, mit Intune synchronisieren.
* Synchronisierte Apps werden in der Intune-Verwaltungskonsole angezeigt und können wie alle anderen Apps bereitgestellt werden.
* Sie können in der Intune-Verwaltungskonsole die Anzahl der verfügbaren und der verwendeten Lizenzen nachverfolgen.
* Intune blockiert die Bereitstellung und Installation von Apps, wenn nicht genügend Lizenzen vorhanden sind.

## <a name="before-you-start"></a>Vorbereitung
Überprüfen Sie die folgenden Informationen, bevor Sie beginnen, Apps aus dem Windows Store für Unternehmen zu synchronisieren und bereitzustellen:
* Sie müssen Intune als Autorität zur Verwaltung mobiler Geräte für Ihre Organisation konfigurieren. Weitere Informationen finden Sie unter [Voraussetzungen für die Registrierung von Geräten in Microsoft Intune](prerequisites-for-enrollment.md).
* Sie müssen im Windows Store für Unternehmen über ein registriertes Konto verfügen.
* Sobald ein Konto für den Windows Store für Unternehmen Intune zugeordnet wurde, können Sie dieses zugeordnete Konto nicht mehr ändern.
* Apps, die im Store erworben wurden, können Intune nicht manuell hinzugefügt oder daraus gelöscht werden. Sie können nur mit dem Windows Store für Unternehmen synchronisiert werden.
* Intune synchronisiert nur online lizenzierte Apps, die Sie aus dem Windows Store für Unternehmen erworben haben.
* Geräte müssen mit Active Directory-Domänendiensten oder einem Arbeitsbereich verknüpft sein, damit diese Funktion verwendet werden kann.
* Registrierte Geräte müssen die Version 1511 von Windows 10 verwenden.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Verknüpfen Ihres Kontos für den Windows Store für Unternehmen mit Intune
Bevor Sie die Synchronisierung in der Intune-Konsole aktivieren, müssen Sie Ihr Konto für den Windows Store für Unternehmen so konfigurieren, dass Intune als Verwaltungstool verwendet wird:
1. Stellen Sie sicher, dass Sie sich beim Windows Store für Unternehmen und bei Intune mit demselben Mandantenkonto anmelden.
2. Wählen Sie im Windows Store für Unternehmen **Einstellungen** > **Verwaltungstools** aus.
3. Wählen Sie auf der Seite „Verwaltungstools“ die Option **Verwaltungstool hinzufügen** und dann **Microsoft Intune** aus.

> [!NOTE]
> Wenn Sie mehr als ein Verwaltungstool zum Bereitstellen von Windows Store für Unternehmen-Apps verwenden, konnten Sie vorher nur eine App dem Windows Store für Unternehmen zuordnen. Nun können Sie mehrere Verwaltungstools dem Store zuordnen, z.B. Intune und Configuration Manager.

Sie können nun fortfahren und die Synchronisierung in der Intune-Konsole einrichten.

## <a name="configure-synchronization"></a>Konfigurieren der Synchronisierung

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Option **Verwaltung** aus.
2. Erweitern Sie im Arbeitsbereich **Verwaltung** den Knoten **Verwaltung mobiler Geräte** > **Windows**, und wählen Sie dann **Store für Unternehmen** aus.
3. Gehen Sie auf der Seite **Windows Store für Unternehmen** folgendermaßen vor:
 * Klicken Sie auf den Link zur Registrierung für den Windows Store für Unternehmen, falls Sie dies noch nicht getan haben.
 * Nachdem Sie sich registriert haben, wählen Sie **Synchronisierung konfigurieren** aus.
4. Wählen Sie im Dialogfeld **App-Synchronisierung mit dem Windows Store für Geschäfte konfigurieren** die Option **Synchronisierung mit dem Windows Store für Geschäfte aktivieren** aus.
5. Wählen Sie aus der Dropdownliste **Sprache** die Sprache aus, in der Apps aus dem Windows Store für Unternehmen in der Intune-Konsole angezeigt werden. Die Installation der Apps erfolgt unabhängig von der Anzeigesprache in der Sprache des Endbenutzers, sofern verfügbar.
6. Klicken Sie auf **OK**.

## <a name="synchronize-apps"></a>Synchronisieren von Apps

1. Wählen Sie auf der Seite **Windows Store für Unternehmen** die Option **Jetzt synchronisieren** aus, um die im Store erworbenen Apps mit Intune zu synchronisieren.
2. Wählen Sie im Arbeitsbereich **Apps** die Option **Apps** > **Per Volumenlizenz erworbene Apps** aus, um die Apps anzuzeigen, die Sie bereitstellen können, und zu überprüfen, ob Ihre erworbenen Apps fehlerfrei importiert wurden. Die Apps werden in diesem Knoten mit der Gesamtzahl der Lizenzen angezeigt, die Sie besitzen, und der Anzahl der Lizenzen, die Ihnen zur Verfügung stehen.
Sie können z. B. die Unternehmensportal-App (online lizenziert) im Windows Store für Unternehmen erwerben, mit der Intune-Konsole synchronisieren und dann als erforderliche App auf den benötigten Windows-10-Geräten bereitstellen. 


## <a name="deploy-apps"></a>Bereitstellen von Apps

Sie stellen Apps aus dem Store auf die gleiche Weise wie andere Intune-Apps bereit. Weitere Informationen finden Sie unter [Bereitstellen von Apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Wenn Sie eine App aus dem Windows Store für Unternehmen bereitstellen, wird von jedem Benutzer, der die App installiert, eine Lizenz verwendet. Wenn alle verfügbaren Lizenzen für eine bereitgestellte App verwendet werden, können keine weiteren Kopien bereitgestellt werden. Sie müssen eine der folgenden Aktionen ausführen:
* Deinstallieren Sie die App auf einigen Geräten.
* Beschränken Sie die aktuelle Bereitstellung auf die Anzahl von Benutzern, für die Sie über Lizenzen verfügen.
* Erwerben Sie zusätzliche Kopien der App im Windows Store für Unternehmen.

> [!Important]
> Bereitgestellte Apps sind nur für den Benutzer verfügbar, der das Gerät ursprünglich registriert hat. Andere Benutzer können nicht auf die App zugreifen.


### <a name="see-also"></a>Weitere Informationen:
[Hinzufügen von Apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)