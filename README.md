# Wallet of Satoshi Self Custody

![WoS](assets/No_WoS_cross.jpg)

## Gennaio 2024

|  |  |
|:---|:---:|
|*Wallet of Satoshi*, uno dei principali portafogli Bitcoin e Lightning Network al mondo, annuncia il suo ritiro dall’App Store di Apple e dal Play Store di Google negli Stati Uniti, sollevando interrogativi sulle sfide di conformità e sul futuro dei servizi di criptovaluta nell’ambito di rigidi regimi normativi. |![X_Post](assets/X_post_Jan_2024.jpg)|

Inizialmente promette di lasciare l'app in funzione per permettere di prelevare i fondi. Peccato che questa possibilità sia durata per poco tempo e che avendo tolto l'applicazione dagli store...... in molti siano rimasti a bocca asciutta.

Un po' per questo motivo ed un po' perché era custodia, ho sempre sconsigliato l'utilizzo di questa app.<br>
Ora, però, *Wallet of Satoshi*, per non sottostare alle leggi Europee (MICAR, DAC8 etc etc etc) ha annunciato la trasformazione in **Wallet Self-Custody**.
***
#### WoW, ceh bella novità direte voi!
Purtroppo no.<br>
Per quanto possibile **WoS** ha peggiorato la situazione.<br>
IL Self-Custody sembrerebbe una novità fantastica, ma, come vedremo, per metterlo in pratica si sono appoggiati ad un servizio che ha creato enormi problemi di privacy.<br>
Vi spiegherò il motivo in seguito perchè prima dobbiamo fare un passo indietro.

## il Trilemma
![Trilemma](assets/Trilemma.jpg)<br>
Sicuramente tutti avrete sentito parlare del Trilemma.<br>
In pratica, questa teoria, sostiene che solo due dei tre vertici possano essere implementati in una Blockchain.<br>
Nel caso di bitcoin [^1] (l'unica vera Blockchain) la Decentralizzazione e la Sicurezza sono stati implementanti a discapito di altre cose.<br>
A bitcoin spesso viene rimproverata la scarsa privacy delle transazioni.<br>
Per garantire la sicurezza, bitcoin non è anonimo, bitcoin è **pseudonimo** ovvero, noi tramite la mempool possiamo seguire a ritroso una qualsiasi transazione fino ad arrivare a quando quel Bitcoin è stato generato come coinbase.<br> 
Altra cosa che si riprovera a bitcoin è la lentezza delle transazioni. Sempre per garantire la Sicurezza delle transazioni i blocchi vengono validati con la Proof of Work che in genere permette di avere un blocco ogni 10 minuti.

### Ligthing Network

Per questo motivo, per scalare il protocollo, sono stati costruiti layer superiori. Il più conosciuto (qualcuno dice anche l'unico, almeno per il momento) è **Lighting Network**.<br>
Già il nome ci fa capire su cosa punta questo protocollo: **sulla velocità**.

Non sono quì a parlare del funzionamento di questo protocollo, ma mi serve farvi capire alcune caratteristiche per poter poi spiegare la pericolosità dell'attuale sistema che sua WoS.

Se in bitcoin vi è traccia di tutto, quello che accade in Lightning Network, scompare una volta chiuso un canale[^2].<br>
Questa specifica caratteristica viene spesso utilizzata per rompere la tracciabilità di un Bitcoin.<br>

Visto che questo è un concetto che può sembrare complesso, provo a spiegarmi in maniera semplice.

*Pippo* compra dei Bitcoin da *Gargamella*, ma non ha piacere che *Gargamella* veda come lui utilizzerà quel denaro, così cerca un modo di rompere la tracciabilità che è intrinseca a bitcoin.<br>
Ci sono vari modi per rompere questa tracciabilità, ma quello che interessa a noi ora è lo **swap su Lightning Network**<br>
Cosa farà quindi *Pippo*? Prenderà i Bitcoin ricevuti da *Gargamella* e tramite un servizio di swap [^3] li trasformerà in Liquidità di un suo wallet Lighting.<br>
Visto che si tratta dei suoi soldi e magari non sono nemmeno pochini, *Pippo* magari cercherà un wallet Lighting Self-Custodial per tenere quei fondi in attesa di trasferirli nuovamente.<br>
Appena sarà pronto, il nostro *Pippo* ripeterà l'operazione al contrario riportando i suoi fondi OnChain. Visto che *Pippo* è un dritto e non uno sprovveduto come tutti pensano, li manderà ad un Wallet assolutamente Self-Custody e di cui ha il pieno controllo.<br>
*Gargamella* il curiosone, controllando la transazione in mempool vedrà i fondi di *Pippo* sparire senza sapere dove siano andati a finire.




[^1]: bitcoin (con l'iniziale minuscola) indica il protocollo, mentre Bitcoin (con l'iniziale maiuscola) indica, invece, la moneta.

[^2]: Canali

[^3]: SWAP