# Diagnosticare il VoIP con NAT, CGNAT e Starlink

La politica IPv4 predefinita di Starlink usa CGNAT. L'inoltro porte sul router del cliente vale per il NAT locale e lascia in funzione il CGNAT a monte. Con **Numero VoIP**, inizia da un telefono IP, ATA o softphone che invia la registrazione SIP verso OlimonTel. Per **VoIP PLUS** controlla il profilo del trunk. Se richiede un ingresso IPv4 iniziato dall'esterno, verifica che il PBX sia raggiungibile nel modo richiesto, per esempio tramite una soluzione ospitata compatibile o un'opzione IPv4 pubblica disponibile sul piano. [Politiche IP di Starlink](https://starlink.com/it/support/article/1192f3ef-2a17-31d9-261a-a59d215629f4) · [Guida OlimonTel su Starlink](https://olimontel.it/blog/starlink-telefono-fisso-voip-satellite/)

## Prova iniziale su Starlink

1. Collega il terminale alla rete Starlink. Per un ATA usa Ethernet quando disponibile. Se ci sono due router in cascata, identifica a quale dei due è collegato il terminale.
2. Inserisci dominio, porta e trasporto del [profilo assegnato](servizi-e-parametri.md). Avvia la registrazione prevista dal profilo. Inizia con la configurazione documentata del modello e mantieni attivo il firewall.
3. Con un secondo telefono prova ingresso e uscita. Parla in entrambe le direzioni e verifica che entrambe le parti sentano. Ripeti l'ingresso dopo un periodo di inattività e, se rilevante, dopo una riconnessione alla rete.
4. Registra l'esito prima di cambiare un'impostazione. Per un confronto utile, ripeti sullo stesso terminale e sullo stesso account. Modifica una variabile per volta e ripristina il valore precedente se la prova peggiora.

## Dove cercare in base al sintomo

| Sintomo | Verifica lato dispositivo |
| --- | --- |
| Il terminale non si registra | Controlla connettività e risoluzione del dominio. Verifica login SIP, dominio, porta remota e trasporto in base all'attivazione. Se la guida del modello prevede una porta alternativa, provala come unica modifica. |
| L'uscita funziona ma l'ingresso si perde dopo inattività | Controlla lo stato SIP prima e dopo l'attesa. Verifica scadenza effettiva, rinnovo della registrazione e keepalive, se documentati per il terminale. Per un softphone ripeti con l'app in primo piano e con lo schermo spento. |
| La chiamata risponde ma l'audio manca in un senso | Annota quale partecipante non sente l'altro e ripeti in ingresso e in uscita. Controlla il codec comune e il percorso RTP. Su un PBX verifica l'indirizzo e la porta audio annunciati in SDP rispetto al percorso di rete del PBX. |
| L'audio o l'ingresso falliscono con due router in cascata | Ripeti la stessa prova con il terminale collegato alla rete del router principale, se possibile. Confronta registrazione, ingresso e audio prima di cambiare configurazione. |

## Impostazioni NAT da verificare

- **Rinnovo e keepalive.** Il rinnovo aggiorna la registrazione e il keepalive può mantenere attivo il flusso attraverso il NAT. Verifica separatamente l'intervallo richiesto dal terminale e la scadenza effettiva restituita dal registrar. Parti dalle indicazioni del produttore e dal profilo assegnato. [Informazioni tecniche OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)
- **SIP ALG.** Se il router comprende una funzione di riscrittura SIP e la documentazione prevede una prova con SIP ALG disattivato, modifica solo quella voce. Ripeti ingresso, uscita e audio con le protezioni del firewall attive.
- **STUN e rport.** STUN aiuta il terminale a rilevare la mappatura NAT. `rport` consente di inviare la risposta SIP alla porta sorgente da cui è arrivata la richiesta. Quando la guida del modello documenta queste opzioni, ripeti la stessa prova dopo ogni modifica. [RFC 8489 su STUN](https://www.rfc-editor.org/rfc/rfc8489.html) · [RFC 3581 su rport](https://www.rfc-editor.org/rfc/rfc3581.html) · [Guida Zoiper Android](https://olimontel.it/guide-configurazioni/configurazione-app-zoiper-android/)
