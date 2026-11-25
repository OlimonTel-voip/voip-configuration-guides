# Numero VoIP e VoIP PLUS

**Numero VoIP** fornisce un account SIP da configurare su un telefono IP, un adattatore ATA, un router con telefonia o un'app compatibile. **VoIP PLUS** offre un trunk SIP per il collegamento a un centralino o a un'applicazione telefonica. Prima di creare un trunk, verifica il metodo di autenticazione, il trasporto e il formato del numero consegnato con quel profilo.

| Obiettivo | Configurazione da aprire | Passo successivo |
| --- | --- | --- |
| Ricevere e chiamare da telefono IP, ATA o router | Un account SIP sul terminale | [Impostazioni per modello](dispositivi.md) |
| Ricevere e chiamare da smartphone o PC | Un account SIP nel softphone | [Impostazioni delle app](softphone.md) |
| Distribuire le chiamate attraverso un PBX | Un trunk SIP e le relative rotte | [Centralini e trunk](centralini.md) |
| Mandare le chiamate a un agente vocale | Una rotta per il DID e una destinazione SIP | [Piattaforme AI vocali](piattaforme-ai.md) |

| Segnaposto | Dove ricavare il valore e a cosa serve |
| --- | --- |
| `<SIP_LOGIN>` | Login SIP completa indicata all'attivazione, con eventuale prefisso già incluso. Usala nei campi di identità previsti dal dispositivo. |
| `<SIP_AUTH_ID>` | Nome di autenticazione. Se il profilo fornisce una sola login e la guida indica di riutilizzarla, inserisci lo stesso valore di `<SIP_LOGIN>`. |
| `<SIP_PASSWORD>` | Password SIP dell'account. Inseriscila direttamente nel dispositivo. |
| `<SIP_DOMAIN>` | Dominio/registrar SIP assegnato all'utenza. Compila il dominio SIP secondo il profilo quando il terminale lo chiede in un campo distinto. |
| `<SIP_PORT>` | Porta remota del servizio. Le guide OlimonTel indicano `5060` e `5062` per alcuni profili UDP/TCP. Abbina porta e trasporto previsti dall'attivazione. |
| `<SIP_PROXY>` | Proxy SIP quando richiesto dal profilo o dalla guida del terminale. Il campo può essere separato dal registrar. |
| `<DID>` | Numero usato per instradare la chiamata in arrivo. Mantieni il formato previsto dal trunk e dal centralino. |
| `<SIP_URI_APP>` | Destinazione SIP fornita dalla piattaforma che deve ricevere la chiamata. |
| `<TERMINATION_URI>` | Indirizzo SIP attraverso cui l'app invia una chiamata in uscita al trunk assegnato. |

## Come compilare i campi

1. Per i dispositivi con campi separati, inserisci `<SIP_LOGIN>` in **User Name** e `<SIP_DOMAIN>` in **Registrar** o **SIP Server**, secondo la guida. Se l'app richiede l'identità completa in un campo solo, usa `<SIP_LOGIN>@<SIP_DOMAIN>`. Usa i dati SIP dell'attivazione, distinti dall'accesso al portale.
2. Per un trunk, tieni separati login SIP, DID ricevuto e numero chiamante autorizzato. Il DID è la chiave della rotta in ingresso. Conserva `+`, prefisso internazionale o formato nazionale secondo il valore consegnato e le regole del PBX.
3. Imposta almeno un codec comune al servizio e all'apparato. G.711 A-law può comparire come **PCMA** o **alaw**. Segui l'ordine indicato per il modello quando la guida lo specifica. Per Numero VoIP, la guida tecnica indica DTMF **RFC 2833**. Se il dispositivo mostra la voce **RTP** per i toni, verifica nel suo manuale che corrisponda alla stessa modalità e prova un menu vocale.

Dopo il salvataggio verifica la registrazione se prevista dal profilo. Chiama da e verso un secondo telefono di prova e controlla l'audio nei due sensi. Per un trunk verifica che il DID raggiunga la destinazione scelta e che in uscita compaia il numero autorizzato. Se c'è un menu vocale, premi una cifra e verifica che selezioni la voce attesa.

## Fonti

- [Informazioni tecniche Numero VoIP](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)
- [VoIP PLUS](https://olimontel.it/voip-plus/)
- [Guide e configurazioni OlimonTel](https://olimontel.it/guide-configurazioni/)
