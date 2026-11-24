# Configurare Numero VoIP su dispositivi e adattatori ATA

Tieni a disposizione i [parametri assegnati](servizi-e-parametri.md). Quando configuri un ATA o un router con telefonia, verifica la porta analogica FXS a cui è collegato il telefono.

## Grandstream HT801 V2 e HT802 V2

1. Apri la pagina della porta FXS che userai e attiva l'account per quella porta.
2. Inserisci `<SIP_DOMAIN>` in **Primary SIP Server**, `<SIP_LOGIN>` in **SIP User ID** e l'identificativo assegnato in **Authenticate ID**. Usa `<SIP_PASSWORD>` in **Authenticate Password**.
3. Mantieni la registrazione SIP attiva per un profilo Numero VoIP con registrazione. Seleziona il trasporto previsto dal servizio. Aggiungi proxy e server di riserva soltanto se previsti dalla configurazione assegnata.
4. Dopo aver applicato le modifiche, controlla **Status → Port Status → Registration** e prova il telefono collegato. L'HT801 V2 ha una porta FXS. Sull'HT802 V2 verifica l'account della porta effettivamente in uso.

I menu V2 seguono il manuale Grandstream della revisione V2. [FAQ ufficiale HT8xx V2](https://documentation.grandstream.com/knowledge-base/ht8xx-v2-faq/) · [Guida al servizio Numero VoIP](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)

## Yealink

Nell'account SIP del telefono completa **Register Name** e **User Name** con `<SIP_LOGIN>`, **Password** con `<SIP_PASSWORD>` e **SIP Server** con `<SIP_DOMAIN>`. La guida OlimonTel usa la login anche nei campi **Label** e **Display Name**. Verifica trasporto, porta remota e stato **Registered**. Se imposti **Server Expires**, distingui il valore richiesto dal telefono da quello effettivamente accordato nella registrazione. I menu possono variare per modello e firmware. [Guida OlimonTel per Yealink](https://olimontel.it/guide-configurazioni/configurazione-telefoni-yealink-voip/)

## FRITZ!Box con funzioni di telefonia

In **Telefonia → Propri numeri** aggiungi un numero e scegli **Altro provider**. La guida OlimonTel usa `<SIP_LOGIN>` nei campi del numero per la registrazione, del numero interno e del nome utente. Imposta `<SIP_PASSWORD>` e usa il dominio assegnato nei campi **Registrar** e **Server Proxy** indicati dalla guida. Dopo la registrazione assegna la numerazione al dispositivo telefonico per le direzioni che ti servono. [Guida OlimonTel per FRITZ!Box](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/)

## Gigaset IP

Dal configuratore della base modifica una connessione di telefonia VoIP. Inserisci login, password e dominio nei campi previsti dalla guida del modello. Dopo il salvataggio controlla lo stato della connessione e l'assegnazione del numero al portatile che userai per rispondere e chiamare. [Guida OlimonTel per Gigaset](https://olimontel.it/guide-configurazioni/configurazione-gigaset-ip-telefono-voip/)

## Prova finale

Da un altro telefono chiama il numero e verifica lo squillo sul terminale collegato. Rispondi e controlla entrambe le direzioni dell'audio. Ripeti con una chiamata in uscita. Se vedi **Registered** ma uno dei test fallisce, usa la [guida di diagnosi](nat-e-starlink.md) in base al sintomo.
