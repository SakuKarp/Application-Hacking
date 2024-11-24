# h5 Se elää! (Tämä tehtävänanto sisältää pääosin Lari Iso-Anttilan laatimia tehtäviä.)

## a) Lab1. Tutkiminen mikä on ohjelmassa vialla ja miten se korjataan.

Alotin lataamalla paketin lab1 ja purkamalla sen virtuaalikoneelleni. 

    wget wget https://terokarvinen.com/application-hacking/lab1.zip
    unzip lab1.zip

Tämän jälkeen ajoin gdb_examle1. 

    make part1 # kääntää ohjelman käyttämällä Makefileä
    ./gdb_example.1  # avaa ohjelman
    gdb ./gdb_example.1 # käynnistää ohjelman gdb

Joka antoi minulle vastaukseksi :

![image](https://github.com/user-attachments/assets/0fc1aa67-e5b0-4bc3-a224-f66a180c3389)

Huomasin heti että siinä tuli Segmentation fault joten lähdin tutkimaan tätä netistä. Ensimmäinen linkki minkä löysin kun kirjoitin segmentation fault oli : https://stackoverflow.com/questions/2346806/what-is-a-segmentation-fault

Sivulla kerrottiin että, segmentation fault on erityinen virhetyyppi joka syntyy, kun ohjelma yrittää käyttää muistia joka ei kuulu sille.

Tämän jälkeen aloitin debuggaamisen:


loin breakpointin mainiin jonka jälkeen lähdin tutkimaan muuttujien arvoja.

    print bad_message
    print good_message

Tämän jälkeen siirryin seuraavaan next ja lähdin tutkimaan missä vika voisi olla.

![image](https://github.com/user-attachments/assets/d9e9d3ed-30de-4925-a44c-9dbe71d5f290)

huomasion että virhe tapahtuu rivillä 18

![image](https://github.com/user-attachments/assets/88edaf3e-959f-45fc-9954-190ed63d67d7)

![image](https://github.com/user-attachments/assets/799aacf1-a12e-4eca-bce8-cbad25a1c5bd)


Joten tämä liittyy jotenkin siihen että 14 rivillä on = NULL;. Ohjelma siis yrittää käyttää osoitinta tässä, joka ei osoita mihinkään mikä toimisi.


Muokkasin tämän null arvon testiin ja tallensin:

    make part1 # käntää ohjelman uudelleen
    gdb ./gdb_example1 # käynnistää ohjelman gdb
    run # runnaa tiedoston

![image](https://github.com/user-attachments/assets/0d3e7c7e-51f3-4a00-831b-8ddf182460c5)





runnasin sen :

![image](https://github.com/user-attachments/assets/9c81be2f-e2c1-4461-9121-5d4b6cc44e94)


Ja näin ainakin ohjelma printtaa molemmat ilman erroria.

 

## b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi.

Aloitin lab2 paktin lataamisen ja purkamisen. Tämän jälkeen alkoitin tutkimaan tiedostoa.

    make passtr2o
    gdb ./passtr2o


Hetken tutkimisen jälkeen löysin mAsdf3a johon loin breakpoitin. Täältä löysin oman salasanan mitä olin testannut sekä salasanan anLTj4u8.


![image](https://github.com/user-attachments/assets/80cf930f-a12d-4741-a718-8411d2123458)

Tämä ei ollut oikea salasana: 

![image](https://github.com/user-attachments/assets/0cc04535-fc5b-483b-9d8e-65d45644f92c)


Tutkiskelin vielä kauan tätä mutta tämä oli liian haastavaa itselleni joten en päässyt tästä pidemmälle.











## c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: NoraCodes / crackmes.

Minulla on mennyt näihin kaikkiin tehtäviin jo noin 10 tuntia mutta yritän vielä jatkaa näitä myöhemmin. Tämän viikon tehtävät ovat olleet todella hankalia minulle ainakin mutta olen silti oppinut jokseenkin miten GDB debuggeri toimii ja muutenkin reverse engineeringistä.


## References:

https://stackoverflow.com/questions/2346806/what-is-a-segmentation-fault

https://terokarvinen.com/application-hacking/

[GDB cheatsheet 2007 Marc Haisenko](https://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)

https://www.youtube.com/watch?v=Dq8l1_-QgAc


