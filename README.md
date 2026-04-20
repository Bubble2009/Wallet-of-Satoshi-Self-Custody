# Wallet of Satoshi Self-Custody

![WoS](assets/No_WoS_cross.jpg)

## Gennaio 2024


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                       |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------: |
| *Wallet of Satoshi*, uno dei principali portafogli bitcoin e Lightning Network al mondo,<br> annuncia il suo ritiro dall’App Store di Apple e dal Play Store di Google negli Stati Uniti,<br> sollevando interrogativi sulle sfide di conformità e sul futuro dei servizi di criptovaluta nell’ambito di rigidi regimi normativi. <br>Inizialmente promette di lasciare l'app in funzione per permettere di prelevare i fondi.<br> Peccato che questa possibilità sia durata per poco tempo e che, avendo tolto l'applicazione dagli store......,<br> in molti siano rimasti a bocca asciutta. | ![X_Post](assets/X_post_Jan_2024.jpg) |

Un po' per questo motivo ed un po' perché era custodial, ho sempre sconsigliato l'utilizzo di questa app.<br>
Ora, però, *Wallet of Satoshi*, per non sottostare alle leggi Europee (MICAR, DAC8 etc etc etc) ha annunciato la trasformazione in **Wallet Self-Custody**.

---

### WoW, che bella novità!

Questo è quello che in genere sento dire, purtroppo non è così.<br>
Per quanto possibile **WoS** ha peggiorato la situazione.<br>
L'introduzione del Self-Custody sembrerebbe una novità fantastica, ma, come vedremo, in questo specifico caso non lo è.<br>
Vi spiegherò il motivo in seguito perchè prima dobbiamo fare un passo indietro.

## il Trilemma

![Trilemma](assets/Trilemma.jpg)<br>
Sicuramente tutti avrete sentito parlare del Trilemma.<br>
In pratica, questa teoria, sostiene che solo due dei tre vertici possano essere implementati in una Blockchain.<br>
Nel caso di Bitcoin [^1] (l'unica vera Blockchain) la Decentralizzazione e la Sicurezza sono stati implementanti a discapito di altre cose.<br>
A Bitcoin spesso viene rimproverata la *scarsa privacy* delle transazioni.<br>
Infatti, per garantire la sicurezza, *Bitcoin non è anonimo*, Bitcoin è **pseudonimo**, ma soprattutto è tutto tracciabile; interrogando la mempool, infatti, possiamo seguire a ritroso una qualsiasi transazione fino ad arrivare al bitcoin generato come coinbase.<br>
Altra cosa che si riprovera a Bitcoin è *la lentezza delle transazioni*. Sempre per garantire la Sicurezza delle transazioni i blocchi vengono validati con la Proof of Work e, come prevede il protocollo, tramite la difficulty adjustment, viene validato un nuovo blocco circa ogni 10 minuti.

### Lightning Network

Per questo motivo, per **scalare il protocollo**, sono stati costruiti layer superiori. Il più conosciuto (qualcuno sostiene che sia l'unico) è **Lightning Network**.<br>
Già il nome ci fa capire su cosa punta questo protocollo: **sulla velocità**, ma, come vedremo, non è l'unica caratteristica importante.

Non sono quì a parlare del funzionamento di questo protocollo, ma serve farvi capire alcune suo caratteristiche per poter poi spiegare la pericolosità del sistema che ha adottato ora WoS.

Se in Bitcoin vi è una traccia indelebile di tutto quello che accade, in Lightning Network, invece, tutto scompare una volta chiuso il canale[^2].<br>
Questa è una caratteristica importante che viene spesso utilizzata per rompere la tracciabilità di una transazione Bitcoin.<br>

Visto che questo è un concetto che può sembrare complesso, provo a spiegarmi in maniera semplice con un esempio prteoricotico.

> *Pippo* riceve dei bitcoin on chain da *Gargamella*, ma non ha piacere che *Gargamella* veda come lui utilizzerà quelle monete, così cerca un modo di rompere la tracciabilità che è intrinseca a Bitcoin.
>
> Ci sono vari modi per rompere questa tracciabilità, ma quello che prendiamo ora in considerazione è lo **swap su Lightning Network**.
>
> Cosa farà quindi *Pippo*? Prenderà i bitcoin ricevuti da *Gargamella* e tramite un servizio di swap [^3] li trasformerà in Liquidità di un suo wallet Lightning.<br>
> Visto che si tratta dei suoi soldi (e magari non sono nemmeno pochini), *Pippo* cercherà un wallet Lightning Self-Custodial che gli permette di custodire personalmente i fondi senza doversi rivolgere ad un ente terzo a cui dovrebbe devolvere la sua fiducia.<br>
> Padrone dei suoi fondi, potrà decidere se usarli nel circuito LN, oppure attendere il momento opportuno per spostarli altrove.
>
> In questo caso, appena sarà pronto, il nostro *Pippo*, effettuerà l'operazione al contrario riportando i suoi fondi OnChain. *Pippo* ha già dimostrato di tenere alla sua privacy e alla custodia dei propri fondi, quindi utilizzerà un Wallet assolutamente Self-Custody di cui ha il pieno controllo.
>
> *Gargamella* il curiosone, controllando la transazione in mempool vedrà i fondi di *Pippo* sparire senza sapere dove siano andati a finire perchè *Pippo* li ha trasferiti su un altro wallet, magari su un cold wallet per utilizzarli come riserva o magari su di un hot wallet perchè vuole spenderli.

Con la speranza che questo esempio vi sia chiaro, andiamo a vedere come possa essere rilevante in questa guida su WoS.

Per l'amor del vero, devo informarvi che gli SWAP hanno dei costi (in genere ogni swap ha uno 0,5% di fee), ma se ne avete compreso l'importanza, potrete valutare liberamente se questo costo sarà adeguato ai benefici.

Ora, però, andiamo a conoscere un altro attore di questa situazione.

## *Spark

Che cos'è **Spark**?<br>
Iniziamo a vedere come si autodefiniscono sul sito [spark.money](https://spark.money):

> Spark is the fastest, cheapest, and most UX-friendly way to build financial apps and launch assets natively on Bitcoin. It’s a **Bitcoin L2** that lets developers move Bitcoin and Bitcoin-native assets (including stablecoins) instantly, at near-zero cost, while staying fully connected to Bitcoin’s infrastructure.

Si definiscono un altro Layer 2 (ricordo che anche Lightning è un L2) e il loro intento è di spostare la liquidità in stablecoin tra finanza decentralizzata, piattaforme centralizzate e asset reali tokenizzati.

**WoS Self-Custody** si appoggia a Spark per gestire i vostri fondi.<br>
In pratica, ora WoS è un wallet spark, ma che vi permette però di operare solo sul circuito di Lightning Network.<br>
WoS non è l'unico wallet LN che si appoggia a questa tecnologia, ma, ad oggi, mi risulta che sia l'unico ad avere questa vulnerabilità.

L'utilizzo di *sidechain* come Spark o Liquid, permette di operare nel circuito Lightning Network senza doversi occupare di gestire i canali.

## WoS + Spark perchè questa accoppiata deve farci paura

Veniamo dunque al nostro Wallet of Satoshi che ora nella versione Self-Custody si appoggia a Spark.

Per farvi comprendere i rischi che si corrono, ho pensato di fare un esempio pratico.

Ho creato un wallet con WoS self custodial, mi sono fatto mandare qualche fondo da qualche conoscente e poi li ho rimandati indietro in maniera un po' randomica.

A questo punto sono in possesso di un wallet con una serie di operazioni sopra.<br>
Ci saranno dei movimenti e ci sarà un saldo.

Mettiamo che ora qualcuno mi debba inviare dei fondi. Per poterli ricevere, devo creare una invoice come questa che segue.<br>
L'invoice può essere mostra come un QR code:

![Invoice](./assets/Invoice.png)

Oppure con una stringa di testo chiamata **lnurl**

`lnbc1u1p57ve8app5vjdcgn3cyy8m0ugm9uphatvsy6ekec4hykxq40pesldn4vqh9u8ssp5kh9j2s3e9s88k2f7m9rp3z3dfw6mk4c3krcm4a7u4emmrxg4xmxsxqyz5vqnp4qvyndeaqzman7h898jxm98dzkm0mlrsx36s93smrur7h0azyyuxc5rzjq25carzepgd4vqsyn44jrk85ezrpju92xyrk9apw4cdjh6yrwt5jgqqqqrt49lmtcqqqqqqqqqqq86qq9qrzjqtrqywde68y6jv9l29dkhqyrhag95njppjc7wvl633uhfsx4m48slapyqr6zgqqqq8hxk2qqae4jsqyugqcqzpudqq9qyyssqawprdkj0kl88nty4m786wewwg2a90yhtf5yxgr42drq3s0065v8ya95rr8sy66fv3mjsplcxyhdklchgfyxqhfcuencvvzhpj0y0upqpva6e9s`

Con questa stringa che indica la mia invoice, basta andare su un sito che la decodifichi come [lightningdecoder.com](https://lightningdecoder.com) ed inserendo quella stringa potremo interpretare alcuni dati.<br>
Dalla decodifica della invoice, vengono mostrati un numero ginormico di dati.<br>
La schermata è decisamente lunga, piena di sigle, codici, numeri e tante alte informazioni:

![lightningdecoder_1](./assets/lightningdecoder_1.jpg)

Potete vedere tantissime informazioni relative a questa invoice.<br>
Quelle più identificabili sono sicuramente l'importo, le FEE, il Timestamp, la Scadenza e ancora tante altre.<br>
Di tutta questa enorme pagina di dati, c'è un piccolo blocco che mostra alcuni dati allarmanti:

![lightningdecoder_2](./assets/lightningdecoder_2.jpg)

Il dato che ci interessa è la **Public Key**:

`02c60239b9d1c9a930bf515b6b8083bf505a4e410cb1e733fa8c7974c0d5dd4f0f`

Ora prendiamo questa stringa esadecimale ed andiamo ad inserirla in un sito che esplora l'ecosistema Spark, nel mio esempio ho usato [sparkscan.io](https://sparkscan.io).<br>
Incollando la **Public Key** identificata sopra, possiamo visualizzare una **AGGHIACCIANTE VIDEATA!!**.<br>
Tutte le transazioni di questo Wallet ed il suo saldo, sono esposti in chiaro a chiunque riceva una mia invoice.

![Sparkscan](./assets/Sparkscan.jpg)

La controprova sta nello screenshot che segue.<br>
Come potete vedere, su *sparkscan.io* sono visibili tutti i movimenti ed il saldo presente sul wallet.<br>
Quello che segue è lo screenshot del WoS che ho utilizzato per questo esempio.

![Screenshot Wallet](./assets/Screenshot_WoS.png)

Chiunque riceva una vostra invoice generata con WoS Self-Custody, può vedere tutto quello che avete fatto con quel wallet.<br>
Chiunque riceva una vostra invoice generata con WoS Self-Custody, può vedere il saldo di quel wallet.<br>

**WoS Self-Custody**

**AIUTO!!**

---

## Conclusioni

Ho deciso di scrivere questa guida, per cercare di aprire gli occhi a tutte quelle persone che ignorano la pericolosità di questa falla in WoS.<br>
Mi è capitato di parlarne in gruppi Telegram e venire deriso, quasi insultato e accusato di provare piacere nel seminare il panico.<br>
Sono stato deriso perchè mi preoccupavo se il barista veniva a scoprire che avevo 20 euro sul wallet.

Quello che però queste persone non riescono a comprendere, è che se presentano Bitcoin come strumento per la sovranità individuale e lo sponsorizzano come strumento pseudonimo, proponendo l'utilizzo di WoS vengono meno a quanto da loro detto in precedenza.<br>

Se si consiglio a qualcuno di utilizzare uno strumento tecnologico, io ritengo che sia importante che vengano mostrati i pro, ma soprattutto i contro.<br>

Mi hanno definito paranoico, ma in Francia, dall'inizio del 2026, gli attacchi fisici, le rapine e i sequestri che coinvolgono persone con possedimenti in Cryptovalute, sono aumentati a dismisura.<br>
Quindi, perchè dover andare a mostrare ad un bar o ad una persona a cui sto vendendo un oggetto in satoshi, l'intero transato ed il saldo del mio wallet?<br>
WoS lo si utilizza di persona, faccia a faccia.<br>
Continuiamo ad essere pseudonimi, ma mettendoci faccia diventiamo riconoscibili!

Quindi, al di la del fatto che non mi piace mostrare il contenuto del mio portafoglio al primo da cui ricevo dei sats, potrei anche tollerare che WoS venga utilizzato per piccolissimi pagamenti e con piccolissime ricariche sporadiche, ma **ASSOLUTAMENTE NON VA MAI E POI MAI ANDREA' PRESO IN CONSIDERAZIONE PER TRANSAZIONI MAGGIORI**; sarà anche **SELF CUSTODIAL**, ma è un Self Custodial che sbandiera ai 4 venti il mio saldo ed il mio transato.

Oggi come oggi esistono molteplici alternative FOSS, perchè proporre una soluzione Closed e fallata come WoS?<br>
Siamo sicuri che proporre tecnologie senza fare un disclaimer su eventuali pericoli nell uso della stessa, sia la soluzione corretta?<br>
Io diffiderei di chi mi mostra solo un lato della medaglia.<br>
Troppo spesso l'ignoranza è stata utilizzata per controllare le masse.<br>

Spero che questa mia guida possa far aprire gli occhi a qualcuno.

### Ringraziamenti
Innanzitutto devo ringraziare Plak perchè sul suo canale YouTube [Final Step Bitcoin](https://www.youtube.com/@final_step_bitcoin) ha pubblicato il video [WALLET OF SATOSHI SELF-CUSTODY: Sembra privato, ma TUTTI vedono i TUOI MOVIMENTI! Ti spiego come](https://youtu.be/aaHfPL_YoVM?si=GgKAQue7v2RVBiDu) che ha fatto aprire gli occhi su WoS a chi, come me, è in grado di comprendere.<br
Lo ringrazio anche per aver condiviso con me parecchio del materiale che ho riportato quì sopra.

Devo poi ringraziare alcuni utenti del gruppo Telegram [Bitcoin EDU Veneto](https://t.me/Bitcoin_Veneto) perchè è stato dopo essere stato da loro attaccato, canzonato, bistrattato e quasi insultato che ho deciso di scrivere questa guida.

In ultimo ringrazio tutti quelli che mi hanno aiutato inviando i fondi per le transazioni di esempio.

| | |
| :------- | :--------: |
|  Come sempre invito chiunque voglia commentare a farlo liberamente, accetto volentieri C&C che possano arricchire e/o correggere questo scritto.<br>Ho buttato tutto giù di getto, pertanto segnalatemi anche qualsiasi tipo di errore.<br><br> Per parlare con me di questa guida, unitevi al gruppo Telegram :link:[ABC del Bitcoin](https://t.me/+GlEaD0WD53BmNGE0).| [![QR](assets/qr-code_ABC.png)](https://t.me/+GlEaD0WD53BmNGE0) |

[^1]: Bitcoin (con l'iniziale maiuscola) indica il protocollo, mentre bitcoin (con l'iniziale minuscola) indica, invece, la moneta.
    
[^2]: Per effettuare una transazione tra due utenti è necessario che i fondi possano passare dall'attore A all'attore B. Questa transizione avviene attraverso ai canali di pagamento.
    
[^3]: SWAP
