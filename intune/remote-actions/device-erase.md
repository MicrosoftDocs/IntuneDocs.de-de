---
title: Löschen eines macOS-Geräts
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2f4ce1295d4a3f2250988d25246c532ff2cdd73
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728233"
---
# <a name="erase-all-data-from-a-macos-device"></a>Löschen aller Daten von einem macOS-Gerät

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie können alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen. Das Gerät wird auch aus der Intune-Verwaltung entfernt. Der Endbenutzer erhält keine Warnung.

1. Navigieren Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) zu **Geräte** > **Alle Geräte**, und wählen Sie das Gerät aus, das Sie löschen möchten.
![Screenshot](./media/device-erase/choosedevice.png)
2. Klicken Sie auf **Weitere** > **Löschen**, und geben Sie eine sechsstellige Nummer für die **PIN für Wiederherstellung** ein. Dies ist die Pin, die Sie dem Benutzer zur Verfügung stellen müssen, damit er das Betriebssystem auf seinem Gerät installieren kann. Achten Sie darauf, dass Sie sich diese Pin notieren, da sie nach der Löschaktion nicht sichtbar ist.
![Screenshot](./media/device-erase/providepin.png)
3. Klicken Sie auf **OK**, um das Gerät zu löschen.