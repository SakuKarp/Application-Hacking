# h6 Sulaa hulluutta

# a) Tutki tiedostoa h1.jpg jo opituilla työkaluilla. Mitä saat selville?

Aloitin tutkimisen ensimmäiseksi lataamalla tiedoston.

    wget https://terokarvinen.com/application-hacking/h1.jpg

Tämän jälkeen katsoin kuvan tiedot ja tulostin merkkijonot joita tutkailin :

    file h1.jpg
    strings h1.jpg

Tiedosto näyttää ihan normaalille kuva tiedostolle.

![image](https://github.com/user-attachments/assets/dc33731f-14a9-4dbd-8b00-cf2e24749e27)

Kun katsoin tiedostoa strings komennolla löysin eri xml ja xmlpk tiedostoja jotka saattavat sisältää jotain piilotettua.



# b) Tutki tiedostoa h1.jpg binwalk:lla. Mitä tietoja löydät nyt tiedostosta? Mitä työkalua käyttäisit tiedostojen erottamiseen?

Aloitin tehtävän asentamalla binwalkin, jonka jälkeen lähdin tutkimaan kuva tiedosta uudestaan.

    Sudo apt-get install binwalk
    binwalk h1.jpg

![image](https://github.com/user-attachments/assets/623e81de-68d7-4099-bb98-526eb73f9eb7)

Kun aloitin tutkimisen binwalkilla huomasin heti että, xml tiedostot ovat zipattuja tiedostoja joten lähdin tutkimaan niitä.

    binwalk --extract --directory h1purku h1.jpg # purkaa kaikki löydetyt tiedostot h1purku -hakemistoon

Lähdin tutkimaan tiedoston sisältöä. Sisältö oli sekavaa joten lähdin tutkimaan miten voisin formatoida tiedoston jotta siitä saisi jotain selvää. Löysin xmllint työkalun jolla pystytään tarkastella XML tiedostoja. Työkalulla pystyy myös validoitata sekä muokata tiedostoja.

    sudo apt-get install libxml2-utils # asentaa työkalun
    xmllint --format document.xml # formatoi document.xml tiedoston

Ennen formatointia:
![image](https://github.com/user-attachments/assets/d979c1a1-3cb5-4709-83f6-e11314d5a00a)


Formatoinnin jälkeen:
![image](https://github.com/user-attachments/assets/2803afce-54aa-4b51-b54e-9c6045c95f15)

documents.xml tiedostosta löytyi hauskoja tulevaisuuteen liittyviä ennustuksia. Nämä varmaan pitävät paikkansa ja voivat olla salaista tietoa.




c) FOSS (Free Android OpenSource). Tutustu Android-sovelluksiin Offan (2024) 
listalta: Android FOSS. Valitse listalla itsellesi mielenkiintoisin applikaatio ja mene sen GitHubiin. 
Lataa ohjelman APK itsellesi ja käytä seuraavia työkaluja tutustuaksesi, miten APK:n voi avata.
ZIP
JADX
Bytecode-viewer

## References

https://terokarvinen.com/application-hacking/
