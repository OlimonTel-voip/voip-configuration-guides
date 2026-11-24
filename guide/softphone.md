# Configurare Numero VoIP con Zoiper

Questa procedura usa i campi descritti per **Zoiper su Android**. I nomi dei menu possono variare in base alla versione. Prepara i [parametri della linea](servizi-e-parametri.md).

1. Aggiungi un account SIP. Nel campo **Username** usa l'identità composta da `<SIP_LOGIN>` e `<SIP_DOMAIN>` nel formato richiesto dall'app. Inserisci `<SIP_PASSWORD>` nella schermata di configurazione.
2. Nel campo **Hostname** usa il dominio assegnato e la porta prevista. Se appaiono i campi avanzati, inserisci `<SIP_LOGIN>` in **Authentication username**. Configura **Outbound Proxy** secondo le indicazioni della guida OlimonTel e del tuo account.
3. Seleziona il trasporto previsto e salva. Verifica lo stato dell'account, poi prova una chiamata in ingresso e una in uscita.
4. Se ricevi solo quando Zoiper è aperto, ripeti la prova con il telefono a schermo spento. Controlla le impostazioni Android per notifiche e attività in background e le funzioni di ricezione supportate dalla versione dell'app. Se il sintomo riguarda anche le chiamate con l'app aperta, verifica prima lo stato SIP e la rete.

Per altri dispositivi mobili e app usa la procedura dedicata in **Numero VoIP – APP**. Verifica le impostazioni NAT una alla volta e ripeti lo stesso test dopo ogni modifica.

## Fonti

- [Guida OlimonTel per Zoiper su Android](https://olimontel.it/guide-configurazioni/configurazione-app-zoiper-android/)
- [Catalogo guide dispositivo e app OlimonTel](https://olimontel.it/guide-configurazioni/)
