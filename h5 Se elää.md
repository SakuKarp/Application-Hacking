# h5 Se elää! (Tämä tehtävänanto sisältää pääosin Lari Iso-Anttilan laatimia tehtäviä.)

a) Lab1. Tutkiminen mikä on ohjelmassa vialla ja miten se korjataan.

Alotin lataamalla paketin lab1 ja purkamalla sen virtuaalikoneelleni. 

    wget wget https://terokarvinen.com/application-hacking/lab1.zip
    unzip lab1.zip

Tämän jälkeen ajoin gdb_examle1. 

    ./gdb_example.1

Joka antoi minulle vastaukseksi :

![image](https://github.com/user-attachments/assets/0fc1aa67-e5b0-4bc3-a224-f66a180c3389)

Huomasin heti että siinä tuli Segmentation fault joten lähdin tutkimaan tätä netistä. Ensimmäinen linkki minkä löysin kun kirjoitin segmentation fault oli :

https://stackoverflow.com/questions/2346806/what-is-a-segmentation-fault

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


Muokkasin tämän null arvon testiin:

![image](https://github.com/user-attachments/assets/0d3e7c7e-51f3-4a00-831b-8ddf182460c5)


runnasin sen :

![image](https://github.com/user-attachments/assets/9c81be2f-e2c1-4461-9121-5d4b6cc44e94)





Huomasin heti että siinä tuli Segmentation fault joten lähdin tutkimaan tätä netistä. Ensimmäinen linkki minkä löysin kun kirjoitin segmentation fault oli :

https://stackoverflow.com/questions/2346806/what-is-a-segmentation-fault

Sivulla kerrottiin että, segmentation fault on erityinen virhetyyppi joka syntyy, kun ohjelma yrittää käyttää muistia joka ei kuulu sille.

Tämän jälkeen aloitin debuggaamisen:









  

b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi.

c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: NoraCodes / crackmes.

Larin kalvot löytyvät Moodlesta
