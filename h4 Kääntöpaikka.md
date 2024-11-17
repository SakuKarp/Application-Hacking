h4 Kääntöpaikka

# x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Hammond 2022: Ghidra for Reverse Engineering (PicoCTF 2022 #42 'bbbloat') (Video, noin 20 min)


- Reverse engineering
- Bbbbloat CTF jossa etsitään flagi binääristä
- Obfuskointi
- ltrace / strace 
- Ghidra sen käyttäminen ja asentaminen
- hexat / decimals


# a) Asenna Ghidra.

Aloitin asentamalla Ghidran kalille komennolla:

    sudo apt-get install ghidra

# b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. ezbin-challenges.zip


Alotin lataamalla ezbin-challenges.zip Teron sivulta ja purim sem. Tämän jälkeen loin uuden projectin packd_saku ghidraan.

![{96103132-FB26-40D9-92F1-7595EEB07076}](https://github.com/user-attachments/assets/9effd24d-0c8c-449c-b364-4b3f232faa24)

Avasin packd tiedoston ja analysoin sen. Etsin tämän jälkeen pääohjleman joka löytyi Functions -> main. Kävimme tunnilla tämän läpi ja nimesin muuttujia ipnut ja password:


![{57EC931A-CD32-45FF-B754-032274640BBB}](https://github.com/user-attachments/assets/be22b42c-5373-42af-a1a8-f68597d59ad4)

    int input; # muuttuja, joohn tallenetaan strcmp-funktion palauttama arvo
    char password[32]; # merkkijono, johon käyttäjän syöttämä salasana tallennetaan
    puts("What\'s the password?"); # ohjelma tulostaa kehotteen, jossa kysytään salasanaa
    __isoc99_scanf("%s", password); # ohjelma odottaa käyttäjän syötettä ja tallentaa sen muuttujaan password
    strcmp(password, "pillos-AnAnAs"); # vertailee käyttäjän syötettä salasanaksi "pillos-AnAnAs". Jos syöte vastaa tätä merkkijonoa, strcmp palauttaa arvon 0
    


# c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. ezbin-challenges.zip



# d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".

# e) Nora crackme01. Ratkaise binääri.

# e) Nora crackme01e. Ratkaise binääri.

# f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.

