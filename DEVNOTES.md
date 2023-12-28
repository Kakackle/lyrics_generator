### Practical tips

#### Z ksiazki NLP Pytorch 2019
* str 61 wlasne przygotowanie Dataset z Pytorcha uwzgledniajace podzial na train/test/val, vectorizing itd w jednej klasie
* str 159 nie rozumiem do konca, ale wazne **conditioning RNNs** dodatkowym inputem, ktory jest przeksztalcany w embedding i dodawany jako pierwszy hidden state RNN, od niego zaczyna i on bedzie kierowac reszta, zamiast zaczynac od niczego - ale to dotyczy uczenia, jak potem zrobic to przy uzywaniu? chyba mozna to przekazywac zgodnie z architektura rnn
* sprobuj GRUs zamiast LSTMs? - bo sa lzejsze
* gradient clipping? clip_grad_norm
* str 207 - training pipelines zaleznie od problemu