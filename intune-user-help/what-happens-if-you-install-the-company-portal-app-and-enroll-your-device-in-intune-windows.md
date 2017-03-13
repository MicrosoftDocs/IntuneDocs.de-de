---
title: "Installieren der Unternehmensportal-App für Windows | Microsoft-Dokumentation"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 0e6b7ae1794ff0857dfb203eb3c67d7ba494bd8e
ms.openlocfilehash: bde2ccc0c170a85e926357d54fcf4ffe6ee50fd9
ms.lasthandoff: 02/21/2017


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>Was geschieht, wenn Sie die Unternehmensportal-App installieren und Ihr Windows-Gerät bei Intune registrieren?

Wenn Sie die Unternehmensportal-App installieren und damit anschließend ein Windows- oder Windows Phone-Gerät registrieren, erlauben Sie Ihrem IT-Administrator, Ihr Gerät zu verwalten, um die Daten von Unternehmen oder Schule zu schützen. In diesem Thema wird beschrieben, was bei Geräten mit einer früheren Version als Windows 10 geschieht. Windows 10-Geräte werden im [verwandten Thema](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md) behandelt.

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>Was mit allen Windows-Geräten nach der Registrierung geschieht
Wenn Sie Ihr Windows- oder Windows Phone-Gerät bei Intune registrieren, haben Sie folgende Möglichkeiten:

-   Zugreifen auf das Netzwerk des Unternehmens und auf E-Mails sowie andere arbeitsbezogene Dateien

-   Abrufen von Unternehmens-Apps aus dem Unternehmensportal (__Hinweis__: Bei Windows 7 und Windows Vista können Sie Unternehmens-Apps nur von der Unternehmensportal-Website abrufen)

-   Automatisches Einrichten Ihres Unternehmens- oder Schul-E-Mail-Kontos

-   Zurücksetzen Ihres Smartphones auf die Werkseinstellungen bei Verlust oder Diebstahl

Wenn Sie Ihr Gerät registrieren, erteilen Sie Ihrem IT-Administrator eine Berechtigung für Aktionen wie die folgenden:

-   Zurücksetzen des Geräts auf die Werkseinstellungen. Dies ist hilfreich, wenn das Gerät verloren geht oder gestohlen wird.

-   Entfernen von ausschließlich unternehmensrelevanten Dateien und Geschäfts-Apps. *Ihre persönlichen Daten und Einstellungen werden nicht entfernt.*

-   Ihr IT-Administrator kann die auf dem Gerät installierte Software anzeigen, einschließlich Software, die Sie persönlich installiert haben.

-   Festlegen von Anforderungen auf Ihrem Gerät. Beispielsweise muss ein Gerätekennwort oder eine PIN festgelegt sein, um zu helfen, Unternehmensdaten zu schützen. Ihr IT-Administrator kann möglicherweise auch einschränken, wie oft Sie ein falsches Kennwort eingeben können und das Gerät für Sie sperren, wenn Sie das Kennwort zu oft falsch eingeben.

-   Erfordern, dass Sie die Daten auf Ihrem Gerät verschlüsseln, um Unternehmensdaten bei Verlust oder Diebstahl Ihres Geräts zu schützen.

-   Sie müssen die Bedingungen akzeptieren.

-   Verhindern, dass Sie Fotos von unternehmensrelevanten Daten machen

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>Was mit allen Windows-PCs nach der Registrierung geschieht

-  Auf Ihrem Computer wird Software installiert, mit deren Hilfe Ihr IT-Administrator den Computer verwalten kann und mit der Sie Unternehmensressourcen wie Apps und Supportinformationen abrufen können. Ihr IT-Administrator kann diese Software möglicherweise automatisch aktualisieren.

-  Intune Endpoint Protection wird möglicherweise auf Ihrem Computer installiert. Diese Software überprüft den Computer auf Viren und Malware.

-  Der IT-Administrator kann Daten von der Festplatte Ihres Computers sammeln oder löschen.

-  Ihr IT-Administrator kann Apps und Updates auf dem Computer installieren.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>Was nach der Registrierung des Geräts alle acht Stunden geschieht

Etwa alle acht Stunden führen registrierte Geräte folgende Aktionen aus:

-   Herunterladen aller Richtlinien- oder App-Updates, die Ihr IT-Administrator zur Verfügung gestellt hat.

-   Senden aller Hardwareinventur-Updates.

-   Senden aller Unternehmens-App-Inventaraktualisierungen.

Wenn Sie Fragen haben, wenden Sie sich an Ihren IT-Administrator. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](http://portal.manage.microsoft.com).
