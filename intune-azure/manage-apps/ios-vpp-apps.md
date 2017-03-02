---
title: Verwalten von per Volumenlizenz erworbenen iOS-Apps | Intune in Azure (Vorschau) | Microsoft Docs
description: 'Intune in Azure (Vorschau): Erfahren Sie, wie Sie Apps, die Sie per Volumenlizenz im iOS Store erworben haben, in Intune synchronisieren und dann ihre Nutzung verwalten und nachverfolgen.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87250baede6c86e7ac5c402e79026908e712f48c
ms.openlocfilehash: 809fe8d8eea7e472d80f6ee22e26c1f376e870eb

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program"></a>Verwalten von iOS-Apps, die über ein Volumenprogramm erworben wurden


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Der iOS-App-Store bietet die Möglichkeit, mehrere Lizenzen für eine App zu erwerben, die in Ihrem Unternehmen ausgeführt werden soll. Dadurch können Sie den Verwaltungsaufwand reduzieren, der durch das Nachverfolgen mehrerer erworbener App-Kopien entsteht.

Microsoft Intune unterstützt Sie bei der Verwaltung von Apps, die über ein solches Programm erworben wurden. Dazu importieren Sie die Lizenzinformationen aus dem App-Store, verfolgen nach, wie viele Lizenzen verwendet wurden, und verhindern, dass mehr App-Kopien installiert werden, als Sie erworben haben.

> [!Important]
> Derzeit weist Intune App-Lizenzen des Programms für Volumenlizenzen für Unternehmen (Volume Purchase Program for Business, VPP) Benutzern und nicht Geräten zu. Aus diesem Grund müssen Benutzer zum Installieren der App ihr Apple-ID-Kennwort eingeben.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Verwalten von Apps für iOS-Geräte, die über ein Volumenprogramm erworben wurden
Sie erwerben mehrere Lizenzen für iOS-Apps über das [Programm für Volumenlizenzen für Unternehmen](http://www.apple.com/business/vpp/) oder das [Programm für Volumenlizenzen für Bildungseinrichtungen](http://volume.itunes.apple.com/us/store) (Volume Purchase Program, VPP) von Apple. Dies umfasst das Einrichten eines Apple VPP-Kontos auf der Apple-Website und das Hochladen des Apple VPP-Tokens in Intune.  Anschließend können Sie Ihre Informationen zum Volumenerwerb mit Intune synchronisieren und die Verwendung der im Rahmen des Volumenprogramms erworbenen App verfolgen.

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie beginnen, müssen Sie ein VPP-Token von Apple abrufen und es in Ihr Intune-Konto hochladen. Beachten Sie darüber hinaus die folgenden Informationen:

* Sie können Ihrem Intune-Konto mehrere Token für das Programm für Volumenlizenzen zuordnen.
* Wenn Sie zuvor ein VPP-Token für ein anderes Produkt verwendet haben, müssen Sie für die Verwendung mit Intune ein neues erstellen.
* Jedes Token ist ein Jahr lang gültig.
* Standardmäßig wird Intune zweimal täglich mit dem Apple VPP-Dienst synchronisiert. Eine manuelle Synchronisierung können Sie jederzeit starten.
* Nachdem Sie den VPP-Token in Intune importiert haben, importieren Sie denselben Token in keine andere Geräteverwaltungslösung. Andernfalls kann dies zu einem Verlust von Lizenzzuweisung und Benutzerdatensätzen führen.
* Bevor Sie iOS VPP mit Intune verwenden, entfernen Sie alle vorhandenen, mit anderen Anbietern für das Mobile-Geräte-Management (MDM) erstellten VPP-Benutzerkonten. Aus Sicherheitsgründen werden diese Benutzerkonten in Intune nicht synchronisiert. Intune synchronisiert nur Daten aus dem Apple VPP-Dienst, der von Intune erstellt wurde.
* Sie können keine iOS-VPP-Apps Geräten zuweisen, die mithilfe des Geräteregistrierungsprotokolls (Device Enrollment Protocol, DEP) registriert wurden.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>So können Sie einen Apple VPP-Token abrufen und hochladen

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste** > **Andere** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Apps verwalten** aus.
1.  Wählen Sie in der Workload **Apps verwalten** die Option **Setup** > **iOS-VPP-Token** aus.
2.  Klicken Sie auf dem Blatt mit der Liste der VPP-Token auf **Hinzufügen**.
3.  Geben Sie auf dem Blatt „Neues VPP-Token“ die folgenden Informationen an:
    - **VPP-Tokendatei:** Sofern nicht bereits geschehen, registrieren Sie sich für das Programm für Volumenlizenzen für Unternehmen oder das Programm für Volumenlizenzen für Bildungseinrichtungen. Sobald Sie registriert sind, laden Sie das Apple-VPP-Token für Ihr Konto herunter und wählen es hier aus.
    - **Apple-ID:** Geben Sie die Apple-ID des Kontos ein, das dem Programm für Volumenlizenzen zugeordnet ist.
    - **Typ des VPP-Kontos:** Wählen Sie **Unternehmen** oder **Bildungswesen** aus.
4. Klicken Sie abschließend auf **Hochladen**.

Das Token wird auf dem Blatt mit der Liste der Token angezeigt.


Sie können die von Apple gespeicherten Daten jederzeit mit Intune synchronisieren, indem Sie **Jetzt synchronisieren** wählen.

## <a name="to-assign-a-volume-purchased-app"></a>So weisen Sie per Volumenlizenz erworbene Apps zu

1. Wählen Sie in der Workload **Apps verwalten** die Option **Verwalten** > **Lizenzierte Apps** aus.
2. Wählen Sie auf dem Blatt mit der Liste der Apps die App, die Sie zuweisen möchten, und dann „**...**“ > **Gruppen zuweisen** aus.
3. Wählen Sie auf dem Blatt <*App-Name*> - **Zugewiesene Gruppen** die Option **Verwalten** > **Gruppen zugewiesen** aus.
4. Wählen Sie **Gruppen zuweisen** und dann auf dem Blatt **Gruppen auswählen** die Azure AD-Gruppen aus, denen Sie die App zuweisen möchten.
Sie müssen eine Zuweisungsaktion vom Typ **Erforderlich** auswählen. „Verfügbare“ Installationen werden derzeit nicht unterstützt.
5. Wählen Sie abschließend **Speichern** aus.

Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von Apps](monitor-apps.md).

## <a name="further-information"></a>Weitere Informationen

Wenn Sie die Anwendung als **erforderliche** Installation zuweisen, verwendet jeder Benutzer, der die App installiert, eine Lizenz.

Zum Freigeben einer Lizenz müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Die Lizenz wird freigegeben, wenn die App deinstalliert wird.

Wenn ein Benutzer mit einem geeigneten Gerät erstmals versucht, eine VPP-App zu installieren, wird er aufgefordert, am Programm für Volumenlizenzen (Volume Purchase Program, VPP) von Apple teilzunehmen. Die Teilnahme muss erfolgen, bevor die App-Installation fortgesetzt wird.



<!--HONumber=Feb17_HO2-->

