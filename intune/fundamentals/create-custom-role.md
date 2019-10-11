---
title: Erstellen einer benutzerdefinierten Rolle in Intune
description: Erfahren Sie, wie Sie eine benutzerdefinierte Rolle in Microsoft Intune erstellen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7e8f5077f2052a11c980ae3f5629af810a8a0b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726114"
---
# <a name="create-a-custom-role-in-intune"></a>Erstellen einer benutzerdefinierten Rolle in Intune

Sie können eine benutzerdefinierte Intune-Rolle erstellen, die alle für einen bestimmten Aufgabenbereich erforderlichen Berechtigungen enthält. Wenn beispielsweise eine IT-Abteilungsgruppe Anwendungen, Richtlinien und Konfigurationsprofile verwaltet, können Sie alle diese Berechtigungen gemeinsam einer benutzerdefinierten Rolle hinzufügen. Nachdem Sie eine benutzerdefinierte Rolle erstellt haben, können Sie sie allen Benutzern [zuweisen](assign-role.md), die diese Berechtigungen benötigen.

Für das Erstellen, Bearbeiten oder Zuweisen von Rollen muss das Konto in Azure AD über eine der folgenden Berechtigungen verfügen:
- **Globaler Administrator**
- **Intune-Dienstadministrator**

## <a name="to-create-a-custom-role"></a>So erstellen Sie eine benutzerdefinierte Rolle

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an.

2. Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** > **Rollen** > **Alle Rollen** > **Hinzufügen** aus.

4. Geben Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** einen Namen und eine Beschreibung für die neue Rolle ein, und klicken Sie dann auf **Berechtigungen**.

5. Wählen Sie auf dem Blatt **Berechtigungen** die Berechtigungen aus, die Sie mit dieser Rolle verwenden möchten.

6. Wählen Sie auf dem Blatt **Bereich (Markierungen)** die Markierungen für diese Rolle aus. Diese Rolle kann auf Ressourcen zugreifen, die ebenfalls diese Markierungen aufweisen.

7. Wenn Sie fertig sind, klicken Sie auf **OK**.

8. Klicken Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** auf **Erstellen**. Die neue Rolle wird in der Liste auf dem Blatt **Intune-Rollen – Alle Rollen** angezeigt.

## <a name="next-steps"></a>Nächste Schritte
- [Zuweisen einer Rolle an einen Benutzer](assign-role.md)
- [Erfahren Sie mehr über die rollenbasierte Zugriffssteuerung in Intune](role-based-access-control.md)