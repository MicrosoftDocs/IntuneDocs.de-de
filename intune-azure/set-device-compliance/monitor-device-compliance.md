---
title: "Überwachen der Gerätekonformität | Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie, wie Sie die Gerätekonformität überwachen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: eb27002f449b3bbebb2a9b4ed780350c71eda881


---
# <a name="how-to-monitor-compliance-in-intune-azure-preview"></a>Überwachen der Gerätekonformität in der Vorschau von Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Sie können sich auf dem Blatt **Übersicht** eine Zusammenfassung des Status Ihrer **Konformitätsprofile** ansehen.
Sie können interaktiv einen Drilldown in den Diagrammen durchführen, um Details anzuzeigen. Wenn Sie mehrere Konformitätsprofile konfiguriert haben, können Sie den Status für jede Richtlinie anzeigen, indem Sie auf dem Blatt „Richtlinie“ im Abschnitt **Verwalten** die Option **Berichte** auswählen.  Die Details der für die Vorschau verfügbaren Berichte werden unten aufgeführt.

##  <a name="device-compliance"></a>Gerätekompatibilität

Die Zusammenfassung des Gerätekonformitätsberichts zeigt zusammengestellte Informationen zur Anzahl der Geräte, für die einer der folgenden Status gemeldet wurde:

- **Kompatibel:** Das Gerät wurde vor Kurzem auf Konformität überprüft und als konform mit den Einstellungen des angegebenen Konformitätsprofils bewertet.
- **Nicht kompatibel:**: Das Gerät wurde überprüft und als nicht konform bewertet.  Wenn im Profil eine Karenzzeit angegeben wurde, ist diese abgelaufen, und das Gerät hat damit in einen nicht konformen Status.
- **Karenzzeit:** Das Gerät wurde überprüft und als nicht konform bewertet. Die Karenzzeit gilt jedoch immer noch, bis das Gerät als nicht konform gekennzeichnet wird.

Sie können in jedem Abschnitt einen Drilldown durchführen, um weitere Details zu den einzelnen Geräten und Benutzern anzuzeigen.

## <a name="setting-compliance"></a>Einstellungskonformität

Der Einstellungskonformitätsbericht enthält Einzelheiten zu jeder Konformitätseinstellung. Beispiele:

- Anzahl der Geräte, die mit der Einstellung nicht konform sind
- Die Plattform, auf der die Einstellung angewendet wird

Sie können für jede Einstellung einen Drilldown durchführen, um weitere Informationen zu den Profilen, für die diese Einstellungen aktiviert wurden, und zu den konfigurierten Werten der Einstellungen zu erhalten.



<!--HONumber=Feb17_HO1-->

