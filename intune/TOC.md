# [Einführung](introduction-intune.md)
## [Was ist das Azure-Portal?](what-is-intune.md)
## [Was ist Intune for Education?](introduction-intune-education.md)
## [Intune-Features in Azure](ui-changes.md)
## [Registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md)
## [Neuerungen](whats-new.md)
### [Änderungen an der App-Benutzeroberfläche](whats-new-app-ui.md)
### [Archiv der Neuerungen (Azure-Portal)](whats-new-archive.md)
### [Archiv der Neuerungen (klassisches Portal)](whats-new-archive-classic.md)

<!--## High-level architecture-->

## [Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md)
### [Gerätelebenszyklus](device-lifecycle.md)
### [App-Lebenszyklus](app-lifecycle.md)
## [Häufige Szenarien](common-scenarios.md)
## [Bekannte Probleme](known-issues.md)
## [Support anfordern](get-support.md)
## [Intune-Dienstbeschreibung](microsoft-intune-service-description.md)

<!--# Get started
## [Manage devices](/intune-classic/understand-explore/mobile-device-management-trial-guide-microsoft-intune?toc=/intune/toc.json)
## [Create policies](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3?toc=/intune/toc.json)
## [Manage apps](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-4?toc=/intune/toc.json) -->


# Planen der Bereitstellung
## [Planungshandbuch](planning-guide.md)
### [Bestimmen von kurz- und langfristigen Zielen](planning-guide-deployment-goals.md)
### [Bestimmen von Szenarien](planning-guide-scenarios.md)
### [Bestimmen der Anforderungen](planning-guide-requirements.md)
### [Entwickeln eines Rolloutplans](planning-guide-rollout-plan.md)
### [Entwickeln eines Kommunikationsplans](planning-guide-communication-plan.md)
### [Entwickeln eines Unterstützungsplans](planning-guide-support-plan.md)
### [Entwurf](planning-guide-design.md)
### [Implementierung](planning-guide-onboarding.md)
### [Test und Überprüfung](planning-guide-test-validation.md)
### [Zusätzliche Ressourcen](planning-guide-resources.md)
<!-- ## Scenario implementation guides
### [BYOD](/enterprise-mobility-security/solutions/enable-byod?toc=/intune/toc.json)
### [Protect O365 data](/enterprise-mobility-security/solutions/protect-office365-data-with-intune?toc=/intune/toc.json)
### [Protect on-premises data](/enterprise-mobility-security/solutions/protect-on-premises-data-with-intune?toc=/intune/toc.json)
### [Protect data without enrollment](/enterprise-mobility-security/solutions/protect-company-data-without-managing-devices?toc=/intune/toc.json)
### [Manage company-owned devices](/enterprise-mobility-security/solutions/issue-corp-devices?toc=/intune/toc.json)
### [Manage shared devices](/enterprise-mobility-security/solutions/limited-use-shared-devices?toc=/intune/toc.json) -->
## [Migrationshandbuch](migration-guide.md)
### [Vorbereiten von Intune](migration-guide-prepare.md)
#### [Grundlegende Einrichtung](migration-guide-setup.md)
#### [Konfigurieren von Richtlinien für die Verwaltung von Apps und Geräten](migration-guide-configure-policies.md)
#### [Konfigurieren von App-Schutzrichtlinien](migration-guide-app-protection-policies.md)
#### [Migrationsüberlegungen](migration-guide-considerations.md)
### [Migration](migration-guide-campaign.md)
#### [Planen der Kommunikation](migration-guide-communication-plan.md)
#### [Steuern der Einführung](migration-guide-drive-adoption.md)
#### [typischer Migrationszyklus](migration-guide-cycle.md)


# Vorgehensweise:

## [Einrichten von Intune](setup-steps.md)
### [Voraussetzungen](supported-devices-browsers.md)
#### [Nutzung der Netzwerkbandbreite](network-bandwidth-use.md)
### [Anmelden bei Intune](account-sign-up.md)
### [Konfigurieren von Domänen](custom-domain-name-configure.md)
### [Hinzufügen von Benutzern](users-permissions-add.md)
### [Zuweisen von Lizenzen](licenses-assign.md)       
### [Anpassen des Unternehmensportals](company-portal-customize.md)     
### [Festlegen der MDM-Autorität](mdm-authority-set.md)

## [Registrieren von Geräten](device-enrollment.md)
### Voraussetzungen
#### [Festlegen von Nutzungsbedingungen](terms-and-conditions-create.md)
#### [Festlegen von Einschränkungen](enrollment-restrictions-set.md)
#### [Abrufen eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md)
#### [Hinzufügen von Unternehmensbezeichnern](corporate-identifiers-add.md)
#### [Einrichten des Geräteregistrierungs-Managers](device-enrollment-manager-enroll.md)
#### [Zuweisen von Geräten zu Gruppen](device-group-mapping.md)
### [Einrichten der Windows-Registrierung](windows-enroll.md)
#### [Automatische Registrierung](windows-enroll.md)
#### [Massenregistrierung](windows-bulk-enroll.md)
### [Einrichten der Android-Registrierung](android-enroll.md)
### Einrichten der iOS-Registrierung
#### [Mit dem Programm zur Geräteregistrierung](device-enrollment-program-enroll-ios.md)
#### [Mit Apple School Manager](apple-school-manager-set-up-ios.md)
#### [Mit Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md)
### [Einrichten der macOS-Registrierung](macos-enroll.md)
### [Schulen von Benutzern](end-user-educate.md)

## [Verwalten von Geräten](device-management.md)
### [Gerät zurücksetzen](devices-wipe.md)
### [Aktivierungssperre umgehen](device-activation-lock-bypass.md)
### [Zurücksetzen des Geräts auf Werkseinstellungen](device-factory-reset.md)
### [Verwalten von Windows Fresh Start](device-fresh-start.md)
### [Finden eines verlorenen iOS-Geräts](device-locate.md)
### [Aktivieren des iOS-Modus für verlorene Geräte](device-lost-mode.md)
### [Gerät sperren](device-remote-lock.md)
### [Unternehmensdaten entfernen](device-company-data-remove.md)
### [Kennung zurücksetzen](device-passcode-reset.md)
### [Gerät neu starten](device-restart.md)
### [Remotesteuerung für Android](device-profile-android-teamviewer.md)
### [Untersuchen des Gerätebestands](device-inventory.md)

## [Verwalten von Benutzern](user-management.md)
### [Erste Schritte mit Gruppen](groups-get-started.md)
<!--### Add and delete users -->

## [Verwalten von Apps](app-management.md)
### [Hinzufügen von Apps](apps-add.md)
#### [Android Store-Apps](store-apps-android.md)
#### [Android-Branchen-Apps](lob-apps-android.md)
#### [iOS Store-Apps](store-apps-ios.md)
#### [Branchenspezifische iOS-Apps](lob-apps-ios.md)
#### [Web-Apps](web-app.md)
#### [Windows Phone 8.1 Store-Apps](store-apps-windows-phone-8-1.md)
#### [Branchenspezifische Windows Phone-Apps](lob-apps-windows-phone.md)
#### [Windows Store-Apps](store-apps-windows.md)
#### [Branchenspezifische iOS-Apps](lob-apps-windows.md)
#### [Android for Work-Apps](apps-add-android-for-work.md)
### [Zuweisen von Apps](apps-deploy.md)
### [Überwachen von Apps](apps-monitor.md)
### [iOS-App-Konfigurationsprofile](app-configuration-policies-use-ios.md)
### [Android-App-Konfigurationsprofile](app-configuration-policies-use-android.md)
### [Verwenden von iOS-App-Bereitstellungsprofilen](app-provisioning-profile-ios.md)
### [Selektives Zurücksetzen von Apps](apps-selective-wipe.md)
### [Arbeiten mit per Volumenlizenz erworbenen Apps und Büchern](vpp-apps.md)
#### [VPP-Apps für iOS](vpp-apps-ios.md)
#### [Windows Store für Unternehmen-Apps](windows-store-for-business.md)
#### [iOS-E-Books](vpp-ebooks-ios.md)
### [Konfigurieren der Unternehmensportal-App](company-portal-app.md)
### [Konfigurieren des Managed Browsers](app-configuration-managed-browser.md)
## [Verwenden von App-Schutzrichtlinien](app-protection-policies.md)
### [Vorbereitungen für WIP-App-Schutzrichtlinien](app-protection-policies-configure-windows-10.md)
### [Erstellen und Zuweisen von WIP-App-Schutzrichtlinien](windows-information-protection-policy-create.md)
### [Einstellungen für Android](app-protection-policy-settings-android.md)
### [Einstellungen für iOS](app-protection-policy-settings-ios.md)
### [Überprüfen von App-Schutzrichtlinien](app-protection-policies-validate.md)
### [Überwachen des Benutzerstatus des App-Schutzes](app-protection-policies-monitor.md)
### [Vorbereitungen für WIP-App-Schutzrichtlinien](app-protection-policies-configure-windows-10.md)
### [Erstellen und Zuweisen von WIP-App-Schutzrichtlinien](windows-information-protection-policy-create.md)
### [Verwalten der Datenübertragung zwischen iOS-Apps](data-transfer-between-apps-manage-ios.md)

## [Konfigurieren von Geräten](device-profiles.md)
### [Konfigurieren von Geräteprofilen](device-profile-create.md)
### [Konfigurieren von Gerätefeatures](device-features-configure.md)
#### [AirPrint für iOS und macOS](air-print-settings-ios-macos.md)
#### [AirPlay für iOS](airplay-settings-ios.md)
#### [Layout der Startseite für iOS](home-screen-settings-ios.md)
#### [App-Benachrichtigungen für iOS](app-notification-settings-ios.md)
#### [Gemeinsam genutzte Geräte für iOS](shared-device-settings-ios.md)
#### [Webfiltereinstellungen für iOS](web-content-filter-settings-ios.md)
### [Konfigurieren von Geräteeinschränkungen](device-restrictions-configure.md)
#### [Android](device-restrictions-android.md)
#### [iOS](device-restrictions-ios.md)
#### [macOS](device-restrictions-macos.md)
#### [Windows 8.1](device-restrictions-windows-8-1.md)
#### [Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
#### [Windows 10](device-restrictions-windows-10.md)
#### [Windows 10 Team](device-restrictions-windows-10-teams.md)
#### [Android for Work](device-restrictions-android-for-work.md)
### [Konfigurieren von E-Mail-Einstellungen](email-settings-configure.md)
#### [Android](email-settings-android.md)
#### [iOS](email-settings-ios.md)
#### [Windows Phone 8.1](email-settings-windows-phone-8-1.md)
#### [Windows 10](email-settings-windows-10.md)
### [Konfigurieren von VPN-Einstellungen](vpn-settings-configure.md)
#### [Android](vpn-settings-android.md)
#### [iOS](vpn-settings-ios.md)
#### [macOS](vpn-settings-macos.md)
#### [Windows 8.1](vpn-settings-windows-8-1.md)
#### [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
#### [Windows 10](vpn-settings-windows-10.md)
### [Konfigurieren von WLAN-Einstellungen](wi-fi-settings-configure.md)
#### [Android](wi-fi-settings-android.md)
#### [iOS](wi-fi-settings-ios.md)
#### [macOS](wi-fi-settings-macos.md)
#### [Windows 8.1 & Windows 10](wi-fi-settings-import-windows-8-1.md)
### [Konfigurieren der Einstellungen des Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md)
### [Konfigurieren von Einstellungen für Windows 10 Education](education-settings-configure.md)
### [Konfigurieren von iOS-Einstellungen für Bildungseinrichtungen](education-settings-configure-ios.md)
### [Konfigurieren von Einstellungen für Windows Update for Business](windows-update-for-business-configure.md)
### [Konfigurieren von Zertifikaten](certificates-configure.md)
#### [SCEP](certificates-scep-configure.md)
#### [PKCS](certficates-pfx-configure.md)
### [Konfigurieren der Windows Information Protection-Einstellungen](windows-information-protection-configure.md)
### [Zuweisen von Profilen](device-profile-assign.md)
### [Überwachen von Profilen](device-profile-monitor.md)
### [Beheben von Problemen mit Profilen](device-profile-troubleshoot.md)

## [Festlegen der Gerätekonformität](device-compliance.md)
### [Voraussetzungen](device-compliance-get-started.md)
### [Erstellen einer Android-Richtlinie](compliance-policy-create-android.md)
### [Erstellen einer Android for Work-Richtlinie](compliance-policy-create-android-for-work.md)
### [Erstellen einer iOS-Richtlinie](compliance-policy-create-ios.md)
### [Erstellen einer Windows-Richtlinie](compliance-policy-create-windows.md)
<!--### Create Actions for noncompliance-->
### [Überwachen der Gerätekonformität](compliance-policy-monitor.md)

## [Einrichten des bedingten Zugriffs](conditional-access.md)
### [Gängige Möglichkeiten der Nutzung des bedingten Zugriffs](conditional-access-intune-common-ways-use.md)
### [App-basierter bedingter Zugriff](app-based-conditional-access-intune.md)
### [Installieren des Connectors für Exchange lokal](exchange-connector-install.md)
### [Erstellen und Zuweisen der Richtlinie für bedingten Zugriff](conditional-access-exchange-create.md)
### [Einrichten des App-basierten bedingten Zugriffs für Exchange Online](app-based-conditional-access-intune-exchange-online-create.md)
### [Einrichten des App-basierten bedingten Zugriffs für SharePoint Online](app-based-conditional-access-intune-sharepoint-online-create.md)
### [ADAL und Intune](app-modern-authentication-block.md)
### [Überwachung der Einhaltung für bedingten Zugriff](conditional-access-exchange-monitor.md)

## Schützen von Daten und Geräten

### [Mobile Threat Defense](mobile-threat-defense.md)

#### [Einrichten von Lookout](lookout-mobile-threat-defense-connector.md)
##### [Lookout- und Intune-Integration](lookout-mtd-subscription-setup.md)
##### [Aktivieren von Lookout in Intune](lookout-mtd-connector-enable.md)
##### [Bereitstellen von Apps für die Verwendung mit Lookout](lookout-for-work-app-configure-deploy.md)
##### [Lookout-Gerätekonformitätsrichtlinie](lookout-device-compliance-policy-create.md)

#### [Einrichten von Skycure](skycure-mobile-threat-defense-connector.md)
##### [Konfigurieren von Azure AD-SSO](skycure-azure-sso-configure.md)
##### [Herunterladen der iOS-App-Konfigurationsrichtlinie](skycure-ios-app-configuration-policy-download.md)
##### [Hinzufügen und Konfigurieren von Apps](skycure-microsoft-authenticator-app-ios-app-configuration-policy-add.md)
##### [Bereitstellen von Apps für die Verwendung mit Skycure](skycure-microsoft-authenticator-app-ios-app-configuration-policy-deploy.md)
##### [Skycure- und Intune-Integration](skycure-mtd-connector-integration.md)
##### [Aktivieren von Skycure in Intune](skycure-mtd-connector-enable.md)
##### [Skycure-Gerätekonformitätsrichtlinie](skycure-device-compliance-policy-create.md)

### [Einrichten von Windows Hello](windows-hello.md)        
<!-- ### Protect devices with remote actions        -->

## [Verwalten von Rollen](role-based-access-control.md)
<!-- ### Create a custom role
### Assign a role -->
### [Verwenden der Rolle „Helpdeskoperator“](help-desk-operators.md)
<!-- ### Custom role settings -->

## [Verwalten von PCs über einen Software-Agent](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune?toc=/intune/toc.json)
### [Installieren des PC-Clients](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune?toc=/intune/toc.json)
### [Allgemeine Aufgaben zur Verwaltung von PCs](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client?toc=/intune/toc.json)
#### [PC-Richtlinien](/intune-classic/deploy-use/use-policies-to-simplify-windows-pc-management?toc=/intune/toc.json)
#### [Anzeigen des Inventars](/intune-classic/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
#### [Außerbetriebnahme von PCs](/intune-classic/deploy-use/retire-a-windows-pc-with-microsoft-intune?toc=/intune/toc.json)
#### [Verknüpfen von PCs mit Benutzern](/intune-classic/deploy-use/manage-user-device-linking-for-windows-pcs-with-microsoft-intune?toc=/intune/toc.json)
#### [Remoteunterstützung](/intune-classic/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
### [Richtlinien zum Schutz von Windows-PCs](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
#### [Softwareupdates](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune?toc=/intune/toc.json)
#### [Windows-Firewall](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune?toc=/intune/toc.json)
#### [Endpoint Protection](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune?toc=/intune/toc.json)
### [Hinzufügen von Apps für Intune-Client-PCs](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
### [Verwalten von Lizenzverträgen](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune?toc=/intune/toc.json)
### [Lösen von Richtlinienkonflikten](/intune-classic/deploy-use/resolve-gpo-and-microsoft-intune-policy-conflicts?toc=/intune/toc.json)


# Überwachung und Problembehandlung
## [Überwachen der Telekommunikationsausgaben](telecom-expenses-monitor.md)


# Entwickeln und Anpassen
## [Konfigurieren von benutzerdefinierten Geräteeinstellungen](custom-settings-configure.md)
### [Android](custom-settings-android.md)
#### [Erstellen eines WLAN-Profils mithilfe eines vorinstallierten Schlüssels](wi-fi-profile-shared-key.md)
#### [Profil für VPN pro App](android-pulse-secure-per-app-vpn.md)
#### [Zulassen/Blockieren von Apps für Samsung KNOX Standard](samsung-knox-apps-allow-block.md)
### [iOS](custom-settings-ios.md)
### [macOS](custom-settings-macos.md)
### [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
### [Windows 10](custom-settings-windows-10.md)
### [Android for Work](custom-settings-android-for-work.md)
## [Vorbereiten von branchenspezifischen Apps für MAM](apps-prepare-mobile-application-management.md)
### [App Wrapping Tool für iOS](app-wrapper-prepare-ios.md)
### [App Wrapping Tool für Android](app-wrapper-prepare-android.md)
## [Querladen von Windows-Apps](app-sideload-windows.md)
## [Intune App SDK](app-sdk.md)
### [Erste Schritte mit dem Intune App SDK](app-sdk-get-started.md)
### [Intune App SDK für iOS](app-sdk-ios.md)
### [Intune App SDK für Android](app-sdk-android.md)
### [Intune App SDK-Cordova-Plug-In](app-sdk-cordova.md)
### [Intune App SDK-Xamarin-Komponente](app-sdk-xamarin.md)
## [Gewusst wie: Verwenden der Intune Graph-APIs](intune-graph-apis.md)
## [Intune Graph-API](https://graph.microsoft.io/docs/api-reference/beta/resources/intune_graph_overview)


# [Glossar](intune-glossary.md)