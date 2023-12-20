---
lab:
  title: 'Übung: Konfigurieren der Überwachung für Computedienste'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Qualifikationsaufgabe

- Erstellen eines Datensammlungsendpunkts
- Erstellen einer Datensammlungsregel
- Hinzufügen einer vorhandenen Datensammlungsregel zu einer IIS-Protokollerfassung
- Konfigurieren des Netzwerkverbindungsmonitor für einen virtuellen Linux IaaS-Computer

## Übungsanweisungen

### Erstellen eines Datensammlungsendpunkts

1. Geben Sie in die Suchleiste im Azure-Portal **Monitor** ein und wählen Sie dann **Monitor** in der Ergebnisliste aus.
1. Wählen Sie auf der Seite **Monitor** unter **Einstellungen**  die Option **Datensammlungsendpunkte** aus.
1. Wählen Sie auf der Seite **Datensammlungsendpunkte** die Option **Erstellen** aus.
1. Geben Sie auf der Seite „Datensammlungsendpunkt erstellen“ die folgenden Einstellungen ein, und wählen Sie dann „Überprüfen + Erstellen“ aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Endpunktname  | IaaSVMCollectionEndpoint   |
    | Subscription  | Ihr Abonnement  |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |

5. Überprüfen Sie die Einstellungen und wählen Sie **Erstellen** aus.

### Erstellen einer Datensammlungsregel

1. Geben Sie in die Suchleiste im Azure-Portal **Monitor** ein und wählen Sie dann **Monitor** in der Ergebnisliste aus.
1. Wählen Sie auf Seite **Monitor** unter **Einstellungen** die Option **Datensammlungsregeln** aus.
1. Wählen Sie auf der Seite **Datensammlungsregeln** die Option **Erstellen** aus.
1. Konfigurieren Sie auf der Seite **Datensammlungsregel erstellen** die folgenden Einstellungen und wählen Sie **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Regelname  | WinVMDCR   |
    | Subscription  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | Plattformtyp | Windows  |
    | Datensammlungsendpunkt  | IaaSVMCollectionEndpoint   |

5. Wählen Sie auf der Seite **Ressourcen** die Option **Ressourcen hinzufügen** aus.
1. Aktivieren Sie auf der Seite **Bereich auswählen** das Kontrollkästchen **WS-VM1** und wählen Sie **Übernehmen** aus.
1. Wählen Sie auf der **Datensammlungsregel erstellen** die Option **Weiter** aus.
1. Wählen Sie auf der Registerkarte **Sammeln und Liefern** die Option **Datenquelle hinzufügen** aus.
1. Wählen Sie auf der Seite **Datenquelle hinzufügen** die Option **Windows-Ereignisprotokolle** aus. Aktivieren Sie in der Kategorie **Anwendung** die Kategorien **Kritisch** und **Fehler**. Wählen Sie in der Kategorie **Sicherheit** die Kategorie **Überwachungsfehler** aus. Aktivieren Sie in der Kategorie **System** die Kategorien **Kritisch** und **Fehler**. 
1. Wählen Sie **Weiter** aus.
1. Konfigurieren Sie auf der Seite **Ziel** die folgenden Einstellungen:

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Zieltyp  | Azure Monitor-Protokolle   |
    | Subscription  | Ihr Abonnement   |
    | Konto oder Namespace  | LogAnalytics1  |

12. Wählen Sie eine **Datenquelle** aus.
1. Wählen Sie **Überprüfen + Erstellen** und dann **Erstellen** aus.


### Hinzufügen einer vorhandenen Datensammlungsregel zu einer IIS-Protokollerfassung

1. Geben Sie in die Suchleiste im Azure-Portal **Monitor** ein und wählen Sie dann **Monitor** in der Ergebnisliste aus.
1. Wählen Sie auf Seite **Monitor** unter **Einstellungen** die Option **Datensammlungsregeln** aus.
1. Wählen Sie die Regel **WinVMDRC** in rg-alpha aus.
1. Wählen Sie unter **Konfiguration** die Option **Datenquellen** aus.
1. Wählen Sie auf der Seite **Datenquellen** die Option **Hinzufügen** aus.
1. Wählen Sie auf der **Datenquelle hinzufügen** die Option **IIS-Protokolle** aus.
1. Wählen Sie **Weiter** aus.
1. Konfigurieren Sie auf der Seite **Ziel** die folgenden Einstellungen:

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Zieltyp  | Azure Monitor-Protokolle   |
    | Subscription  | Ihr Abonnement   |
    | Konto oder Namespace  | LogAnalytics1  |

9. Wählen Sie eine **Datenquelle** aus.

### Konfigurieren des Netzwerkverbindungsmonitor für einen virtuellen Linux IaaS-Computer

1. Geben Sie in der Suchleiste des Azure-Portals **Network Watcher** ein und wählen Sie **Network Watcher** aus der Liste der Ergebnisse aus.
1. Wählen Sie unter **Monitor** die Option **Verbindungsmonitor** aus.
1. Wählen Sie auf der Seite **Verbindungsmonitor** die Option **Erstellen** aus.
1. Geben Sie auf der Seite **Grundlagen** des **Assistenten zum Erstellen des Verbindungsmonitors** die folgenden Informationen an und wählen Sie **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Name des Verbindungsmonitors  | LinuxVMPubIP   |
    | Subscription  | Ihr Abonnement   |
    | Region    | USA, Osten  |
    | Arbeitsbereich | LogAnalytics1  |

5. Geben Sie auf der Seite **Testgruppendetails hinzufügen** den Namen **LinuxIPTest** ein und wählen Sie **Quellen hinzufügen** aus.
1. Wählen Sie auf der Seite **Quellen hinzufügen** die Option **Azure-Endpunkte** aus und legen Sie den Typ auf **Virtual Machines** fest. Wählen Sie **Subnetz** aus, und aktivieren Sie dann das Kontrollkästchen **Linux-VM**. Wählen Sie **Endpunkte hinzufügen** aus.
1. Wählen Sie **Testkonfiguration hinzufügen** aus. 
1. Geben Sie auf der Seite **Testkonfiguration hinzufügen** den Namen **DefaultHTTP** ein und wählen Sie dann **Testkonfiguration hinzufügen** aus.
1. Wählen Sie **Ziele hinzufügen** aus. Wählen Sie **Azure-Endpunkte** aus, und legen Sie den Typ auf **Virtual Machines** fest. Wählen Sie **Subnetz** aus, und aktivieren Sie dann das Kontrollkästchen **WS-VM1**. Wählen Sie **Endpunkte hinzufügen** aus.
1. Wählen Sie **Testgruppe hinzufügen** aus.
1. Wählen Sie **Überprüfen + Erstellen** und dann **Erstellen** aus.
