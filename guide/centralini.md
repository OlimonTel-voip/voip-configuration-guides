# Collegare un centralino a VoIP PLUS

Verifica [dominio, porta, autenticazione e formato DID](servizi-e-parametri.md) del profilo assegnato. Applica le istruzioni di registrazione quando il profilo prevede REGISTER. I menu e le opzioni SIP cambiano in base a versione, edizione e hosting.

## FreePBX con chan_pjsip

1. Apri **Connectivity → Trunks** e aggiungi un trunk SIP con **chan_pjsip**.
2. Usa `<SIP_LOGIN>` per **Username** e **Auth username**, `<SIP_PASSWORD>` in **Secret**, `<SIP_DOMAIN>` in **SIP Server** e `<SIP_PORT>` in **SIP Server Port**.
3. Per il profilo illustrato da OlimonTel usa la login anche per **Contact User** e **From User**, e il dominio assegnato per **From Domain**. Verifica il Caller ID autorizzato per le chiamate in uscita.
4. Salva il trunk e configura le rotte. Per l'ingresso associa `<DID>` alla destinazione nel PBX. Per l'uscita seleziona il trunk nella regola del proprio piano di numerazione.

La guida pubblica di FreePBX include anche un esempio CLI storico. Usa le impostazioni della sezione **chan_pjsip** per la procedura descritta qui. [Guida pubblica OlimonTel per FreePBX](https://olimontel.it/guide-configurazioni/configurazione-voip-plus-olimontel-freepbx-trunk/)

## Asterisk con res_pjsip

Per un profilo con registrazione, configura un oggetto `registration` con `server_uri` nel formato `sip:<SIP_DOMAIN>:<SIP_PORT>`, `client_uri` nel formato `sip:<SIP_LOGIN>@<SIP_DOMAIN>` e il riferimento `outbound_auth` all'oggetto di autenticazione previsto. Configura endpoint, destinazione delle chiamate e dialplan secondo la tua versione di Asterisk. Verifica la registrazione con `pjsip show registrations` e prova separatamente le chiamate. Questa mappa copre la registrazione e va integrata con la configurazione del proprio PBX. [Riferimento Asterisk res_pjsip](https://docs.asterisk.org/Configuration/Channel-Drivers/SIP/Configuring-res_pjsip/Configuring-Outbound-Registrations/)

## Yeastar

In **Extension and Trunk → Trunk → Add** scegli il profilo illustrato dalla guida OlimonTel. Per **Register Trunk**, inserisci il dominio assegnato in **Hostname/IP** e **Domain**, quindi porta, trasporto, utente e nome di autenticazione. In **DIDs/DDIs** inserisci il DID nel formato assegnato e associa la rotta entrante al destinatario. La guida OlimonTel indica G.729A e G.711 A-law nell'ordine mostrato per quel profilo. Verifica l'effettiva disponibilità dei codec nella tua edizione. [Guida OlimonTel per Yeastar](https://olimontel.it/guide-configurazioni/configurazione-sip-trunk-olimontel-yeastar-voip-plus/) · [Register Trunk su P-Series Cloud](https://help.yeastar.com/en/p-series-cloud-edition/administrator-guide/create-a-sip-register-trunk.html)

## 3CX

Verifica quali trunk supporta la tua edizione e se puoi usare un template generico. Crea il trunk con il metodo di autenticazione assegnato, inserisci il numero principale e aggiungi i DID. Associa ciascun numero alla destinazione e crea la regola di uscita. Confronta il formato DID richiesto da 3CX con quello consegnato dal profilo attivo. Questa mappatura usa il manuale 3CX e va verificata sulla combinazione di edizione, hosting e servizio. [Manuale 3CX per trunk SIP](https://www.3cx.com/docs/manual/sip-trunks/)

## Prova finale

Per un account con REGISTER controlla lo stato della registrazione. Chiama ciascun DID da una linea di prova, verifica che risponda la destinazione corretta e controlla l'audio nei due sensi. In uscita prova la regola del trunk e il numero chiamante mostrato. Un trunk registrato conferma la registrazione. Solo le prove di chiamata verificano anche instradamento e audio.
