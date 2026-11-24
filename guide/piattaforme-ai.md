# Collegare piattaforme AI vocali via SIP

Usa queste indicazioni per verificare l'integrazione con il profilo SIP assegnato da OlimonTel. Le fonti dei produttori descrivono i campi e le funzioni delle piattaforme. La compatibilità con ogni combinazione di profilo, app, trasporto e direzione va verificata prima di mettere il numero in servizio.

## Dati da confermare prima della prova

- **In ingresso** — `<DID>`, formato del numero, `<SIP_URI_APP>` e agente a cui assegnarlo.
- **In uscita** — `<TERMINATION_URI>` o dominio del trunk assegnato e numero autorizzato per la presentazione del chiamante.
- **Per entrambe le direzioni** — metodo di autenticazione, trasporto SIP e codec comuni. Se l'app richiede SIP diretto, conferma il tipo di trunk prima di usare una configurazione con REGISTER.

## Dove intervenire nella piattaforma

| Piattaforma | Configurazione lato cliente |
| --- | --- |
| **Retell AI** | In **Phone Numbers** importa il numero tramite SIP trunking e assegnalo all'agente. La destinazione Retell riguarda l'ingresso. Inserisci in **Termination URI** la destinazione assegnata per l'uscita. Usa **Test SIP Connection** se disponibile, poi fai una prova di chiamata per ogni direzione. [Guida Retell](https://docs.retellai.com/deploy/custom-telephony) |
| **AutoCalls** | In **Phone Numbers** usa **Integrate SIP trunk**. Scegli **Phone Number (DID)** per una numerazione dedicata o **PBX Extension** per un interno di un proprio centralino. Verifica il formato DID, la modalità SIP e l'assegnazione all'assistente. [Guida AutoCalls](https://docs.autocalls.ai/provisioning/sip-trunking/sip-integration) |
| **ElevenLabs** | Importa il numero con **SIP Trunking** e assegnalo all'agente. Controlla che l'identificativo della URI in ingresso corrisponda al numero importato, incluso il segno più quando previsto. Per l'uscita verifica il campo **Address** e il trasporto concordato. [Guida ElevenLabs](https://elevenlabs.io/docs/eleven-agents/phone-numbers/sip-trunking) |
| **Vapi** | Collega un numero **BYO** alla risorsa trunk SIP e all'assistente. Usa un gateway assegnato e verifica che regione della configurazione e regione SIP coincidano. [Guida Vapi](https://docs.vapi.ai/advanced/sip/sip-trunk) |
| **Grok Voice Agent** | Per un numero proprio in ingresso verifica la modalità **Direct SIP**, l'associazione del numero e la relativa destinazione. Concorda l'autenticazione e il trasporto prima del test. [Guida xAI](https://docs.x.ai/developers/model-capabilities/audio/speech-to-speech/sip) |

## Prova con un numero di test

Fai una chiamata entrante e verifica che arrivi all'agente configurato. Se il profilo abilita l'uscita, prova anche quella e verifica il numero chiamante mostrato. Controlla audio bidirezionale, durata e chiusura della chiamata. Un test SIP di raggiungibilità verifica solo la risposta del server alla richiesta di prova.
