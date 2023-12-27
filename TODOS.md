### todos / konkretne kroki

1. TODO: prosty character-based model na szekspirowskich sonetach (bo takie tutsy)
2. TODO: sprobuj go powiekszyc o wiecej warstw LSTM i epochs
3. TODO: word embeddings zamiast character
4. TODO: zbierz dataset lyrics z ta biblioteka do geniusa dla pythona
5. TODO: sprobuj z tym tekstem poprzednie
6. TODO: research cos wiecej zeby uwzglednialo rymy, poetyzm, konkretne ograniczenia metryczne (ilosc sylab?, znakow, slow)

* z https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-1-3-8979eb65cb3a: dodaj jak tutaj dodatkowa funkcje samplowania z temperatura (+ poszukaj moze wytlumaczenia matematycznie tej temperatury), poza tym words, sprobuj bidirectional lstm itd

### ways to develop

also:
* TODO: parametryzacja typu ile znakow / slow rozwaza przed generacja kolejnego, jaki dropout itd
* cos z wykorzystaniem pretrained modeli jak GPT2
* https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-1-3-8979eb65cb3a - zaczyna od generowaniu na podstawie znakow, ale potem przechodzi do slow, zdan i wprowadza troche losowosci z temperatura i trenuje dwa modele, by jeden uczyl sie na znakach i slowach i generowal zdania, a drugi na tych generowanych zdaniach i wybieral jakos najlepsze, zeby calsoc miala wiecej sensu - rezultaty srednie, ale ciekawe - rozwiniete dalej

* te przyklady dzialaja z wlasnymi oknami znakow i zamianieniu znakow na proste inty, ale gdyby przeszlo do slow, to trzeba by przejsc do rzeczywistych embeddings, w tym np. moze pretrained beda lepsze

+ ciekawe rozwiniecia:
* moze przygotowac kilka modeli na podstawie tekstow kilku artystow i umozliwiac uzytkownikowi mieszanie rezultatow w wybrany sposob (np. DOOM 80%, GZA 20%), bo generalnie modele to sa po prostu computation graphs, mozna laczyc, dodawac etc wyjscia i jest tez temat model ensemble - pytanie czy jest to mozliwe do realizacji jakos po wycwiczeniu juz w taki sposob, czy raczej trzeba by myslec, by samemu stworzyc jakis sposob mieszania rezultatow z roznych modeli, np. troche tego, troche tego losowo itd, cos z tym ze dodajesz do outputu z jednego modelu, ktory idzie do drugiego, przez co bedzie zmieniony itd, tylko wtedy musza albo zwracac pelne slowa albo jeszcze lepiej pelne zdania a nie symbole

* wykorzystanie konceptow named entity recognition, part of sentence, structure of sentences

* jakos narzucanie dlugosci zdan, tzn po ilus znakach dodajesz manualnie newline etc

* znaczenia slow, wordnet, spacy np. w swoim lemmitazorze wykorzystuje, ale to wtedy w uczeniu po slowach

* wykorzystanie czestosci slow, TF-IDF itd

* https://github.com/robbiebarrat/rapping-neural-network - giga ciekawy, przemyslany projekt, wykorzystujacy markov chains, wykrywanie sylab, branie slowa i generowanie potencjalnych rymow, koncowek, uwzglednianie dlugosci linijek (16 sylab etc), model na LSTM bierze nie tylko generowane slowa, ale tez rhyme index, odrzuca konczace zdania nie-rymy itd i to wszystko robi na podstawie pierwszej linijki lub linijek ktore mu podasz. Generalnie nie rozumiem, bo bardzo low level, ale ciekawe w chuj + kwestia penalizowania, oceniania modelu jesli nie zwraca rymow itd

### extra directions

* eksperymenty z dlugoscia wyjscia jak z tutorialu TF udemy predicting - bo nie musi byc jeden znak

* https://huggingface.co/blog/how-to-generate - wykorzystanie pretrained tokenizatorow, roznyz transformatorow, strategie generowania

* https://www.kaggle.com/code/purvasingh/text-generation-via-rnn-and-lstms-pytorch - niezly kod w pytorchu

### GPT-2 etc
* https://github.com/minimaxir/gpt-2-simple
* https://github.com/minimaxir/aitextgen

### extra datasets
* https://www.kaggle.com/datasets/tgdivy/poetry-foundation-poems
* https://github.com/gsurma/text_predictor/tree/master/data - kilka roznych zbiorow


### Inspiring projects
* https://www.johnwmillr.com/trucks-and-beer/ - swietne vizualizacje z wlasnie scrapowania utworow
* https://github.com/tsandefer/dsi_capstone_3 - DL tlumaczenie rap lyrics na ich znaczenie/funkcje tzn to jak ludzie przetlumaczyli na geniusie, swietnie opisane
* https://github.com/Hugo-Nattagh/2017-Hip-Hop - sentiment analysis
* http://jdaytn.com/posts/download-blink-182-data/ - plus uzycie danych z spotify o utworach obok lyrics do analizy
* https://pudding.cool/ - bajeczne wizualizacje
* https://towardsdatascience.com/49-years-of-lyrics-why-so-angry-1adf0a3fa2b4 - ocenianie lyrics na przestrzeni lat pod katem "agresywnosci"

* https://github.com/johnwmillr?tab=repositories

* https://www.kaylinpavlik.com/classifying-songs-genres/
* https://github.com/matthewfdaniels/scripts/?ref=kaylinpavlik.com - inny dataset, ale moze jakies proby miksowania

### pytorch general

* TODO: explore ways of saving the best model during training in order to be able to stop training when needed, prevent overfitting etc

### NTLK book
https://www.nltk.org/book/ch01.html

### Practical tips

#### Z ksiazki NLP Pytorch 2019
* str 61 wlasne przygotowanie Dataset z Pytorcha uwzgledniajace podzial na train/test/val, vectorizing itd w jednej klasie
* str 159 nie rozumiem do konca, ale wazne **conditioning RNNs** dodatkowym inputem, ktory jest przeksztalcany w embedding i dodawany jako pierwszy hidden state RNN, od niego zaczyna i on bedzie kierowac reszta, zamiast zaczynac od niczego - ale to dotyczy uczenia, jak potem zrobic to przy uzywaniu? chyba mozna to przekazywac zgodnie z architektura rnn
* sprobuj GRUs zamiast LSTMs? - bo sa lzejsze
* gradient clipping? clip_grad_norm
* str 207 - training pipelines zaleznie od problemu


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


### GANs research
* https://github.com/williamSYSU/TextGAN-PyTorch
* https://arxiv.org/pdf/2212.11119.pdf
* https://www.scielo.org.mx/pdf/cys/v24n1/1405-5546-cys-24-01-17.pdf
* https://arxiv.org/ftp/arxiv/papers/2308/2308.00939.pdf
* https://becominghuman.ai/generative-adversarial-networks-for-text-generation-part-2-rl-1bc18a2b8c60

### research reseults
* https://aclanthology.org/2021.acl-long.6.pdf - jakis pomysl generowania dan od prawej do lewej a nie lewej do prawej, by rozpoczynac od rymu + jakos wykorzystanie n-gramow zeby uwzglednic tez kilka slow przed ostatnim w rymach + jakies pomysly na metricsy **+ inne papiery linkowane zwiazane z tematem**

* https://colab.research.google.com/drive/12g07FS2WkNctNy_bYb7a5ZNFAsJcN0dz?usp=sharing&hl=en#scrollTo=Gxk7rxv50APc - jakis notebook z phonetic wykrywaniem rymow

* https://replicate.com/blog/turn-your-llm-into-a-poet - tez wspomina fajne papiery,z enkodowaniem informacji o sylabach, koncach zdan itd

* https://towardsdatascience.com/generating-haiku-with-deep-learning-dbf5d18b4246 - dodaje dodatkowe funkcje jako czesc sieci generujacej slowa i potem cale haiku, konwertujaca rezultaty na strukture haiku (5 sylab - 7 - 5) + musi dzielic na sylaby zeby to robic, generalnie dziala, wiec fajnie gdybys chcial iles sylab na zdanie zeby ci dzielilo
