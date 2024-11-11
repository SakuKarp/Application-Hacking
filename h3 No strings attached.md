## a) Strings. Lataa ezbin-challenges.zip Aja 'passtr'. Selvitä oikea salasana 'strings' avulla. Selvitä myös lippu. (Ensisijaisesti katsomatta sorsia, jos osaat.)

Aloitin lataamalla paketin ezbin-challenges.zip Teron sivulta https://terokarvinen.com/application-hacking/. Purin tiedoston jonka jälkeen lähdin tutkimaan tiedostoa.


![image](https://github.com/user-attachments/assets/24560ff3-11e8-4910-b741-df3a93dd4ddb)

Ajoin komennon strings passtr joka avasi tiedoston josta löytyi flagi:

        strings passtr # strings komento etsii tiedostosta kaikki tulostettavat merkkijonot ja tulostaa ne "passtr" kohde tiedostosta


![image](https://github.com/user-attachments/assets/a73feb48-30fd-4179-994d-ea78b9e2c4db)




![image](https://github.com/user-attachments/assets/f69d8784-0602-42e0-bc1b-6bbc674068c3)




## b) Tee passtr.c -ohjelmasta uusi versio, jossa salasana ei näy suoraan sellaisenaan binääristä. Osoita testillä, että salasana ei näy. (Obfuskointi riittää.)

En tiedä miten obfuskointi toimii koodissa joten käytin tähän tehtävään Copilottia joka avasi hieman tätä miten tämä toimii.  lähde: https://copilot.microsoft.com/


Alkuperäinen: 

![image](https://github.com/user-attachments/assets/b809811e-af19-4bb9-ac40-8fe58534b9fa)

Muutettu:

![image](https://github.com/user-attachments/assets/2d1e4e5a-1c1f-4ec2-b5e8-1b4a0dd441be)

Kun koodi muunnettu käännetään se :

    gcc -o passtr passtr.c # gcc kutsuu kääntäjän, -o Määrittää tiedoston nimeksi psstr, psstr.c tiedosto joka käännetään

Koodiin lisätään obfuscate -funktio, joka käyttää XOR-operaatiota obfuskoimiseen. Se käy läpi jokaisen salassanan merkin ja tekee XOR operaation annetulla avaimella key.

    char key = 'k'; # Obfuskaatioavain
    obfuscate(secret, key); # obfuskoidaan salainen salasana
    obfuscate(password, key); # obfuskoidaan käyttäjän syöttämä salasana


![image](https://github.com/user-attachments/assets/b0cb274b-d7b8-4005-8a3e-ae11c02a1dcd)

kuvassa näkyy salasanaa ei näy enää strings passtr komennolla.





## c) Packd. Aja 'packd' paketista ezbin-challenges.zip. Mikä on salasana? Mikä on lippu? (Tämä tehtävä on hieman haastavampi. Kirjaa ylös kokeilemasi lähestymistavat ja keksimäsi hypoteesit. Toivottavasti pääset itse maaliin, mutta jos et, läpikävely paljastuu tunnilla...)

Alotin tekemällä tehtvää katsomalla strings packd komennolla packd tiedostoa. Huomasin että kirjoitus on salattu ja löysin alhaalta tekstin että, paketti on pakattu UPX executable packerillä. Kysyin tekoälyltä miten tämän voisi purkaa ja se antoi vastauksesksi lataamalla UPX ja purkaamalla tiedoston.

![image](https://github.com/user-attachments/assets/d04daaaa-9e91-4073-8f53-2b803a6ad241)

![image](https://github.com/user-attachments/assets/ba620831-8dbf-49be-babb-382e0dd218fc)

Latasin UPX ja purin tiedoston https://github.com/upx/upx/releases/tag/v4.2.4 käyttäen wget  ja tar komentoja

![image](https://github.com/user-attachments/assets/63f6cb6f-8ce1-48fa-8f64-d9f28dbcef37)

Menin upx hakemistoon ja purin "packd" tiedoston komennolla: 

    ./upx -d ~/Downloads/challenges/packd/packd # purkaa tiedoston ja palauttaa sen alkuperäiseen mutoon. -d decompress eli käskee purkamaan tiedoston.
    
UPX ilmoitti että purkasi tiedoston. Tämän jälkeen menin katsomaan uudestaan packd tiedostoa strings packd komennolla ja löysin salasanan sekä flagin :

![image](https://github.com/user-attachments/assets/34250a99-c751-4d23-9cb5-466e7fcc235a)


# References

https://www.javatpoint.com/linux-strings-command

https://github.com/upx/upx/releases

https://terokarvinen.com/application-hacking/

https://copilot.microsoft.com/
