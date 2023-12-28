## todos / konkretne kroki

1. ~~prosty character-based model na szekspirowskich sonetach (bo takie tutsy)~~
2. ~~sprobuj go powiekszyc o wiecej warstw LSTM i epochs~~
3. ~~zbierz dataset lyrics z ta biblioteka do geniusa dla pythona~~
4. TODO: sprobuj z tym tekstem poprzednie - what?
5. ~~research cos wiecej zeby uwzglednialo rymy, poetyzm, konkretne ograniczenia metryczne (ilosc sylab?, znakow, slow)~~

=============================================

6. ~~word embeddings zamiast character~~
nauka: przy uczeniu na slowach, window musi byc mniejszy, zeby zdania mialy sens
za duzy traci cokolwiek, kontekst
ale tez nie za maly, bo chwyta nie to co trzeba
7. TODO: okej, dziala ze slowami, ale chwyta apostrofy itd, moze by je usunac itp i zoaczyc
8. TODO: a mzoe jakis dropout itd
9. TODO: temperatura
10. TODO: ocena zdan
11. TODO: stanford, nlpoverview
12. TODO: kompletniejsza wektoryzacja i embedowanie ze spacy itd? bo na pewno da sie lepiej niz recznie z tym int_to_word i word_to_int itd
7. TODO: parametryzacja typu ile znakow / slow rozwaza przed generacja kolejnego, jaki dropout itd - dokonuj jakiegos porownania
8. TODO: cos z wykorzystaniem pretrained modeli jak GPT2
9. TODO: z https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-1-3-8979eb65cb3a: dodaj jak tutaj dodatkowa funkcje samplowania z temperatura (+ poszukaj moze wytlumaczenia matematycznie tej temperatury), poza tym words, sprobuj bidirectional lstm itd

10. TODO: sproboj jak https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-1-3-8979eb65cb3a - zaczyna od generowaniu na podstawie znakow, ale potem przechodzi do slow, zdan i wprowadza troche losowosci z temperatura i trenuje dwa modele, by jeden uczyl sie na znakach i slowach i generowal zdania, a drugi na tych generowanych zdaniach i wybieral jakos najlepsze, zeby calsoc miala wiecej sensu - rezultaty srednie, ale ciekawe - rozwiniete w pliku [SOLUTIONS_RESEARCH.md]

11. TODO: explore ways of saving the best model during training in order to be able to stop training when needed, prevent overfitting etc

12. TODO: Sproboj RNNs, GRUs, Bidirectional LSTMs

13. TODO: eksperymenty z dlugoscia wyjscia jak z tutorialu TF udemy predicting - bo nie musi byc jeden znak - tzn z horizontem do przewidywania

### ways to develop

* moze przygotowac kilka modeli na podstawie tekstow kilku artystow i umozliwiac uzytkownikowi mieszanie rezultatow w wybrany sposob (np. DOOM 80%, GZA 20%), bo generalnie modele to sa po prostu computation graphs, mozna laczyc, dodawac etc wyjscia i jest tez temat model ensemble - pytanie czy jest to mozliwe do realizacji jakos po wycwiczeniu juz w taki sposob, czy raczej trzeba by myslec, by samemu stworzyc jakis sposob mieszania rezultatow z roznych modeli, np. troche tego, troche tego losowo itd, cos z tym ze dodajesz do outputu z jednego modelu, ktory idzie do drugiego, przez co bedzie zmieniony itd, tylko wtedy musza albo zwracac pelne slowa albo jeszcze lepiej pelne zdania a nie symbole

* wykorzystanie konceptow named entity recognition, part of sentence, structure of sentences

* jakos narzucanie dlugosci zdan, tzn po ilus znakach dodajesz manualnie newline etc

* znaczenia slow, wordnet, spacy np. w swoim lemmitazorze wykorzystuje, ale to wtedy w uczeniu po slowach

* wykorzystanie czestosci slow, TF-IDF itd

* Transformers, BERT

### extra directions

* https://huggingface.co/blog/how-to-generate - wykorzystanie pretrained tokenizatorow, roznyz transformatorow, strategie generowania

* https://www.kaggle.com/code/purvasingh/text-generation-via-rnn-and-lstms-pytorch - niezly kod w pytorchu

* https://aclanthology.org/2021.acl-long.6.pdf - jakis pomysl generowania dan od prawej do lewej a nie lewej do prawej, by rozpoczynac od rymu + jakos wykorzystanie n-gramow zeby uwzglednic tez kilka slow przed ostatnim w rymach + jakies pomysly na metricsy **+ inne papiery linkowane zwiazane z tematem**

* https://colab.research.google.com/drive/12g07FS2WkNctNy_bYb7a5ZNFAsJcN0dz?usp=sharing&hl=en#scrollTo=Gxk7rxv50APc - jakis notebook z phonetic wykrywaniem rymow

* https://replicate.com/blog/turn-your-llm-into-a-poet - tez wspomina fajne papiery,z enkodowaniem informacji o sylabach, koncach zdan itd

* https://towardsdatascience.com/generating-haiku-with-deep-learning-dbf5d18b4246 - dodaje dodatkowe funkcje jako czesc sieci generujacej slowa i potem cale haiku, konwertujaca rezultaty na strukture haiku (5 sylab - 7 - 5) + musi dzielic na sylaby zeby to robic, generalnie dziala, wiec fajnie gdybys chcial iles sylab na zdanie zeby ci dzielilo


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

### NTLK book
https://www.nltk.org/book/ch01.html
