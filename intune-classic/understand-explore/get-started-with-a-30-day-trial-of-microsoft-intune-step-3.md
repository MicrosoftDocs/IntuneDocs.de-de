---
title: "Kostenlose Testversion zum Erstellen von Gruppen zum Organisieren von Benutzern und Geräten"
description: "So erstellen Sie Geräte- und Benutzergruppen, wenn Sie sich für eine kostenlose 30-tägige Evaluierungsversion von Microsoft Intune registrieren."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 084cc155a64a58582e3008df10e86c1e5266054d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2017
---
# <a name="create-groups-to-organize-evaluation-subscription-users-and-devices"></a>Erstellen von Gruppen zum Organisieren von Benutzern und Geräten für das Evaluierungsabonnement

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Mit Gruppen erhalten Sie in Intune maximale Flexibilität beim Verwalten Ihrer Geräte und Benutzer. Sie können Gruppen einrichten, die Ihren organisatorischen Anforderungen (z. B. nach geografischem Standort, nach Abteilung oder nach Hardwareeigenschaften) entsprechen und diese verwenden, um verschiedene anstehende Verwaltungsaufgaben auszuführen, die von der Festlegung von Richtlinien für eine Gruppe von Benutzern bis zur Bereitstellung von Anwendungen auf einer Reihe von Geräten reichen.

## <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe
Verwenden Sie Gerätegruppen zum Bereitstellen von Software und Updates sowie zum Konfigurieren von Richtlinien für Microsoft Intune-Agent-Einstellungen und Windows-Firewalleinstellungen. Richten Sie z. B. eine Gruppe "Meine Testgeräte" mithilfe der folgenden Schritte ein:

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Gruppen** &gt; **Übersicht** &gt; **Gruppe erstellen** aus.

2.  Geben Sie unter **Gruppenname** „Meine Testgeräte“ ein, wählen Sie in der übergeordneten Gruppenliste **Alle Geräte**, und anschließend **Weiter** aus.

3.  Wählen Sie **Alle Geräte** auf der Seite **Mitgliedschaftskriterien definieren** aus, um anzugeben, dass die Gruppe sowohl mobile Geräte als auch Computer enthält.

4.  Klicken Sie auf der Seite **Direkte Mitgliedschaft definieren** auf **Weiter**. Hätten Sie zuvor eine Gruppe erstellt, die nicht alle Geräte enthält, und wollten Sie dieser neuen Gruppe nun bestimmte Geräte hinzufügen, dann können Sie dies an dieser Stelle tun.

5.  Überprüfen Sie auf der Seite **Zusammenfassung** die Aktionen, die ausgeführt werden, und wählen Sie anschließend **Fertig stellen** aus.

Sie finden die neue Gruppe in der Liste **Gruppen** im Arbeitsbereich **Gruppen** unter **Alle Geräte**. Hier können Sie die Gruppe auch bearbeiten oder löschen.

## <a name="create-a-user-group"></a>Erstellen einer Benutzergruppe
Verwenden Sie Benutzergruppen, um Software- und Geräterichtlinien bereitzustellen. Richten Sie z. B. eine Gruppe "Meine Testbenutzer" mithilfe der folgenden Schritte ein:

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Gruppen** &gt; **Übersicht** &gt; **Gruppe erstellen** aus.

2.  Geben Sie für **Gruppenname** „Meine Testbenutzer“ ein, wählen Sie in der übergeordneten Gruppenliste **Alle Benutzer**, und anschließend **Weiter** aus.

3.  Setzen Sie auf der Seite **Mitgliedschaftskriterien definieren** die Option **Gruppenmitgliedschaft starten mit** auf **Alle Benutzer in der übergeordneten Gruppe**.

4.  Klicken Sie neben **Mitglieder dieser Sicherheitsgruppen ausschließen** auf **Durchsuchen** und anschließend auf **Unternehmensadministrator**. Durch diesen Ausschluss können Sie die Gruppe "Meine Testbenutzer" verwalten, ohne dass das Konto "Unternehmensadministrator" (auch als Mandantenadministrator bezeichnet) davon betroffen ist.

5.  Klicken Sie auf der Seite **Direkte Mitgliedschaft definieren** auf **Weiter**. Hier brauchen Sie nichts zu tun, denn die Gruppe „Testbenutzer“ soll alle Benutzer außer dem Unternehmensadministrator einschließen.

6.  Überprüfen Sie auf der Seite **Zusammenfassung** die Aktionen, die ausgeführt werden, und wählen Sie anschließend **Fertig stellen** aus.

Sie finden die neue Gruppe in der Liste **Gruppen** im Arbeitsbereich **Gruppen** unter **Alle Benutzer**. Hier können Sie die Gruppe auch bearbeiten oder löschen.

Weitere Informationen zum Verwenden von Gruppen finden Sie unter [Erstellen von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune](/intune-classic/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="next-steps"></a>Nächste Schritte
[Erstellen von Richtlinien](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  