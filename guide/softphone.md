# Configurare Numero VoIP su smartphone e PC

Prepara i [parametri della linea](servizi-e-parametri.md). I nomi dei menu e le opzioni audio possono variare con la versione e l'edizione dell'app.

## Zoiper su Android

1. Nella configurazione iniziale scegli **Create an account**. Per modificare un profilo esistente apri **Settings → Accounts** e seleziona l'account.
2. Usa `<SIP_LOGIN>@<SIP_DOMAIN>` in **Username**, `<SIP_PASSWORD>` in **Password** e `<SIP_DOMAIN>:<SIP_PORT>` in **Hostname** quando la porta va indicata. In **Authentication username** usa `<SIP_AUTH_ID>`. Compila **Outbound Proxy** secondo il profilo. La procedura OlimonTel illustrata usa `5062` e **SIP UDP**.
3. Salva e verifica che l'account sia registrato. In **Settings → Accounts → account → Audio Codec Settings** verifica la disponibilità di G.711 A-law e degli altri codec richiesti dal profilo. La guida indica G.729 come prima scelta quando disponibile. [Guida OlimonTel per Zoiper su Android](https://olimontel.it/guide-configurazioni/configurazione-app-zoiper-android/)

**Prova.** Fai una chiamata in uscita e fatti richiamare con l'app aperta. Ripeti la chiamata entrante con lo schermo spento per controllare la ricezione in background.

## Zoiper su iPhone

Scegli **Configurazione manuale → Account SIP**. Inserisci `<SIP_LOGIN>@<SIP_DOMAIN>` in **Username** e `<SIP_PASSWORD>` nel campo password. Se la versione mostra campi distinti per dominio o trasporto, usa quelli del profilo assegnato. Tocca **Registra** e controlla lo stato nella lista degli account. Nel menu **Audio** verifica la presenza di almeno un codec comune, per esempio G.711 A-law se previsto. [Guida OlimonTel per Zoiper su iPhone](https://olimontel.it/guide-configurazioni/video-guida-configurazione-softphone-voip/)

**Prova.** Chiama dalla rete Wi-Fi che userai normalmente, poi fatti richiamare e verifica che l'audio passi in entrambe le direzioni. Se conti di ricevere anche a schermo bloccato, prova quello scenario a parte.

## Zoiper 5 su Windows

1. Usa la procedura iniziale di Zoiper 5 o apri **Settings → Accounts → Add**. Inserisci `<SIP_LOGIN>@<SIP_DOMAIN>` in **Username** e `<SIP_PASSWORD>` in **Password**.
2. In **Hostname** conferma il dominio assegnato. Aggiungi la porta remota nel formato richiesto dall'app se l'attivazione la specifica. Compila **Authentication username** se il profilo indica un valore dedicato.
3. Nel profilo illustrato su PC OlimonTel usa **SIP TCP** e lascia disattivato **Outbound Proxy**. Segui le impostazioni assegnate se il tuo profilo usa parametri diversi. Salva e controlla lo stato dell'account.

**Prova.** Verifica il segno di spunta accanto all'account e selezionalo. Chiama un secondo telefono e fatti richiamare. Con cuffie collegate, verifica che Zoiper usi quel microfono e quelle cuffie. [Guida OlimonTel per Zoiper su PC](https://olimontel.it/guide-configurazioni/configurazione-zoiper-pc/) · [Manuale Zoiper 5](https://www.zoiper.com/pdf/User%20Guide%20Zoiper%205%20v.1.0.6.pdf)

## MicroSIP su Windows

1. Dal menu scegli **Add Account**. Usa `<SIP_DOMAIN>` in **SIP Server** e **Domain**, con la porta remota nel campo server se il profilo la richiede.
2. Usa `<SIP_LOGIN>` in **Username** e `<SIP_AUTH_ID>` in **Login** quando serve un identificativo di autenticazione distinto. Compila **Password** con `<SIP_PASSWORD>` e **Transport** con il trasporto assegnato.
3. Salva l'account e controlla la registrazione. In **Settings** verifica microfono, altoparlanti e codec abilitati. Dopo una chiamata di prova, se l'audio manca, controlla anche quale dispositivo audio è selezionato in Windows. [Guida OlimonTel per MicroSIP](https://olimontel.it/guide-configurazioni/configurazione-microsip-voip/) · [Manuale MicroSIP](https://www.microsip.org/help)

**Prova.** Effettua e ricevi una chiamata dall'account selezionato. Verifica che l'altro telefono senta il tuo microfono e che tu senta l'interlocutore dal dispositivo scelto.

## Linphone su Android

Apri **Account SIP di terze parti**. Usa `<SIP_LOGIN>` in **Username**, `<SIP_PASSWORD>` in **Password** e `<SIP_DOMAIN>` in **Domain**. Seleziona il trasporto previsto. Se la porta assegnata va impostata in modo esplicito, usa il campo server o proxy previsto dalla versione dell'app. Tocca **Login** e verifica lo stato dell'account.

**Prova.** Con l'app aperta chiama un altro telefono e fatti richiamare. Se ricevi su Wi-Fi e rete mobile, ripeti l'ingresso su entrambe e confronta lo stato della registrazione. [Guida OlimonTel per Linphone su Android](https://olimontel.it/guide-configurazioni/configurazione-app-linphone-android/) · [Accesso con account SIP di terze parti](https://www.linphone.org/en/docs/login-sip-account/)

## Linphone Desktop

Scegli **Third-Party SIP Account** nella procedura di accesso. Compila **Username**, **SIP Domain** e **Password** con `<SIP_LOGIN>`, `<SIP_DOMAIN>` e `<SIP_PASSWORD>`. Imposta il trasporto se l'interfaccia lo richiede e conferma con **Login**. Se ci sono più account, seleziona quello OlimonTel prima di chiamare.

**Prova.** Con il microfono del PC selezionato, effettua una chiamata e fatti richiamare. Verifica che la chiamata entrante arrivi sul profilo appena aggiunto e che l'audio funzioni nei due sensi. [Manuale Linphone per account SIP di terze parti](https://www.linphone.org/en/docs/login-sip-account/) · [Parametri Numero VoIP OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)

## MizuDroid su Android

Nella schermata iniziale inserisci `<SIP_DOMAIN>:<SIP_PORT>` in **Server** e `<SIP_PASSWORD>` in **Password**. In **Username** inserisci il nome di autenticazione SIP, che per il profilo illustrato da OlimonTel coincide con la login. Se la linea prevede un proxy, impostalo nelle opzioni SIP. Salva con **OK** e verifica **Registered** nella schermata del tastierino.

**Prova.** Chiama e fatti richiamare con il tastierino aperto. Controlla lo squillo e l'audio nei due sensi. Se usi l'app in mobilità, ripeti il test con la rete dati. [Guida OlimonTel per MizuDroid](https://olimontel.it/guide-configurazioni/configurazione-app-mizudroid/) · [Manuale MizuDroid](https://www.mizu-voip.com/Portals/0/Files/Android_Softphone_Guide.pdf)

## FRITZ!App Fon su Android e iPhone

1. Configura Numero VoIP sul [FRITZ!Box](dispositivi.md). Collega lo smartphone alla rete Wi-Fi principale del FRITZ!Box e avvia **FRITZ!App Fon**.
2. Seleziona il FRITZ!Box e completa l'associazione richiesta dall'app. In **Telefonia → Dispositivi di telefonia** apri il dispositivo creato per l'app. Imposta il numero OlimonTel per **Chiamate in uscita** e selezionalo anche tra i numeri a cui l'app deve rispondere. I campi SIP della linea si compilano sul FRITZ!Box.

**Prova su Android e iPhone.** Restando sul Wi-Fi domestico, chiama da **FRITZ!App Fon**. Fatti richiamare e verifica che squilli l'app e che ci sia audio nei due sensi. [Configurazione FRITZ!App Fon](https://fritz.com/it-it/apps/knowledge-base/FRITZ-Box-4040/251_Configurare-FRITZ-App-Fon/) · [Guida OlimonTel per FRITZ!Box](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/)

## Verificare chiamate e ricezione in background

1. Con l'app aperta, prova una chiamata entrante e una uscente. Verifica squillo, microfono e audio in entrambe le direzioni.
2. Sullo smartphone ripeti l'ingresso con lo schermo spento e dopo qualche minuto di inattività. Se funziona solo in primo piano, verifica permessi per notifiche, impostazioni di risparmio energetico e supporto alla ricezione in background o via push della tua versione.
3. Ripeti su Wi-Fi e rete mobile, se usi entrambe. Se una sola rete presenta il problema, confronta lo stato della registrazione e usa la [diagnosi NAT](nat-e-starlink.md).

Altre app e versioni sono elencate nelle [guide Numero VoIP per smartphone e PC](https://olimontel.it/categorie-configurazioni/app-softphone-smartphone-pc/).
