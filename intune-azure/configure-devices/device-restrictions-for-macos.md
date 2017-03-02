---
title: "Intune-Einstellungen für Geräteeinschränkungen für macOS | Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie etwas über die Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf macOS-Geräten."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1e9c97d66e80de635ad43a1339d092b7987f738b
ms.openlocfilehash: 6856303581f5275c88d5d4efe07088de8f7ab713


---

# <a name="macos-device-restriction-settings-in-intune-azure-preview"></a>Einstellungen für Geräteeinschränkungen für macOS in der Vorschau von Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="password"></a>Kennwort
-   **Kennwort erforderlich:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
    -   **Erforderlicher Kennworttyp:** Geben Sie an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss). Diese Einstellung wird lediglich unter Mac OS X 10.10.3 und höher unterstützt.
    -   **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Geben Sie die erforderliche Anzahl komplexer Zeichen im Kennwort an (**0** bis **4**).<br>Bei komplexen Zeichen handelt es sich um Symbole (z. B. ein Fragezeichen**?**).
    -   **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen **4** und **16** Zeichen).
    -   **Einfache Kennwörter:** Erlauben Sie die Verwendung einfacher Kennwörter wie **0000** oder **1234**.
    -   **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts:** Geben Sie an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
    -   **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Geben Sie die Zeitdauer an, die der Computer inaktiv sein muss, bevor der Bildschirms gesperrt wird.
    -   **Kennwortablauf (Tage):** Geben Sie an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
    -   **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen (**1** bis **24**).

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

**Unzulässige Apps:** Listet die (nicht von Intune verwalteten) Apps auf, die Benutzer nicht installieren und ausführen dürfen.
**Genehmigte Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Um die Kompatibilität zu gewährleisten, dürfen Benutzer keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie dann einen Namen Ihrer Wahl sowie optional den Herausgeber der App und die Paket-ID der App an (z.B. *com.apple.calculator*).





<!--HONumber=Feb17_HO1-->

