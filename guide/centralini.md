# Collegare un centralino a VoIP PLUS

Verifica [dominio, porta, autenticazione e formato DID](servizi-e-parametri.md) del profilo assegnato. Applica le istruzioni di registrazione quando il profilo prevede REGISTER. I menu e le opzioni SIP cambiano in base a versione, edizione e hosting.

## FreePBX con chan_pjsip

1. Apri **Connectivity → Trunks → Add SIP (chan_pjsip) Trunk**. In **General** assegna un nome al trunk e verifica il **Caller ID** autorizzato per l'uscita.
2. Compila **pjsip Settings** come indicato nella tabella, poi salva e applica la configurazione.
3. Crea una **Inbound Route** per `<DID>` e associa un interno, un gruppo o un risponditore. Crea una **Outbound Route** con il pattern del tuo piano di numerazione e seleziona il trunk appena aggiunto.

| Sezione | Campo | Valore per il profilo a registrazione illustrato |
| --- | --- | --- |
| **General** | **Username** e **Auth username** | `<SIP_LOGIN>` secondo la guida OlimonTel. |
| **General** | **Secret** | `<SIP_PASSWORD>` |
| **General** | **SIP Server** e **SIP Server Port** | `<SIP_DOMAIN>` e `<SIP_PORT>`. |
| **Advanced** | **Contact User** e **From User** | `<SIP_LOGIN>` secondo la guida OlimonTel. |
| **Advanced** | **From Domain** | Dominio indicato per il trunk. |

La procedura segue la sezione **chan_pjsip** della guida. [Guida OlimonTel per FreePBX](https://olimontel.it/guide-configurazioni/configurazione-voip-plus-olimontel-freepbx-trunk/)

## Asterisk con res_pjsip

Per un profilo con REGISTER puoi partire da questi due oggetti in `pjsip.conf`. Sostituisci i segnaposto localmente. Se il profilo richiede un trasporto specifico, associa all'oggetto `registration` il `transport` già configurato per quel profilo.

```ini
[olimontel-registration]
type=registration
server_uri=sip:<SIP_DOMAIN>:<SIP_PORT>
client_uri=sip:<SIP_LOGIN>@<SIP_DOMAIN>
outbound_auth=olimontel-auth

[olimontel-auth]
type=auth
auth_type=userpass
username=<SIP_AUTH_ID>
password=<SIP_PASSWORD>
```

Questi oggetti configurano la registrazione in uscita. Completa a parte l'endpoint, la destinazione delle chiamate in uscita e l'identificazione delle richieste entranti secondo il profilo e la versione di Asterisk. Associa poi l'endpoint al contesto di ingresso e aggiungi al dialplan la rotta del DID. Controlla `pjsip show registrations` dalla CLI. [Riferimento Asterisk res_pjsip](https://docs.asterisk.org/Configuration/Channel-Drivers/SIP/Configuring-res_pjsip/Configuring-Outbound-Registrations/)

## Yeastar

1. In **Extension and Trunk → Trunk → Add** crea un **Register Trunk** se il profilo assegnato prevede REGISTER. Abilita il trunk, se l'edizione mostra l'opzione.
2. Compila **Hostname/IP** e **Domain** con `<SIP_DOMAIN>`, quindi **Port** con `<SIP_PORT>`. L'esempio OlimonTel usa UDP e lascia disattivato **Enable Outbound Proxy**. Segui il trasporto e il proxy previsti dal tuo profilo.
3. Inserisci `<SIP_LOGIN>` in **Username**, `<SIP_AUTH_ID>` in **Authentication Name** e `<SIP_PASSWORD>` in **Password**. In **Advanced**, l'esempio OlimonTel indica G.729A seguito da G.711 A-law. Verifica i codec disponibili nella tua edizione.
4. In **DIDs/DDIs** inserisci `<DID>` nel formato effettivamente ricevuto. Associa trunk e DID alla rotta in ingresso, poi crea la rotta in uscita secondo il tuo piano di numerazione. [Guida OlimonTel per Yeastar](https://olimontel.it/guide-configurazioni/configurazione-sip-trunk-olimontel-yeastar-voip-plus/) · [Register Trunk su P-Series Cloud](https://help.yeastar.com/en/p-series-cloud-edition/administrator-guide/create-a-sip-register-trunk.html)

## 3CX

1. Nella console di amministrazione apri **Voice & Chat → Add Trunk**. Verifica quale template è consentito dalla tua edizione e dal tipo di hosting. Usa un template generico solo se disponibile per quella installazione.
2. Inserisci il **Main Trunk Number**. Per un profilo a registrazione compila registrar/porta e autenticazione con i valori assegnati nei campi esposti dal template. Per un profilo con autenticazione IP segui il template abilitato e i requisiti del trunk.
3. In **DID Numbers** aggiungi i numeri e assegna ciascun DID alla destinazione in **Call Handling** o **Users**. Il manuale 3CX indica il formato internazionale E.164 con `+`. Verifica che il formato consegnato dal trunk corrisponda a quello gestito dal template.
4. In **Outbound Rules** abilita il trunk per i soli pattern previsti dal piano di numerazione. Prova un numero consentito e verifica la rotta e il Caller ID. [Manuale 3CX per trunk SIP](https://www.3cx.com/docs/manual/sip-trunks/) · [Regole di uscita 3CX](https://www.3cx.com/docs/manual/outbound-call-routing/)

## Prova finale

Per un trunk con REGISTER controlla prima lo stato della registrazione. Chiama ciascun DID da una linea di prova e verifica destinazione e audio bidirezionale. In uscita prova la regola del trunk e il numero chiamante mostrato. Se il PBX riceve la chiamata ma non squilla l'interno previsto, verifica prima il DID ricevuto e la rotta associata. Per problemi dopo la risposta, passa alla [diagnosi di segnalazione e audio](nat-e-starlink.md).
