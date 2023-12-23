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


### pytorch general

* TODO: explore ways of saving the best model during training in order to be able to stop training when needed, prevent overfitting etc

