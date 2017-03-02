---
title: "Auswählen der Registrierungsmethode für iOS-Geräte in Intune | Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie, wie Sie die Registrierung von iOS-Geräten in Microsoft Intune einrichten."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c228601451b33238d0f6929987dcdec3a5e56e8d


---

# <a name="choose-how-to-enroll-ios-devices"></a>Auswählen der Registrierungsmethode für iOS-Geräte

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Dieses Thema beschreibt die möglichen Methoden zum Registrieren von iOS-Geräten und die Voraussetzungen für die Anmeldung.

Ihre Entscheidung, welche Methode zum Registrieren von iOS-Geräten verwendet wird, sollte auf den folgenden Informationen basieren. Alle der folgenden Methoden mit Ausnahme von BYOD sind für die Registrierung von firmeneigenen Geräten ausgelegt.

**Voraussetzung:** Ein [Apple Push Notification Service-Zertifikat](get-an-apple-mdm-push-certificate.md) ist erforderlich.

## <a name="user-owned-ios-devices-byod"></a>iOS-Gerät im Besitz des Benutzers (BYOD)

Wenn Benutzer ihre privaten BYOD-Geräte (Bring Your Own Device) registrieren möchten, besteht die einzige verfügbare Registrierungsmethode darin, dass Benutzer die Unternehmensportal-App für iOS aus dem App Store herunterladen und die Registrierungsanweisungen in der App befolgen. Nach der Registrierung können Benutzer eine Verbindung mit dem Unternehmensnetzwerk herstellen, der Domäne oder Azure Active Directory beitreten und Zugriff auf Unternehmensressourcen erhalten.

## <a name="apple-configurator"></a>Apple Configurator

Sie können iOS-Geräte registrieren, indem Sie ein Unternehmensregistrierungsprofil exportieren und diese mobilen Geräte anschließend mit einem Mac verbinden, auf dem [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) ausgeführt wird. Apple Configurator unterstützt zwei Formen der Registrierung:

- **Setup-Assistent für die Registrierung**: Setzt das Gerät auf die Werkseinstellungen zurück und bereitet es für die Einrichtung durch den neuen Benutzer des Geräts vor. Bei dieser Methode muss der Administrator das iOS-Gerät per USB mit einem Macintosh-Computer verbinden, auf dem Apple Configurator ausgeführt wird, um die Registrierung vorzukonfigurieren. Die Geräte werden dann an ihre Benutzer übergeben, die den Setup-Assistenten ausführen. Dieser Prozess konfiguriert das Gerät mit den Anmeldeinformationen Ihres Geschäfts- oder Schulkontos und schließt den Registrierungsvorgang ab. Weitere Informationen finden Sie unter [Registrieren von iOS-Geräten mithilfe von Apple Configurator und Setup-Assistent](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md).

- **Direkte Registrierung**: Erstellt eine Apple Configurator-kompatible Datei zur Verwendung während der Vorbereitung des Geräts. Das registrierte Gerät wird nicht auf die Werkseinstellungen zurückgesetzt und ist keinem Benutzer zugewiesen. Um Geräte anzumelden, muss der Administrator das iOS-Gerät per USB mit einem Macintosh-Computer verbinden, auf dem Apple Configurator ausgeführt wird. Weitere Informationen finden Sie unter [Registrierung von iOS-Geräte mit der Option „Direkte Registrierung“ von Apple Configurator](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md).

## <a name="use-the-device-enrollment-program-dep"></a>Verwenden des Geräteregistrierungsprogramms (Device Enrollment Program, DEP)

Auf über das DEP erworbenen Geräten wird ein Registrierungsprofil „Drahtlos“ bereitgestellt. Wenn ein Benutzer auf dem Gerät den Setup-Assistenten ausführt, wird das Gerät bei Intune registriert. Die Registrierung von Geräten über DEP kann von Benutzern nicht rückgängig gemacht werden. Weitere Informationen finden Sie unter [Registrieren von iOS-Geräten mithilfe des Programms zur Geräteregistrierung](enroll-ios-devices-using-device-enrollment-program.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Verwenden des Geräteregistrierungs-Managers
Der Geräteregistrierungs-Manager ist eine Art von Benutzerkonto, mit der bis zu 1.000 Geräte registriert werden können. Sie fügen dem Konto des Geräteregistrierungs-Managers (DEM) vorhandene Benutzer hinzu, damit diese bestimmte Fähigkeiten erhalten. Jedes Gerät, das der DEM-Benutzer registriert, verwendet eine einzelne Intune-Lizenz. Weitere Informationen finden Sie unter [Registrieren von Geräten mithilfe des Geräteregistrierungs-Managers](enroll-devices-using-device-enrollment-manager.md).



<!--HONumber=Feb17_HO1-->

