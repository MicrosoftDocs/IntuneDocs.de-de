## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>Einrichten der automatischen Registrierung mit Azure Active Directory Premium für Windows 10 und Windows 10 Mobile

Mit der automatischen Registrierung können Benutzer entweder unternehmenseigene oder private Windows 10-PCs und Windows 10 Mobile-Geräte in Intune registrieren, indem Sie ein Geschäfts- oder Schulkonto hinzufügen und zustimmen, dass das Gerät verwaltet wird. So einfach ist das. Im Hintergrund registriert sich das Gerät des Benutzers und tritt Azure Active Directory bei. Nach der Registrierung wird das Gerät mit Intune verwaltet.

**Voraussetzungen**
- Azure Active Directory Premium-Abonnement ([Testabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-Abonnement


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurieren der automatischen MDM-Registrierung

1. Wechseln Sie im [Azure-Verwaltungsportal](https://manage.windowsazure.com) (https://manage.windowsazure.com) zum Knoten **Active Directory**, und wählen Sie Ihr Verzeichnis aus.

2. Wählen Sie die Registerkarte **Anwendungen** aus. **Microsoft Intune** wird in der Liste der Anwendungen angezeigt.

    ![Azure AD-Apps mit Microsoft Intune](../media/aad-intune-app.png)

3. Wählen Sie den Pfeil für **Microsoft Intune** aus. Es wird eine Seite angezeigt, auf der Sie Microsoft Intune konfigurieren können.

4. Wählen Sie **Konfigurieren** aus, um mit der Konfiguration der automatischen MDM-Registrierung mit Microsoft Intune zu beginnen.

5. Verwenden Sie die Standardwerte für die folgenden URLs:

  - **MDM-Registrierung**
  - **MDM-Nutzungsbedingungen** 
  - **MDM-Konformität**

6.  Geben Sie an, welche Geräte von Benutzern von Microsoft Intune verwaltet werden sollen. Die Windows 10-Geräte dieser Benutzer werden automatisch für die Verwaltung mit Microsoft Intune registriert.

  - **Alle**
  - **Gruppen**
  - **Keine**

7. Wählen Sie **Speichern** aus.