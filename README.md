# DBmulti

 Progetto:
# Task 1:

:question: Bisogna implementare tutti i metodi descritti
:question:
--- 
 Implementa un programma che, dato il nome di un file immagine e uno dei seguenti modelli di feature, visualizza l'immagine e poi estrae e stampa (in una forma leggibile) i corrispondenti descrittori di feature:    

> primo metodo

Color moments, CM10x10: Ridimensiona l'immagine a 300x100, partiziona l'immagine in una griglia 10x10, per ogni cella della griglia calcola tre momenti di colore (media,standard deviation e skewness) per ogni canale nello spazio colore RGB, e combina questi color moments per ottenere un descrittore di feature unificato di dimensione 10x10x3x3 = 900.    
Vedi https://en.wikipedia.org/wiki/Color_moments  
  
> Secondo metodo

Histograms of oriented gradients, HOG: Mappa l'immagine in scala di grigi, ridimensiona l'immagine a 300 x 10, partiziona l'immagine in una griglia 10x10, calcola l'istogramma del gradiente con  magnitude-weighted a 9 bin (con segno) (ogni bin corrispondente a 40 gradi) per ogni cella della griglia e combina questi istogrammi in un descrittore di feature di dimensione 10x10x9 = 900.    
Puoi usare {-1, 0, 1} e {-1, 0, 1}^T maschere per ottenere dI/dx e dI/dy per ogni posizione di pixel nella cella della griglia.    

Si prega di consultare i seguenti articoli per ulteriori informazioni sulle feature HOG:    

∗ https://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf 

∗ https://ieeexplore.ieee.org/document/6523794 

∗ https://filebox.ece.vt.edu/jbhuang/teaching/ece5554-4554/fa16/lectures/Lecture23ObjectDetection2.pdf 

∗ https://personalpages.surrey.ac.uk/j.collomosse/pubs/Hu-CVIU-2013.pdf 

> Terzo metodo

ResNet-AvgPool-1024: Ridimensiona l'immagine a 224x24; collega un "hook" all'output del livello "avgpool" dell'architettura pre-addestrata ResNet per ottenere un vettore di dimensione 2048, riduci il numero di dimensioni del vettore a 1024 calcolando la media di due voci consecutive nel vettore.  

> Quarto metodo

  
ResNet-Layer3-1024: Ridimensiona l'immagine a 224x224; collega un "hook" all'output del livello "layer3" dell'architettura pre-addestrata ResNet per ottenere un tensore di dimensione 1024x14x14, converti questo tensore in un vettore di dimensione 1024 calcolando la media di ogni slice 14x14. 

> Quinto metodo

   
ResNet-FC-1000: Ridimensiona l'immagine a 224x224; collega un "hook" all'output del livello "fc" dell'architettura pre-addestrata ResNet per ottenere un tensore di dimensione 1000.  


# Task 2:
 Implementa un programma che estrae e memorizza i descrittori di feature per tutte le immagini nel set di dati.    

# Task 3:
 Implementa un programma che, dato il nome di un file immagine e un valore "k", restituisce e visualizza le k immagini più simili in base a ciascun modello visivo - selezionerai l'appropriata misura di distanza/similarità per ciascun modello di feature.  Per ogni corrispondenza, elenca anche il corrispondente punteggio di distanza/similarità.    

# Task 4:

>Task 4a:

 Utilizzando il modello di rete neurale pre-addestrato RESNET50, mappa le immagini con numero pari (etichettate) nella parte 1 del set di dati in 5 diversi spazi di feature e memorizza i vettori di dati risultanti:    

Color moments, CM10x10
Histograms of oriented gradients, HOG
ResNet-AvgPool-1024
ResNet-Layer3-1024
ResNet-FC-1000
Nel database, memorizza non solo i nomi dei file immagine e i vettori di feature, ma anche le etichette "dx type".    

>Task 4b:

 Implementa un programma che, dato (a) un nome di file immagine della parte 1 o parte 2, (b) uno spazio di feature selezionato dall'utente e (c) un numero intero positivo k, identifica e visualizza le k immagini più simili della parte 1, insieme ai loro punteggi, nello spazio di feature selezionato.    

# Task 5:    

> Task 5a:

 Implementa un programma che, dati (a) un file immagine di query della parte 2, (b) uno spazio di feature selezionato dall'utente e (c) un numero intero positivo k, identifica ed elenca le k etichette di corrispondenza più probabili, insieme ai loro punteggi, nello spazio di feature selezionato.    


# Task 6 (LS1): 
Implementa un programma che (a) dato uno dei modelli di feature, (b) un valore k specificato dall'utente, (c) una delle tre tecniche di riduzione della dimensionalità (SVD, LDA, k-means) scelte dall'utente, riporta le prime k semantiche latenti estratte nello spazio di feature selezionato.    

Memorizza le semantiche latenti in un file di output adeguatamente nominato.    

Elenca le coppie imageID-peso, ordinate in ordine decrescente di pesi.    

# Task 7

>Task 7a:

 Implementa un programma che calcola e stampa la "inherent dimensionality" associata alle immagini della parte 1.    

> Task 7b: 

Implementa un programma che calcola e stampa la "dimensionalità intrinseca" (numero di dim indipendenti minime necassari per rappresentare set) associata a ciascuna etichetta univoca delle immagini della parte 1.  
  
# Task 8: 
Implementa un programma che,per ciascuna etichetta univoca l, calcola le corrispondenti k semantiche latenti (a tua scelta) associate alle immagini della parte 1, e
per le immagini della parte 2, prevede le etichette più probabili utilizzando distanze/similarità calcolate sotto le semantiche latenti specifiche dell'etichetta.    
Il sistema dovrebbe anche fornire valori di precision, recall, and F1-score per etichetta, nonché un valore di accuratezza complessiva.    

# Task 9: 
Implementa un programma che, per ciascuna etichetta univoca l, calcola i corrispondenti c cluster più significativi associati alle immagini della parte 1 (utilizzando l'algoritmo DBScan);
i cluster risultanti devono essere visualizzati sia
come nuvole di punti colorate in modo diverso in uno spazio MDS a 2 dimensioni, sia
come gruppi di miniature di immagini.


# Task 10: 
Implementa un programma che, dati le immagini della parte 1:

*crea un classificatore m-NN (per una m specificata dall'utente),

*crea un classificatore ad albero decisionale,
Per questo task, puoi utilizzare lo spazio delle feature di tua scelta.    

Per le immagini della parte 2, prevede le etichette più probabili utilizzando il classificatore selezionato dall'utente.
Il sistema dovrebbe anche fornire valori di precisione, richiamo e punteggio F1 per etichetta, nonché un valore di accuratezza complessiva.    

# Task 11:    

> 11a:

 Implementa uno strumento di Locality Sensitive Hashing (LSH) (per la distanza euclidea) che prende come input (a) il numero di livelli, L, (b) il numero di hash per livello, h, e (c) un insieme di vettori come input e crea una struttura di indice in memoria contenente l'insieme di vettori dato. 

Vedi:
"Near-Optimal Hashing Algorithms for Approximate Nearest Neighbor in High Dimensions" (di Alexandr Andoni e Piotr Indyk). Communications of the ACM, vol. 51, no. 1, 2008, pp. 117-122.    

> 11b:

 Implementa un algoritmo di ricerca di immagini simili utilizzando questa struttura di indice che memorizza le immagini della parte 1 e un modello visivo di tua scelta (il modello visivo combinato deve avere almeno 256 dimensioni): per una data immagine di query e un numero intero t, 
 
*visualizza le t immagini più simili,
*fornisce il numero di immagini univoche e il numero complessivo di immagini considerate durante il processo.    