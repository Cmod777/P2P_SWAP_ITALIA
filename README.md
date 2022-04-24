# P2P_SWAP_ITALIA

Mercato di swap Bitcoin tra
Lightning Network LN-BTC, Onchain BTC e Liquid L-BTC
***
Ogni scambio si compone di due parti, la parte debole (quella che invia satoshi con il metodo più immediato) e una parte forte (quella che invia satoshi con il metodo più lento ma li riceve dalla controparte con il metodo più veloce)
La parte forte, indipendentemente dal fatto che abbia o meno pubblicato l'annuncio di richiesta di swap, sarà quella che dovrà pagare il pegno all'arbitro come garanzia che condurrà lo scambio in modo corretto e manderà alla controparte quanto pattuito.
***

# FUNZIONAMENTO DELLO SCAMBIO: ESEMPIO
1. Alice e Bob vogliono scambiarsi dei satoshi tra Lightning network e Bitcoin onchain, Alice ha dei satoshi sul suo wallet Lightning e vuole dei satoshi Onchain, Bob invece ha satoshi onchain e li vuole portare su Lightning network.

2. Alice pubblica una richiesta (seguendo il modello indicato) specificando la quantità di satoshi che vuole spostare da Lightning network a Onchain.

3. Bob risponde alla richiesta accettando lo scambio.

4. Si attende l'arbitro e, una volta comunicata accettazione da entrambe le parti, si prosegue con chat privata tra i 3 soggetti.

5. L'arbitro crea una chat privata, invita i due partecipanti e controlla che lo scambio avvenga regolarmente.

6. Bob invia via Lightning network una quantità pari al 100% dell'importo da scambiare come garanzia (essendo la parte avvantaggiata nello scambio).

7. Alice invia il 100,5% di quanto concordato (100% = importo sottoposto a swap + 0,5% di tip) a Bob e ottiene una transazione onchain dalla controparte.

8. Bob riceve il 100,5% via Lightning network da alice e in cambio manda il 100% (le fee della tx su mainnet sono a carico di chi invia la transazione onchain) ad Alice sull'indirizzo onchain specificato da alice.

9. L'arbitro verifica che le persone partecipanti allo scambio si comportino in modo onesto.

10. Una volta ottenute 6 conferme su rete mainnet onchain (o su Liquid), L'arbitro restituisce a Bob il 99% di quanto inviatogli come pegno in precedenza, trattenendo l'1% come commissioni di servizio.

11. L'operazione si é conclusa.

***
Nel caso in cui la parte onchain (Bob) non invia la transazione su mainnet (rete Bitcoin o rete Liquid), perde il pegno e L'arbitro invia il 99% dell'importo ad Alice come rimborso della perdita. Bob sarà bannato definitivamente dal gruppo.
***

# OPERAZIONE DI SWAP CONCLUSA CON SUCCESSO
In caso in cui L'operazione si concluda normalmente:
Alice pagherà lo 0.5% per lo swap, 
Bob pagherà lo 0.5% per lo swap, 
L'arbitro guadagnerà l'1% dello swap.

Le fee di transazione sulle rispettive reti sono a carico di chi invia la relativa transazione.
***

# ESEMPIO DI UNO SCAMBIO:
Alice ha 100.000 sat LN e li vuole Onchain
Bob ha 100.000 sat Onchain e li vuole LN

Bob paga 100.000 sat all'arbitro (equivalente al 100% del valore dello scambio, questo importo è il pegno e verrà restituito dall'arbitro a scambio concluso con successo -le fee dell'arbitro stesso)
Alice paga 100.500 sat a bob (paga il 100% di quanto intende scambiare + 0,5% come commissione a Bob)
Bob paga 100.000 ad Alice (paga il 100% di quanto Alice vuole scambiare)

# COSTI DELLO SCAMBIO:
Se tutto va bene l'arbitro paga 99.000 sat a Bob (restituisce il pegno e tiene la sua percentuale di guadagno)
Alice ha pagato 500 sat + le fee su rete LN
Bob ha ricevuto 500 sat da Alice, ha pagato le fee su rete onchain e ha pagato 1.000 sat all'arbitro (perché riceve 99% del pegno di 100.000 sat)
Larbitro ha guadagno 1.000 sat

Se Bob non manda 100.000 sat ad Alice (cercando di truffare la controparte) allora l'arbitro paga 99.000 sat ad Alice per conto di Bob. (utilizza l'importo pagato da Bob come pegno per pagare Alice e rimborsare il valore dello scambio)
Alice ha pagato 500 sat a Bob ma ha ottenuto 99.000 sat dall'arbitro, quindi ha perso in totale 1.500 sat (pari a 1,5% dell'importo)
Bob ha perso il pegno. (Pari al 100%) ma ha guadagnato lo 0.5% da Alice (500 sat)
L' arbitro ha guadagnato 1.000 sat (1% dello scambio)


# Commissioni di transazione:
Le commissioni su rete bitcoin onchain sono quelle indicate al momento dello scambio su mempool.space riferite a "priorità media"
Le commissioni in caso in cui la controparte che invia da onchain a Lightning partecipa a più scambi contemporaneamente (quindi faccia una sola tx che includa più destinatari onchain in contemporanea) sono quelle riferite a "priorità alta"
L' arbitro si occuperà di indicare le giuste fee in caso di dubbi dei partecipanti allo scambio.

# ALTRE SPECIFICHE
Sono validi per gli swap BTC onchain, Liquid L-BTC e Lightning network LN-BTC
Chi pubblica una richiesta indica anche con quale sistema effettuare lo scambio, esempi: 
"Scambio 1.000 sat LN con Onchain"
Oppure
"Scambio 1.000 sat Liquid L-BTC con Onchain"
Oppure
"Scambio 1.000 sat Onchain con Lightning LN"
Si usa il sistema di hashtag per facilitare la ricerca degli annunci.
Tutti gli importi sono espressi in satoshi.
La controparte che invia da rete Liquid oppure Onchain é sempre quella che deve inviare il pegno all'arbitro in quanto la sua transazione, a differenza di quella effettuata su rete Lightning, è sempre quella più lenta e potrebbe essere annullata effettuando una nuova tx che spenda lo stesso importo verso un indirizzo diverso da quello concordato. Per tale motivo si aspettano anche 6 conferme Onchain prima di ottenere indietro il pegno.
Le controparti possono scambiarsi gli indirizzi Onchain utilizzando pgp per ottenere ulteriore privacy nei confronti dell'arbitro.
