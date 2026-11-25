# Collegare piattaforme AI vocali via SIP

Usa queste indicazioni per verificare l'integrazione con il profilo SIP assegnato da OlimonTel. Le fonti dei produttori descrivono i campi e le funzioni delle piattaforme. La compatibilità con ogni combinazione di profilo, app, trasporto e direzione va verificata prima di mettere il numero in servizio.

## Decidere il percorso della chiamata

| Direzione | Percorso | Impostazione da confermare |
| --- | --- | --- |
| Ingresso | `<DID>` → trunk o PBX del cliente → `<SIP_URI_APP>` → agente | Dove si configura la rotta e in quale formato l'app deve ricevere il DID. |
| Uscita | Agente → `<TERMINATION_URI>` o server del trunk → destinatario | Quale destinazione SIP usare, formato del numero chiamato e Caller ID autorizzato. |

Verifica per ogni tratta il metodo di autenticazione, il trasporto e i codec comuni. Un'integrazione con SIP diretto richiede un profilo o un PBX che possa inoltrare la chiamata alla URI dell'app. Se il collegamento parte da un PBX, associa prima il DID di prova alla relativa rotta e limita l'uscita dell'agente alle destinazioni previste.

## Retell AI

1. In **Phone Numbers** scegli l'importazione tramite SIP trunking, inserisci il numero e assegna l'agente che deve rispondere.
2. Sul lato trunk o PBX del cliente configura la tratta in ingresso verso la destinazione SIP pubblicata da Retell per questa modalità. Se l'agente deve chiamare, imposta **Termination URI** con la destinazione assegnata per l'uscita.
3. Usa **Test SIP Connection** dove disponibile. Il test usa SIP `OPTIONS`. Dopo la risposta del server prova una vera chiamata in ogni direzione abilitata e controlla la negoziazione dell'audio. [Guida Retell](https://docs.retellai.com/deploy/custom-telephony)

## AutoCalls

1. In **Phone Numbers → Integrate SIP trunk** scegli **Phone Number (DID)** per un numero dedicato o il tipo **SIP Extension** per un interno, in base alla versione del pannello e al percorso concordato.
2. In **Outbound Settings**, inserisci in **SIP Address** il server del trunk o del tuo PBX senza porta, come richiesto dalla piattaforma. Scegli il formato di composizione richiesto dal trunk e configura l'autenticazione secondo il profilo.
3. Per l'ingresso usa **Our SIP Address** come destinazione della rotta sul lato trunk o PBX e applica il metodo di autenticazione concordato. Associa il numero all'assistente, chiama il DID e, se prevista, prova la funzione di chiamata in uscita. [Guida AutoCalls](https://docs.autocalls.ai/provisioning/sip-trunking/sip-integration)

## Altre piattaforme

| Piattaforma | Configurazione lato cliente |
| --- | --- |
| **ElevenLabs** | Importa il numero con **SIP Trunking** e assegnalo all'agente. Fai coincidere il numero importato con l'identificativo inviato nella URI in ingresso, incluso `+` se previsto. Per l'uscita compila **Address** con la destinazione assegnata e scegli un trasporto supportato da entrambe le parti. [Guida ElevenLabs](https://elevenlabs.io/docs/eleven-agents/phone-numbers/sip-trunking) |
| **Vapi** | Configura la risorsa trunk con il gateway assegnato. Collega il numero **BYO** al trunk e all'assistente. Verifica che la regione SIP corrisponda a quella della configurazione. [Guida Vapi](https://docs.vapi.ai/advanced/sip/sip-trunk) |
| **Grok Voice Agent** | Per un numero proprio in ingresso usa il percorso **Direct SIP**. Associa il numero alla relativa destinazione SIP e verifica che il PBX o il trunk usi il trasporto previsto prima di provare l'ingresso. [Guida xAI](https://docs.x.ai/developers/model-capabilities/audio/speech-to-speech/sip) |

## Prova con un numero di test

Usa un DID di prova. In ingresso verifica che risponda l'agente corretto e che l'audio funzioni nei due sensi. Se l'uscita è abilitata, verifica il numero chiamato e il Caller ID mostrato. Chiudi una chiamata per ciascun lato e controlla che termini anche sull'altro. Se la chiamata raggiunge la piattaforma ma l'agente non risponde, controlla l'associazione tra numero e agente. Se risponde senza audio, verifica codec comuni e percorso RTP.
