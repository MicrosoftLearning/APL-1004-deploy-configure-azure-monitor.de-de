---
lab:
  title: 'Übung: Konfigurieren von Warnungen'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Qualifikationsaufgabe

- Erstellen einer Aktionsgruppe, um eine E-Mail zu senden
- Erstellen einer Warnung zur CPU-Auslastung virtueller Computer

## Übungsanweisungen

### Erstellen einer Aktionsgruppe, um eine E-Mail zu senden

1. Geben Sie im Azure-Portal in der Suchleiste **Monitor** ein, und wählen Sie in den Suchergebnissen **Monitor** aus.
1. Klicken Sie im Navigationsmenü auf **Warnungen**.
1. Wählen Sie **Aktionsgruppen** aus.
1. Wählen Sie auf der Seite **Aktionsgruppen** die Option **Erstellen** aus.
1. Konfigurieren Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen einer Aktionsgruppe die folgenden Einstellungen, und wählen Sie dann **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe  | rg-alpha   |
    | Region    | Global  |
    | Aktionsgruppenname | NotifyCPU  |
    | Anzeigename  | NotifyCPU  |

6. Legen Sie auf der Seite **Benachrichtigungen** den Benachrichtigungstyp auf **E-Mail/SMS-Nachricht/Push/VoIP** fest, und legen Sie als Name **NotificationEmail** fest. Wählen Sie **Bearbeiten** (Bleistiftsymbol) aus.
1. Aktivieren Sie unter „E-Mail/SMS-Nachricht/Push/VoIP“ das Kontrollkästchen **E-Mail**, und geben Sie die Adresse **prime@fabrikam.com** ein. Klicken Sie auf **OK**. 
1. Wählen Sie **Überprüfen und erstellen** aus. Wählen Sie **Erstellen** aus.


### Erstellen einer Warnung zur CPU-Auslastung virtueller Computer

1. Geben Sie im Azure-Portal in der Suchleiste **rg-alpha** ein, und wählen Sie in den Suchergebnissen **rg-alpha** aus.
1. Wählen Sie aus der Liste der Elemente in der Ressourcengruppe **Linux-VM2** aus.
1. Wählen Sie auf der Seite **Eigenschaften von Linux-VM2** dit Option **Warnungen** unter **Überwachung** aus.
1. Wählen Sie auf der Seite **Warnungen** die Option **Erstellen** aus, und wählen Sie dann **Warnungsregel** aus.
1. Legen Sie auf der Seite **Bedingung** des Assistenten zum Erstellen einer Warnungsregel als Signalnamen **Percentage CPU** fest. Übernehmen Sie die Standardeinstellung, und wählen Sie **Weiter** aus.
1. Wählen Sie auf der Seite **Aktionen** die Option **Aktionsgruppe auswählen** aus.
1. Wählen Sie auf der Seite **Aktionsgruppen auswählen** die Option **NotifyCPU** und dann **Auswählen** aus.
1. Geben Sie auf der Seite **Details** den Namen der Warnungsregel **HighCPU** ein. Wählen Sie **Überprüfen und erstellen** aus, und wählen Sie dann **Erstellen** aus.

## Bereinigen des Abonnements

Um das Abonnement zu bereinigen, löschen Sie die Ressourcengruppe **rg-alpha** und die Sicherheitsgruppe **AppLogExaminers**.
