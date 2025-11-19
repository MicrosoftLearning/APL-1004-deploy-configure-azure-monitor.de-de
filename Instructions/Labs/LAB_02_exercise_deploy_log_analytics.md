---
lab:
  title: 'Übung: Bereitstellen von Log Analytics'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Qualifikationsaufgaben

- Erstellen eines Log Analytics-Arbeitsbereichs
- Konfigurieren der Datenaufbewahrungs- und Archivierungsrichtlinien für Log Analytics
- Aktivieren des Zugriffs auf einen Log Analytics-Arbeitsbereich

## Übungsanweisungen

### Erstellen eines Log Analytics-Arbeitsbereichs

1. Geben Sie im Azure-Portal in der Suchleiste **Log Analytics** ein, und wählen Sie in den Suchergebnissen **Log Analytics-Arbeitsbereiche** aus.
1. Wählen Sie auf der Seite **Log Analytics-Arbeitsbereiche** die Option **Erstellen** aus.
1. Geben Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen eines Log Analytics-Arbeitsbereichs die folgenden Informationen an, und wählen Sie dann **Überprüfen und erstellen** aus.
   
    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Name  | LogAnalytics1  |
    | Region    | USA, Osten  |

4. Überprüfen Sie die Informationen, und wählen Sie **Erstellen** aus.

### Installieren und Konfigurieren des Log Analytics-Agents auf Linux-VM2

1. Geben Sie im Azure-Portal in der Suchleiste **Virtuelle Computer** ein, und wählen Sie in den Suchergebnissen **Virtuelle Computer** aus.
1. Wählen Sie auf der Seite **Virtual Machines** die Option **Linux-VM2** aus.
1. Wählen Sie auf der Seite **Linux-VM2** unter **Einstellungen** **Erweiterungen + Anwendungen** aus.
1. Wählen Sie **Hinzufügen** und dann den **Log Analytics-Agent für Linux** (auch als „OmsAgentForLinux“ bezeichnet) aus. Wählen Sie **Weiter** aus.
1. Navigieren Sie für die Arbeitsbereichs-ID und den Arbeitsbereichsschlüssel in einer separaten Browserregisterkarte oder einem separaten Browserfenster zu **LogAnalytics1 > Einstellungen > Agents**.
1. Kopieren Sie die **Arbeitsbereichs-ID** und den **Primärschlüssel** aus dem Arbeitsbereich „LogAnalytics1“.
1. Kehren Sie zur Installationsseite der Linux-VM2-Erweiterung zurück und fügen Sie die Arbeitsbereichs-ID und den Arbeitsbereichsschlüssel ein. Wählen Sie **Überprüfen und Erstellen** und dann **Erstellen** aus.
1. Wählen Sie nach Abschluss der Installation auf der Seite **Linux-VM2 Erweiterungen + Anwendungen** die Option **AzureNetworkWatcherExtension** aus.
1. Stellen Sie auf der Seite mit den Erweiterungsdetails sicher, dass **Automatisches Upgrade aktivieren** auf **Ja** festgelegt ist. Wenn nicht, aktivieren Sie die Option und wählen Sie **Speichern** aus.
1. Kehren Sie zur Seite **Erweiterungen + Anwendungen** zurück und wählen Sie die Erweiterung **OmsAgentForLinux** aus.
1. Stellen Sie auf der Seite mit den Erweiterungsdetails sicher, dass **Automatisches Upgrade aktivieren** auf **Ja** festgelegt ist. Wenn nicht, aktivieren Sie die Option und wählen Sie **Speichern** aus.

### Konfigurieren der Datenaufbewahrungs- und Archivierungsrichtlinien für Log Analytics

1. Geben Sie im Azure-Portal in der Suchleiste **Log Analytics** ein, und wählen Sie in den Suchergebnissen **Log Analytics-Arbeitsbereiche** aus.
1. Wählen Sie auf der Seite **Log Analytics-Arbeitsbereiche** die Option **LogAnalytics1** aus.
1. Wählen Sie auf der Seite **Log Analytics-Arbeitsbereich** für LogAnalytics1 die Option **Nutzung und geschätzte Kosten** aus.
1. Wählen Sie **Datenaufbewahrung** aus, und legen Sie mit dem Schieberegler 60 Tage fest. Wählen Sie **OK** aus.
1. Wählen Sie auf der Seite **Log Analytics-Arbeitsbereich** für LogAnalytics1 die Option **Nutzung und geschätzte Kosten** aus.
1. Wählen Sie **Obergrenze pro Tag** aus. Wählen Sie **Ein** aus. Legen Sie die Obergrenze pro Tag auf 10 GB fest, und wählen Sie **OK** aus.

### Aktivieren des Zugriffs auf einen Log Analytics-Arbeitsbereich

1. Geben Sie im Azure-Portal in der Suchleiste **Log Analytics** ein, und wählen Sie in den Suchergebnissen **Log Analytics-Arbeitsbereiche** aus.
1. Wählen Sie auf der Seite **Log Analytics-Arbeitsbereiche** die Option **LogAnalytics1** aus.
1. Wählen Sie **Zugriffssteuerung (IAM)** aus.
1. Wählen Sie **Hinzufügen** und dann **Rollenzuweisung hinzufügen** aus.
1. Wählen Sie in der Liste der Rollen **Log Analytics-Leser** aus, und wählen Sie dann **Weiter**.
1. Wählen Sie auf der Seite **Mitglieder** die Option **Mitglieder auswählen** und dann die Sicherheitsgruppe „AppLogExaminers“ aus. **Wählen Sie „Auswählen“ aus**.
1. Wählen Sie im Bereich **Mitglieder** die Option **Überprüfen und zuweisen** aus.
