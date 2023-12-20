---
lab:
  title: Vorbereiten Ihrer Azure-Umgebung
  module: Guided Project - Deploy and configure Azure Monitor
---

## Vorbereiten Ihres Bring-your-own-Subscription (BYOS)

Bei diesen Labübungen wird davon ausgegangen, dass Sie über globale Administratorberechtigungen für ein Azure-Abonnement verfügen.

1. Geben Sie in der Suchleiste des Azure-Portals **Ressourcengruppen** ein und wählen Sie **Ressourcengruppen** aus der Ergebnisliste aus.
1. Wählen Sie auf der Seite **Ressourcengruppen** die Option **Erstellen** aus.
1. Wählen Sie auf der Seite **Ressourcengruppe erstellen** Ihr Abonnement aus und geben Sie den Namen „rg-alpha“ ein. Legen Sie die Region auf „East US“ fest, wählen Sie **Überprüfen und Erstellen** und dann Erstellen** aus**.

> [!NOTE]
> Bei dieser Übung wird davon ausgegangen, dass Sie sich für die Bereitstellung in der Region „East US“ entscheiden, dies aber auf Wunsch in eine andere Region ändern können. Denken Sie einfach daran, dass Sie jedes Mal, wenn Sie „East US“ in diesen Anweisungen sehen, Sie die Region ersetzen, die Sie ausgewählt haben.

## Erstellen einer Sicherheitsgruppe von App-Protokollprüfern

In dieser Übung erstellen Sie eine Entra ID-Sicherheitsgruppe.

1. Geben Sie in der Azure Portal-Suchleiste Azure Active Directory (oder Entra-ID) aus der Liste der Ergebnisse ein.
1. Wählen Sie auf der Seite **Standardverzeichnis** die Option **Gruppen** aus.
1. Wählen Sie auf der Seite **Gruppen** die Option **Neue Gruppe** aus.
1. Geben Sie auf der Seite **Neue Gruppe** die Werte in der folgenden Tabelle an und wählen Sie **Erstellen** aus.


    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Gruppentyp  | Sicherheit   |
    | Gruppenname  | App-Protokollprüfer   |
    | Gruppenbeschreibung  | App-Protokollprüfer   |


## Bereitstellen und Konfigurieren von WS-VM1

In dieser Übung stellen Sie einen virtuellen Windows Server-Computer bereit und konfigurieren ihn.

1. Suchen Sie im Azure-Portal nach **Virtual Machines** und wählen Sie **Virtual Machines** in den Suchergebnissen aus.
1. Wählen Sie auf der Seite **Virtual Machines** die Option **Erstellen** und dann **Virtueller Azure-Computer** aus.
1. Wählen Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen eines virtuellen Computers die folgenden Einstellungen aus und wählen Sie dann **Überprüfen+ Erstellen** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Subscription  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Name des virtuellen Computers  | WS-VM1   |
    | Region    | USA, Osten  |
    | Verfügbarkeitsoptionen  | Keine Infrastrukturredundanz erforderlich  |
    | Sicherheitstyp | Standard   |
    | Abbildung | Windows Server 2022 Datacenter: Azure Edition – x64 Gen2  |
    | VM-Architektur   | x64  |
    | Größe  | Standard_D4s_v3 – 4 vCPUs, 16 GiB Arbeitsspeicher  |
    | Administratorkonto | Prime  |
    | Kennwort  | [Wählen Sie ein eindeutiges sicheres Kennwort aus] P@ssw0rdP@ssw0rd   |
    | Eingehende Ports | RDP 3389   |

4. Überprüfen Sie die Einstellungen, und wählen Sie **Erstellen** aus.
1. Warten Sie, bis die Bereitstellung abgeschlossen ist. Wählen Sie nach Abschluss der Bereitstellung die Option **Zu Ressource wechseln** aus.
1. Wählen Sie auf der Seite **WS-VM1-Eigenschaften** die Option **Netzwerk** aus.
1. Wählen Sie auf der Seite **Netzwerk** die RDP-Regel aus. 
1. Ändern Sie im RDP-Regelbereich die Quelle in „Meine IP-Adresse“ und wählen Sie **Speichern** aus.

    Dadurch werden eingehende RDP-Verbindungen auf die aktuell verwendete IP-Adresse beschränkt.

9. Wählen Sie auf der Seite **Netzwerk** die Option **Regel für eingehende Ports hinzufügen** aus.
1. Konfigurieren Sie auf der Seite **Sicherheitsregel für eingehenden Datenverkehr hinzufügen** die folgenden Einstellungen und wählen Sie **Hinzufügen**.

    | Eigenschaft | Value    |
    |:---------|:---------|
    | `Source`  | Alle  |
    | Source port ranges    | *   |
    | Destination  | Any   |
    | Dienst   | HTTP  |
    | Aktion    | Allow  |
    | Priorität  | 310   |
    | Name  | AllowAnyHTTPInbound  |

11. Wählen Sie auf der Seite **WS-VM1** die Option**Verbinden** aus.
1. Wählen Sie unter „Native RDP“ die Option **Auswählen** aus.
1. Wählen Sie auf der Seite **Native RDP** die Option **RDP-Datei herunterladen** aus und öffnen Sie dann die Datei. Wenn die RDP-Datei geöffnet wird, öffnet sich das Dialogfeld „Remotedesktopverbindung“.
1. Klicken Sie im Dialogfeld **Windows-Sicherheit** erst auf **Weitere Optionen** und dann auf „Anderes Konto verwenden“.
1. Geben Sie den Benutzernamen „.\prime“ und als Kennwort das sichere Kennwort ein, das Sie in Schritt 3 ausgewählt haben, und wählen Sie **OK** aus.
1. Wenn Sie sich bei dem virtuellen Windows Server-Computer angemeldet haben, klicken Sie mit der rechten Maustaste auf den **Starthinweis**, und wählen Sie dann **Windows PowerShell (Admin)** aus.
1. Geben Sie in der Eingabeaufforderung den folgenden Befehl ein und drücken Sie die **Eingabetaste**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Wenn die Installation abgeschlossen ist, führen Sie den folgenden Befehl aus, um zum Stammverzeichnis des Webservers zu wechseln.
    cd c:\inetpub\wwwroot\
1. Führen Sie den folgenden Befehl aus.
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html -OutFile index.html


## Bereitstellen und Konfigurieren von LX-VM2

In dieser Übung erstellen und konfigurieren Sie einen virtuellen Linux-Computer.

1. Suchen Sie im Azure-Portal nach **Virtual Machines** und wählen Sie **Virtual Machines** in den Suchergebnissen aus.
1. Wählen Sie auf der Seite **Virtual Machines** die Option **Erstellen** und dann **Virtueller Azure-Computer** aus.
1. Wählen Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen eines virtuellen Computers die folgenden Einstellungen aus und wählen Sie dann **Überprüfen+ Erstellen** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Subscription  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Name des virtuellen Computers  | Linux-VM2   |
    | Region    | USA, Osten  |
    | Verfügbarkeitsoptionen  | Keine Infrastrukturredundanz erforderlich  |
    | Sicherheitstyp | Standard   |
    | Abbildung | Ubuntu Server 20.04 LTS – x64 Gen2  |
    | VM-Architektur   | x64  |
    | Größe  | Standard_D2s_v3 – 2 vCPUs, 8 GiB Arbeitsspeicher  |
    | Authentifizierungstyp   | Kennwort  |
    | Username  | Prime   |
    | Kennwort  | [Wählen Sie ein eindeutiges sicheres Kennwort aus] P@ssw0rdP@ssw0rd   |
    | Öffentliche Eingangsports  | Keine   |

4. Überprüfen Sie die Informationen und wählen Sie **Erstellen** aus.
1. Öffnen Sie nach der Bereitstellung der VM die Seite **VM-Eigenschaften** und wählen Sie **Erweiterungen + Anwendungen** unter **Einstellungen** aus.
1. Wählen Sie **Hinzufügen** und dann **Network Watcher-Agent für Linux** aus. Wählen Sie **Weiter** und dann **Überprüfen und Erstellen** aus. Wählen Sie **Erstellen** aus.
1. Konfigurieren Sie NetworkWatcherExtension und die OmsAgentForLinux-Erweiterung so, dass sie automatisch aktualisiert werden.


## Bereitstellen einer Web-App mit einem SQL-Datenbank

1. Stellen Sie sicher, dass Sie beim Azure-Portal angemeldet sind.
1. Öffnen Sie im Browser eine neue Registerkarte und navigieren Sie zu https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database.
1. Wählen Sie auf der GitHub-Seite **Bereitstellen in Azure** aus.
1. Es wird ein neuer Tab geöffnet. Melden Sie sich bei Azure bei Bedarf erneut mit dem Konto an, das über globale Administratorrechte verfügt.
1. Wählen Sie auf der Seite **Vorlage bearbeiten** die Option **Grundlagen** aus.
1. Löschen Sie im Vorlagen-Editor den Inhalt der Zeilen 158 bis einschließlich 174, und löschen Sie as „,“ in Zeile 157. Wählen Sie **Speichern** aus.
1. Geben Sie auf der Seite **Grundlagen** die folgenden Informationen ein und wählen Sie anschließend **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Subscription  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | SKU-Name  | F1  |
    | SKU-Kapazität  | 1   |
    | Anmeldename des SQL-Administrators   | Prime  |
    | Anmeldekennwort des SQL-Administrators  | [Wählen Sie ein eindeutiges sicheres Kennwort aus] P@ssw0rdP@ssw0rd   |

8. Überprüfen Sie die angezeigten Informationen und wählen Sie **Erstellen** aus.
1. Wählen Sie nach Abschluss der Bereitstellung die Option **Zu Ressourcengruppe wechseln**.

## Bereitstellen einer Linux-Web-App

1. Stellen Sie sicher, dass Sie beim Azure-Portal angemeldet sind.
1. Öffnen Sie im Browser eine neue Browser-Registerkarte, und navigieren Sie zu https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/.
1. Wählen Sie auf der GitHub-Seite **Bereitstellen in Azure** aus.
1. Geben Sie auf der Seite **Grundlagen** die folgenden Informationen ein und wählen Sie anschließend **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Subscription  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | Name der Web-App  | AzureLinuxAppWXYZ (Zuweisen einer Zufallszahl zu den letzten vier Zeichen des Namens)  |
    | Sku   | S1   |
    | Linux Fx-Version  | PHP|7.4  |

5. Überprüfen Sie die Informationen und wählen Sie **Erstellen** aus.
