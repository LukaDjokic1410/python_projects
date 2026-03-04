Kreiranje i poređenje modela za klasifikaciju teksta
Tema i predmet rada: U ovom radu se bavim analizom i poređenjem različitih načina na koje računar može da razume tekst i svrsta ga u određenu kategoriju. Konkretno, testiram nekoliko modela mašinskog učenja kako bih video koji najbolje prepoznaje sentiment (emociju) u objavama navijača na Twitter-u.

Svrha rada: Glavni cilj mi je da proverim da li se isplati koristiti komplikovane i spore algoritme (poput XGBoost-a) ili su za kratke poruke, kao što su tvitovi, dovoljni i jednostavniji modeli (poput Naive Bayes-a). Želim da pronađem model koji je najprecizniji, a da pritom nije previše složen bez potrebe.

Izvor podataka: Podatke sam preuzeo sa Kaggle platforme. U pitanju je dataset "FIFA World Cup 2022 Tweets" koji sadrži preko 22.000 tvitova objavljenih na dan početka Svetskog prvenstva.
Link ka datasetu: https://www.kaggle.com/datasets/tirendazacademy/fifa-world-cup-2022-tweets

Metodologija i obrazloženje izbora:
Za rad sam napravio četiri različita modela koristeći Pipeline:

Model 1 (TF-IDF + Naive Bayes):
Za razliku od običnog brojanja, TF-IDF umanjuje značaj rečima koje se prečesto pojavljuju, a ističe one koje nose specifično značenje.
Naive Bayes je algoritam mašinskog učenja za klasifikaciju koji predviđa klasu nekog podatka koristeći verovatnoću. Zasniva se na pretpostavci da su sve karakteristike međusobno nezavisne.
Naive Bayes daje dobre rezultate u mnogim realnim primenama pa tako i u analizi sentimenata.


Model 2 (Word Embeddings + Random Forest):
Word Embeddings:Pristup modelovanju teksta gde se svaka reč predstavlja višedimenzionalnim vektorom koji bi trebalo da enkodira što je moguće više značenja (semantike) reči.Značenje reči je u velikoj meri određeno rečima u “okruženju”, odnosno rečima sa kojima se često zajedno pojavljuje.
Random Forest je veoma efikasan i radi sa stablima, slicna bagging ideji sa poboljšanim umanjenjem varijanse.

Model 3 (Hibridni (kombinovani): TF-IDF + Logistička regresija):
U kombinovanom modelu sam uz tekst dodao i numerički podatak – broj lajkova tvita.
Logistička regresija je supervizovani algoritam mašinskog učenja koji se koristi za klasifikaciju i predviđa verovatnoću da nešto pripada određenoj klasi.

Model 4 (XGBoost):
XGBoost je napredni algoritam mašinskog učenja koji poboljšava tačnost i brzinu u odnosu na klasične modele poput običnih stabala odlučivanja i već korišćenog Random Forest-a.

Evulacione metrike:
Accuracy (Tačnost): Ovo mi je glavna mera jer mi jasno govori u koliko procenata je model pogodio tačan sentiment.
F1-score: Ovu metriku koristim kao dodatnu proveru. Pošto u podacima imam mnogo manje negativnih tvitova nego ostalih, F1-score mi pomaže da budem siguran da model nije samo "naučio napamet" najčešće klase, već da stvarno prepoznaje i one ređe kategorije
