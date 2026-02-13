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


----------------
--------
------

## Part 0: Introduction: a brand new theory for modern neural networks
- Framing the problem. Modern neural networks defies classical understanding. For example, against classical statistical learning: tradeoff between bias and variance. Overparametrization (quantitatively defined under VC dim) should lead to overfitting and worse performances. Modern networks employ large numbers of parameters, often exceeding training data size by several orders of magnitude. Still, empirical studies proves the contrary. Cite AlexNet and, above all, Zhang, Bengio et Al (2017) providing a nice experiment on this subject (overparametrized nets performing well on natural data, overfit on random labels). A first hint that gen. error may depend on data structure too. Then Belkin et Al (2019) with empirical double descent (explaining the "inductive bias of smoothness") to harmonize together old and new perspective.

- On the same level, empirical neural scaling laws Kaplan @ OpenAI (2020). The microscopic architecture seems irrelevant, only macroscopic variable (num. parameters, compute time) seems to matter. Interesting "statphys" perspective, btw. A power law implies "bigger is better", which again is paradoxical under "old" classical statistical learning theory.

## Part 1: Random feature models and kernel machines (~ paper 1)
- Consider (Belkin 2018: To Understand Deep Learning We Need to Understand  Kernel Learning): this kinda provides a justification for us shifting from neural nets to kernels or random feature models. In case, explain lazy regime for NNs and Neural Tangent Kernel to defend this switch even further (Jacot 2020)
- Definition of random feature models (starting from seminal paper Rahimi Recht and Montecarlo sampling, hence connecting to kernels). Random feature models (RFM) are also interesting as shallow neural networks. Learning task under RFM (definition, ...). Characterizing the learning problem by the spectral property of the integral operator $Tf = \int dx p(x) \varphi(x;w)f(x)$. 
- Introduction to deterministic equivalent, highlighting self-averaging property (quenched disorder over random weights). Deterministic formula as in Paper 1 and kernel limit under $p\to\infty$.
- Scaling law derivation under source and capacity conditions (assuming exact power-law spectral decay!)

## Part 2: How data affects spectral structure (~ Paper 2)
- Focus on kernel ridge regression. How does the structure of data influence the spectral properties of the learning problem?
- Theorems and propositions in Paper 2 for dot-product kernels. Spectral gap and continuous spectrum differentiation. Generalization error depends also on data structure

How to proceed
- The scaling law obtained in Paper 1 assume a perfect power law scaling. In Paper 2, we've shown that this is not always the case (gaps, elbows, ...). How does this reflect on generalization error? Insert precise eigenvalues (Paper 2) in Equations of Paper 1. 

- Use a $\alpha < 0.5$ so that you can see the spectral gap (and finite $d$). What happens to the deterministic equivalent in this case here? Has this any effect on the learning curve, for example? Numerically or analytically? If numerically, then I can directly inject the eigenvalues into the deterministic equivalent formula. Maybe I can start with the numerical evaluation

- Not precisely related to P1+P2, but. In modern deep learning, regularization sometimes is not really relevant. I can fix a value of $\alpha$ (assuming perfect power law) and $\lambda$ and obtain the learning curve exponent, depending on $\lambda$. If $\alpha$ lies in a specific region, then there should be no difference in varying $\lambda$ (regularization has little effect). 

- Another interesting research direction would be to verify whether this "inheritance" property holds true for random feature models as well ($p$ is finite). Or at least when $p$ is sufficiently large
---



