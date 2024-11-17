h4 Kääntöpaikka

## x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Hammond 2022: Ghidra for Reverse Engineering (PicoCTF 2022 #42 'bbbloat') (Video, noin 20 min)


- Reverse engineering
- Bbbbloat CTF jossa etsitään flagi binääristä
- Obfuskointi
- ltrace / strace 
- Ghidra sen käyttäminen ja asentaminen
- hexat / decimals


## a) Asenna Ghidra.

Aloitin asentamalla Ghidran kalille komennolla:

    sudo apt-get install ghidra

## b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. ezbin-challenges.zip


Alotin lataamalla ezbin-challenges.zip Teron sivulta ja purin sen. Tämän jälkeen loin uuden projektin packd_saku ghidraan.

![{96103132-FB26-40D9-92F1-7595EEB07076}](https://github.com/user-attachments/assets/9effd24d-0c8c-449c-b364-4b3f232faa24)

Avasin packd tiedoston ja analysoin sen. Etsin tämän jälkeen pääohjleman joka löytyi Functions -> main. Kävimme tunnilla tämän läpi ja nimesin muuttujia input ja password:


![{57EC931A-CD32-45FF-B754-032274640BBB}](https://github.com/user-attachments/assets/be22b42c-5373-42af-a1a8-f68597d59ad4)

    int input; # muuttuja, joohn tallenetaan strcmp-funktion palauttama arvo
    char password[32]; # merkkijono, johon käyttäjän syöttämä salasana tallennetaan
    puts("What\'s the password?"); # ohjelma tulostaa kehotteen, jossa kysytään salasanaa
    __isoc99_scanf("%s", password); # ohjelma odottaa käyttäjän syötettä ja tallentaa sen muuttujaan password
    strcmp(password, "pillos-AnAnAs"); # vertailee käyttäjän syötettä salasanaksi "pillos-AnAnAs". Jos syöte vastaa tätä merkkijonoa, strcmp palauttaa arvon 0
    
Ohjelma pyytää käyttäjältä salasanan ja tarkistaa, vastaako se oikeaa salasanaa "pillos-AnAnAs". Jos salasana on oikea, ohjelma tulostaa FLAG-arvon. Muuten tulostetaan epäonnistumisviesti.

## c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. ezbin-challenges.zip

Aloitin luomalla uuden projektin passtr ghidrassa. kun sain avattua tiedoston lähdin etsimään mistä pääsisi muokkaamaan tiedostoa.

![{E275215A-F52C-484E-8F44-E7BC2880689C}](https://github.com/user-attachments/assets/a844f59f-7cac-4dae-b73b-d62c0843f1b3)

Menin taas symbol tree -> main josta tupla klikkaamalla if (iVar1 == 0) kohtaa 

Sieltä löytyi JNZ jump if not zero. vaihdoin sen JZ eli jump if zeroksi.

![{DC3E6A49-A8CC-47F2-8763-0D7A1E4935D5}](https://github.com/user-attachments/assets/019de30e-b5b0-40fc-84d0-c5a5df340e9e)

Tämän jälkeen tallensin tiedoston uudella nimellä passtr_1 jonka jälkeen annoin sille oikeudet: chmod +x passtr_1. 

![{CEF7DE3D-8608-45DD-9B7F-024C84C9D78F}](https://github.com/user-attachments/assets/b0e656db-fd87-40de-ae92-51d4db7421e5)


Testasin toimiiko salasana eri sanoilla kuin sala-hakkeri-321 ja sain tulokseksi:

![{8B227A71-17F2-4180-ADDE-F9267E462F41}](https://github.com/user-attachments/assets/39bde52e-8a99-433b-92d0-7c1ac347c7c5)

eli salasana toimii kaikilla muilla salasanoilla paitsi oikealla.

## d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".

Aloitin tehtävän kloonaamalla repon https://github.com/NoraCodes/crackmes omalle .

    git clone https://github.com/NoraCodes/crackmes.git

![{1335276D-FC60-4693-8FD3-CBE21D576271}](https://github.com/user-attachments/assets/1efb08f8-eecd-4b4c-9b16-7b1df427b554)

readme:

![{969668E5-BE38-4E64-B167-6F36039209A2}](https://github.com/user-attachments/assets/5da7a158-0702-43a3-92a1-f7b09d2f1029)



## e) Nora crackme01. Ratkaise binääri.


aloitin luomalla tiedoston 

    make crackme01
    

![{17B4D4FF-F93F-4A3A-9D69-DE1307C7AF87}](https://github.com/user-attachments/assets/5e658bad-47e3-405a-881d-1431381cbc00)

testailin kaikkea:

    file crackme01.64 # selvittää tiedston tyypin

    strings crackme01.64 # näyttää tulostettavat merkkijonot

    ltrace crackme01.64 # näyttää kutsutut kirjastofunktiot

    

![{BDDD39DA-3F5F-465C-B434-024D146332BC}](https://github.com/user-attachments/assets/34e94008-ce8a-4868-8fb7-c03a54af0727)


![{6429ADC5-4251-4123-910A-38F8E13FA241}](https://github.com/user-attachments/assets/32ba436e-a0b7-4def-9acf-f20fecdd5bf5)


komennolla ltrace ./crackme01.64 pass löysin kohdan mistä löytyi : strncmp("pass", "password1", 9) 

Testasin salasanaa password1 ja se oli oikein.

![{FB4C2958-7C18-4502-B451-C59531ECACEA}](https://github.com/user-attachments/assets/f78616d4-19af-4c6a-8a2d-a7ff9195fcbc)
    



## e) Nora crackme01e. Ratkaise binääri.

Aloitin taas luomalla tiedoston:

    make crackme01e

![{6D944AF5-82E0-462C-97B0-071C99F8DB5D}](https://github.com/user-attachments/assets/7d238fbb-1a75-4182-aab4-fd0350118e53)

Tämän jälkeen testasin samat kuin viime tehtävässä.

    file crackme01e.64 

    strings crackme01e.64

    ltrace crackme01e.64

![{BEDAE18F-5A7B-4DEC-8F58-AF6D68DC0426}](https://github.com/user-attachments/assets/ac9dce49-fe53-4f6f-9c86-a8f13de52654)

testasin salasanaa slm!paas.k joka ei ollut oikea. oikea salasana on : slm\!paas.k


käyttämällä \ huutomerkin edessä varmistetaan ettei shell ei tulkitse huutomerkkiä erityisenä merkkinä tai komennon osana.

## f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.

Kokeilin tässäkin samoja mitä edellisissä tehtävissä. Sain salasanaksi tässä password1 joka ei ollut oikein.

aloitin tukimalla tiedostoa Ghidralla

![{6382071D-D2C2-401B-9DDC-26C5EB18FC33}](https://github.com/user-attachments/assets/b97ada61-cf2d-4b44-ace7-253061e94a0f)


jatkan tehtävää myöhemmin..



# References

https://terokarvinen.com/application-hacking/

https://www.youtube.com/watch?v=oTD_ki86c9I (GHIDRA for Reverse Engineering (PicoCTF 2022 #42 'bbbloat'))

https://github.com/NoraCodes/crackmes

https://nora.codes/tutorial/an-intro-to-x86_64-reverse-engineering/

https://copilot.microsoft.com/



