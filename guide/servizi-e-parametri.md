# Numero VoIP e VoIP PLUS

**Numero VoIP** fornisce un account SIP da configurare su un telefono IP, un adattatore, un router con telefonia o un'app compatibile. **VoIP PLUS** offre un trunk SIP per il collegamento a un centralino o a un'applicazione telefonica. Per il trunk verifica con OlimonTel il metodo di autenticazione e il formato del numero consegnato prima di configurare le rotte.

| Segnaposto | Dove ricavare il valore e a cosa serve |
| --- | --- |
| `<SIP_LOGIN>` | Login SIP indicata all'attivazione. Usala nei campi di identità e autenticazione previsti dalla guida del dispositivo. |
| `<SIP_PASSWORD>` | Password SIP dell'account. Inseriscila direttamente nel dispositivo. |
| `<SIP_DOMAIN>` | Dominio o server SIP assegnato all'utenza. Usalo per il registrar e, quando richiesto dalla guida, per il dominio SIP. |
| `<SIP_PORT>` | Porta remota del servizio. Le guide OlimonTel indicano 5060 o 5062 in alcuni profili. Segui quella applicabile all'utenza e al dispositivo. |
| `<DID>` | Numero usato per instradare la chiamata in arrivo. Mantieni il formato previsto dal trunk e dal centralino. |
| `<SIP_URI_APP>` | Destinazione SIP fornita dalla piattaforma che deve ricevere la chiamata. |
| `<TERMINATION_URI>` | Indirizzo SIP attraverso cui l'app invia una chiamata in uscita al trunk assegnato. |

La login SIP e la password SIP sono distinte dai dati di accesso al portale. Se la login ricevuta include già il prefisso richiesto, copiala per intero. Alcune interfacce accettano login e dominio in campi separati, altre in un'unica identità SIP. La guida specifica del prodotto aiuta a scegliere il formato.

Dopo il salvataggio verifica la registrazione se prevista dal profilo. Fai una chiamata entrante e una uscente e controlla che entrambe abbiano audio nei due sensi. Per un trunk verifica anche che il DID raggiunga la destinazione scelta e che in uscita compaia il numero autorizzato.

## Fonti

- [Informazioni tecniche Numero VoIP](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/)
- [VoIP PLUS](https://olimontel.it/voip-plus/)
- [Guide e configurazioni OlimonTel](https://olimontel.it/guide-configurazioni/)
