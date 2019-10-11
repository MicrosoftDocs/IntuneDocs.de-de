---
title: Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie branchenspezifische Windows-Apps mithilfe von Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d9b579e944827e511700073f0b3348b5ef20adc
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724697"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Branchenspezifische Apps werden über eine App-Installationsdatei hinzugefügt. Diese Art von App wird in der Regel intern geschrieben. Die folgenden Schritte enthaltenen Informationen zum Hinzufügen einer LOB-Windows-App mit Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie in der Workload **Client-Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie oberhalb der App-Liste **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** aus.

## <a name="step-2-configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Windows-Installationsdatei mit der Erweiterung **MSI**. **APPX** oder **APPXBUNDLE**.

    > [!NOTE]
    > Zu den Dateierweiterungen für Windows-Apps gehören **.msi**, **.appx**, **.appxbundle**, **.msix** und **.msixbundle**.  

1. Wählen Sie danach **OK**.


## <a name="step-3-configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen**.
2. Konfigurieren Sie im Bereich **App-Informationen** die folgenden Informationen. Einige der Werte in diesem Bereich wurden möglicherweise automatisch ausgefüllt.
    - **Name**: Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **App-Version ignorieren**: Legen Sie diese Option auf **Ja** fest, wenn der App-Entwickler die App automatisch aktualisiert. Diese Option gilt nur für mobile MSI-Apps.
    - **Kategorie**: Wählen Sie eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional die URL einer Website ein, die Informationen über die App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional die URL einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Befehlszeilenargumente**: Geben Sie optional Befehlszeilenargumente ein, die bei Ausführung auf die MSI-Datei angewendet werden sollen.  Ein Beispiel ist **/q**. Schließen Sie den Befehl „msiexec“ und Argumente wie **/i** oder **/x** nicht ein, da diese automatisch verwendet werden. Weitere Informationen finden Sie unter [Befehlszeilenoptionen](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Wenn die MSI-Datei zusätzliche Befehlszeilenoptionen benötigt, verwenden Sie [Win32-App-Verwaltung](app-management.md).
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Das Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wählen Sie danach **OK**.

## <a name="step-4-finish-up"></a>Schritt 4: Fertig stellen

1. Überprüfen Sie im Bereich **App hinzufügen**, ob die konfigurierten App-Informationen richtig sind.
2. Wählen Sie **Hinzufügen**, um die App in Intune hochzuladen.

## <a name="step-5-update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Damit der Intune-Dienst eine neue APPX-Datei erfolgreich auf dem Gerät bereitstellt, müssen Sie die Zeichenfolge `Version` in der Datei „AndroidManifest.xml“ in Ihrem APPX-Paket erhöhen.
    
## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurieren Sie eine mobile MSI-App, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren.

Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. 

Einige auf den MSI-Installer basierende Apps werden vom App-Entwickler automatisch aktualisiert. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** im Bereich **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, erzwingt Microsoft Intune keine App-Version, die auf dem Windows-Client installiert ist. 

Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Beispielsweise kann eine Racebedingung auftreten, wenn die App automatisch vom App-Entwickler und von Intune aktualisiert wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Siehe [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen erhalten Sie unter [Übersicht über den App-Lebenszyklus in Microsoft Intune](app-lifecycle.md).