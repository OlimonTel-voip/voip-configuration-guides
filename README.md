# Guide di configurazione VoIP OlimonTel

Guide per attivare e verificare **Numero VoIP** e **VoIP PLUS** su telefoni IP, adattatori ATA, router con telefonia, softphone, centralini SIP e app di telefonia con agenti vocali.

| Se devi… | Apri la guida |
| --- | --- |
| Scegliere il profilo e capire quali valori inserire | [Numero VoIP e VoIP PLUS](guide/servizi-e-parametri.md) |
| Trovare la configurazione di un telefono IP, ATA, router o base cordless | [Indice dei dispositivi](#indice-dei-dispositivi) |
| Trovare la configurazione di un'app per smartphone o computer | [Indice delle app](#indice-delle-app) |
| Collegare Asterisk, FreePBX, Yeastar o 3CX | [Centralini e trunk SIP](guide/centralini.md) |
| Collegare una piattaforma di agenti vocali via SIP | [Retell AI, AutoCalls, ElevenLabs, Vapi e Grok](guide/piattaforme-ai.md) |
| Diagnosticare registrazione o audio su Starlink e altre reti con NAT | [NAT, CGNAT e Starlink](guide/nat-e-starlink.md) |

Usa i parametri assegnati all'attivazione. Nelle guide i valori specifici dell'utenza sono segnaposto. Per ogni configurazione trovi i campi da compilare, le prove da fare e i riferimenti pubblici di OlimonTel o del produttore.

## Indice dei dispositivi

| Marca | Modello o serie | Configurazione Numero VoIP | Fonti pubbliche |
| --- | --- | --- | --- |
| FRITZ! | FRITZ!Box 4060 | [Registrazione e assegnazione del numero](guide/dispositivi.md#fritzbox-con-funzioni-di-telefonia) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/) · [Scheda 4060](https://fritz.com/it-it/products/fritz-box-4060-20002952) |
| FRITZ! | FRITZ!Box 5590 Fiber | [Registrazione e assegnazione del numero](guide/dispositivi.md#fritzbox-con-funzioni-di-telefonia) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/) · [Telefono analogico su 5590 Fiber](https://fritz.com/it-it/apps/knowledge-base/FRITZ-Box-5590-Fiber/3285_Configurare-un-telefono-analogico-nel-FRITZ-Box) |
| FRITZ! | FRITZ!Box 7530 AX | [Registrazione e assegnazione del numero](guide/dispositivi.md#fritzbox-con-funzioni-di-telefonia) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/) · [Scheda 7530 AX](https://fritz.com/it-it/products/fritz-box-7530-ax-20002944) |
| FRITZ! | FRITZ!Box 7590 AX | [Registrazione e assegnazione del numero](guide/dispositivi.md#fritzbox-con-funzioni-di-telefonia) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/) · [Scheda 7590 AX](https://fritz.com/it-it/products/fritz-box-7590-ax-20002999) |
| Gigaset | Basi cordless con supporto SIP | [Account VoIP della base](guide/dispositivi.md#basi-cordless-gigaset-ip) | [Guida OlimonTel per Gigaset IP](https://olimontel.it/guide-configurazioni/configurazione-gigaset-ip-telefono-voip/) |
| Grandstream | GRP2612, GRP2613, GRP2614 | [Account SIP del telefono](guide/dispositivi.md#grandstream-grp2612-grp2613-e-grp2614) | [Parametri OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Manuale GRP261x](https://documentation.grandstream.com/knowledge-base/grp261x-grp262x-grp263x-series-administration-guide/) |
| Grandstream | HT801 V2, HT802 V2 | [Registrazione sulla porta FXS](guide/dispositivi.md#grandstream-ht801-v2-e-ht802-v2) | [Parametri OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Manuale HT80x V2](https://documentation.grandstream.com/knowledge-base/ht80x-v2-administration-guide/) |
| Grandstream | HT812 V2, HT814 V2, HT818 V2 | [Profilo SIP e assegnazione delle porte](guide/dispositivi.md#grandstream-ht812-v2-ht814-v2-e-ht818-v2) | [Parametri OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Manuale HT81x V2](https://documentation.grandstream.com/knowledge-base/ht81x-v2-administration-guide/) |
| Keenetic | Linear KN-3110 su router compatibile con Phone Station | [Linea SIP e porte FXS](guide/dispositivi.md#keenetic-linear-kn-3110) | [Parametri OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Manuale della linea SIP](https://support.keenetic.com/titan-se/kn-4210/it/19336-setting-up-a-telephone-line.html) |
| Panasonic | KX-UT113, KX-UT123, KX-UT133, KX-UT136 | [Linea SIP del telefono](guide/dispositivi.md#panasonic-kx-ut113-kx-ut123-kx-ut133-e-kx-ut136) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-panasonic-telefoni-voip/) · [Manuali Panasonic](https://docs.connect.panasonic.com/pcc/support/sipphone/download/UT1/others.html) |
| Yealink | T33G, T43U, T46U, T54W, T57W | [Registrazione dell'account](guide/dispositivi.md#yealink-t33g-t43u-t46u-t54w-e-t57w) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-telefoni-yealink-voip/) · [Manuale Yealink](https://support.yealink.com/docs/sip-t53/account-registration/cb7e0331cba0407a975f6e76e5309930) |
| Yeastar | TA100, TA200 | [Account SIP della porta](guide/dispositivi.md#yeastar-ta100-e-ta200) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-voip-olimontel-yeastar-gateway-fxs/) · [Manuale TA100/TA200](https://help.yeastar.com/download/docs/ta100-ta200-user-manual-en.pdf) |
| Yeastar | TA400, TA800 | [Profilo SIP e registrazione per porta](guide/dispositivi.md#yeastar-ta400-e-ta800) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-voip-olimontel-yeastar-gateway-fxs/) · [Documentazione Yeastar](https://help.yeastar.com/en/voip-gateways/) |

## Indice delle app

| Marca o progetto | App | Piattaforma | Configurazione Numero VoIP | Fonti pubbliche |
| --- | --- | --- | --- | --- |
| Belledonne Communications | Linphone | Android | [Account SIP su Android](guide/softphone.md#linphone-su-android) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-app-linphone-android/) · [Manuale Linphone](https://www.linphone.org/en/docs/login-sip-account/) |
| Belledonne Communications | Linphone Desktop | Windows, macOS, Linux | [Account SIP su desktop](guide/softphone.md#linphone-desktop) | [Parametri OlimonTel](https://olimontel.it/guide-configurazioni/informazioni-tecniche-voip/) · [Manuale Linphone](https://www.linphone.org/en/docs/login-sip-account/) · [Piattaforme](https://www.linphone.org/en/download/) |
| FRITZ! | FRITZ!App Fon | Android, iOS | [Associazione al FRITZ!Box e alla linea](guide/softphone.md#fritzapp-fon-su-android-e-iphone) | [Configurazione della linea sul FRITZ!Box](https://olimontel.it/guide-configurazioni/guida-configurazione-fritzbox-voip/) · [Guida dell'app](https://fritz.com/it-it/apps/knowledge-base/FRITZ-Box-4040/251_Configurare-FRITZ-App-Fon/) |
| MicroSIP | MicroSIP | Windows | [Account SIP su MicroSIP](guide/softphone.md#microsip-su-windows) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-microsip-voip/) · [Manuale MicroSIP](https://www.microsip.org/help) |
| Mizu VoIP | MizuDroid | Android | [Account SIP su MizuDroid](guide/softphone.md#mizudroid-su-android) | [Guida OlimonTel](https://olimontel.it/guide-configurazioni/configurazione-app-mizudroid/) · [Manuale MizuDroid](https://www.mizu-voip.com/Portals/0/Files/Android_Softphone_Guide.pdf) |
| Zoiper | Zoiper | Android | [Account SIP su Android](guide/softphone.md#zoiper-su-android) | [Guida OlimonTel per Android](https://olimontel.it/guide-configurazioni/configurazione-app-zoiper-android/) |
| Zoiper | Zoiper | iOS | [Account SIP su iPhone](guide/softphone.md#zoiper-su-iphone) | [Guida OlimonTel per iPhone](https://olimontel.it/guide-configurazioni/video-guida-configurazione-softphone-voip/) |
| Zoiper | Zoiper 5 | Windows | [Account SIP su Zoiper 5](guide/softphone.md#zoiper-5-su-windows) | [Guida OlimonTel per PC](https://olimontel.it/guide-configurazioni/configurazione-zoiper-pc/) · [Manuale Zoiper 5](https://www.zoiper.com/pdf/User%20Guide%20Zoiper%205%20v.1.0.6.pdf) |
