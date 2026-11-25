# Configurare Numero VoIP su dispositivi e adattatori ATA

Tieni a disposizione i [parametri assegnati](servizi-e-parametri.md). Quando configuri un ATA o un router con telefonia, verifica la porta analogica FXS a cui è collegato il telefono.

## Grandstream HT801 V2 e HT802 V2

1. Collega l'ATA alla rete via Ethernet e il telefono analogico alla porta **PHONE/FXS**. L'HT801 V2 ha una porta FXS. Sull'HT802 V2 prendi nota della porta che stai configurando e controlla di usare quella per le chiamate di prova.
2. In **Port Settings → FXS Port** seleziona la porta e apri **SIP Settings**. Imposta **Account Active** su **Yes**, compila i campi della tabella e lascia attiva la registrazione. Aggiungi un proxy o un server di riserva quando il profilo lo prevede.
3. Applica le modifiche. In **Status → Port Status** verifica **Registration** per quella porta. Se la porta risulta registrata ma il telefono resta muto, controlla il collegamento analogico e ripeti la prova sulla stessa porta.

| Campo Grandstream | Valore |
| --- | --- |
| **Primary SIP Server** | `<SIP_DOMAIN>`, con `:<SIP_PORT>` se serve specificare la porta nel campo server. |
| **SIP User ID** | `<SIP_LOGIN>` |
| **Authenticate ID** | `<SIP_AUTH_ID>` |
| **Authenticate Password** | `<SIP_PASSWORD>` |
| **SIP Transport** | Trasporto previsto dal profilo. |

I menu seguono la revisione V2. [Manuale HT80x V2](https://documentation.grandstream.com/knowledge-base/ht80x-v2-administration-guide/) · [FAQ ufficiale HT8xx V2](https://documentation.grandstream.com/knowledge-base/ht8xx-v2-faq/)

## Yealink

1. Nell'interfaccia del telefono apri **Account → Register**, seleziona l'account da configurare e abilita la linea con **Line Active**. Il percorso può variare con modello e firmware.
2. Compila **Register Name** e **User Name** con `<SIP_LOGIN>`, **Password** con `<SIP_PASSWORD>` e **SIP Server** con `<SIP_DOMAIN>`. La guida OlimonTel usa la login anche in **Label** e **Display Name**. Imposta la porta e il trasporto del profilo.
3. Nella sezione **Codec**, per il modello illustrato, la guida dà precedenza a G.729A e indica G.711 A-law come opzione successiva. Usa quelli disponibili sul modello e previsti dal profilo.
4. Salva e verifica **Registered**. Se regoli **Server Expires**, controlla il valore effettivamente accordato e ripeti la prova in ingresso dopo inattività. [Guida OlimonTel per Yealink](https://olimontel.it/guide-configurazioni/configurazione-telefoni-yealink-voip/)

## FRITZ!Box con funzioni di telefonia

1. Apri **Telefonia → Propri numeri → Nuovo numero** e scegli **Altro provider**. Nel profilo illustrato dalla guida inserisci `<SIP_LOGIN>` in **Numero per la registrazione**, **Numero interno** e **Nome utente**.
2. Inserisci `<SIP_PASSWORD>` e imposta **Registrar** e **Server Proxy** come indicato per il tuo profilo. Se usi una porta esplicita e l'interfaccia lo prevede, inseriscila come `<SIP_DOMAIN>:<SIP_PORT>`. Nelle **Funzioni** la guida indica l'opzione di registrazione tramite la connessione Internet, dove presente.
3. Dopo il salvataggio, controlla lo stato in **Propri numeri**. In **Dispositivi di telefonia** modifica il telefono collegato e assegna il numero per ingresso e uscita. Se il centralino o il servizio da chiamare usa un menu vocale, prova anche i toni DTMF.
4. Se il FRITZ!Box è dietro un altro router o su una rete CGNAT, verifica il comportamento del modello sul collegamento effettivo seguendo la [diagnosi NAT](nat-e-starlink.md). [Guida OlimonTel per FRITZ!Box](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/)

## Gigaset IP

1. Nell'interfaccia della base apri **Configurazioni → Telefono → Connessioni** e modifica un account VoIP. Inserisci login e password nelle impostazioni dell'account.
2. Apri **Mostra impostazioni avanzate** e usa il server assegnato per **Dominio**, **Indirizzo server proxy** e **Server di registrazione** secondo la guida. Nel profilo illustrato, la configurazione di partenza lascia disattivati **STUN** e il proxy in uscita.
3. Salva e aggiorna lo stato della connessione. Assegna poi la numerazione al portatile che deve ricevere o chiamare e fai entrambe le prove. [Guida OlimonTel per Gigaset](https://olimontel.it/guide-configurazioni/configurazione-gigaset-ip-telefono-voip/)

## Prova finale

Da un altro telefono chiama il numero e verifica lo squillo sul terminale collegato. Rispondi e controlla entrambe le direzioni dell'audio. Ripeti con una chiamata in uscita. Se vedi **Registered** ma uno dei test fallisce, usa la [guida di diagnosi](nat-e-starlink.md) in base al sintomo.
