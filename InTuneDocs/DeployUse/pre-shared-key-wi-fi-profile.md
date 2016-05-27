---
# required metadata

title: WLAN über PSK | Microsoft Intune
description: 
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:


---
# Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel
Hier wird erläutert, wie Sie anhand der **benutzerdefinierten Konfiguration** von Intune ein WLAN-Profil mit einem vorinstallierten Schlüssel erstellen. Dieses Thema umfasst außerdem ein Beispiel für die Erstellung eines EAP-basierten WLAN-Profils.

Hinweis:
-   Möglicherweise ist es für Sie einfacher, den Code von einem Computer zu kopieren, der eine Verbindung mit dem jeweiligen Netzwerk herstellt, wie unten beschrieben.
- Bei Android haben Sie auch die Möglichkeit, diesen von Johnathon Biersack bereitgestellten [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) zu verwenden.
-   Sie können mehrere Netzwerke und Schlüssel hinzufügen, indem Sie weitere OMA-URI-Einstellungen hinzufügen.
-  Verwenden Sie für iOS den Apple Configurator auf einer Mac-Station, um das Profil zu konfigurieren. Verwenden Sie alternativ diesen [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/), der von Johnathon Biersack bereitgestellt wird.


1.  Um ein WLAN-Profil mit einem vorinstallierten Schlüssel für Android oder Windows oder ein EAP-basiertes WLAN-Profil zu erstellen, wählen Sie beim Erstellen einer Richtlinie statt eines WLAN-Profils die Option **Benutzerdefinierte Konfiguration** für die jeweilige Geräteplattform aus.

2.  Geben Sie einen Namen und eine Beschreibung an.
3.  Fügen Sie eine neue OMA-URI-Einstellung hinzu:

   a.   Geben Sie einen Namen für diese WLAN-Netzwerkeinstellung ein.

   b.   Geben Sie eine Beschreibung für die OMA-URI-Einstellung ein, oder lassen Sie sie leer.

   c.   **Datentyp**: Legen Sie diesen auf "String(XML)" fest.

   d.   **OMA-URI**: ./Vendor/MSFT/Wi-Fi /Profile/<SSID>/Settings

Hinweis: Stellen Sie sicher, dass Sie den Punkt am Anfang eingeben.

SSID steht für die SSID, für die Sie die Richtlinie erstellen. Beispiel:
`./Vendor/MSFT/Wi-Fi/Profile/Hotspot-1/Settings`

  e.    Feld „Wert“: Hier fügen Sie Ihren XML-Code ein. Hier sehen Sie ein Beispiel. Die einzelnen Werte sollten an Ihre Netzwerkeinstellungen angepasst werden. Einige Hinweise finden Sie im Kommentarabschnitt des Codes.


    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
    -->
    <WLANProfile
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <hex>53534944</hex>
        <name><SSID of wifi profile></name>
        </SSID>
        <nonBroadcast>false</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication><Type of authentication></authentication>
            <encryption><Type of encryption></encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial>MyPassword</keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>

## EAP-basiertes WLAN-Profil
Hier sehen Sie ein Beispiel für den XML-Code eines EAP-basierten WLAN-Profils:

    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>

4.  Klicken Sie auf „OK“, speichern Sie die Richtlinie, und stellen Sie sie dann bereit.
HINWEIS. Diese Richtlinie kann nur für Benutzergruppen bereitgestellt werden.

Wenn sich die einzelnen Geräte das nächste Mal anmelden, wird die Richtlinie angewendet, und auf dem Gerät wird ein WLAN-Profil erstellt. Das Gerät kann automatisch eine Verbindung mit dem Netzwerk herstellen.
## Erstellen der XML-Datei aus einer vorhandenen WLAN-Verbindung
Sie können die XML-Datei auch aus einer vorhandenen WLAN-Verbindung erstellen:
1.     Öffnen Sie auf einem Computer, der mit dem WLAN verbunden ist oder vor kurzem damit verbunden wurde, den folgenden Ordner: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}. Es wird empfohlen, einen Computer zu verwenden, der nicht mit allzu vielen WLANs verbunden ist, weil Sie die einzelnen Profile durchsuchen müssen, um das richtige zu finden.
3.     Durchsuchen Sie die XML-Dateien, um die Datei mit dem richtigen Namen zu finden.
4.     Wenn Sie die richtige XML-Datei gefunden haben, kopieren Sie den XML-Code in das Feld „Daten“ auf der Seite mit den OMA-URI-Einstellungen.

## Bereitstellen der Richtlinie

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und klicken Sie dann auf **Bereitstellung verwalten**..

2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:

    -   **Wenn Sie die Richtlinie bereitstellen möchten:** Wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und klicken Sie auf **Hinzufügen** &gt; **OK**..

    -   **Wenn Sie das Dialogfeld schließen möchten, ohne die Richtlinie bereitzustellen:** Klicken Sie auf **Abbrechen**..

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Richtlinienliste anzeigen.

### Weitere Informationen:
[WLAN-Verbindungen in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->

