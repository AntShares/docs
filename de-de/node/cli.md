# CLI Command Referenz

�ffnen Sie die Kommandozeile und navigieren Sie in den Installationsordner von NEO-CLI. Geben Sie 

`dotnet neo-cli.dll`

ein um die Kommandozeilen-Wallet zu starten.

Dieses Tutorial stellt alle Befehle f�r die Kommandozeilen-Wallet vor. Sie k�nnen in NEO-CLI eine Wallet erstellen, private Schl�ssel im- und exportieren, Assets transferieren, an der Konsensbildung beteiligen etc.

Zuerst werden wir verschiedene Befehle kennenlernen, die in der Kommandozeile gelistet sind. Geben sie `help` ein und dr�cken sie `Enter` damit Ihnen folgende Liste angezeigt wird:

![image](/assets/cli_2.png)

Im Folgenden werden alle Befehle und die Anordnung der Klammern erkl�rt:
Winkelklammern ``<>`` markieren Parameter.
Eckige Klammern ``[]`` markieren optionale Parameter.
Das Symbol ``|`` zeigt einen beliebigen F�llparameter an.
Das Gleichheitszeichen `=` definiert den Standardwert f�r optionale Parameter ohne Input.

## 1. Kommandozeilen Befehle

| Command      | Funktion     |
| ------- | --------- |
| version | Zeigt die aktuelle Versionsnummer |
| help    | Hilfemen�      |
| clear   | Bildschirm leeren     |
| exit    | Programm beenden      |

## 2. Wallet Operatoren

Command | Funktion | Anmerkungen |
| ---------------------------------------- | -------------------------------- | ------ |
| create wallet \<path> | Wallet anlegen |
| open wallet \<path> | Wallet �ffnen |
| rebuild wallet index | | Wallet muss f�r diese Funktion ge�ffnet sein |
| list address | Listet alle Accounts der Wallet auf | Wallet muss f�r diese Funktion ge�ffnet sein |
| list asset | Listet alle Adressen der Wallet auf | Wallet muss f�r diese Funktion ge�ffnet sein |
| list key | Listet alle �ffentlichen Schl�ssel der Wallet auf | Wallet muss f�r diese Funktion ge�ffnet sein |
| create address [n = 1] | Adresse generieren / Mehrere Adressen generieren | Wallet muss f�r diese Funktion ge�ffnet sein |
| import key \<wif\|path> | Importiere privaten Schl�ssel / Mehrfachimport privater Schl�ssel | Wallet muss f�r diese Funktion ge�ffnet sein |
| export key \[address] [path] | Exportiert privaten Schl�ssel| Wallet muss f�r diese Funktion ge�ffnet sein |
| send \<id\|alias> \<address> \<value> [fee=0]| Sendet an bestimmte Adresse |Wallet muss f�r diese Funktion ge�ffnet sein |

Die folgenden Befehle werden im Detail erkl�rt:

👉 `rebuild index`

Mit diesem Befehl wird der Wallet Index wiederhergestellt.
Warum ist dies �berhaupt erforderlich?

Es gibt ein Feld in der Wallet, dass die H�he des aktuell synchronisierten Blocks mitschreibt. F�r jeden neuen Block synchronisiert die Wallet die Blocks und aktualisiert die Assets und Transaktionen, die die Wallet betreffen. Angenommen, die Blockh�he ist aktuell 100 und Sie importieren einen privaten Schl�ssel, dann berechnet die Wallet Ihre Assets ab der Blockh�he 100. Wenn Ihre Adresse Transaktionen vor der Blockh�he 100 hatte, dann werden diese nicht ber�cksichtigt. Durch den Rebuild wird das Programm gezwungen, Ihre Assets ab Block 0 neu zu berechnen und anzuzeigen.

Eine neu generierte Wallet ben�tigt keinen Wallet Index Rebuild. Lediglich nach dem Import eines privaten Schl�ssels ist ein Rebuild n�tig.

👉 `create address [n = 1]`

Mit diesem Befehl kann eine neue Adresse angelegt werden. Sie k�nnen auch 100 Adressen gleichzeitig generieren, indem Sie `create address 100` eingeben. Mehrfachgenerierungen f�hren automatisch zu einem Adressenexport in die address.txt-Datei.

👉 `export key [address] [path]`

Sie k�nnen spezifizieren, zu welcher Adresse der private Schl�ssel exportiert werden soll. Auch k�nnen Sie bestimmen, in welche Datei und in welchen Ordner der Schl�ssel exportiert werden soll. Dieser Befehl ben�tigt eine Passworteingabe zur Best�tigunt.

Export key

Export key AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b

Export key key.txt

Export key AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b key.txt

👉 `import key <wif | path>`

Wenn Sie einen privaten Schl�ssel importieren, k�nnen Sie entweder einen einzelnen privaten Schl�ssel oder aber eine Datei mit mehreren Schl�sseln importieren. 

Import key L4zRFphDJpLzXZzYrYKvUoz1LkhZprS5pTYywFqTJT2EcmWPPpPH

Import key key.txt

Die zu importierende Datei muss das `private key format` haben um erfolgreich importiert werden zu k�nnen. Bitte sehen Sie sich zum Vergleich eine Export-Datei an.

👉 `send <id | alias> <address> <value> [fee = 0]`

F�r Transfers gibt es insgesamt vier Parameter. Der erste Parameter ist die Asset-ID, der zweite die Ziel-Adresse, der dritte die Menge und der vierte Parameter ist die Geb�hr (der letzte Parameter kann leergelassen werden, da die Geb�hr zur Zeit 0 betr�gt). Dieser Befehl muss durch Eingabe des Wallet-Passworts best�tigt werden. Wenn Sie z.B. 100 NEO an die Adresse: "AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b" transferieren wollen, m�ssen Sie folgende Befehle eingeben:

Send c56f33fc6ecfcd0c225c4ab356fee59390af8560be0e930faebe74a6daff7c9b AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b 100

Wenn Sie sich �ber die Asset-ID nicht im Klaren sind, nutzen Sie den `list asset`-Befehl um alle Assets Ihrer Wallet anzeigen zu lassen.

## 3. Node Informationen anzeigen lassen

Command | Funktion |
| ---------- | ----------------------- |
show state | Zeigt den Status der Blockchainsynchronisation an
show node | Zeigt IP-Adresse und Port der verbundenen Node |
show pool | Zeigt die Transaktionen im Memory-Pool an (Transaktionen mit 0 Best�tigungen) 

## 4. Fortgeschrittene

Command | Funktion |
| --------------- | ---- |
Start consensus | Beginnt Teilnahme an der Konsensbildung

Dieser Befehl funktioniert nur, wenn die Wallet eine Berechtigung hat, an der Konsensbildung teilzunehmen. Die Berechtigung kann auf dem MainNet durch den Wahlmechanimus erlangt werden. In einem privaten Netzwerk kann der �ffentliche Schl�ssel in die `protocol.json` eingetragen werden. 
F�r weitere Informationen lesen Sie bitte [hier](private-chain.md).
