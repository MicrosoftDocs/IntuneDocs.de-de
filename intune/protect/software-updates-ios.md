---
title: Konfigurieren von Richtlinien für iOS-Softwareupdates in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie in Microsoft Intune eine Konfigurationsrichtlinie, oder fügen Sie eine hinzu, um einzuschränken, wann Softwareupdates auf iOS-Geräten, die von Intune verwaltet oder überwacht werden, automatisch installiert werden. Sie können auswählen, an welchem Datum und zu welcher Uhrzeit Updates nicht installiert werden sollen. Sie können diese Richtlinie ebenfalls Gruppen, Benutzern oder Geräten zuweisen oder Überprüfungen auf Installationsfehler durchführen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54e6cc0b3df95c74abf4b4ef1b827f8e121e3645
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726660"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Hinzufügen von iOS-Softwareupdaterichtlinien in Intune

Durch Richtlinien für Softwareupdates können Sie erzwingen, dass das neueste Update für das Betriebssystem auf überwachten iOS-Geräten automatisch installiert wird. Wenn Sie eine Richtlinie konfigurieren, können Sie angeben, an welchen Tagen und zu welchen Uhrzeiten keine Updates auf Geräten installiert werden sollen.

Diese Funktion gilt für:

- iOS 10.3 und höher (überwacht)

Das Gerät wird etwa alle acht Stunden bei Intune eingecheckt. Wenn ein Update verfügbar und das Einchecken nicht während eines eingeschränkten Zeitraums stattfindet, lädt das Gerät das neueste Update für das Betriebssystem herunter und installiert es. Es ist kein Benutzereingriff erforderlich, um das Gerät zu aktualisieren. Die Richtlinie verhindert nicht, dass ein Benutzer das Betriebssystem manuell aktualisiert.

## <a name="configure-the-policy"></a>Konfigurieren der Richtlinie

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Softwareupdates** > **Update policies for iOS** (Updaterichtlinien für iOS)  > **Erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name**: Geben Sie einen Namen für Ihre Softwareupdaterichtlinie ein. Geben Sie beispielsweise `iOS restricted update times` ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für Ihre Richtlinie ein. Diese Einstellung ist optional, wird jedoch empfohlen.

4. Klicken Sie auf **Einstellungen > Konfigurieren**. Legen Sie folgende Einstellungen fest:

    - **Select times to prevent update installations** (Zeiten auswählen, zu denen Updateinstallationen verhindert werden sollen): Legen Sie einen eingeschränkten Zeitrahmen fest, in dem keine Updateinstallationen erzwungen werden.
      - Zeitblöcke zu Nachtzeiten werden nicht unterstützt und funktionieren möglicherweise nicht. Konfigurieren Sie beispielsweise keine Richtlinie mit der *Startzeit* 20 Uhr und der *Endzeit* 6 Uhr.
      - Richtlinien mit der Start- und Endzeit 0 Uhr umfassen einen Zeitraum von 0 anstatt 24 Stunden – es liegt also keine Beschränkung vor.

      Wenn Sie einen eingeschränkten Zeitrahmen festlegen, geben Sie die folgenden Details ein:

      - **Tage:** Wählen Sie die Wochentage aus, an denen keine Updates erstellt werden sollen. Wenn also montags, mittwochs und freitags keine Updates installiert werden sollen, wählen Sie diese Tage aus.
      - **Zeitzone:** Wählen Sie eine Zeitzone aus.
      - **Startzeit**: Wählen Sie die Startzeit für den eingeschränkten Zeitrahmen aus. Wenn Sie beispielsweise 5 Uhr angeben, werden von dieser Uhrzeit an keine Updates mehr installiert.
      - **Endzeit:** Wählen Sie die Endzeit für den eingeschränkten Zeitrahmen aus. Wenn Sie beispielsweise 1 Uhr eingeben, können von dieser Uhrzeit an Updates installiert werden.

    - **Sichtbarkeit von Softwareupdates für Endbenutzer ohne Änderungen der geplanten Updates im Softwareupdate (Tage) verzögern**: 

      **Wenn Sie die Sichtbarkeit von Softwareupdates für einen bestimmten Zeitraum auf Ihren überwachten iOS-Geräten verzögern möchten, konfigurieren Sie diese Einstellungen unter [Geräteeinschränkungen](../configuration/device-restrictions-ios.md#general). Softwareupdaterichtlinien setzen jegliche Geräteeinschränkungen außer Kraft. Wenn Sie beide Einstellungen festgelegt haben, hat die Softwareupdaterichtlinie immer Priorität.

      > [!IMPORTANT]  
      > Eine Richtlinie, bei der die *Startzeit* und die *Endzeit* auf 12 Uhr festgelegt wurde, wird als „0 Stunden“ und nicht als „24 Stunden“ ausgewertet. Diese Einstellung führt dazu, dass es keine Einschränkungen gibt.  

5. Klicken Sie auf **OK** > **Erstellen**, um Ihre Änderungen zu speichern und die Richtlinie zu erstellen.

Das Profil wird erstellt und in der Richtlinienliste angezeigt.

Unterstützung vom Supportteam für Intune erhalten Sie unter [Delay visibility of software updates in Intune for supervised devices (Verzögern der Sichtbarkeit von Softwareupdates in Intune für überwachte Geräte)](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Die mobile Geräteverwaltung von Apple lässt nicht zu, dass das Installieren von Updates auf einem Gerät an einem bestimmten Datum oder zu einer bestimmten Uhrzeit erzwungen werden soll.

## <a name="change-the-restricted-times-for-the-policy"></a>Ändern der eingeschränkten Zeiten für die Richtlinie

1. Klicken Sie unter **Softwareupdates** auf **Update policies for iOS (Updaterichtlinien für iOS)** .
2. Wählen Sie eine vorhandene Richtlinie aus, und klicken Sie dann auf **Eigenschaften**.
3. Aktualisieren Sie die eingeschränkten Zeiträume:

    1. Auswählen der Wochentage
    2. Wählen Sie die Zeitzone aus, in der diese Richtlinie angewendet wird.
    3. Wählen Sie die Start- und Endzeit des gesperrten Zeitraums aus.

    > [!NOTE]
    > Wenn sowohl die **Start-** als auch die **Endzeit** auf 0 Uhr festgelegt sind, überprüft Intune nicht, ob Einschränkungen in Bezug auf Updateinstallationen vorliegen. D. h., dass alle Konfigurationen, die Sie für die Einstellung **Select times to prevent update installations** (Zeiten auswählen, zu denen Updateinstallationen verhindert werden sollen) festgelegt haben, ignoriert werden und jederzeit Updates installiert werden können.  

## <a name="assign-the-policy-to-users"></a>Zuweisen der Richtlinie zu Benutzern

Vorhandene Richtlinien werden Gruppen, Benutzern oder Geräten zugewiesen. Wenn eine Richtlinie zugewiesen ist, wird sie angewendet.

1. Klicken Sie unter **Softwareupdates** auf **Update policies for iOS (Updaterichtlinien für iOS)** .
2. Wählen Sie eine vorhandene Richtlinie aus, und klicken Sie dann auf **Zuweisungen**.
3. Wählen Sie die Azure Active Directory-Gruppen, -Benutzer oder -Geräte aus, die dieser Richtlinie hinzugefügt oder von ihr ausgeschlossen werden sollen.
4. Klicken Sie auf **Speichern**, um die Richtlinie für Ihre Gruppen bereitzustellen.

Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Updatekompatibilität überprüft. Diese Richtlinie unterstützt ebenfalls Geräte ohne Benutzer.

## <a name="monitor-device-installation-failures"></a>Überwachung von Installationsfehlern bei Geräten
<!-- 1352223 -->
Unter **Softwareupdates** > **Installationsfehler für iOS-Geräte** wird eine Liste der überwachten iOS-Geräte angezeigt, für die eine Updaterichtlinie gilt und bei denen erfolglos ein Update versucht wurde. Für jedes Gerät können Sie den Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. Fehlerfreie, aktuelle Geräte werden in der Liste nicht angezeigt. Ein Gerät gilt als aktuell, wenn das neueste Update installiert ist, das das Gerät unterstützt.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../configuration/device-profile-assign.md) und [Überwachen von Profilen](../configuration/device-profile-monitor.md)