# Diagnosticare il VoIP con NAT, CGNAT e Starlink

Starlink usa normalmente CGNAT per l'IPv4 predefinita. Il router locale può gestire il traffico della propria rete, ma un inoltro di porte sul router non rimuove il CGNAT a monte. Con un terminale SIP che si registra verso l'esterno, prova prima registrazione e chiamate sul percorso reale. Un trunk che richiede una connessione IPv4 iniziata dall'esterno va verificato separatamente. [Politiche IP di Starlink](https://starlink.com/support/article/1192f3ef-2a17-31d9-261a-a59d215629f4) · [Guida OlimonTel su Starlink](https://olimontel.it/blog/starlink-telefono-fisso-voip-satellite/)

| Sintomo | Verifica lato dispositivo |
| --- | --- |
| Il terminale non si registra | Controlla connettività e risoluzione del dominio. Verifica login SIP, dominio, porta remota e trasporto in base all'attivazione. Se la guida del modello prevede una porta alternativa, provala come unica modifica. |
| L'uscita funziona ma l'ingresso si perde dopo inattività | Controlla se l'account resta registrato nel tempo. Verifica il rinnovo della registrazione e l'uso del keepalive previsto dal terminale. Per un softphone ripeti la prova con l'app in primo piano e in background. |
| La chiamata risponde ma l'audio manca in un senso | Controlla quale partecipante non sente l'altro e ripeti il test in ingresso e in uscita. Verifica i codec comuni, il percorso RTP e le impostazioni NAT previste dal manuale. |
| L'audio o l'ingresso falliscono con due router in cascata | Ripeti la stessa prova con il terminale collegato alla rete del router principale, se possibile. Confronta registrazione, ingresso e audio prima di cambiare configurazione. |

Verifica se il router include una funzione **SIP ALG** o un'opzione equivalente di riscrittura dei messaggi SIP. Se la guida del dispositivo ne prevede la disattivazione, prova la sola modifica su quell'opzione e mantieni attive le protezioni del firewall. Il keepalive SIP mantiene il flusso del terminale e va verificato a parte. Tratta STUN come una scelta legata al modello e alla rete.

Per ogni prova annota il modello, l'esito della registrazione, la direzione della chiamata e l'audio. Ripeti il controllo dopo un periodo di inattività e ripristina l'impostazione precedente se la modifica peggiora l'esito. [Informazioni tecniche OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [FAQ OlimonTel](https://olimontel.it/faq/)
