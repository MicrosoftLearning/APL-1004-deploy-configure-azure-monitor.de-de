---
lab:
  title: Vorbereiten Ihrer Azure-Umgebung
  module: Guided Project - Deploy and configure Azure Monitor
---

## Vorbereiten von BYOS (Bring-your-own-Subscription)

Bei diesen Lab-Übungen wird davon ausgegangen, dass Sie über globale Administratorberechtigungen für ein Azure-Abonnement verfügen.

1. Geben Sie im Azure-Portal in der Suchleiste **Ressourcengruppen** ein, und wählen Sie in den Suchergebnissen **Ressourcengruppen** aus.
1. Wählen Sie auf der Seite **Ressourcengruppen** die Option **Erstellen** aus.
1. Wählen Sie auf der Seite **Ressourcengruppe erstellen** Ihr Abonnement aus, und geben Sie den Namen „rg-alpha“ ein. Legen Sie die Region auf „USA, Osten“ fest, wählen Sie **Überprüfen + erstellen** und dann **Erstellen** aus.

> [!NOTE]
> Bei diesen Übungen wird davon ausgegangen, dass Sie sich für die Bereitstellung in der Region „USA, Osten“ entscheiden. Sie können jedoch auch eine andere gewünschte Region auswählen. Vergessen Sie dann jedoch nicht, immer die von Ihnen ausgewählte Region anzugeben, wenn in diesen Anweisungen die Region „USA, Osten“ aufgeführt wird.

## Erstellen der Sicherheitsgruppe „AppLogExaminers“

In dieser Übung erstellen Sie eine Entra ID-Sicherheitsgruppe.

1. Geben Sie im Azure-Portal in der Suchleiste „Azure Active Directory“ (oder „Entra-ID“) ein, und wählen Sie in der Ergebnisliste „Azure Active Directory“ (oder „Entra-ID“) aus.
1. Wählen Sie auf der Seite **Standardverzeichnis** die Option **Gruppen** aus.
1. Wählen Sie auf der Seite **Gruppen** die Option **Neue Gruppe** aus.
1. Geben Sie auf der Seite **Neue Gruppe** die Werte in der folgenden Tabelle an, und wählen Sie **Erstellen** aus.


    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Gruppentyp  | Sicherheit   |
    | Gruppenname  | AppLogExaminers   |
    | Gruppenbeschreibung  | AppLogExaminers   |


## Bereitstellen und Konfigurieren von WS-VM1

In dieser Übung stellen Sie einen virtuellen Windows Server-Computer bereit und konfigurieren ihn.

1. Geben Sie im Azure-Portal in der Suchleiste **Virtuelle Computer** ein, und wählen Sie in den Suchergebnissen **Virtuelle Computer** aus.
1. Wählen Sie auf der Seite **Virtuelle Computer** die Option **Erstellen** und dann **Virtueller Azure-Computer** aus.
1. Wählen Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen eines virtuellen Computers die folgenden Einstellungen aus, und wählen Sie dann **Überprüfen und erstellen** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Name des virtuellen Computers  | WS-VM1   |
    | Region    | USA, Osten  |
    | Verfügbarkeitsoptionen  | Keine Infrastrukturredundanz erforderlich  |
    | Sicherheitstyp | Standard   |
    | Abbildung | Windows Server 2022 Datacenter: Azure Edition – x64 Gen2  |
    | VM-Architektur   | x64  |
    | Größe  | Standard_D4s_v3 – 4 vCPUs, 16 GiB Arbeitsspeicher  |
    | Administratorkonto | prime  |
    | Kennwort  | [Wählen Sie ein eindeutiges und sicheres Kennwort] P@ssw0rdP@ssw0rd   |
    | Eingehende Ports | RDP 3389   |

4. Überprüfen Sie die Einstellungen, und wählen Sie **Erstellen** aus.
1. Warten Sie, bis die Bereitstellung abgeschlossen ist. Wählen Sie nach Abschluss der Bereitstellung die Option **Zu Ressource wechseln** aus.
1. Wählen Sie auf der Seite **Eigenschaften von WS-VM1** die Option **Netzwerk** aus.
1. Wählen Sie auf der Seite **Netzwerk** die RDP-Regel aus. 
1. Ändern Sie im RDP-Regelbereich die Quelle in „Meine IP-Adresse“, und wählen Sie **Speichern** aus.

    Dadurch werden eingehende RDP-Verbindungen auf die aktuell verwendete IP-Adresse beschränkt.

9. Wählen Sie auf der Seite **Netzwerk** die Option **Regel für eingehenden Port hinzufügen** aus.
1. Konfigurieren Sie auf der Seite **Eingangssicherheitsregel hinzufügen** die folgenden Einstellungen, und wählen Sie **Hinzufügen** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Source  | Beliebig  |
    | Quellportbereiche    | *   |
    | Destination  | Beliebig   |
    | Aktion    | Allow  |
    | Priorität  | 310   |
    | Name  | AllowAnyHTTPInbound  |

11. Wählen Sie auf der Seite **WS-VM1** die Option **Verbinden** aus.
1. Wählen Sie unter „Natives RDP“ die Option **Auswählen** aus.
1. Wählen Sie auf der Seite **Natives RDP** die Option **RDP-Datei herunterladen** aus, und öffnen Sie dann die Datei. Durch das Öffnen der RDP-Datei wird das Dialogfeld „Remotedesktopverbindung“ geöffnet.
1. Wählen Sie im Dialogfeld **Windows-Sicherheit** die Option **Weitere Optionen** und dann „Anderes Konto verwenden“ aus.
1. Geben Sie den Benutzernamen „.\prime“ und als Kennwort das sichere Kennwort ein, das Sie in Schritt 3 gewählt haben. Wählen Sie dann **OK** aus.
1. Wenn Sie sich beim virtuellen Windows Server-Computer angemeldet haben, klicken Sie mit der rechten Maustaste auf den **Starthinweis**, und wählen Sie dann **Windows PowerShell (Administrator)** aus.
1. Geben Sie in der erhöhten Eingabeaufforderung den folgenden Befehl ein, und drücken Sie die **Eingabetaste**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Wenn die Installation abgeschlossen ist, führen Sie den folgenden Befehl aus, um zum Stammverzeichnis des Webservers zu wechseln.
    Cd c:\inetpub\wwwroot\
1. Führen Sie den folgenden Befehl aus.
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html-OutFile index.html


## Bereitstellen und Konfigurieren von LX-VM2

In dieser Übung erstellen und konfigurieren Sie einen virtuellen Linux-Computer.

1. Geben Sie im Azure-Portal in der Suchleiste **Virtuelle Computer** ein, und wählen Sie in den Suchergebnissen **Virtuelle Computer** aus.
1. Wählen Sie auf der Seite **Virtuelle Computer** die Option **Erstellen** und dann **Virtueller Azure-Computer** aus.
1. Wählen Sie auf der Seite **Grundlagen** des Assistenten zum Erstellen eines virtuellen Computers die folgenden Einstellungen aus, und wählen Sie dann **Überprüfen und erstellen** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Name des virtuellen Computers  | Linux-VM2   |
    | Region    | USA, Osten  |
    | Verfügbarkeitsoptionen  | Keine Infrastrukturredundanz erforderlich  |
    | Sicherheitstyp | Standard   |
    | Abbildung | Ubuntu Server 20.04 LTs – x64 Gen2  |
    | VM-Architektur   | x64  |
    | Größe  | Standard_D2s_v3 – 2 vCPUs, 8 GiB Arbeitsspeicher  |
    | Authentifizierungstyp   | Kennwort  |
    | Username  | Prime   |
    | Kennwort  | [Wählen Sie ein eindeutiges und sicheres Kennwort] P@ssw0rdP@ssw0rd   |
    | Öffentliche Eingangsports  | Keine   |

4. Überprüfen Sie die Informationen, und wählen Sie **Erstellen** aus.
1. Öffnen Sie nach dem Bereitstellen der VM die Seite **VM-Eigenschaften**, und wählen Sie **Erweiterungen + Anwendungen** unter **Einstellungen** aus.
1. Wählen Sie **Hinzufügen** und dann den **Network Watcher-Agent für Linux** aus. Wählen Sie **Weiter** und anschließend **Überprüfen und erstellen** aus. Wählen Sie **Erstellen** aus.
1. Konfigurieren Sie die AzureNetworkWatcherExtension und die OmsAgentForLinux-Erweiterung so, dass sie automatisch aktualisiert werden.


## Bereitstellen einer Web-App mit einer SQL-Datenbank

1. Stellen Sie sicher, das Sie noch beim Azure-Portal angemeldet sind.
1. Öffnen Sie im Browser eine neue Registerkarte, und navigieren Sie zu https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database.
1. Wählen Sie auf der GitHub-Seite **Bereitstellung in Azure** aus.
1. Es wird eine neue Registerkarte geöffnet. Melden Sie sich bei Bedarf erneut bei Azure mit dem Konto an, das über globale Administratorrechte verfügt.
1. Wählen Sie auf der Seite **Grundlagen** die Option **Vorlage bearbeiten** aus.
1. Löschen Sie im Vorlagen-Editor den Inhalt der Zeilen 158 bis einschließlich 174, und löschen Sie das Komma (,) in Zeile 157. Wählen Sie **Speichern** aus.
1. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein, und wählen Sie anschließend **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | SKU-Name  | F1  |
    | SKU-Kapazität  | 1   |
    | Anmeldename des SQL-Administrators   | prime  |
    | Anmeldekennwort des SQL-Administrators  | [Wählen Sie ein eindeutiges und sicheres Kennwort] P@ssw0rdP@ssw0rd   |

8. Überprüfen Sie die angezeigten Informationen, und wählen Sie **Erstellen** aus.
1. Wählen Sie nach Abschluss der Bereitstellung die Option **Zu Ressourcengruppe wechseln** aus.

## Bereitstellen einer Linux-Web-App

1. Stellen Sie sicher, das Sie noch beim Azure-Portal angemeldet sind.
1. Öffnen Sie im Browser eine neue Registerkarte, und navigieren Sie zu https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/.
1. Wählen Sie auf der GitHub-Seite **Bereitstellung in Azure** aus.
1. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein, und wählen Sie anschließend **Weiter** aus.

    | Eigenschaft | Wert    |
    |:---------|:---------|
    | Abonnement  | Ihr Abonnement   |
    | Ressourcengruppe    | rg-alpha  |
    | Region    | USA, Osten  |
    | Name der Web-App  | AzureLinuxAppWXYZ (weisen Sie für die letzten vier Zeichen des Namens eine zufällige Zahl zu)  |
    | SKU   | S1   |
    | Linux Fx-Version  | php|7.4  |

5. Überprüfen Sie die Informationen, und wählen Sie **Erstellen** aus.
