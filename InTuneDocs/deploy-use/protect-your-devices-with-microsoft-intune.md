---
title: "Schützen von Geräten | Microsoft Intune"
description: "Erfahren Sie mehr über die Methoden, mit denen Intune Ihnen helfen kann, Ihre Geräte vor nicht autorisiertem Zugriff und anderen Bedrohungen zu schützen."
keywords: 
author: Robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 5c82e905afeab2d7da8a2e9cebf651ed3c8ce21c


---

# Schützen von Geräten mit Microsoft Intune

Microsoft Intune bietet einen vollständigen Satz von Funktionen, um Ihnen beim Schutz der von Ihnen verwalteten Geräte sowie den Daten, die auf diesen Geräten gespeichert sind, zu helfen. Lesen Sie dieses Thema, um die Grundlagen dieser Funktionen kennenzulernen und herauszufinden, wie Sie mehr darüber erfahren können.

## Allgemeine Vorgehensweisen zum Schützen aller Geräte

### Gerätekonfiguration
Die Intune-[Konfigurationsrichtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) helfen Ihnen dabei, durch das Steuern zahlreicher Einstellungen und Funktionen Geräte zu schützen und zu konfigurieren. Beispiel:
- Sie können die Verwendung von Hardwarefeatures auf dem Gerät, z.B. die Kamera oder Bluetooth, einschränken.
- Sie können kompatible und nicht kompatible Apps konfigurieren. Sie werden benachrichtigt, wenn eine nicht kompatible App installiert wird (und einige Plattformen können die Installation tatsächlich blockieren).

### Zurücksetzen von Kennungen, wenn Geräte für ihre Benutzer gesperrt sind
Da der erste Schritt zum Schutz von Unternehmensdaten auf mobilen Geräten darin besteht, eine Kennung abzufragen, damit das Gerät verwendet werden kann, müssen Sie mitunter eine [Kennung zurücksetzen](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) oder einem Mitarbeiter hierbei helfen, entweder indem Sie die Kennung entfernen oder remote eine vorübergehende Kennung festlegen. Sie können nach einem Verlust oder Diebstahl ein [Gerät auch remote sperren](use-remote-lock-and-passcode-reset-in-microsoft-intune.md).

### Außerkraftsetzen von Geräten und Entfernen von Daten
Wenn ein Gerät [aus der Intune-Verwaltung entfernt](retire-devices-from-microsoft-intune-management) werden muss (z.B. weil ein Benutzer die Organisation verlässt oder das Gerät verloren wurde oder gestohlen wurde), dann möchten Sie wahrscheinlich Daten von diesem Gerät entfernen. Intune bietet eine Reihe von Methoden, die sicherstellen, dass Ihre Unternehmensdaten sicher bleiben.

### Verlangen, dass Geräte kompatibel sein müssen
Intune bietet [Gerätekompatibilitätsrichtlinien](introduction-to-device-compliance-policies-in-microsoft-intune), mit deren Hilfe Sie Geräte auswerten (und in einigen Fällen auch korrigieren) können, die mit den von Ihnen angegebenen Regeln nicht kompatibel sind. Sie können z.B. iOS-Geräte melden, die gehackt wurden, oder Sie melden ob Geräte verschlüsselt sind oder ob Windows 10-Geräte durch den Dienst zum Nachweis der Geräteintegrität als fehlerfrei gemeldet wurden.

### Schützen von Apps und Daten, die verwendet werden
Intune bietet Ihnen eine Reihe von Funktionen an, die Sie zum Schützen Ihrer Apps und deren Daten verwenden können. Mobile Anwendungsverwaltungsrichtlinien (MAM) können z.B. verhindern, dass Daten von einer geschützten App gesichert werden, das Kopieren und Einfügen zu anderen Apps beschränken, und angeben, dass eine PIN für den Zugriff auf eine App nötig ist usw. Weitere Informationen zum Schutz von Apps finden Sie unter [Schützen von Apps und Daten mit Microsoft Intune](protect-apps-and-data-with-microsoft-intune).

## Weitere Funktionen für Windows-Geräte

### Hinzufügen einer zusätzlichen Schutzebene für Windows-Geräte
Die [mehrstufige Authentifizierung](protect-windows-devices-with-multi-factor-authentication.md) (Multi-Factor Authentication, MFA) ist eine sicherere Methode der Authentifizierung der Benutzer von Windows- und Windows Phone-Geräten im Netzwerk.  Bei Verwendung von MFA müssen Benutzer ihre Identität zusätzlich zu Benutzername und Kennwort über einen Telefonanruf oder eine SMS bestätigen.

### Steuern der Einstellungen von Windows Hello for Business auf Windows-Geräten
Intune ermöglicht die Integration in [Windows Hello for Business](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (zuvor Microsoft Passport). Dies ist eine alternative Anmeldemethode für Windows 10 und höher, die Active Directory oder ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen.

## Weitere Funktionen für iOS-Geräte

### Umgehung der Aktivierungssperre auf iOS-Geräten
Die Aktivierungssperre ist eine Funktion, mit der Geräte von Benutzern geschützt werden, indem die Eingabe der Apple ID und des Kennworts gefordert wird, bevor das Gerät gelöscht oder reaktiviert werden kann. Dies kann jedoch zu Problemen führen, z.B. wenn der Benutzer das Unternehmen verlässt, ohne die Sperre wieder aufzuheben. Mit [Umgehung der iOS-Aktivierungssperre](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) kann die Sperre von überwachten iOS-Geräten umgangen werden, sodass sie neu zugewiesen oder gelöscht werden können.



## Schützen von mit dem Intune-Client verwalteten Windows-PCs
Intune unterstützt auch Sicherheitsrichtlinien für Windows-PCs, die Sie nicht registrieren, sondern über die Intune-Computerclientsoftware verwalten. Erfahren Sie, wie diese Richtlinien Sie beim Schützen Ihrer Windows-PCs unterstützen: [Verwenden von Richtlinien zum Schutz von Windows-PCs, auf denen die Intune-Clientsoftware ausgeführt wird](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Oct16_HO4-->

