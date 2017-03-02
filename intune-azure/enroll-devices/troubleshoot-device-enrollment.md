---
title: "Behandeln von Problemen bei der Geräteregistrierung| Intune in Azure (Vorschau) | Microsoft Docs"
description: "Intune in Azure (Vorschau): Erfahren Sie, wie Sie Probleme bei der Registrierung von Geräten behandeln."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/010/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c324c74e-e225-40ad-88b7-72a6d9ea09b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 151e71f719b459a4f2c9612035201908d2610980
ms.openlocfilehash: 78f0ff9a1b7bdaf30721d8702c36ff0e613b109e


---

# <a name="troubleshoot-device-enrollment-in-intune"></a>Behandlung von Problemen bei der Geräteregistrierung bei Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Dieses Thema enthält Vorschläge zur Problembehandlung bei Problemen mit der Geräteregistrierung. Wenn sich das Problem mit diesen Informationen nicht beheben lässt, finden Sie unter [How to get support for Microsoft Intune](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) (Anfordern von Support für Microsoft Intune) weitere Möglichkeiten, Hilfe zu erhalten.


## <a name="initial-troubleshooting-steps"></a>Erste Schritte bei der Problembehandlung

Bevor Sie mit der Problembehandlung beginnen, stellen Sie sicher, dass Intune ordnungsgemäß konfiguriert wurde, um die Registrierung zu ermöglichen. Unter [Registrieren von Android- und Standard KNOX-Geräten](/intune-azure/enroll-devices/enroll-android-and-knox-standard-devices.md) finden Sie Links zu den Registrierungsschritten für jede Plattform.

Ihre Benutzer verwalteter Geräte können Registrierungs- und Diagnoseprotokolle erfassen, die Sie überprüfen können. Benutzeranleitungen zur Erfassung der Protokolle finden Sie unter:

- [Senden von Android-Registrierungsfehlern an Ihren IT-Administrator](https://docs.microsoft.com/intune/enduser/send-enrollment-errors-to-your-it-admin-android)
- [Send iOS errors to your IT admin (Senden von iOS-Fehlern an Ihren IT-Administrator)](https://docs.microsoft.com/intune/enduser/send-errors-to-your-it-admin-ios)

## <a name="general-enrollment-issues"></a>Allgemeine Probleme bei der Registrierung
Diese Probleme können auf allen Geräteplattformen auftreten.

### <a name="device-cap-reached"></a>Gerätekapazität erreicht
**Problem**: Benutzer erhalten während der Registrierung eine Fehlermeldung auf ihrem Gerät, z. B. den Fehler **Unternehmensportal vorübergehend nicht verfügbar** auf einem iOS-Gerät, und die Datei „DMPdownloader.log“ in Configuration Manager enthält den Fehler **DeviceCapReached**.

**Lösung:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Überprüfen Sie die Anzahl der registrierten und zulässigen Geräte.

Wechseln Sie im Azure-Portal auf dem Blatt „Intune“ zu **Geräte registrieren** > **Registrierungsbeschränkungen**, und vergewissern Sie sich, dass dem Benutzer nicht mehr als die zulässige Höchstzahl von 15 Geräten zugewiesen ist.

<!--- Mobile device users can delete devices at the following URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/). --->

Administratoren können Geräte im Azure Active Directory-Portal löschen.

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>So löschen Sie Geräte im Azure Active Directory-Portal

1.  Navigieren Sie zu [http://aka.ms/accessaad](http://aka.ms/accessaad), oder klicken Sie unter [https://portal.office.com](https://portal.office.com) auf **Verwaltung** &gt; **Azure AD**.

2.  Melden Sie sich mit Ihrer Organisations-ID über den Link im linken Bereich der Seite an.

3.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierzu sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie ein gebührenpflichtiges Konto besitzen (klicken Sie auf den Abonnementlink **Ihr kostenloses Azure Active Directory registrieren** ).

4.  Wählen Sie zuerst **Active Directory** und dann Ihre Organisation aus.

5.  Wählen Sie die Registerkarte **Benutzer** aus.

6.  Wählen Sie den Benutzer aus, dessen Geräte Sie löschen möchten.

7.  Klicken Sie auf **Geräte**.

8.  Entfernen Sie Geräte nach Bedarf, z. B. solche, die nicht mehr verwendet werden oder fehlerhafte Definitionen haben.

> [!NOTE]

> Sie können das Erreichen der Kapazitätsgrenze für Geräteregistrierungen vermeiden, indem Sie Geräteregistrierungs-Manager verwenden, wie unter [Registrieren von Geräten mit dem Geräteregistrierungs-Manager](/intune-azure/enroll-devices/enroll-devices-using-device-enrollment-manager.md) beschrieben.
>
> Ein Benutzerkonto, das der Gruppe „Geräteregistrierungs-Manager“ hinzugefügt wird, kann die Registrierung nicht abschließen, wenn die bedingte Zugriffsrichtlinie für diese spezielle Benutzeranmeldung erzwungen wird.

### <a name="company-portal-temporarily-unavailable"></a>Unternehmensportal vorübergehend nicht verfügbar
**Problem**: Sie erhalten auf dem Gerät die Fehlermeldung **Unternehmensportal vorübergehend nicht verfügbar**.

**Lösung:**

1.  Entfernen Sie die Intune-Unternehmensportal-App von dem Gerät.

2.  Öffnen Sie auf dem Gerät den Browser, navigieren Sie zu [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), und versuchen Sie eine Benutzeranmeldung.

3.  Wenn sich der Benutzer nicht anmelden kann, lassen Sie ihn ein anderes Netzwerk ausprobieren.

4.  Wenn auch dies fehlschlägt, überprüfen Sie, ob die Anmeldeinformationen des Benutzers korrekt mit Azure Active Directory synchronisiert wurden.

5.  Wenn sich der Benutzer erfolgreich angemeldet hat, werden Sie auf einem iOS-Gerät aufgefordert, die Intune-Unternehmensportal-App zu installieren und sich zu registrieren. Auf einem Android-Geräten müssen Sie die Intune-Unternehmensportal-App manuell installieren, wonach Sie die Registrierung erneut versuchen können.

### <a name="mdm-authority-not-defined"></a>MDM-Autorität nicht definiert
**Problem**: Sie erhalten die Fehlermeldung **MDM-Autorität nicht definiert**.

**Lösung:**

1.  Stellen Sie sicher, dass die MDM-Autorität entsprechend dem Typ des von Ihnen verwendeten Intune-Diensts festgelegt wurde, d.h. für Intune, Office 365 oder System Center Configuration Manager mit Intune. Eine Anleitung finden Sie unter [Festlegen der Autorität für die Verwaltung mobiler Geräte](https://docs.microsoft.com/en-us/intune-azure/enroll-devices/set-mdm-authority).

    > [!NOTE]
    > Nachdem Sie die MDM-Autorität festgelegt haben, können Sie sie nur ändern, indem Sie sich an den Support wenden, wie unter [Anfordern von Support für Microsoft Intune](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) beschrieben.

2.  Stellen Sie sicher, dass die Anmeldeinformationen des Benutzers korrekt mit Azure Active Directory synchronisiert wurden, indem Sie überprüfen, ob der UPN mit den Active Directory-Informationen im Kontoportal übereinstimmt.
    Wenn der UPN nicht mit den Active Directory-Informationen übereinstimmt:

    1.  Deaktivieren Sie DirSync auf dem lokalen Server.

    2.  Löschen Sie den nicht übereinstimmenden Benutzer aus der Benutzerliste **Intune-Kontoportal** .

    3.  Warten Sie etwa eine Stunde, damit der Azure-Dienst die fehlerhaften Daten entfernen kann.

    4.  Aktivieren Sie DirSync erneut, und überprüfen Sie, ob der Benutzer jetzt ordnungsgemäß synchronisiert ist.

3.  In einem Szenario, in dem Sie System Center Configuration Manager mit Intune verwenden, stellen Sie sicher, dass der Benutzer eine gültige Cloudbenutzer-ID besitzt:

    1.  Öffnen Sie SQL Management Studio.

    2.  Stellen Sie eine Verbindung mit der entsprechenden Datenbank her.

    3.  Öffnen Sie den Datenbankenordner, und suchen und öffnen Sie den Ordner **CM_DBName**, wobei „DBName“ der Name der Kundendatenbank ist.

    4.  Klicken Sie im oberen Bereich auf **Neue Abfrage**, und führen Sie die folgenden Abfragen aus:

        -   Zum Anzeigen aller Benutzer: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Zum Anzeigen bestimmter Benutzer verwenden Sie die folgende Abfrage, wobei „%testuser1%“ für username@domain.com des Benutzers steht, den Sie nachschlagen möchten: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Klicken Sie nach dem Schreiben der Abfrage auf **Ausführen**.
        Nachdem die Ergebnisse zurückgegeben wurden, suchen Sie nach der Cloudbenutzer-ID.  Wenn Sie keine ID finden, ist der Benutzer nicht für die Verwendung von Intune lizenziert.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Erstellen einer Richtlinie oder Registrieren von Geräten ist nicht möglich, wenn der Firmenname Sonderzeichen enthält
**Problem:** Sie können keine Richtlinie erstellen bzw. keine Geräte registrieren.

**Lösung**: Entfernen Sie im [Office 365 Admin Center](https://portal.office.com/) die Sonderzeichen aus den Firmennamen, und speichern Sie die Unternehmensinformationen.

### <a name="unable-to-log-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Anmelden oder Registrieren von Geräten ist nicht möglich, wenn Sie mehrere überprüfte Domänen haben
**Problem:** Wenn Sie Ihren AD FS eine zweite überprüfte Domäne hinzufügen, können Benutzer mit dem Benutzerprinzipalnamen-Suffix (UPN) der zweiten Domäne sich möglicherweise nicht bei Portalen anmelden oder Geräte registrieren.


**Lösung:** Microsoft Office 365-Kunden, die einmaliges Anmelden (Single Sign-On, SSO) über AD FS 2.0 verwenden und in ihrer Organisation über mehrere Domänen der obersten Ebene für Benutzer-UPN-Suffixe verfügen (z.B. @contoso.com oder @fabrikam.com)), müssen für jedes Suffix eine separate Instanz des AD FS 2.0-Verbunddiensts bereitstellen.  Es gibt jetzt einen [Rollup für AD FS 2.0](http://support.microsoft.com/kb/2607496), der in Verbindung mit der Option **SupportMultipleDomain** den AD FS-Server zur Unterstützung dieses Szenarios aktiviert, ohne dass zusätzliche AD FS 2.0-Server erforderlich sind. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Android-Probleme
### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Geräte können nicht beim Intune-Dienst eingecheckt werden und werden als in der Intune-Administratorkonsole als „Fehlerhaft“ angezeigt.
**Problem**: Einige Samsung-Geräte, auf denen die Android-Versionen 4.4.x und 5.x ausgeführt werden, beenden den Vorgang zum Einchecken beim Intune-Dienst. Für nicht eingecheckte Geräte gilt Folgendes:

- Sie können keine Richtlinien, Apps und Remotebefehle vom Intune-Dienst empfangen.
- Sie werden in der Administratorkonsole mit dem Status **Fehlerhaft** angezeigt.
- Benutzer, die über Richtlinien für den bedingten Zugriff geschützt werden, verlieren möglicherweise ihren Zugriff auf Unternehmensressourcen.

Samsung hat bestätigt, dass die Samsung Smart Manager-Software, die auf bestimmten Samsung-Geräten vorinstalliert ist, das Intune-Unternehmensportal und die zugehörigen Komponenten deaktivieren kann. Wenn sich das Unternehmensportal in einem deaktivierten Zustand befindet, kann es nicht im Hintergrund ausgeführt werden und somit nicht mit dem Intune-Dienst kommunizieren.

**Lösung 1**:

Weisen Sie Ihre Benutzer an, die Unternehmensportal-App manuell zu starten. Nach dem App-Neustart wird das Gerät beim Intune-Dienst eingecheckt.

> [!IMPORTANT]
> Das manuelle Öffnen der Unternehmensportal-App ist eine vorübergehende Lösung, weil die Unternehmensportal-App durch den Samsung Smart Manager erneut deaktiviert werden kann.

**Lösung 2**:

Weisen Sie Ihre Benutzer an, ein Upgrade auf Android 6.0 durchzuführen. Das Problem der Deaktivierung tritt auf Android 6.0-Geräten nicht auf. Um zu überprüfen, ob ein Update verfügbar ist, können die Benutzer zu **Einstellungen** > **Geräteinformationen** > **Updates manuell herunterladen**, und folgen Sie den Anweisungen auf dem Gerät.

**Lösung 3**:

Wenn Lösung 2 nicht zur Behebung des Problems führt, führen Sie die folgenden Schritte aus, um die Unternehmensportal-App als Smart Manager-Ausnahme festzulegen:

1. Starten Sie die Smart Manager-App auf dem Gerät.

  ![Smart Manager-Symbol auf dem Gerät auswählen](./media/smart-manager-app-icon.png)

2. Wählen Sie die Kachel **Akku** aus.

  ![Kachel „Akku“ auswählen](./media/smart-manager-battery-tile.png)

3. Wählen Sie unter **App-Energiesparmodus** oder **App-Optimierung** die Option **Detail** aus.

  ![Option „Detail“ unter „App-Energiesparmodus“ oder „App-Optimierung“ auswählen](./media/smart-manager-app-power-saving-detail.png)

4. Wählen Sie aus der Liste der Apps den Eintrag **Unternehmensportal** aus.

  ![Unternehmensportal aus der Liste der Apps auswählen](./media/smart-manager-company-portal.png)

5. Wählen Sie **Deaktivieren** aus.

  ![Option „Deaktivieren“ im Dialogfeld „App-Optimierung“ auswählen](./media/smart-manager-app-optimization-turned-off.png)

6. Vergewissern Sie sich unter **App-Energiesparmodus** oder **App-Optimierung**, dass das Unternehmensportal deaktiviert ist.

  ![Überprüfen, ob das Unternehmensportal deaktiviert ist](./media/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Fehler bei der Profilinstallation
**Problem**: Sie erhalten auf einem Android-Gerät die Fehlermeldung **Fehler bei der Profilinstallation**.

**Lösung:**

1.  Vergewissern Sie sich, dass dem Benutzer eine geeignete Lizenz für die Version des von Ihnen verwendeten Intune-Diensts zugewiesen wurde.

2.  Stellen Sie sicher, dass das Gerät nicht bereits bei einem anderen MDM-Anbieter registriert ist oder dass nicht bereits ein Verwaltungsprofil darauf installiert ist.

3.  Vergewissern Sie sich, dass Chrome für Android der Standardbrowser ist und dass Cookies aktiviert sind.

### <a name="android-certificate-issues"></a>Android-Zertifikatsprobleme

**Problem**: Benutzer erhalten die folgende Meldung auf ihren Geräten: *Sie können sich nicht anmelden, da dem Gerät ein erforderliches Zertifikat fehlt.*

**Lösung 1**:

Bitten Sie die Benutzer, die Anweisungen unter [Dem Gerät fehlt ein erforderliches Zertifikat](https://docs.microsoft.com/intune/enduser/your-device-is-missing-a-required-certificate-landing-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) zu befolgen. Wenn der Fehler weiterhin auftritt, nachdem die Benutzer die Anweisungen ausgeführt haben, versuchen Sie es mit Lösung 2.

**Lösung 2**:

Tritt der Fehler wegen des fehlenden Zertifikats weiterhin auf, nachdem die Benutzer die Anmeldeinformationen des Unternehmens eingegeben haben und zur Umgebung für die Verbundanmeldung umgeleitet wurden, fehlt möglicherweise ein Zwischenzertifikat auf Ihrem AD FS-Server (Active Directory-Verbunddienste).

Der Zertifikatfehler tritt auf, da auf Android-Geräten Zwischenzertifikate für ein [SSL-Server-Hello](https://technet.microsoft.com/library/cc783349.aspx) benötigt werden, eine standardmäßige AD FS-Server- oder AD FS-Proxyserverinstallation in der SSL-Server-Hello-Antwort auf ein SSL-Client-Hello aktuell aber nur das SSL-Zertifikat des AD FS-Diensts sendet.

Um das Problem zu beheben, importieren Sie die Zertifikate wie folgt in die persönlichen Zertifikate des Computers auf dem AD FS-Server oder den Proxys:

1.  Starten Sie die Konsole zur Zertifikatverwaltung für den lokalen Computer auf dem AD FS- und dem Proxyserver, indem Sie mit der rechten Maustaste auf die Schaltfläche **Start** klicken, **Ausführen** auswählen und **certlm.msc** eingeben.
2.  Erweitern Sie **Persönlich**, und wählen Sie **Zertifikate** aus.
3.  Suchen Sie das Zertifikat für Ihre Kommunikation mit dem AD FS-Dienst (ein öffentlich signiertes Zertifikat), und doppelklicken Sie darauf, um seine Eigenschaften anzuzeigen.
4.  Klicken Sie auf die Schaltfläche **Zertifizierungspfad**, um die übergeordneten Zertifikate des Zertifikats anzuzeigen.
5.  Wählen Sie in jedem übergeordneten Zertifikat die Option **Zertifikat anzeigen** aus.
6.  Klicken Sie auf der Registerkarte **Details** auf **In Datei kopieren**.
7.  Führen Sie die Anweisungen des Assistenten aus, um den des öffentlichen Schlüssel des Zertifikats an den gewünschten Speicherort zu exportieren oder zu speichern.
8.  Importieren Sie die übergeordneten Zertifikate, die in Schritt 3 nach „Local Computer\Personal\Certificates“ exportiert wurden, indem Sie mit der rechten Maustaste auf **Zertifikate** klicken, **Alle Aufgaben** > **Importieren** auswählen und dann den Anweisungen des Assistenten zum Importieren der Zertifikate folgen.
9.  Starten Sie die AD FS-Server neu.
10. Wiederholen Sie die oben stehenden Schritte auf allen AD FS- und Proxyservern.
Der Benutzer sollte sich jetzt mit dem Android-Gerät bei der Unternehmensportal-App anmelden können.

**So überprüfen Sie, ob das Zertifikat richtig installiert wurde**

Die folgenden Schritte beschreiben nur eine von vielen Methoden und Tools, die Sie verwenden können, um zu überprüfen, ob das Zertifikat richtig installiert wurde.

1. Wechseln Sie zum [kostenlosen Digicert-Tool](ttps://www.digicert.com/help/).
2. Geben Sie den vollqualifizierten Domänennamen Ihres AD FS-Servers ein (z. B. sts.contoso.com), und wählen Sie **CHECK SERVER** aus.

Wenn das Serverzertifikat ordnungsgemäß installiert wurde, werden in den Ergebnissen alle Häkchen angezeigt. Wenn das oben beschriebene Problem vorhanden ist, wird in den Abschnitten „Certificate Name Matches“ und „SSL Certificate is correctly Installed“ des Berichts ein rotes X angezeigt.


## <a name="ios-issues"></a>iOS-Probleme

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Geräte sind inaktiv oder die Verwaltungskonsole kann nicht mit ihnen kommunizieren.
**Problem:** iOS-Geräte sind nicht beim Intune-Dienst eingecheckt. Geräte müssen in regelmäßigen Abständen beim Dienst eingecheckt sein, um den Zugriff auf geschützte Unternehmensressourcen zu behalten. Für nicht eingecheckte Geräte gilt Folgendes:

- Sie können keine Richtlinien, Apps und Remotebefehle vom Intune-Dienst empfangen.
- Sie werden in der Administratorkonsole mit dem Status **Fehlerhaft** angezeigt.
- Benutzer, die über Richtlinien für den bedingten Zugriff geschützt werden, verlieren möglicherweise ihren Zugriff auf Unternehmensressourcen.

**Lösung:** Teilen Sie die folgenden Lösungen mit Ihren Endbenutzern, damit Sie wieder Zugriff auf Unternehmensressourcen erhalten.

Wenn Benutzer die iOS-Unternehmensportal-App starten, können sie sehen, ob deren Gerät keinen Kontakt mehr mit Intune hat. Wenn erkannt wird, dass kein Kontakt mehr mit Intune besteht, wird automatisch versucht, eine Synchronisation mit Intune durchzuführen, um die Verbindung wieder herzustellen. Benutzer sehen die **Synchronisierungsversuch...**- Inlinemeldung. 

  ![Versuch, Benachrichtigungen zu synchronisieren](./media/ios_cp_app_trying_to_sync_notification.png)

Wenn die Synchronisierung erfolgreich ist, sehen Sie die Inlinemeldung **Synchronisierung erfolgreich** in der iOS-Unternehmensportal-App, die zeigt, dass der Integritätsstatus Ihres Geräts gut ist.

  ![Benachrichtigung „Synchronisierung erfolgreich“](./media/ios_cp_app_sync_successful_notification.png)

Wenn die Synchronisierung nicht erfolgreich ist, sehen Benutzer die Inlinemeldung **Synchronisierung nicht möglich** in der iOS-Unternehmensportal-App. 

  ![Benachrichtigung „Synchronisierung nicht möglich“](./media/ios_cp_app_unable_to_sync_notification.png)

Um das Problem zu beheben, müssen Benutzer die Schaltfläche **Set up** (Einrichten) auswählen, die sich rechts von der Meldung **Synchronisierung nicht möglich** befindet. Die Schaltfläche „Set up“ (Einrichten) führt die Benutzer zum Bildschirm „Company Access Setup“ (Unternehmenszugriff einrichten), auf dem sie die Anforderungen befolgen können, um ihr Gerät zu registrieren. 

  ![Bildschirm „Unternehmenszugriff einrichten“](./media/ios_cp_app_company_access_setup.png)

Sobald die Geräte registriert sind, ist ihr Integritätsstatus gut, und sie erhalten erneut Zugriff auf Unternehmensressourcen.

### <a name="profile-installation-failed"></a>Fehler bei der Profilinstallation
**Problem**: Sie erhalten auf einem iOS-Gerät die Fehlermeldung **Fehler bei der Profilinstallation**.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Schritte zur Problembehandlung bei fehlgeschlagener Profilinstallation

1.  Vergewissern Sie sich, dass dem Benutzer eine geeignete Lizenz für die Version des von Ihnen verwendeten Intune-Diensts zugewiesen wurde.

2.  Stellen Sie sicher, dass das Gerät nicht bereits bei einem anderen MDM-Anbieter registriert ist oder dass nicht bereits ein Verwaltungsprofil darauf installiert ist.

3.  Wechseln Sie zu [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), und versuchen Sie, das Profil zu installieren, wenn Sie dazu aufgefordert werden.

4.  Vergewissern Sie sich, dass Safari für iOS der Standardbrowser ist und dass Cookies aktiviert sind.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Ein registriertes iOS-Gerät wird nicht in der Konsole angezeigt, wenn der System Center Configuration Manager mit Intune verwendet wird.
**Problem:** Der Benutzer registriert das iOS-Gerät, aber es wird nicht in der Configuration Manager-Verwaltungskonsole angezeigt. Das Gerät zeigt nicht an, dass es registriert wurde. Mögliche Ursachen:

- Vielleicht haben Sie Ihren Intune-Connector erst in einem Konto und dann in einem anderen Konto registriert.
- Vielleicht haben Sie das MDM-Zertifikat von einem Konto heruntergeladen und auf einem anderen Konto verwendet.


**Lösung:** Führen Sie die folgenden Schritte aus:

1. Deaktivieren Sie iOS im Windows Intune-Connector.
    1. Klicken Sie mit der rechten Maustaste auf das Intune-Abonnement, und wählen Sie **Eigenschaften** aus.
    1. Deaktivieren Sie auf der Registerkarte „iOS“ die Option „iOS-Registrierung aktivieren“.



2. Führen Sie in SQL die folgenden Schritte in der CAS-Datenbank aus:

    1. update SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%'
    1. delete from MDMPolicy where PolicyType = 7
    1. delete from MDMPolicyAssignment where PolicyType = 7
    1. update SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%'
    1. delete from MDMPolicy where PolicyType = 11
    1. delete from MDMPolicyAssignment where PolicyType = 11
    1. DELETE Drs_Signals
3. Starten Sie den SMS-Executive-Dienst oder den CM-Server neu.

4. Rufen Sie ein neues APN-Zertifikat ab, und laden Sie es hoch. Klicken Sie dazu mit der rechten Maustaste im linken Bereich des Configuration Manager auf das Intune-Abonnement. Wählen Sie **APNs-Zertifikatanforderung erstellen **, und folgen Sie den Anweisungen.
5. 
## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Probleme bei der Verwendung von System Center Configuration Manager mit Intune

### <a name="mobile-devices-disappear"></a>Mobile Geräte verschwinden

**Problem:** Nach der erfolgreichen Registrierung eines mobilen Geräts bei Configuration Manager verschwindet es aus der Sammlung der Mobilgeräte, aber das Gerät besitzt weiterhin das Verwaltungsprofil und wird im CSS-Gateway aufgeführt.

**Lösung:** Dieses Problem kann auftreten, wenn Sie einen benutzerdefinierten Prozess haben, der Geräte entfernt, die keiner Domäne angehören, oder weil der Benutzer das Gerät aus dem Abonnement entfernt hat. Um zu überprüfen, welcher Prozess oder welches Benutzerkonto das Gerät aus der Configuration Manager-Konsole entfernt hat, führen Sie die folgenden Schritte aus, die überprüfen, wie das Gerät entfernt wurde.

1.  Wählen Sie in der Configuration Manager-Verwaltungskonsole **Überwachung** &gt; **Systemstatus** &gt; **Statusmeldungsabfragen** aus.

2.  Klicken Sie mit der rechten Maustaste auf **Manuell gelöschte Auflistungselementressourcen**, und wählen Sie **Meldungen anzeigen** aus.

3.  Wählen Sie eine geeignete Datum/Uhrzeit-Kombination innerhalb der letzten 12 Stunden aus.

4.  Suchen Sie das fragliche Gerät, und überprüfen Sie, wie das Gerät entfernt wurde. Das folgende Beispiel zeigt, dass das Konto „SCCMInstall“ das Gerät über eine unbekannte Anwendung gelöscht hat.

    ![Screenshot für die Gerätelöschungsdiagnose](./media/cm-with-intune-unknown-app-deleted-device.png)

5.  Überprüfen Sie, ob Configuration Manager keine geplanten Aufgaben, geplanten Skripts oder andere geplante Prozesses hat, die eventuell Geräte löschen, die keiner Domäne angehören oder mobile oder ähnliche Geräte sind.




### <a name="other-ios-enrollment-errors"></a>Weitere iOS-Registrierungsfehler

Sehen Sie sich eine Liste der [iOS-Registrierungsfehler](https://docs.microsoft.com/intune/enduser/you-see-errors-while-trying-to-enroll-your-device-in-intune-ios) an, die Endbenutzern möglicherweise angezeigt werden. Die Liste enthält Informationen zu Fehlermeldungen, die Endbenutzern angezeigt werden, sowie die Schritte, mit denen Sie das Problem beheben können.

## <a name="pc--issues"></a>PC-Probleme

### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>Der Computer ist bereits registriert – Fehler hr 0x8007064c
**Problem:** Fehler bei Registrierung: **Der Computer ist bereits registriert**. Das Registrierungsprotokoll zeigt Fehler **hr 0x8007064c** an.

Möglicherweise trat dieser Fehler auf, weil der Computer bereits vorher registriert wurde oder über das geklonte Image eines Computers verfügt, der registriert wurde. Das Kontozertifikat des vorherigen Kontos ist immer noch auf dem Computer vorhanden.

**Lösung:**

1.. Geben Sie im Menü **Start** **Ausführen** -> **MMC** ein.
1. Wählen Sie **Datei** > **Snap-Ins hinzufügen/entfernen** aus.
1. Doppelklicken Sie auf **Zertifikate**, wählen Sie **Computerkonto**, ** > Weiter**, und wählen Sie die Option **Lokaler Computer** aus.
1. Doppelklicken Sie auf **Zertifikate (lokaler Computer)**, und wählen Sie **Persönlich/Zertifikate** aus.
1. Suchen Sie nach dem von Sc_Online_Issuing ausgestellten Intune-Zertifikat, und löschen Sie es, falls vorhanden.
1. Wenn der folgende Registrierungsschlüssel vorhanden ist, löschen Sie ihn: ** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** und alle untergeordneten Schlüssel.
1. Versuchen Sie, eine erneute Registrierung durchzuführen.
1. Wenn der PC sich immer noch nicht registrieren kann, suchen und löschen Sie diesen Schlüssel, sofern vorhanden: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Versuchen Sie, eine erneute Registrierung durchzuführen.

    > [!IMPORTANT]
    > Dieser Abschnitt, diese Methode oder Aufgabe enthält Schritte, die Ihnen zeigen, wie Sie die Registrierung ändern. Wenn Sie die Registrierung falsch ändern, können jedoch schwerwiegende Probleme auftreten. Achten Sie darum auf eine sorgfältige Ausführung der folgenden Schritte. Sichern Sie die Registrierung zum zusätzlichen Schutz, bevor Sie sie ändern. Sie können dann die Registrierung wiederherstellen, falls ein Problem auftritt.
    > Weitere Informationen zum Sichern und Wiederherstellen der Registrierung finden Sie unter [Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/en-us/kb/322756).

## <a name="general-enrollment-error-codes"></a>Allgemeine Fehlercodes bei der Registrierung

|Fehlercode|Mögliches Problem|Lösungsvorschlag|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |Die Uhr des Clientcomputers ist nicht auf die richtige Uhrzeit eingestellt.|Stellen Sie sicher, dass die Uhr und die Zeitzone des Clientcomputers richtig eingestellt sind.|
|0x80240438, 0x80CF0438, 0x80CF402C|Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Proxy-Einstellungen des Clients.|Überprüfen Sie, ob die Proxykonfiguration des Clientcomputers von Intune unterstützt wird, und ob der Clientcomputer Zugang zum Internet hat.|
|0x80240438, 0x80CF0438|Proxyeinstellungen in Internet Explorer und im lokalen System sind nicht konfiguriert.|Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Proxyeinstellungen des Clients, und vergewissern Sie sich, dass die Proxykonfiguration des Clientcomputers von Intune unterstützt wird, und der Clientcomputer mit dem Internet verbunden ist.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Das Registrierungspaket ist nicht mehr aktuell.|Laden Sie das aktuellste Clientsoftwarepaket vom Arbeitsbereich „Verwaltung“ herunter, und installieren Sie es.|
|0x80043002, 0x80CF3002|Das Konto befindet sich im Wartungsmodus.|Wenn sich das Konto im Wartungsmodus befindet, können Sie keine neuen Clientcomputer registrieren. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto an.|
|0x80043003, 0x80CF3003|Das Konto wurde gelöscht.|Prüfen Sie, ob Ihr Konto und Ihr Abonnement für Intune noch aktiv sind. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto an.|
|0x80043005, 0x80CF3005|Der Clientcomputer wurde abgekoppelt.|Warten Sie einige Stunden, entfernen Sie ältere Versionen der Clientsoftware von dem Computer, und versuchen Sie dann erneut, die Clientsoftware auf dem Computer zu installieren.|
|0x80043006, 0x80CF3006|Die für das Konto maximal zulässige Anzahl Arbeitsplätze ist erreicht.|Ihr Unternehmen muss zusätzliche Arbeitsplätze erwerben, bevor Sie weitere Clientcomputer bei dem Dienst registrieren können.|
|0x80043007, 0x80CF3007|Zertifikatsdatei wurde im Ordner des Installationsprogramms nicht gefunden.|Extrahieren Sie alle Dateien, bevor Sie die Installation starten. Die extrahierten Dateien dürfen nicht umbenannt oder verschoben werden: Alle Dateien müssen im selben Ordner vorhanden sein, da die Installation sonst fehlschlägt.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Die Software kann nicht installiert werden, weil ein Neustart des Clientcomputers aussteht.|Starten Sie den Computer neu, und wiederholen Sie dann die Installation der Clientsoftware.|
|0x80070032|Eine oder mehrere Voraussetzungen, die für die Installation der Clientsoftware erforderlich sind, wurden auf dem Clientcomputer nicht gefunden.|Stellen Sie sicher, dass alle erforderlichen Updates auf dem Clientcomputer installiert sind, und versuchen Sie dann erneut, die Clientsoftware zu installieren.|
|0x80043008, 0x80CF3008|Microsoft-Onlinedienst zur Updateverwaltung konnte nicht gestartet werden.|Wenden Sie sich dazu an den Microsoft Support, wie unter [Anfordern von Support für Microsoft Intune](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) beschrieben.|
|0x80043009, 0x80CF3009|Der Clientcomputer ist bereits für den Dienst registriert.|Sie müssen den Clientcomputer abkoppeln, bevor sie ihn erneut für den Dienst registrieren können.|
|0x8004300B, 0x80CF300B|Das Installationspaket für die Clientsoftware kann nicht ausgeführt werden, da die Windows-Version auf dem Client nicht unterstützt wird.|Die auf dem Client ausgeführte Windows-Version wird von Intune nicht unterstützt.|
|0xAB2|Fehler beim Zugriff auf die VBScript-Laufzeit für die benutzerdefinierte Aktion.|Dieser Fehler wird von einer benutzerdefinierten Aktion verursacht, die auf DLLs (Dynamic-Link Libraries) aufbaut. Um den DLL-Fehler zu ermitteln, benötigen Sie möglicherweise die Tools, die im Artikel&19803;8 der [Microsoft Support-KB: Hilfreiche Tools bei Problemen mit der Paketerstellung und Weitergabe](https://support.microsoft.com/en-us/kb/198038) erläutert werden.|
|0x80cf0440|Die Verbindung zum Dienstendpunkt wurde abgebrochen.|Test- oder kostenpflichtige Konto wird angehalten. Erstellen Sie ein neues Test- oder kostenpflichtiges Konto und registrieren Sie sich erneut.|




### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) beschrieben an den Microsoft Support.



<!--HONumber=Feb17_HO1-->

