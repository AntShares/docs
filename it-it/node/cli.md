# Comandi CLI
+
+Apri la linea di comando, naviga fino alla directory dove il programma è collocato, ed inserisci il docice seguente per avviare il wallet a linea di comando (Il nodo NEO).
+
+`dotnet neo-cli.dll`
+
+Questo tutorial introdurrà  tutti i comandi del wallet a linea di comando. con questi comandi è possibile manipolare il wallet per creare un wallet, importare ed esportare la chiave privata, trasferire, iniziare il consenso, etc.
+
+Esamineremo prima i vari comandi listati nella linea di comando. Se inserisci `help` seguito dal comando "indietro", ti verrà mostrata una lista di comandi.
+
+![image](/assets/cli_2.png)
+
+Qaunto segue è una descrizione di tutti i comandi e l'ordine delle oarentesi:
+Le parentesi angolari ``<> `` , indicano un parametro.
+Le parentesi quadre `[]`, vengono usate per parametri opzionali.
+Il simbolo `|` mostra i parametri di riempimento, che possono essere di qualunque tipo.
+Il simbolo uguale `=` indica il valore predefinito di un di un parametro opzionale senza input. 
+
+## 1. Istruzioni della Console
+
+| Comando      | Descrizione della funzione      |
+| ------- | --------- |
+| version | Mostra la versione corrente del software |
+| help    | Menu di aiuto      |
+| clear   | Pulisce lo schermo      |
+| exit    | Esce dal programma      |
+
+## 2. Operazioni con il Wallet
+
+Comando | Descrizione della funzione | Osservazioni |
+| ---------------------------------------- | -------------------------------- | ------ |
+| create wallet \<path> | creare il file wallet|
+| open wallet \<path> | Aprire il file wallet |
+| rebuild wallet index | | riapertura del wallet |
+| list address | Fare una lista di tutti gli account del wallet | Occorre aprire il wallet |
+| list asset | Fare una lista di tutti gli asset nel wallet| Occorre aprire il wallet |
+| list key | Fare una lista di tutte le chiavi pubbliche del wallet | Occorre aprire il wallet |
+| create address [n = 1] | Creare un indirizzo / creare lotti di indirizzi | Occorre aprire il wallet |
+| import key \<wif\|path> | Importare la chiave privata / importare chiavi private in gruppo | Occorre aprire il wallet |
+| export key \[address] [path] | Esportare la chiave privata | Occorre aprire il wallet |
+| send \<id\|alias> \<address> \<value> [fee=0]| Mandare all'indirizzo specificato | Occorre aprire il wallet |
+
+I comandi seguenti vengono spiegati in dettaglio:
+
+👉 `rebuild index`
+
+Questo comando è utilizzato per ricostruire l'index del wallet.
+Perchè è necessario ricostruire l'index del wallet?
+
+C'è un campo nel wallet che registra l'altezza della sincronizzazione del blocco corrente. per ciascuno di essi, il client del wallet sincronizza i blocchi e aggiorna gli assets e le transazioni nel wallet. Supponendo che il blocco correntemente registrato sia 100, e stai eseguendo il comando di importazione della chiave privata, il wallet continua a calcolare i tuoi asset dal blocco all'altezza 100. Se l'indirizzo importato ha alcune transazioni quando l'altezza del blocco è 100, le transazioni e gli assets corrispondenti non saranno mostrati nel wallet, quindi va ricostruito l'index del wallet, forzando il wallet a calcolare i tuoi assets dall'altezza del blocco 0. 
+
+Il wallet appena creato non ha bisogno di ricostruire l'index del wallet, solamente la chiave privata importata è richiesta per ricostruire l'index del wallet.
+
+👉 `create address [n = 1]`
+
+Questo comande può essere usato per creare un nuovo indirizzo. Vi è anche la possibilità di insierire 'create address 100' per creare 100 nuovi indirizzi in lotto; La creazione all'ingrosso di indirizzi verrà automaticamente esportata al file address.txt.
+
+👉 `export key [address] [path]`
+
+E' possibile specificare a quali indirizzi esportare le corrispondenti chiavi private. Inoltre, è possibile specificare l'esportazione del determinato file. (Vedi gli esempi successivi). Il comando, inoltre, richiede anche la verificazione della password del wallet.
+
+Export key
+
+Export key AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b
+
+Export key key.txt
+
+Export key AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b key.txt
+
+👉 `import key <wif | path>`
+
+Quando si sta importando la chiave privata, è possibile specificare di importare una chiave privata, oppure importare un file con un numero di chiavi private. (Vedere i seguenti comandi).
+
+Import key L4zRFphDJpLzXZzYrYKvUoz1LkhZprS5pTYywFqTJT2EcmWPPpPH
+
+Import key key.txt
+
+Vi è  un file specificato, il file è nel formato della chiave privata. Si riferisce all'output export key.txt.
+
+👉 `send <id | alias> <address> <value> [fee = 0]`
+
+Per i trasferimenti, vi è un totale di quattro parametri. Il primo parametro e l'ID dell'asset, il secondo parametro è l'indirizzo di pagamento, il terzo parametro è  la quantità  da trasferire e il quarto parametro è la commissione. (Questo parametro può essere lasciato vuoto, di default è 0) Il comando verifica la password del wallet. Per esempio, al fine di trasferire 100 NEO all'indirizzo "AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b", occorre inserire il seguente comando.
+
+Send c56f33fc6ecfcd0c225c4ab356fee59390af8560be0e930faebe74a6daff7c9b AeSHyuirtXbfZbFik6SiBW2BEj7GK3N62b 100
+
+Se non sei sicuro dell'ID dell'asset, per favore esegui il comando per vedere la lista di asset nel tuo wallet.
+
+## 3. Vedere le Informazioni del Nodo
+
+Comando | Descrizione della Funzione |
+| ---------- | ----------------------- |
+show state | Mostra lo stato corrente della sincronizzazione della blockchain |
+show node | Mostra l'indirizzo e la porta dei nodi connessi |
+show pool | Mostra le transazioni nella memoria (queste transazioni hanno ricevuto 0 conferme) 
+
+## 4. Istruzioni Avanzate
+
+Comando | Descrizione della Funzione|
+| --------------- | ---- |
+Start consensus | iniziare il consenso 
+Iniziare il consenso sulla premessa che il wallet abbia l'autorità di consenso, permette che l'autorità di consenso stessa possa essere ottenuta sulla mainnet tramite votazione. Se una chain privata è eseguita, le chiavi pubbliche del consenso possono essere istituite in `protocol.json`. Per favore fare riferimento a [Chain privata](private-chain.md) per dettagli futuri.
