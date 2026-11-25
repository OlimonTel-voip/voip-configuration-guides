# Configurare Numero VoIP su dispositivi e adattatori ATA

Tieni a disposizione i [parametri assegnati](servizi-e-parametri.md). Quando configuri un ATA o un router con telefonia, verifica la porta analogica FXS a cui è collegato il telefono.

## Telefoni IP

### Yealink T33G, T43U, T46U, T54W e T57W

1. Nell'interfaccia del telefono apri **Account → Register**, seleziona l'account e attiva **Line Active**.
2. Usa `<SIP_LOGIN>` in **User Name**, `<SIP_AUTH_ID>` in **Register Name**, `<SIP_PASSWORD>` in **Password** e `<SIP_DOMAIN>` in **SIP Server**. Imposta porta remota e trasporto del profilo. Nell'esempio OlimonTel il nome di autenticazione coincide con la login.
3. In **Codec** scegli quelli comuni al modello e alla linea. La guida OlimonTel dà precedenza a G.729A e include G.711 A-law. Salva e controlla **Registered**.

**Prova su ciascun modello.** Seleziona il tasto della linea configurata e chiama da quella linea. Richiama dall'altro telefono e verifica che squilli lo stesso account. Se ci sono più account, controlla l'etichetta della linea usata. Ascolta l'audio nei due sensi. Se regoli **Server Expires**, controlla la scadenza effettiva e ripeti la prova in ingresso dopo inattività. [Guida OlimonTel per Yealink](https://olimontel.it/guide-configurazioni/configurazione-telefoni-yealink-voip/) · [Registrazione account e modelli Yealink](https://support.yealink.com/docs/sip-t53/account-registration/cb7e0331cba0407a975f6e76e5309930)

### Grandstream GRP2612, GRP2613 e GRP2614

In **Accounts** seleziona l'account e apri **General Settings**. Attiva **Account Active**. Inserisci `<SIP_DOMAIN>` in **SIP Server**, con la porta remota esplicita se richiesta. Usa `<SIP_LOGIN>` in **SIP User ID**, `<SIP_AUTH_ID>` in **SIP Authentication ID** e `<SIP_PASSWORD>` in **SIP Authentication Password**. In **SIP Settings** mantieni attiva **SIP Registration** e seleziona **SIP Transport** secondo il profilo. Compila **Outbound Proxy** solo se previsto.

**Prova su ciascun modello.** Controlla in **Status → Account Status** lo stato della registrazione. Seleziona la linea corrispondente sul telefono, chiama un secondo telefono e fatti richiamare. Verifica che lo squillo arrivi sull'account configurato e che l'audio funzioni nelle due direzioni. [Manuale Grandstream GRP261x](https://documentation.grandstream.com/knowledge-base/grp261x-grp262x-grp263x-series-administration-guide/) · [Parametri Numero VoIP OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)

### Panasonic KX-UT113, KX-UT123, KX-UT133 e KX-UT136

Nella configurazione web apri **VoIP → SIP Settings → Line N** per la linea in uso. In **SIP URI** usa `<SIP_LOGIN>@<SIP_DOMAIN>` come illustrato da OlimonTel, oppure la forma completa `sip:<SIP_LOGIN>@<SIP_DOMAIN>` se richiesta dal firmware. Usa `<SIP_AUTH_ID>` in **Authentication ID** e `<SIP_PASSWORD>` in **Authentication Password**. Imposta **Registrar Server Address** e **Service Domain** con `<SIP_DOMAIN>` e **Registrar Server Port** con `<SIP_PORT>`.

**Prova su ciascun modello.** Controlla la registrazione della linea configurata e usala per una chiamata in uscita. Da un altro numero richiama la linea e verifica squillo e audio nei due sensi. [Guida OlimonTel per Panasonic KX-UT](https://olimontel.it/guide-configurazioni/configurazione-panasonic-telefoni-voip/) · [Manuali Panasonic per le versioni europee KX-UT1xx](https://docs.connect.panasonic.com/pcc/support/sipphone/download/UT1/others.html)

## Adattatori ATA e gateway FXS

### Cisco SPA112 e SPA122

Entrambi hanno due porte per telefoni analogici. Cisco indica il 31 maggio 2025 come ultima data di supporto. [Avviso Cisco di fine supporto](https://www.cisco.com/c/en/us/products/collateral/unified-communications/small-business-voice-gateways-ata/eos-eol-notice-c51-743206.html)

1. In **Voice → Line 1** o **Line 2** seleziona la linea della presa **PHONE 1** o **PHONE 2** e imposta **Line Enable** su **Yes**.
2. In **Proxy and Registration**, inserisci `<SIP_DOMAIN>` in **Proxy**, indica la porta remota nell'indirizzo del proxy se richiesta e imposta **Register** su **Yes**. Attiva **Use Outbound Proxy** e compila **Outbound Proxy** se previsto dal profilo. In **SIP Settings**, scegli il **SIP Transport** assegnato. La voce **SIP Port** regola la porta locale della linea.
3. In **Subscriber Information**, inserisci `<SIP_LOGIN>` in **User ID** e `<SIP_PASSWORD>` in **Password**. Se il profilo prevede un identificativo di autenticazione separato, imposta **Use Auth ID** su **Yes** e usa `<SIP_AUTH_ID>` in **Auth ID**. Salva con **Submit**. [Guida OlimonTel per SPA112/SPA122](https://olimontel.it/guide-configurazioni/configurazione-ata-cisco-voip/) · [Manuale Cisco per le impostazioni voce](https://www.cisco.com/c/en/us/td/docs/voice_ip_comm/csbpvga/spa100-200/admin_guide_SPA100/spa100_ag/voice.html)

**Prova su SPA112 e SPA122.** In **Voice → Information** verifica **Registration State** per la linea usata. Chiama il Numero VoIP da un altro telefono e verifica lo squillo sulla porta associata. Rispondi, controlla l'audio nei due sensi e richiama dalla stessa porta. Se usi due account, ripeti per ognuno.

### Grandstream HT801 e HT802 di prima generazione

Apri direttamente la scheda **FXS PORT** dell'HT801 o quella della porta desiderata sull'HT802. Imposta **Account Active** e **SIP Registration** su **Yes**. Usa il dominio e la porta remota assegnati in **Primary SIP Server**, `<SIP_LOGIN>` in **SIP User ID**, `<SIP_AUTH_ID>` in **Authenticate ID** e `<SIP_PASSWORD>` in **Authenticate Password**. Imposta **SIP Transport** secondo il profilo. Aggiungi **Outbound Proxy** se previsto, poi applica le modifiche.

**Prova.** Apri **Status → Port Status** e controlla **Registration**. Su HT801 verifica ingresso e uscita dalla porta unica. Su HT802, ripeti su ciascuna porta configurata e verifica che il numero chiamato faccia squillare il telefono assegnato. [Guida OlimonTel per HT80x di prima generazione](https://olimontel.it/guide-configurazioni/configurazione-ata-grandstream-voip/) · [Manuale Grandstream HT80x](https://documentation.grandstream.com/knowledge-base/ht80x-administration-guide/)

### Grandstream HT801 V2 e HT802 V2

1. Collega l'ATA alla rete via Ethernet e il telefono analogico alla porta **PHONE/FXS**. L'HT801 V2 ha una porta FXS. Sull'HT802 V2 prendi nota della porta che stai configurando e controlla di usare quella per le chiamate di prova.
2. In **Port Settings → FXS Port** seleziona la porta e apri **SIP Settings**. Imposta **Account Active** su **Yes**, compila i campi della tabella e lascia attiva la registrazione. Aggiungi un proxy o un server di riserva quando il profilo lo prevede.
3. Applica le modifiche. In **Status → Port Status** verifica **Registration** per quella porta.

| Campo Grandstream | Valore |
| --- | --- |
| **Primary SIP Server** | `<SIP_DOMAIN>`, con `:<SIP_PORT>` se serve specificare la porta nel campo server. |
| **SIP User ID** | `<SIP_LOGIN>` |
| **Authenticate ID** | `<SIP_AUTH_ID>` |
| **Authenticate Password** | `<SIP_PASSWORD>` |
| **SIP Transport** | Trasporto previsto dal profilo. |

**Prova.** Su HT801 V2 effettua e ricevi una chiamata dalla porta unica. Su HT802 V2 ripeti su ogni porta configurata e verifica che squilli quella associata al numero chiamato. Se compare **Registered** e il telefono resta muto, controlla il collegamento analogico. I menu seguono la revisione V2. [Manuale HT80x V2](https://documentation.grandstream.com/knowledge-base/ht80x-v2-administration-guide/) · [FAQ ufficiale HT8xx V2](https://documentation.grandstream.com/knowledge-base/ht8xx-v2-faq/)

### Grandstream HT812 V2, HT814 V2 e HT818 V2

1. Apri **Port Settings → Profile N → General Settings → Account Registration**. Imposta **Primary SIP Server** con `<SIP_DOMAIN>` e la porta remota se richiesta. Tieni attiva **SIP Registration**. Imposta **SIP Transport** secondo il profilo e aggiungi **Outbound Proxy** se previsto.
2. In **Port Settings → FXS Port**, per ogni porta che usi, imposta **SIP User ID**, **Authenticate ID** e **Authenticate Password** rispettivamente con `<SIP_LOGIN>`, `<SIP_AUTH_ID>` e `<SIP_PASSWORD>`. Seleziona il **Profile ID** configurato, abilita la porta e salva.

| Modello | Porte FXS | Prova dopo aver verificato **Status → Port Status → Registration** |
| --- | --- | --- |
| **HT812 V2** | 2 | Fai squillare il telefono sulla porta assegnata e richiama dalla stessa porta. Se usi entrambe, verifica ogni associazione. |
| **HT814 V2** | 4 | Chiama ogni numero configurato e verifica che risponda il telefono sulla porta corrispondente. Prova anche l'uscita da quelle porte. |
| **HT818 V2** | 8 | Confronta numero, profilo e porta in uso. Prova ingresso e uscita da ogni porta configurata, compresa l'ultima se usata. |

[Manuale Grandstream HT81x V2](https://documentation.grandstream.com/knowledge-base/ht81x-v2-administration-guide/) · [Parametri Numero VoIP OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)

### Linksys PAP2T e SPA2102

1. Apri **Line 1** o **Line 2** nel pannello voce dell'ATA, secondo la presa a cui è collegato il telefono. Se compare **Line Enable**, attiva la linea.
2. In **Proxy and Registration** compila **Proxy** con il dominio SIP assegnato, includendo la porta remota se richiesta dal profilo. Imposta **Register** su **Yes**. Configura **Outbound Proxy** quando è previsto.
3. In **Subscriber Information** usa `<SIP_LOGIN>` in **User ID** e `<SIP_PASSWORD>` in **Password**. Per un profilo con identificativo di autenticazione separato attiva **Use Auth ID** e inserisci `<SIP_AUTH_ID>` in **Auth ID**. La guida OlimonTel usa la login anche in **Display Name**. Salva le modifiche.

**Prova su PAP2T e SPA2102.** Nella pagina **Info** controlla **Registration State** della linea scelta. Chiama il numero da un telefono esterno, verifica squillo e audio nei due sensi, poi prova una chiamata in uscita dalla stessa porta. Se la seconda porta è configurata, ripeti la prova per la sua numerazione. [Guida OlimonTel per Linksys SPA](https://olimontel.it/guide-configurazioni/configurazione-cisco-linksys-spa-voip/) · [Manuale Cisco per PAP2T e SPA2102](https://community.cisco.com/legacyfs/online/legacy/7/6/4/75467-ATA_AG_v3_NC-WEB.pdf)

### Yeastar TA100 e TA200

Apri **Gateway → Port Settings → FXS Port** e modifica la porta. In **Basic**, usa `<SIP_LOGIN>` in **User Name**, `<SIP_AUTH_ID>` in **Authentication Name** e `<SIP_PASSWORD>` in **Password**. Inserisci `<SIP_DOMAIN>` in **Hostname/IP** e **Domain**, con `<SIP_PORT>` nel campo della porta accanto al server. Seleziona **Transport**. Se il profilo richiede un proxy, compila **Outbound Proxy Server**. Per **From User** usa la login se il profilo corrisponde a quello illustrato da OlimonTel. Imposta **DID Number** secondo il formato associato alla porta.

**Prova.** Su TA100 chiama il numero da un'altra linea, rispondi sull'unica porta e richiama. Su TA200, se usi due numeri, verifica che ciascuno faccia squillare la porta assegnata e prova a chiamare da entrambe. [Guida OlimonTel per gateway Yeastar](https://olimontel.it/guide-configurazioni/configurazione-voip-olimontel-yeastar-gateway-fxs/) · [Manuale Yeastar TA100/TA200](https://help.yeastar.com/download/docs/ta100-ta200-user-manual-en.pdf)

### Yeastar TA400 e TA800

In **VoIP Server Settings**, crea o modifica un profilo di tipo **SIP**. Imposta **Hostname/IP**, **Port**, **Domain** e **Transport** con i valori della linea. Usa **Port Register** quando ciascuna porta ha un account assegnato. In **Gateway → Port List** modifica ciascuna porta in uso, seleziona il profilo **VoIP Server** e compila **User Name**, **Authentication Name** e **Password** con i dati SIP della porta.

**Prova.** Per TA400 (quattro porte) e TA800 (otto porte), verifica nello stato del gateway la registrazione di ciascuna porta configurata. Chiama i numeri uno per volta, confronta squillo e porta, poi fai una chiamata in uscita da ciascuna porta usata. [Guida OlimonTel per gateway Yeastar](https://olimontel.it/guide-configurazioni/configurazione-voip-olimontel-yeastar-gateway-fxs/) · [Documentazione Yeastar per TA400/TA800](https://help.yeastar.com/en/voip-gateways/)

### Keenetic Linear KN-3110

Linear aggiunge due porte FXS a un router Keenetic compatibile con USB e con il componente **Keenetic Phone Station**. I menu indicati provengono dai manuali Titan e Titan SE. [Scheda Linear KN-3110](https://keenetic.com/it/keenetic-linear) · [Configurazione di Phone Station con Linear](https://support.keenetic.com/titan/kn-1812/it/19332-setting-up-phone-station-with-a-linear-adapter.html)

1. Nelle opzioni dei componenti di KeeneticOS installa **Keenetic Phone Station**. Collega Linear via USB al router e il telefono analogico alla presa FXS che vuoi usare.
2. Apri **Telephony → Telephone lines**, aggiungi una linea e attiva **Enable SIP registration**. Per la configurazione manuale seleziona **Other** in **Provider**.
3. Inserisci `<SIP_DOMAIN>` in **SIP registrar** e in **SIP domain** per il profilo che usa il dominio assegnato in entrambi i campi. Se il registrar usa una porta diversa da quella predefinita, scrivi `<SIP_DOMAIN>:<SIP_PORT>` nel campo **SIP registrar**. Compila **SIP proxy** con i valori previsti dal profilo.
4. Usa `<SIP_LOGIN>` in **SIP User ID**, `<SIP_AUTH_ID>` in **SIP Auth ID** e `<SIP_PASSWORD>` in **Password**. Seleziona il **SIP transport** assegnato. Tra i codec di Linear abilita **G.711a** (A-law/PCMA), previsto da Numero VoIP. Per i toni DTMF seleziona **RFC2833**.
5. In **Phone Station** apri le impostazioni della porta FXS collegata e abilita **Incoming** e **Outgoing** per la nuova linea. [Parametri Numero VoIP OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Campi della linea SIP](https://support.keenetic.com/titan-se/kn-4210/it/19336-setting-up-a-telephone-line.html) · [Impostazioni della porta FXS](https://support.keenetic.com/titan-se/kn-4210/it/19334-setting-up-an-fxs-port.html)

**Prova.** Controlla **Registered** in **Telephone lines**. Chiama il Numero VoIP da un altro telefono e verifica lo squillo sulla porta assegnata. Rispondi e controlla l'audio nei due sensi, poi richiama da quella porta. Se hai configurato entrambe le porte, ripeti la prova per ciascuna associazione.

## Gateway SIP con interfaccia ISDN

### Mediatrix serie 4400

La guida OlimonTel documenta un gateway della serie 4400 collegato via **ISDN BRI** a un centralino. Usa i passaggi di registrazione per il profilo SIP con **REGISTER**. Per un profilo con autenticazione IP, usa i parametri e le rotte forniti per quel trunk.

1. In **SIP → Gateway** crea un gateway di tipo **Trunk** e associa le interfacce di segnalazione e audio previste dalla rete del cliente.
2. In **SIP → Servers** seleziona il gateway appena creato e compila **Registrar Host** con `<SIP_DOMAIN>:<SIP_PORT>`. Imposta **Proxy Host** e **Outbound Proxy Host** secondo il profilo. Il profilo con registrazione illustrato da OlimonTel usa l'indirizzo del registrar anche per i due campi proxy.
3. In **SIP → Registration**, imposta **Unit Registration → User Name** con `<SIP_LOGIN>` e abilita la registrazione per quel gateway. In **SIP → Authentication** seleziona **Gateway** come **Criteria**, associa lo stesso gateway e compila **User Name** con `<SIP_AUTH_ID>` e **Password** con `<SIP_PASSWORD>`. Compila **Realm** se previsto dal profilo. Applica e controlla lo stato **Registered**.
4. In **Call Router → Route Config** associa in ingresso il numero nel formato ricevuto alla porta BRI, o al gruppo di porte, del centralino. Configura anche la rotta in uscita dalla BRI verso il gateway SIP autorizzato. [Guida OlimonTel per Mediatrix](https://olimontel.it/guide-configurazioni/configurazione-mediatrix-voip/) · [Autenticazione SIP M5 Technologies](https://documentation.m5technologies.com/sip-authentication) · [Call Router M5 Technologies](https://documentation.m5technologies.com/call-router)

**Prova.** Chiama il numero da una linea esterna. Verifica che sul centralino risponda la destinazione collegata alla BRI prevista e che l'audio funzioni nei due sensi. Effettua poi una chiamata da un interno del centralino attraverso il gateway e controlla il numero chiamante mostrato e la chiusura della chiamata.

## FRITZ!Box con funzioni di telefonia

1. Apri **Telefonia → Propri numeri → Nuovo numero** e scegli **Altro provider**. Nel profilo illustrato dalla guida inserisci `<SIP_LOGIN>` in **Numero per la registrazione**, **Numero interno** e **Nome utente**.
2. Inserisci `<SIP_PASSWORD>` in **Password** e `<SIP_DOMAIN>` in **Registrar**. Per **Server Proxy** usa il valore previsto dal profilo. Se il firmware richiede la porta nello stesso campo, usa la forma `<SIP_DOMAIN>:<SIP_PORT>` per il registrar. Nelle **Funzioni** la guida indica l'opzione di registrazione tramite la connessione Internet, dove presente.
3. Dopo il salvataggio, controlla lo stato in **Propri numeri**. In **Dispositivi di telefonia** associa il numero per **Chiamate in uscita** e scegli i numeri a cui quel telefono deve rispondere. Se usi un menu vocale, prova anche i toni DTMF.
4. Se il FRITZ!Box è dietro un altro router o su una rete CGNAT, verifica il comportamento del modello sul collegamento effettivo seguendo la [diagnosi NAT](nat-e-starlink.md). [Guida OlimonTel per FRITZ!Box](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/)

| Modello | Cosa configurare dopo il numero SIP | Prova |
| --- | --- | --- |
| **FRITZ!Box 7530 AX** | Associa la presa analogica o il portatile DECT nelle impostazioni del dispositivo. | Chiama il numero da un secondo telefono. Verifica che squilli l'apparecchio scelto e che da quello stesso apparecchio l'uscita mostri il numero previsto. [Scheda 7530 AX](https://fritz.com/it-it/products/fritz-box-7530-ax-20002944) |
| **FRITZ!Box 7590 AX** | Se usi più telefoni, controlla a quale presa FON o portatile DECT è assegnata ciascuna numerazione. | Chiama ogni numero e verifica che squilli solo il dispositivo assegnato. Prova l'uscita da ogni apparecchio configurato. [Scheda 7590 AX](https://fritz.com/it-it/products/fritz-box-7590-ax-20002999) |
| **FRITZ!Box 5590 Fiber** | Per un telefono analogico seleziona la presa effettivamente utilizzata nel menu di configurazione del dispositivo. | Dopo che il numero risulta attivo, verifica squillo in ingresso e audio nei due sensi tramite quella presa. Prova poi l'uscita dallo stesso apparecchio. [Telefono analogico su 5590 Fiber](https://fritz.com/it-it/apps/knowledge-base/FRITZ-Box-5590-Fiber/3285_Configurare-un-telefono-analogico-nel-FRITZ-Box) |
| **FRITZ!Box 4060** | Configura il telefono DECT o IP come dispositivo di telefonia, poi assegna la linea in ingresso e uscita. | Chiama da e verso il terminale DECT o IP e verifica la linea utilizzata. Per una chiamata dall'app, vedi **FRITZ!App Fon** nella [guida alle app](softphone.md). [Scheda 4060](https://fritz.com/it-it/products/fritz-box-4060-20002952) |

## Altri router con porta per telefono

### Huawei B525s

La procedura si applica al firmware che espone **VoIP → Account SIP** e **Server SIP**. In **Account SIP** aggiungi un account e usa `<SIP_LOGIN>` nei campi **Account SIP** e **Nome utente**. Inserisci `<SIP_PASSWORD>` in **Password**. In **VoIP → Server SIP** compila **Proxy**, **Registrazione** e **Dominio** con il server assegnato per il profilo illustrato. Per **Proxy** e **Registrazione**, imposta le porte remote assegnate. Per i toni DTMF, la guida indica **RFC 2833**.

**Prova.** Collega il telefono alla porta telefonica del router. Sulla connessione LTE che userai, chiama il Numero VoIP da un secondo telefono. Verifica squillo e audio bidirezionale e richiama dalla stessa presa. [Guida OlimonTel per Huawei B525s](https://olimontel.it/guide-configurazioni/configurazione-router-huawei-4g-voip/)

### TP-Link Archer VR1210v e router con porta FXS

La guida OlimonTel copre i modem router TP-Link con **Telefonia** o **VoIP** nel pannello. Archer VR1210v è un esempio con funzione VoIP documentata da TP-Link.

1. In **Avanzate → Telefonia → Numero telefonico** aggiungi un account SIP. Sui firmware con la voce **VoIP**, apri la pagina **Telephone Numbers**.
2. Compila **Numero telefono** con `<SIP_LOGIN>`, **Autenticazione ID** con `<SIP_AUTH_ID>` e **Password** con `<SIP_PASSWORD>`. Nel profilo OlimonTel illustrato, **Registrar Address**, **SIP Proxy** e **Outbound Proxy** usano il dominio assegnato. Imposta **Proxy Port** con la porta remota prevista dal profilo.
3. In **Phone Devices** associa il numero alla presa telefonica per le chiamate entranti e uscenti.

**Prova.** Controlla **Registered** in **Telephone Numbers**. Chiama il numero da un altro telefono, rispondi dalla presa assegnata e ascolta l'audio nei due sensi. Prova poi l'uscita dalla stessa presa. [Guida OlimonTel per router TP-Link](https://olimontel.it/guide-configurazioni/guida-configurazione-voip-router-tp-link/) · [Configurazione VoIP TP-Link](https://www.tp-link.com/it/support/faq/2020/) · [Scheda VR1210v](https://service-provider.tp-link.com/it/vdsl/vr1210v/)

## Basi cordless Gigaset IP

1. Nell'interfaccia della base apri **Configurazioni → Telefono → Connessioni** e modifica un account VoIP. Inserisci login e password nelle impostazioni dell'account.
2. Apri **Mostra impostazioni avanzate** e usa il server assegnato per **Dominio**, **Indirizzo server proxy** e **Server di registrazione** secondo la guida. Nel profilo illustrato, la configurazione di partenza lascia disattivati **STUN** e il proxy in uscita.
3. Salva e aggiorna lo stato della connessione. Assegna poi la numerazione al portatile che deve ricevere o chiamare e fai entrambe le prove. [Guida OlimonTel per Gigaset](https://olimontel.it/guide-configurazioni/configurazione-gigaset-ip-telefono-voip/)

## Prova finale

Da un altro telefono chiama il numero e verifica lo squillo sul terminale collegato. Rispondi e controlla entrambe le direzioni dell'audio. Ripeti con una chiamata in uscita. Se vedi **Registered** ma uno dei test fallisce, usa la [guida di diagnosi](nat-e-starlink.md) in base al sintomo.

Per altri apparati consulta il [catalogo pubblico OlimonTel per Numero VoIP](https://olimontel.it/categorie-configurazioni/apparati-dispositivi-voip/).
