---
lab:
  title: 'Übung: Überwachen von Web-Apps'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Qualifikationsaufgabe

- Aktivieren von Application Insights
- Deaktivieren der Protokollierung für den .NET-Core-Momentaufnahmedebugger
- Konfigurieren der Web-App-HTTP-Protokolle, die in einen Log Analytics-Arbeitsbereich geschrieben werden sollen
- Konfigurieren der SQL Insights-Daten, die in einen Log Analytics-Arbeitsbereich geschrieben werden sollen
- Aktivieren der Nachverfolgung von Datei- und Konfigurationsänderungen für Web-Apps

## Übungsanweisungen

### Aktivieren von Application Insights

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe die Option für **App Services für die Web-App mit einer SQL-Datenbank**.
1. Wählen Sie unter **Einstellungen** die Option **Application Insights** aus.
1. Wählen Sie auf der Seite **Application Insights** die Option **Application Insights aktivieren** aus.
1. Stellen Sie auf der Seite **Application Insights** sicher, dass **Neue Ressource erstellen** ausgewählt ist und der Log Analytics-Arbeitsbereich auf **LogAnalytics1** festgelegt ist. Wählen Sie dann **Übernehmen** aus.
1. Wählen Sie im Dialogfeld **Überwachungseinstellungen anwenden** die Option **Ja** aus.

### Deaktivieren der Protokollierung für den .NET-Core-Momentaufnahmedebugger

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe die Option für **App Services für die Web-App mit einer SQL-Datenbank**.
1. Wählen Sie unter **Einstellungen** die Option **Application Insights** aus.
1. Wählen Sie unter **Anwendung instrumentieren** die Option **.NET Core** aus, und legen Sie dann die Einstellung für den Momentaufnahmedebugger auf **Aus** fest. Wählen Sie **Übernehmen** aus.
1. Wählen Sie im Dialogfeld **Überwachungseinstellungen anwenden** Einstellungen **Ja** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Name der Diagnoseeinstellung  | httplogs   |
    | Kategorien    | HTTP-Protokolle  |
    | Zieldetails   | An den Log Analytics-Arbeitsbereich senden  |
    | Abonnement  | Ihr Abonnement  |
    | Log Analytics-Arbeitsbereich   | LogAnalytics1   |

### Konfigurieren der Web-App-HTTP-Protokolle, die in einen Log Analytics-Arbeitsbereich geschrieben werden sollen

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe die Option für **App Services für die Web-App mit einer SQL-Datenbank**.
1. Wählen Sie unter **Überwachen** die Option **Diagnoseeinstellungen** aus.
1. Wählen Sie auf der Seite **Diagnoseeinstellungen** die Option **+ Diagnoseeinstellung hinzufügen** aus.
1. Wählen Sie auf der Seite **Diagnoseeinstellungen** Folgendes aus, und wählen Sie dann **Speichern** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Name der Diagnoseeinstellung  | httplogs   |
    | Kategorien    | HTTP-Protokolle  |
    | Zieldetails   | An den Log Analytics-Arbeitsbereich senden  |
    | Abonnement  | Ihr Abonnement  |
    | Log Analytics-Arbeitsbereich   | LogAnalytics1   |

### Konfigurieren der SQL Insights-Daten, die in einen Log Analytics-Arbeitsbereich geschrieben werden sollen

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe die SQL-Beispieldatenbank aus.
1. Wählen Sie unter **Überwachen** die Option **Diagnoseeinstellungen** aus.
1. Wählen Sie auf der Seite **Diagnoseeinstellungen** die Option **Diagnoseeinstellung hinzufügen** aus.
1. Geben Sie auf der Seite **Diagnoseeinstellungen** die folgenden Informationen an, und wählen Sie dann **Speichern** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Name der Diagnoseeinstellung  | InsightLogAnalytics   |
    | Kategorien    | SQL Insights  |
    | Zieldetails   | An den Log Analytics-Arbeitsbereich senden  |
    | Abonnement  | Ihr Abonnement  |
    | Log Analytics-Arbeitsbereich   | LogAnalytics1   |

### Aktivieren der Nachverfolgung von Datei- und Konfigurationsänderungen für Web-Apps

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe „AzureLinuxAppWXYZ-webapp“ aus.
1. Wählen Sie **Diagnose und Problembehandlung** aus.
1. Geben Sie im Suchdialogfeld **Anwendungsänderungen** ein.
1. Wählen Sie auf der Seite **Änderungsanalyse** die Option **Konfigurieren** aus.
1. Stellen Sie auf der Seite zum **Aktivieren der Nachverfolgung von Datei- und Konfigurationsänderungen** den Schieberegler für den Status auf **Ein**, und wählen Sie dann **Speichern** aus.
