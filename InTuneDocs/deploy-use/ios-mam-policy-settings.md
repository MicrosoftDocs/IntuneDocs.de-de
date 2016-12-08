---
title: iOS-MAM-Richtlinieneinstellungen | Microsoft Intune
description: "In diesem Thema werden die Richtlinieneinstellungen zur Verwaltung mobiler Apps für iOS-Geräte beschrieben."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 913008568226621de4824c5bac287e8a65dc6533


---

#  <a name="ios-mobile-app-management-policy-settings"></a>iOS-Richtlinieneinstellungen für die Verwaltung mobiler Apps
Die in diesem Thema beschriebenen Richtlinieneinstellungen können im Azure-Portal auf dem Blatt **Einstellungen** für eine MAM-Richtlinie (mobile application management, Verwaltung mobiler Anwendungen) [konfiguriert](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) werden.

Es gibt zwei Kategorien von Richtlinieneinstellungen: Datenverlagerungs- und Zugriffseinstellungen. In diesem Thema verweist der Begriff *Richtlinienverwaltete Apps* auf Apps, die mit MAM-Richtlinien konfiguriert sind.

##  <a name="data-relocation-settings"></a>Einstellungen für die Datenverlagerung

- **iTunes- und iCloud-Sicherungen verhindern**: Wählen Sie **Ja**, um die Funktion zu deaktivieren, oder **Nein**, um das Sichern von Unternehmensdaten über richtlinienverwaltete Apps zuzulassen.

  Standardwert = **Ja**

- **Zulassen, dass die App Daten an andere Apps überträgt**: Wählen Sie eine der Optionen, um die Apps anzugeben, die Daten von richtlinienverwalteten Apps empfangen dürfen:
  - **Richtlinienverwaltete Apps**: Datenübertragung nur an andere Apps zulassen, für die die MAM-Richtlinie gilt.
  - **Alle Apps**: Datenübertragung an beliebige Apps zulassen
  - **Keine**: Keine Datenübertragung an beliebige Apps zulassen, auch nicht an andere richtlinienverwaltete Apps.

  Wenn Sie diese Option auf **Richtlinienverwaltete Apps** oder **Keine** festlegen, wird zudem das iOS 9-Feature blockiert, das der Spotlight-Suche die Suche von Daten in Apps erlaubt.

  >[!NOTE]
  >Diese Einstellung steuert nicht die Verwendung des Features „Öffnen in“ auf mobilen Geräten. Informationen zum Verwalten von „Öffnen in“ finden Sie unter [Verwalten der Datenübertragung zwischen iOS-Apps mit Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

  Standardwert = **Richtlinienverwaltete Apps**

- **Zulassen, dass die App Daten von anderen Apps empfängt:** Geben Sie Apps an, die Daten an die richtlinienverwalteten Apps übertragen dürfen:
  -  **Richtlinienverwaltete Apps**: Datenübertragung nur von anderen richtlinienverwalteten Apps zulassen
  -  **Alle Apps**: Datenübertragung von beliebigen Apps zulassen
  -  **Keine**: Keine Datenübertragung von anderen Apps zulassen.

  Standardwert = **Alle Apps**

- **„Speichern unter“ verhindern:** Wählen Sie **Ja** aus, um die Verwendung der Option „Speichern unter“ in jeder App zu deaktivieren, die diese Richtlinie verwendet. Wählen Sie **Nein** aus, wenn die Verwendung von „Speichern unter“ zulässig sein soll.

  Standardwert = **Ja**

- **Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken:** Geben Sie an, ob Ausschneiden, Kopieren und Einfügen eingeschränkt werden sollen. Wählen Sie aus:
  -   **Blockiert**: Ausschneiden, Kopieren und Einfügen zwischen richtlinienverwalteten Apps nicht zulassen
  -   **Richtlinienverwaltete Apps**: Ausschneiden, Kopieren und Einfügen nur zwischen richtlinienverwalteten Apps zulassen.
  -   **Richtlinienverwaltete Apps mit Einfügen**: Ausschneiden oder Kopieren zwischen richtlinienverwalteten Apps zulassen. Einfügen der aus beliebigen Apps ausgeschnittenen oder kopierten Daten in diese App zulassen.
  - **Jede App**: Keine Einschränkungen für das Ausschneiden, Kopieren und Einfügen zwischen beliebigen Apps.

  Standardwert = **Richtlinienverwaltete Apps mit Einfügen**

- **Anzeige von Webinhalten auf den Managed Browser beschränken:** Wenn diese Einstellung aktiviert ist, werden alle Links aus der App in der Managed Browser-App geöffnet.

  Für Geräte, die nicht bei Intune registriert sind, können Weblinks in richtlinienverwalteten Apps nur in der Managed Browser-App geöffnet werden.

  Wenn Sie Intune zum Verwalten Ihrer Geräte verwenden, lesen Sie [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

  Standardwert = **Ja**

- **App-Daten verschlüsseln**: Für Apps, die einer Intune-MAM-Richtlinie zugeordnet sind, werden ruhende Daten mit vom Betriebssystem bereitgestellter Verschlüsselung auf Geräteebene verschlüsselt. Wenn eine PIN erforderlich ist, werden die Daten gemäß den Einstellungen in der MAM-Richtlinie verschlüsselt. Wie in der Apple-Dokumentation angegeben, [sind die von iOS 7 verwendeten Module FIPS 140-2-zertifiziert](http://support.apple.com/en-us/HT202739).

  In den Richtlinieneinstellungen können Sie PIN-Verschlüssungswerte festlegen. Diese Werte bestimmen, wann die Daten verschlüsselt werden. Folgende Optionen sind verfügbar:
  -   **Wenn das Gerät gesperrt ist**: Alle App-Daten unter dieser Richtlinie werden verschlüsselt, solange das Gerät gesperrt ist.
  -   **Wenn das Gerät gesperrt ist (außer geöffnete Dateien)**: Alle App-Daten unter dieser Richtlinie werden verschlüsselt, solange das Gerät gesperrt ist, außer den Daten in Dateien, die derzeit in der App geöffnet sind.
  -   **Nach Geräteneustart**: Alle App-Daten unter dieser Richtlinie werden verschlüsselt, wenn das Gerät neu gestartet wird, bis das Gerät zum ersten Mal entsperrt wird.
  -   **Geräteeinstellungen verwenden**: App-Daten werden basierend auf den Standardeinstellungen des Geräts verschlüsselt.
  Wenn Sie diese Einstellung aktivieren, muss der Benutzer eine PIN einrichten und verwenden, um auf sein Gerät zuzugreifen.  Wenn keine PIN eingerichtet wurde, werden die Apps nicht geöffnet, und der Benutzer wird mit der Meldung „Ihr Unternehmen hat festgelegt, dass Sie zunächst eine Geräte-PIN aktivieren müssen, um auf diese Anwendung zuzugreifen“ aufgefordert, eine PIN einzurichten.

  Standardwert = Die Verschlüsselungsoption ist nicht ausgewählt.
- **Kontaktsynchronisierung deaktivieren:** Wählen Sie **Ja** aus, um zu verhindern, dass Kontaktinformationen mit der nativen Adressbuch-App auf dem Gerät synchronisiert werden. Wenn Sie **Nein** auswählen, speichert die App die Kontaktinformationen in der nativen Adressbuch-App auf dem Gerät.

  Wenn Sie zum Entfernen von Unternehmensdaten eine selektive Zurücksetzung durchführen, werden Kontakte entfernt, die direkt aus der App mit dem nativen Adressbuch synchronisiert werden. Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. Dies gilt derzeit nur für die Microsoft Outlook-App.

  Standardwert = **Ja**

- **Drucken deaktivieren:** Wählen Sie **Ja** aus, um zu verhindern, dass Unternehmensdaten aus Apps gedruckt werden, die mit der MAM-Richtlinie verknüpft sind.

    Standardwert = **Ja**

##  <a name="access-settings"></a>Zugriffseinstellungen

- **PIN für Zugriff erforderlich:** Wählen Sie **Ja** aus, um für richtlinienverwaltete Apps eine PIN anzufordern. Benutzer werden beim ersten Ausführen der App im beruflichen Kontext aufgefordert, diese einzurichten.

  Standardwert = **Ja**
    -  **Einfache PIN zulassen:** Geben Sie an, ob Benutzer einfache PIN-Sequenzen wie z B. 1234 oder 1111 verwenden dürfen. Standardwert = **Ja**
    - **PIN-Länge:** Geben Sie die Mindestanzahl von Ziffern in einer PIN an. Standardwert = **4**
    - **Anzahl der Versuche bis zum Zurücksetzen der PIN:** Geben Sie die Anzahl der möglichen PIN-Eingabeversuche an, bevor der Benutzer die PIN zurücksetzen muss. Für diese Einstellung gibt es keinen Standardwert.

- **Fingerabdruck anstelle von PIN erforderlich (iOS 8.0+):** Wählen Sie **Ja** aus, um für den Zugriff auf die App einen Identitätsnachweis in Form eines Fingerabdrucks anstelle einer PIN anzufordern.
Auf iOS-Geräten können Sie zulassen, dass sich die Benutzer per Fingerabdruck anstelle einer PIN identifizieren. Wenn der Benutzer versucht, mit seinem Geschäftskonto auf diese App zuzugreifen, wird er aufgefordert, seine Identität per Fingerabdruck und nicht durch Eingabe einer PIN zu bestätigen.

  Standardwert = **Ja**
- **Unternehmensanmeldeinformationen für den Zugriff erforderlich:** Wählen Sie **Ja** aus, um Unternehmensanmeldeinformationen anstelle einer PIN für den Zugriff auf die App anzufordern. Wenn Sie diese Einstellung auf **Ja** festlegen, sind PIN oder Fingerabdruckidentifizierung damit hinfällig. Der Benutzer wird aufgefordert, die Unternehmensanmeldeinformationen einzugeben.

  Standardwert = **Nein**
- **Ausführen verwalteter Apps auf Geräten mit Jailbreak oder Rootzugriff blockieren:** Wählen Sie **Ja** aus, wenn Sie die Ausführung von verwalteten Apps auf Geräten mit entfernten Nutzungsbeschränkungen blockieren möchten. Der Benutzer kann die Apps weiterhin für private Zwecke verwenden, muss für berufliche Zwecke jedoch ein anderes Gerät verwenden.

  Standardwert = **Ja**
- **Überprüfen der Zugriffsanforderungen nach (Minuten)**
  -   **Timeout:** Geben Sie die Zeit (in Minuten) an, bevor die Zugriffsanforderungen der App erneut überprüft werden.
  -   **Offline-Toleranzperiode**: Wenn das Gerät offline ist, geben Sie die Zeit (in Minuten) an, bevor die Zugriffsanforderungen für die App erneut geprüft werden.

  Standardwerte = **30** Minuten Timeout, Offline-Toleranzperiode = **720** Minuten
- **Offline-Intervall, bevor App-Daten zurückgesetzt werden (in Tagen):** Sie können die Unternehmensdaten zurücksetzen, wenn ein Gerät für einen bestimmten Zeitraum offline war. Legen Sie die Anzahl der Tage fest, die ein Gerät offline sein kann, bevor die Unternehmensdaten vom Gerät entfernt werden.

  >[!TIP]
  >Durch die Eingabe des Werts **0** wird diese Einstellung deaktiviert.

  Standardwert = **90** Tage



<!--HONumber=Oct16_HO5-->

