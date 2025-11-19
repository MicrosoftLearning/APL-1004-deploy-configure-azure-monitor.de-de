---
lab:
  title: 'Übung: Konfigurieren der Überwachung für Computedienste'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Qualifikationsaufgaben

- Erstellen eines Datensammlungsendpunkts
- Erstellen einer Datensammlungsregel
- Hinzufügen einer IIS-Protokollsammlung zu einer vorhandenen Datensammlungsregel
- Konfigurieren des Netzwerkverbindungsmonitors für einen virtuellen Linux-IaaS-Computer

## Übungsanweisungen

### Erstellen eines Datensammlungsendpunkts

1. Geben Sie in die Suchleiste im Azure-Portal **Monitor** ein und wählen Sie dann **Monitor** in der Ergebnisliste aus.
1. Wählen Sie auf der Seite **Monitor** unter **Einstellungen**  die Option **Datensammlungsendpunkte** aus.
1. Wählen Sie auf der Seite **Datensammlungsendpunkte** die Option **Erstellen** aus.
1. Geben Sie auf der Seite zum Erstellen von Datensammlungsendpunkten die folgenden Einstellungen an, und wählen Sie dann „Überprüfen und erstellen“ aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Endpunktname  | IaaSVMCollectionEndpoint   |
    | Abonnement  | Ihr Abonnement  |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |

5. Überprüfen Sie die Einstellungen und wählen Sie **Erstellen** aus.

### Erstellen einer Datensammlungsregel

1. Geben Sie im Azure-Portal in der Suchleiste **Monitor** ein, und wählen Sie in den Suchergebnissen **Monitor** aus.
1. Wählen Sie auf der Seite **Monitor** unter **Einstellungen** die Option für **Datensammlungsregeln** aus.
1. Wählen Sie auf der Seite mit den **Datensammlungsregeln** die Option **Erstellen** aus.
1. Konfigurieren Sie auf der Seite **einer Datensammlungsregel erstellen** die folgenden Einstellungen, und wählen Sie **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Regelname  | WinVMDCR   |
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | Plattformtyp | Windows  |
    | Datensammlungsendpunkt  | IaaSVMCollectionEndpoint   |

5. Klicken Sie auf der Seite **Ressourcen** auf **Ressourcen hinzufügen**.
1. Aktivieren Sie auf der Seite **Bereich auswählen** das Kontrollkästchen **WS-VM1**, und wählen Sie **Übernehmen** aus.
1. Wählen Sie auf der Seite **einer Datensammlungsregel erstellen** die Option **Weiter** aus.
1. Wählen Sie auf der Seite **Sammeln und liefern** die Option **Datenquelle hinzufügen** aus.
1. Wählen Sie auf der Seite **Datenquelle hinzufügen** die Option **Windows-Ereignisprotokolle** aus. Aktivieren Sie in der Kategorie **Anwendung** die Kategorien **Kritisch** und **Fehler**. Wählen Sie in der Kategorie **Sicherheit** die Kategorie **Überwachungsfehler** aus. Aktivieren Sie in der Kategorie **System** die Kategorien **Kritisch** und **Fehler**. 
1. Wählen Sie **Weiter** aus.
1. Konfigurieren Sie auf der Seite **Ziel** die folgenden Einstellungen:

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Zieltyp  | Azure Monitor-Protokolle   |
    | Abonnement  | Ihr Abonnement   |
    | Konto oder Namespace  | LogAnalytics1  |

12. Wählen Sie **Datenquelle hinzufügen** aus.
1. Wählen Sie **Überprüfen und erstellen** aus, und wählen Sie dann **Erstellen** aus.


### Hinzufügen einer IIS-Protokollsammlung zu einer vorhandenen Datensammlungsregel

1. Geben Sie im Azure-Portal in der Suchleiste **Monitor** ein, und wählen Sie in den Suchergebnissen **Monitor** aus.
1. Wählen Sie auf der Seite **Monitor** unter **Einstellungen** die Option für **Datensammlungsregeln** aus.
1. Wählen Sie die in „rg-alpha“ die Regel **WinVMDRC** aus.
1. Wählen Sie unter **Konfiguration** die Option **Datenquellen** aus.
1. Wählen Sie auf der Seite **Datenquellen** die Option **Hinzufügen** aus.
1. Wählen Sie auf der Seite **Datenquelle hinzufügen** die Option **IIS-Protokolle** aus.
1. Wählen Sie **Weiter** aus.
1. Konfigurieren Sie auf der Seite **Ziel** die folgenden Einstellungen:

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Zieltyp  | Azure Monitor-Protokolle   |
    | Abonnement  | Ihr Abonnement   |
    | Konto oder Namespace  | LogAnalytics1  |

9. Wählen Sie **Datenquelle hinzufügen** aus.

### Konfigurieren des Netzwerkverbindungsmonitors für einen virtuellen Linux-IaaS-Computer

1. Geben Sie im Azure-Portal in der Suchleiste **Network Watcher** ein, und wählen Sie in den Suchergebnissen **Network Watcher** aus.
1. Wählen Sie unter **Überwachung** die Option **Verbindungsmonitor** aus.
1. Wählen Sie auf der Seite **Verbindungsmonitor** die Option **Erstellen** aus.
1. Geben Sie auf der Seite **Grundlagen** des **Assistenten zum Erstellen des Verbindungsmonitors** die folgenden Informationen an und wählen Sie **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Name des Verbindungsmonitors  | LinuxVMPubIP   |
    | Abonnement  | Ihr Abonnement   |
    | Region    | USA (Ost) 2 |
    | Arbeitsbereich | LogAnalytics1  |

5. Geben Sie auf der Seite **Testgruppendetails hinzufügen** den Namen **LinuxIPTest** ein, und wählen Sie **Quellen hinzufügen** aus.
1. Wählen Sie auf der Seite **Quellen hinzufügen** die Option **Azure-Endpunkte** aus, und legen Sie als Typ **Virtuelle Computer** fest. Wählen Sie **Subnetz** aus, und aktivieren Sie das Kontrollkästchen **Linux-VM**. Wählen Sie **Endpunkte hinzufügen** aus.
1. Wählen Sie **Testkonfiguration hinzufügen** aus. 
1. Geben Sie auf der Seite **Testkonfiguration hinzufügen** den Namen **DefaultHTTP** ein, und wählen Sie dann **Testkonfiguration hinzufügen** aus.
1. Wählen Sie **Ziele hinzufügen** aus. Wählen Sie **Azure-Endpunkte** aus, und legen Sie als Typ **Virtuelle Computer** fest. Wählen Sie **Subnetz** aus, und aktivieren Sie dann das Kontrollkästchen **WS-VM1**. Wählen Sie **Endpunkte hinzufügen** aus.
1. Wählen Sie **Testgruppen hinzufügen** aus.
1. Wählen Sie **Überprüfen und erstellen** aus, und wählen Sie dann **Erstellen** aus.
