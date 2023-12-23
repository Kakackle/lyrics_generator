### todos

1. TODO: prosty character-based model na szekspirowskich sonetach (bo takie tutsy)
2. TODO: sprobuj go powiekszyc o wiecej warstw LSTM i epochs
3. TODO: word embeddings zamiast character
4. TODO: zbierz dataset lyrics z ta biblioteka do geniusa dla pythona
5. TODO: sprobuj z tym tekstem poprzednie
6. TODO: research cos wiecej zeby uwzglednialo rymy, poetyzm, konkretne ograniczenia metryczne (ilosc sylab?, znakow, slow)

### ways to develop

also:
* TODO: parametryzacja typu ile znakow / slow rozwaza przed generacja kolejnego, jaki dropout itd
* cos z wykorzystaniem pretrained modeli jak GPT2
* https://medium.com/@david.campion/text-generation-using-bidirectional-lstm-and-doc2vec-models-1-3-8979eb65cb3a - zaczyna od generowaniu na podstawie znakow, ale potem przechodzi do slow, zdan i wprowadza troche losowosci z temperatura i trenuje dwa modele, by jeden uczyl sie na znakach i slowach i generowal zdania, a drugi na tych generowanych zdaniach i wybieral jakos najlepsze, zeby calsoc miala wiecej sensu - rezultaty srednie, ale ciekawe
* te przyklady dzialaja z wlasnymi oknami znakow i zamianieniu znakow na proste inty, ale gdyby przeszlo do slow, to trzeba by przejsc do rzeczywistych embeddings, w tym np. moze pretrained beda lepsze

### extra directions

* eksperymenty z dlugoscia wyjscia jak z tutorialu TF udemy predicting - bo nie musi byc jeden znak

* https://huggingface.co/blog/how-to-generate - wykorzystanie pretrained tokenizatorow, roznyz transformatorow, strategie generowania

* https://www.kaggle.com/code/purvasingh/text-generation-via-rnn-and-lstms-pytorch - niezly kod w pytorchu

### GPT-2 etc
* https://github.com/minimaxir/gpt-2-simple
* https://github.com/minimaxir/aitextgen

### extra datasets
* https://www.kaggle.com/datasets/tgdivy/poetry-foundation-poems
* 

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

