# h6 Sulaa hulluutta

# a) Tutki tiedostoa h1.jpg

Aloitin tutkimisen ensimmäiseksi lataamalla tiedoston.

    wget https://terokarvinen.com/application-hacking/h1.jpg

Tämän jälkeen katsoin kuvan tiedot ja tulostin merkkijonot joita tutkailin :

    file h1.jpg
    strings h1.jpg

Tiedosto näyttää ihan normaalille kuva tiedostolle.

![image](https://github.com/user-attachments/assets/dc33731f-14a9-4dbd-8b00-cf2e24749e27)

Kun katsoin tiedostoa strings komennolla löysin eri xml ja xmlpk tiedostoja jotka saattavat sisältää jotain piilotettua.



# b) Tutki tiedostoa h1.jpg binwalk:lla

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




c) FOSS (Free Android OpenSource).

Etsin mieluisen sovelluksen sivulta https://github.com/offa/android-foss ja valitsin sieltä FreePaintin

ZIP
Aloitin nimeämällä tiedoston uudestaan:

    mv app-release.apk app-release.zip
    mkdir ss #luo uuden kansion
    mv app-release.zp ss # siirtää uuteen kansioon
    unzip app-release.zip # purkaa

Tämän jälkeen päästiinkin katsomaan mitä tiedoston sisällä on:

![image](https://github.com/user-attachments/assets/f7e6ae4e-640f-4bde-81cf-0b4d64d8182c)


JADX

Aloitin lataamalla JADX gitistä : https://github.com/skylot/jadx

        wget https://github.com/skylot/jadx/releases/download/v1.5.1/jadx-1.5.1.zip
        unzip jadx-1.5.1.zip
        ./jadx-gui

Avasin classes.dex tiedoston käyttäen jadx ja sain sieltä kaiken auki. Siellä oli paljon tietoa ohjelmasta.

![image](https://github.com/user-attachments/assets/74bc9f3c-f679-4671-86ff-0644518c80ed)


Bytecode-viewer

Aloitin lataamalla paketin verkosta. 

    wget https://github.com/Konloch/bytecode-viewer/releases/download/v2.12/Bytecode-Viewer-2.12.jar
    java -jar Bytecode-Viewer-2.12.jar # avaa

![image](https://github.com/user-attachments/assets/0767640d-3c49-4bda-97ae-ef87e3da5eaf)

Kun sain bytecoderin auki avasin zippi tiedoston app-release ja pääsin taas tutkimaan tiedoston sisältöä: 

![image](https://github.com/user-attachments/assets/9eb5a055-13b7-41d8-b051-eb4485f1ab1a)



## References

https://askubuntu.com/questions/733169/how-to-install-libxml2-in-ubuntu-15-10

https://github.com/skylot/jadx

https://github.com/Konloch/bytecode-viewer/

https://terokarvinen.com/application-hacking/
