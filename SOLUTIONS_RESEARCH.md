### To Research
* language modeling (w kontekscie predicting words before, between, windows)
* Sequence 2 sequence (for generation), moze dla generacji rymow zawierajacych rym do jakiegos slowa ktore sam wymyslisz itd - mozna je takze nazywac **conditioned generation models**
* Attention for text generation etc - teoretycznie, uwzgledniajac nie tylko koncowe wyjscie ale tez poprzednie stany, uczac sie wlasnych attention vector/weights/alignment, tworzy dodatkowy uwzgledniany context / context vector dla slowa itd / tzw. glimpse, ktory sluzy np. dekoderowi jako wejscie, z niego tworzony jest output
* Bidirectional RNNs for text gen - obserwuje przeszlosc i przyszlosc, moze byc to GRU, LSTM itd
* content-aware, location-aware
* multiheaded attention - track different region of the input, self-attention
* metody oceny - n-gram score costam / bleu score
* jakies porownywanie zdan / podobienstwo do oceny jak nasze teksty wygenerowane sa podobne do oryginalow

* ocenianie generowanych tekstow pod katem np "fluency, relevance, diversity, and originality"




### Projekty

* https://github.com/robbiebarrat/rapping-neural-network - giga ciekawy, przemyslany projekt, wykorzystujacy markov chains, wykrywanie sylab, branie slowa i generowanie potencjalnych rymow, koncowek, uwzglednianie dlugosci linijek (16 sylab etc), model na LSTM bierze nie tylko generowane slowa, ale tez rhyme index, odrzuca konczace zdania nie-rymy itd i to wszystko robi na podstawie pierwszej linijki lub linijek ktore mu podasz. Generalnie nie rozumiem, bo bardzo low level, ale ciekawe w chuj + kwestia penalizowania, oceniania modelu jesli nie zwraca rymow itd

### GANs research
* https://github.com/williamSYSU/TextGAN-PyTorch
* https://arxiv.org/pdf/2212.11119.pdf
* https://www.scielo.org.mx/pdf/cys/v24n1/1405-5546-cys-24-01-17.pdf
* https://arxiv.org/ftp/arxiv/papers/2308/2308.00939.pdf
* https://becominghuman.ai/generative-adversarial-networks-for-text-generation-part-2-rl-1bc18a2b8c60


### notatki z https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-3-3-4d192a4c47ba
czyli z wykorzystaniem doc2vec i oceniania zdan  
kroki:  
1. stworz model generujacy slowa na podstawie jakiegos poczatkowego seedu (zbioru) slow
2. stworz i wycwicz z gensim i doc2vec "model" doc2vec przeksztalcajacy zdania na wektory
3. slowa wygenerowane z pierwszego modelu lacz w zdania. Moze byc to wykrywane przez znaki interpunkcyjne itd ktore sam wygeneruje, lub ustawienie samemu sztywnej dlugosci slow i dzielenie
4. stworz model uczacy sie na zdaniach, jakie bedzie kolejne zdanie, tez na lstm itd, taki jak dla slow tylko przyjmuje wektory zdan i "przewiduje" kolejne zdania
5. polaczenie wszystkiego:
    1. dajesz seed slow poczatkowy
    2. model gen slow generuje slowa ile mu kazesz
    3. z tych slow tworzysz zdania
    4. z tych wytworzonych zdan tworzysz seed dla modelu generujacego zdania
    5. model ten generuje kolejne zdania
    6. wybierasz najlepsze
    7. powtorz, przy czym uwzglednij to wygenerowane zdanie w krokach 4 i 5
    + praktyczne notki: seed dla modelu gen. slow to moze byc seq_len, na ilu slowach sie uczy, a dla zdan, na ilu zdaniach sie uczy, czyli np. 20, wiec z wygenerowanych slow musisz utworzyc 20 zdan itd zanim podasz do drugiego modelu
    + jak dobiera najlespsze zdanie? cosine similarity ze spacy etc
    + albo mozesz inaczej: jako poczatkowy seed wygenerowac wiele zdan (np. 10), bo moze lepiej nada to kierunek, a potem kolejne dopiro generowac tak
    + kwestia temperatury - przy generowaniu znakow, moze ni miec tak duzo sensu/wprowadzac bledne slowa, ale przy generowaniu slow - czemu nie, grozi tylko niegramatycznmi zdaniami

### GPT-2 etc
* https://github.com/minimaxir/gpt-2-simple
* https://github.com/minimaxir/aitextgen