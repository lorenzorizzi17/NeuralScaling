@ Feb. 4
Due paper, due problemi:
1) Il primo articolo tratta della determinazione dell'errore di generalizzazione per un RFM (o kernel) usando gli equivalenti deterministici. Il tutto dipende fondamentalmente dalla struttura del kernel (operatore integrale associato) e dal suo spettro (oltre che dai parametri come N, d, P, ...). Se poi si ha la condizione di source/capacity, allora si può ulteriormente riscrivere il problema e ottenere leggi di scaling ben determinate
2) Si può usare la condizione di source/capacity? Se ne parla nel secondo articolo. Per kernel dot-product (solo loro!) si dimostra che la struttura spettrale dei dati influenza (se gaussiani ma power law) la struttura spettrale del kernel (again, dell'operatore integrale)


Limitazioni: Il paper 1 è del tutto generale e dipende dalla struttura spettrale dell'operatore associato. Il paper 2 dà conferme per un caso abbastanza specifico:
- Sui dati: dati gaussiani, covarianza power law
- Sul kernel: solo dot-product kernel
In tal caso, la struttura è comunque non precisamente power-law like, ma può presentare dei gradini. asintoticamente però ristabilisce la struttura power-law (e la solita source and capacity condition)


In generale, sull'articolo (2), dato un generico kernel dot-product si può dimostrare che (depending on alpha):
- Per alpha > 1, allora vale di fatto corollario 2:

