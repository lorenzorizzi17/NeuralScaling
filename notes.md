@ Feb. 4
Due paper, due problemi:
1) Il primo articolo ratta della determinazione dell'errore di generalizzazione per un RFM (o kernel) usando gli equivalenti deterministici. Il tutto dipende fondamentalmente dalla struttura del kernel (operatore integrale associato) e dal suo spettro (oltre che dai parametri come N, d, P, ...). Se poi si ha la condizione di source/capacity, allora si può ulteriormente riscrivere il problema e ottenere leggi di scaling ben determinate
2) Si può usare la condizione di source/capacity? Se ne parla nel secondo articolo. Per kernel dot-product (solo loro!) si dimostra che la struttura spettrale dei dati influenza (se gaussiani ma power law) la struttura spettrale del kernel (again, dell'operatore integrale)


Limitazioni: Il paper 1 è del tutto generale e dipende dalla struttura spettrale dell'operatore associato. Il paper 2 dà conferme per un caso abbastanza specifico:
- Sui dati: dati gaussiani, covarianza power law
- Sul kernel: solo dot-product kernel
In tal caso, la struttura è comunque non precisamente power-law like, ma può presentare dei gradini. asintoticamente però ristabilisce la struttura power-law (e la solita source and capacity condition)


In generale, sull'articolo (2), dato un generico kernel dot-product si può dimostrare che (depending on alpha):
- Per alpha > 1, allora vale di fatto corollario 2:




Qui le note relative ad un abstract di tesi.


-- Parte sulla overparametrization; [Zhang 2017: UNDERSTANDING DEEP LEARNING REQUIRES RETHINKING GENERALIZATION][Bruno Deterministic-free ...] nei dati. Problema (e cioè basandosi su tradeoff varianza-bias, statistical learning theory, grande numero di pesi rispetto ai dati, ottima generalizzazione. Magari ), soprattutto negi neural networks --> ma in realtà proprietà shared con molte sistemi (learning task). In sintesi: Zhang ha detto "La vecchia teoria è morta, le reti memorizzano il rumore". Il lavoro che stai leggendo e facendo tu (sui Kernel e le Power Laws) è la "Nuova Teoria" che cerca di spiegare come sia possibile generalizzare nonostante questa capacità di memorizzazione. ++ vedi appunti ++ 

-- Risposta parziale con il fenomeno del double descent [Belkin 2019]. La risposta che dà (da approfondire) è che, aumentando il numero di parametri, accedo a funzioni sempre più lisce e regolari (ottime nel caso di dati reali!). La teoria classica mi dice che:
1) Bassa complessità, imparo funzioni regolari ma alto bias 
2) Alta complessità, imparo con training error minuscola ma funzioni spiky, oscillanti e brutte. Collegamento con la norma RKHS e la liscezza della funzione (eliminare frequenze alte)

(è interessante anche l'articolo di Montanari e Mei, praticamente learning sulla sfera con RFM e nel limite termodinamico) e trovano formule analitiche! Come Loureiro, ma qui i dati non sono sulla sfera ma in R^d (imprintano sullo spettro dell'operatore) e d non è più vincolata ad una generica formula --> grande estensione. Leggilo perché spiega bene (e meglio) anche la questione del training di una two-layer neural nets/ random feature model (qualche parentesi sul quenched disorder, concentration)---> alla fine anche i bound di loureiro sono dei quanched disorder! Concentration property, self-averaging. Guarda anche [The more is better] in cui c'è la spiegazione della trasformazione g. é spiegata anche bene la parte dell'operatore
Questo paper, "Scaling Laws for Neural Language Models" (Kaplan et al., 2020), è considerato il "Principia Mathematica" dell'era moderna dei Large Language Models (LLM).

Per un fisico, questo articolo è pura poesia. Trasforma il Deep Learning da una disciplina "alchemica" (prova questa architettura, cambia quel layer, spera che funzioni) a una scienza sperimentale precisa, governata da leggi di potenza (Power Laws) universali, simili alla termodinamica.

Ecco l'analisi approfondita, tradotta nel linguaggio della fisica dei sistemi complessi.
1. L'Intuizione Fondamentale: La Termodinamica dell'Apprendimento
Fino al 2020, si pensava che per migliorare un modello si dovesse inventare una nuova architettura (LSTM, Transformer, Attention heads, etc.). Kaplan e colleghi dimostrano che l'architettura conta pochissimo. La Rivoluzione: Kaplan mostra che, su scala logaritmica, queste modifiche sono rumore. Una rete LSTM (vecchia scuola) e un Transformer (nuova scuola) seguono la stessa pendenza della power law. Il Transformer ha solo un offset migliore (una costante moltiplicativa), ma la fisica sottostante è identica. Messaggio: Smettetela di micro-ottimizzare l'architettura. L'unica cosa che conta davvero per abbattere la Loss è scalare N (parametri) e D (dati).