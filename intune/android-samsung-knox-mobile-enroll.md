---
title: Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment
titlesuffix: Microsoft Intune
description: Informationen zum Registrieren von Android-Geräten mit Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88cb733c688019b2fc5455a0184e968d91e77806
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2018
ms.locfileid: "33915810"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment

Dieses Thema bietet Ihnen Hilfe beim Einrichten von Intune für die Registrierung unterstützter Android-Geräte mit Samsung Knox Mobile Enrollment (KME). Wenn Sie Intune mit Samsung KME verwenden, können Sie eine große Anzahl unternehmenseigener Android-Geräte registrieren, wenn Endbenutzer ihre Geräte zum ersten Mal einschalten und eine Verbindung mit einem WLAN oder Mobilfunknetz herstellen. Darüber hinaus können Geräte bei Verwendung der Knox Deployment App auch über Bluetooth oder NFC registriert werden.

Um die Intune-Registrierung mit Samsung KME zu aktivieren, müssen Sie sowohl das Intune- als auch das Samsung Knox-Portal in der folgenden Reihenfolge verwenden:

1. Im Knox-Portal:
    1. [Erstellen eines MDM-Profils](#create-mdm-profile)
    2. [Hinzufügen von Geräten](#add-devices)
    3. [Zuweisen eines MDM-Profils für die Geräte](#assign-an-mdm-profile-to-devices)
2. Im Azure-Portal: [Identifizieren Sie Geräte als unternehmenseigen](#identify-devices-as-corporate-owned).
3. Im Knox-Portal: [Konfigurieren Sie die Endbenutzeranmeldung](#configure-how-end-users-sign-in).
4. [Verteilen Sie die Geräte](#distribute-devices).


Beim Erwerb von Geräten von autorisierten Fachhändlern, die am Knox Deployment Program teilnehmen, wird dem Knox-Portal automatisch eine Liste der Geräte-IDs (Seriennummern und IMEIs) hinzugefügt.


## <a name="prerequisites"></a>Voraussetzungen

Damit Sie sich bei Intune mit KME registrieren können, müssen Sie zuerst Ihr Unternehmen im Samsung Knox-Portal registrieren, indem Sie die folgenden Schritte ausführen:
1.  [Vergewissern Sie sich, dass KME in Ihrer Region verfügbar ist](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME ist in über 55 Ländern verfügbar. Überprüfen Sie, ob Ihr Land/Region für die Bereitstellung unterstützt wird.

2.  [Unterstützte Geräte](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME ist auf allen Samsung-Geräten mit mindestens Knox 2.4 verfügbar.

3.  [Netzwerkanforderungen](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Stellen Sie sicher, dass die erforderlichen Firewall- und Netzwerkzugriffsregeln in Ihrem Netzwerk zulässig sind.

4.  [Registrieren Sie sich für ein Samsung-Konto](https://www2.samsungknox.com/en/user/register):Ein Samsung-Konto ist erforderlich, um KME zu registrieren und zu aktivieren und alle Knox Enterprise-Berechtigungen an einem zentralen Ort zu verwalten.

5.  Registrierungsüberprüfung: Nachdem Ihr Profil vervollständigt und übermittelt wurde, führt Samsung eine Überprüfung Ihres Gesuchs durch und genehmigt es entweder sofort oder versetzt es in einen ausstehenden Überprüfungsstatus zur weiteren Nachverfolgung. Nachdem Ihr Konto genehmigt wurde, können Sie mit weiteren Schritten fortfahren.

## <a name="create-mdm-profile"></a>Erstellen eines MDM-Profils

Wenn Ihr Unternehmen erfolgreich registriert wurde, können Sie Ihr MDM-Profil für Microsoft Intune im Knox-Portal anhand der nachstehenden Informationen erstellen. Schritt-für-Schritt-Anleitungen können Sie dem [Samsung Knox-Assistenten für die Profileinrichtung](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) entnehmen.

| MDM-Profilfelder| Erforderlich? | Werte |
|-------------------|-----------|-------|
|MDM Server URI     | Nein        |Lassen Sie dieses Feld leer.
|Profile Name       | Ja        |Geben Sie einen Profilnamen Ihrer Wahl ein.
|Description        | Nein        |Geben Sie Text ein, der das Profil beschreibt.
|MDM Agent APK      | Ja        |https://aka.ms/intune_kme
|Skip Setup wizard  | Nein        |Wählen Sie diese Option aus, um die Eingabeaufforderungen für die Standardgeräteeinrichtung im Namen des Endbenutzers zu überspringen.
|Allow End User to Cancel Enrollment | Nein | Wählen Sie diese Option aus, um Benutzern zu erlauben, KME abzubrechen.
|Custom JSON        | Nein        |Lassen Sie dieses Feld leer.
| EULAs, Terms of Service and User Agreements| Nein | Wählen Sie diese Option aus, um Knox-bezogene Vereinbarungen für die Benutzerakzeptanz anzuzeigen.
Associate a Knox license with this profile | Nein | Lassen Sie diese Option deaktiviert. Für die Registrierung bei Intune mit KME ist keine Knox-Lizenz erforderlich.

## <a name="add-devices"></a>Hinzufügen von Geräten

Damit Sie Geräten MDM-Profile zuweisen können, müssen dem Knox-Portal mithilfe einer der folgenden Methoden unterstützte Samsung Knox-Geräte hinzugefügt werden:
- **Verwenden von autorisierten Samsung-Fachhändlern:** Verwenden Sie diese Methode, wenn Sie Geräte von einem der von Samsung zugelassenen Fachhändler erwerben. Bei entsprechender Genehmigung können Fachhändler Geräte für Sie automatisch hochladen. [Rufen Sie den Samsung Knox Enrollment User Guide auf, um Informationen zum Hinzufügen von Fachhändlern zu erhalten](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Verwenden der Knox Deployment App (KDA):** Verwenden Sie diese Methode, wenn Sie über bestehende Geräte verfügen, die mit KME registriert werden müssen. Bei dieser Methode können Sie Bluetooth oder NFC verwenden, um Geräte zum Knox-Portal hinzuzufügen. [Rufen Sie den Samsung Knox Enrollment User Guide auf, um Informationen zum Verwenden der KDA zu erhalten](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Zuweisen eines MDM-Profils für Geräte
Sie müssen hinzugefügten Geräten im Knox-Portal ein MDM-Profil zuweisen, bevor sie registriert werden können. [Rufen Sie den Samsung Knox Enrollment User Guide auf, um Informationen zur Gerätekonfiguration zu erhalten](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="identify-devices-as-corporate-owned"></a>Identifizieren von Geräten als unternehmenseigen
Sie können mit KME registrierte Geräte als unternehmenseigen identifizieren. Dies muss vor der Registrierung der Geräte erfolgen. Dadurch können Sie zusätzliche Verwaltungsaufgaben ausführen und zusätzliche Informationen sammeln, wie etwa die vollständige Telefonnummer und den Bestand von Apps.

Führen Sie die folgenden Schritte aus, um Geräte als unternehmenseigen zu identifizieren:

1. Exportieren Sie die Liste der Geräte aus dem Knox-Portal als CSV-Datei.

2. Formatieren Sie die CSV-Datei mit einer IMEI oder Seriennummer wie [hier](https://docs.microsoft.com/en-us/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number) angegeben.

3. Laden Sie im Azure-Portal die CSV-Datei nach **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen** hoch.

Jetzt werden identifizierte Geräte, die registriert werden, als unternehmenseigen gekennzeichnet.

> [!NOTE]
>Intune weist Geräten, die mit dem [Geräteregistrierungs-Manager](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)-Konto registriert wurden, automatisch den Status „Unternehmenseigen“ zu.

## <a name="configure-how-end-users-sign-in"></a>Konfigurieren der Endbenutzeranmeldung

Für bei Intune mit KME registrierte Geräte können Sie wie folgt konfigurieren, wie sich ein Endbenutzer anmelden kann:

- **Ohne Benutzernamenzuordnung:** Lassen Sie im Knox-Portal unter **Gerätedetails** die Felder **Benutzer-ID** und **Kennwort** für die hinzugefügten Geräte leer. Dadurch muss der Endbenutzer bei der Registrierung bei Intune den Benutzernamen und ein Kennwort eingeben.

- **Mit Benutzernamenzuordnung:** Geben Sie im Knox-Portal unter **Gerätedetails** eine **Benutzer-ID** (z. B. einen Benutzernamen für den zugewiesenen Benutzer oder ein [Geräteregistrierungs-Manager](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)-Konto) für die hinzugefügten Geräte an. Dadurch wird der Benutzername vorab ausgefüllt, und der Endbenutzer muss bei der Registrierung bei Intune ein Kennwort eingeben.

> [!NOTE]
>
>Wenn eine Benutzerzuordnung definiert ist, kann nur der zugeordnete Benutzer das Gerät mit KME registrieren. Dies gilt auch nach einer Zurücksetzung des Geräts auf die Werkseinstellungen. Wenn im Knox-Portal keine Benutzerzuordnung definiert ist, kann jeder Benutzer mit einer gültigen Intune-Lizenz das Gerät mit KME registrieren.
>

## <a name="distribute-devices"></a>Verteilen von Geräten

Nachdem Sie ein MDM-Profil erstellt und zugewiesen, einen Benutzernamen zugeordnet und in Intune die Geräte als unternehmenseigen identifiziert haben, können Sie die Geräte an Benutzer verteilen.

Benötigen Sie weitere Unterstützung? Lesen Sie den vollständigen [Knox Mobile Enrollment User Guide](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
- **Google Play-Konto:** Für die Registrierung des Geräts bei Microsoft Intune ist kein Google Play-Konto erforderlich. Für zukünftige Updates der Intune-Unternehmensportal-App ist jedoch möglicherweise ein Google Play-Konto auf dem Gerät erforderlich.

- **Google-Geräteinhabermodus:** Eine Registrierung im Google-Geräteinhabermodus (Device Owner Mode) mit KME wird in dieser Vorschauversion nicht unterstützt. Dieses Szenario wird derzeit untersucht.

- **Das Feld „Kennwort“ wird ignoriert:** Wenn im Knox-Portal unter **Gerätedetails** das Feld **Kennwort** aufgefüllt wird, dann wird es von der Intune-Unternehmensportal-App ignoriert. Der Endbenutzer muss auf dem Gerät ein Kennwort eingeben, um die Geräteregistrierung abzuschließen.

## <a name="getting-support"></a>Unterstützung erhalten
Erfahren Sie mehr darüber, wie Sie [Support für Samsung KME erhalten](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).

