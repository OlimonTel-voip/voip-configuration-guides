# Configurare Numero VoIP su smartphone e PC

Prepara i [parametri della linea](servizi-e-parametri.md). I nomi dei menu e le opzioni audio possono variare con la versione e l'edizione dell'app.

## Zoiper su Android

1. Nella configurazione iniziale scegli **Create an account**. Per modificare un profilo esistente apri **Settings → Accounts** e seleziona l'account.
2. Usa `<SIP_LOGIN>@<SIP_DOMAIN>` in **Username**, `<SIP_PASSWORD>` in **Password** e `<SIP_DOMAIN>:<SIP_PORT>` in **Hostname** quando la porta va indicata. In **Authentication username** usa `<SIP_AUTH_ID>`. Compila **Outbound Proxy** secondo il profilo. La procedura OlimonTel illustrata usa `5062` e **SIP UDP**.
3. Salva e verifica che l'account sia registrato. In **Settings → Accounts → account → Audio Codec Settings** verifica la disponibilità di G.711 A-law e degli altri codec richiesti dal profilo. La guida indica G.729 come prima scelta quando disponibile. [Guida OlimonTel per Zoiper su Android](https://olimontel.it/guide-configurazioni/configurazione-app-zoiper-android/)

## Zoiper su iPhone

Scegli **Configurazione manuale → Account SIP**. Inserisci `<SIP_LOGIN>@<SIP_DOMAIN>` in **Username** e `<SIP_PASSWORD>` nel campo password. Se la versione mostra campi distinti per dominio o trasporto, usa quelli del profilo assegnato. Tocca **Registra** e controlla lo stato nella lista degli account. Nel menu **Audio** verifica la presenza di almeno un codec comune, per esempio G.711 A-law se previsto. [Guida OlimonTel per Zoiper su iPhone](https://olimontel.it/guide-configurazioni/video-guida-configurazione-softphone-voip/)

## MicroSIP su Windows

1. Dal menu scegli **Add Account**. Usa `<SIP_DOMAIN>` in **SIP Server** e **Domain**, con la porta remota nel campo server se il profilo la richiede.
2. Usa `<SIP_LOGIN>` in **Username** e `<SIP_AUTH_ID>` in **Login** quando serve un identificativo di autenticazione distinto. Compila **Password** con `<SIP_PASSWORD>` e **Transport** con il trasporto assegnato.
3. Salva l'account e controlla la registrazione. In **Settings** verifica microfono, altoparlanti e codec abilitati. Dopo una chiamata di prova, se l'audio manca, controlla anche quale dispositivo audio è selezionato in Windows. [Guida OlimonTel per MicroSIP](https://olimontel.it/guide-configurazioni/configurazione-microsip-voip/) · [Manuale MicroSIP](https://www.microsip.org/help)

## Verificare chiamate e ricezione in background

1. Con l'app aperta, prova una chiamata entrante e una uscente. Verifica squillo, microfono e audio in entrambe le direzioni.
2. Sullo smartphone ripeti l'ingresso con lo schermo spento e dopo qualche minuto di inattività. Se funziona solo in primo piano, verifica permessi per notifiche, impostazioni di risparmio energetico e supporto alla ricezione in background o via push della tua versione.
3. Ripeti su Wi-Fi e rete mobile, se usi entrambe. Se una sola rete presenta il problema, confronta lo stato della registrazione e usa la [diagnosi NAT](nat-e-starlink.md).

Altre app e versioni sono elencate nelle [guide Numero VoIP per smartphone e PC](https://olimontel.it/categorie-configurazioni/app-softphone-smartphone-pc/).
