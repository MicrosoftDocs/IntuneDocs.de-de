---
title: Erstellen einer MTD-Konformitätsrichtlinie für Geräte mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Erstellen Sie eine Intune-Konformitätsrichtlinie für Geräte, die die Bedrohungsstufen Ihres MTD-Partners verwendet, um zu ermitteln, ob ein mobiles Gerät auf Unternehmensressourcen zugreifen darf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2315136fe277f06f6dbb11c13139a9dc193ce6f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722110"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Erstellen einer Mobile Threat Defense-Gerätekompatibilitätsrichtlinie (MTD) mit Intune

> [!NOTE] 
> Diese Informationen gelten für alle Mobile Threat Defense-Partner.

Intune mit MTD hilft Ihnen dabei, Bedrohungen zu erkennen und Risiken auf mobilen Geräten zu bewerten. Sie können eine Regel für eine Intune-Gerätekompatibilitätsrichtlinie erstellen, mit der das Risiko bewertet wird, um zu ermitteln, ob das Gerät kompatibel ist oder nicht. Anschließend können Sie eine [Richtlinie für bedingten Zugriff](create-conditional-access-intune.md) verwenden, um den Zugriff auf Dienste basierend auf der Gerätekonformität zu blockieren.

## <a name="before-you-begin"></a>Vorbereitung

Beim Einrichten von MTD haben Sie in der MTD-Partnerkonsole eine Richtlinie erstellt, die verschiedene Bedrohungen als hoch, mittel und niedrig klassifiziert. Nun müssen Sie Mobile Threat Defense-Stufe in der Intune-Gerätekompatibilitätsrichtlinie festlegen.

Voraussetzungen für die Gerätekompatibilitätsrichtlinie mit MTD:

- Einrichten der MTD-Integration in Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>So erstellen Sie eine MTD-Gerätekonformitätsrichtlinie

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com/) mit Ihren Intune-Anmeldeinformationen an.

2. Klicken Sie im **Azure-Dashboard** im linken Menü auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** aus. Das **Intune-Dashboard** wird geöffnet.

4. Wählen Sie im **Intune-Dashboard** **Gerätekompatibilität** und dann im Abschnitt **Verwalten** die Option **Richtlinien** aus.

5. Wählen Sie **Richtlinie erstellen** aus, geben Sie den **Namen** und die **Beschreibung** der Gerätekompatibilität ein, wählen Sie die **Plattform** aus, und wählen Sie dann **Konfigurieren** im Abschnitt **Einstellungen** aus.

6. Wählen Sie im Bereich **Konformitätsrichtlinie** die Option **Geräteintegrität** aus.

7. Wählen Sie im Bereich **Geräteintegrität** aus der Dropdownliste **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht** die gewünschte Stufe für mobile Bedrohungen aus.

    ein.  **Secured** (Geschützt): Diese Stufe ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.

    b.  **Niedrig:** Das Gerät ist konform, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.

    c.  **Mittel:** Das Gerät ist konform, wenn auf dem Gerät Bedrohungen niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.

    d.  **Hoch:** Diese Stufe gewährleistet das geringste Maß an Sicherheit. Sie lässt alle Bedrohungsstufen zu und verwendet Mobile Threat Defense nur zu Berichtszwecken. Auf Geräten muss mit dieser Einstellung die MTD-App aktiviert sein.

8. Klicken Sie zweimal auf **OK**, und wählen Sie dann **Erstellen** aus.

> [!IMPORTANT]
> Wenn Sie Richtlinien für bedingten Zugriff für Office 365 oder andere Dienste erstellen, wird die Konformitätsbewertung ausgewertet, und auf nicht konformen Geräten wird der Zugriff auf Unternehmensressourcen blockiert, bis die Bedrohung auf dem Gerät beseitigt ist.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>So weisen Sie eine MTD-Gerätekonformitätsrichtlinie zu

Wählen Sie zum Zuweisen einer Gerätekompatibilitätsrichtlinie zu Benutzern eine Richtlinie aus, die Sie zuvor konfiguriert haben. Vorhandene Richtlinien finden Sie im Bereich **Gerätekonformität > Richtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Mit dieser Aktion öffnen Sie den Bereich, in dem Sie **Azure Active Directory-Sicherheitsgruppen** auswählen und der Richtlinie zuweisen können.

2. Klicken Sie auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen.  Die Auswahl von **Auswählen** bewirkt die Bereitstellung der Richtlinie für Benutzer.

    > [!NOTE] 
    > Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte

- [Aktivieren von Mobile Threat Defense in Intune](mtd-connector-enable.md)