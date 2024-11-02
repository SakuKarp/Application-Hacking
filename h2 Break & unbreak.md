# x) Lue/katso/kuuntele ja tiivistä. Linkit lähteissä.

OWASP: OWASP Top 10: A01 Broken Access Control
- Haavoittuvuudet jotka sisältävät luvattoman pääsyn, URL manipulointi, tilitietojen väärinkäyttö ja eri API-kutsujen puutteelliset suojat.
- Haavoittuvuuden ennalta ehkäisy. Pääsynhallintaa kannattaa käyttää vain palvelinpuolella, estää pääsy oletuksena, käyttää yhtenäöiosiä pääsynhallintamekanismeja, seurata epäonnistuneet yritykset ja varmistaa tunnisteiden turvallisuus.

Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf
- Avoimen lähdekoodintyökalu jonka on tehnyt joohoi.
- Brute force etsintään käytettävä
- Tehokas fuzzaus työkalu

PortSwigger: Access control vulnerabilities and privilege escalation

- Käyttöoikeuksien muuttaminen (esim. roolit)
- Pääsynhallinan estäminen

Karvinen 2006: Raportin kirjoittaminen

- raportissa kerrotaan miten raportin pitää olla toistettava ja täsmällinen. Raportin pitää olla helpostiluettava ja selkeä rakenteeltaan.
- Lähteisiin pitää muistaa viitata.
- Pahoja mokia on esim. tekijänoikeuksien rikkominen.


# a) Murtaudu 010-staff-only. Ks. Karvinen 2024: Hack'n Fix

Aloitin laittamalla serverin päälle käyttäen teron ohjeita : https://terokarvinen.com/hack-n-fix/ 010 - Staff Only kohdasta.

Tehtävänä on löytää salasana käyttäen SQL-injektiota. Aluksi testasin normaalisti oman pin koodin 123:

![image](https://github.com/user-attachments/assets/6488181b-b5ba-4998-9f7b-f5d1a39438a3)

Huomasin että kenttään ei voi kirjoittaa kirjaimia joten lähdin etsimään miten se muutetaan koodissa.

Suljin serverin ja menin muokkaamaan index.html koodia. kuvassa näkyy polku index.html tiedostoon.
![image](https://github.com/user-attachments/assets/bc88e0d6-cd47-4308-a2b6-fa1e4b6ca36e)

Index.html tiedostosta löytyi kohta missä on input type="number". Jätin type kohdan tyhjäksi ja testasin toimiiko kirjaimet nyt sivustolla. 

![image](https://github.com/user-attachments/assets/1d7b4773-2819-45e7-8a1c-878bbd161f37)

Testi toimiiko kirjoitus: ![image](https://github.com/user-attachments/assets/1ba1dea4-9974-4f58-a346-88a6cdd39608)

index.html tiedoston tallentamisen ja serverin uudelleen käyynnistämisen jälkeen se toimii joten aloitetaan testailu.

    
    'OR1=1-- LIMIT 1,2; (muut limitit)
    123'OR 1=1-- LIMIT 1,2; (muut limitit)
    foo'OR 1=1 LIMIT 1,2; (muut limitit)
    
Ja muiden yritysten jälkeen löysin oikean:

    'OR 1=1 LIMIT 2,1; --
    
- OR 1=1 tekee ehdon joka on aina tosi
- LIMIT rajoittaa tulostaulun rivit 
- ; päättää lauseen 
- -- aloittaa kommentin

![image](https://github.com/user-attachments/assets/f6b69029-c8f2-464a-af51-4cc04588ef7b)

Kuvan yläpuolella näkyy salasana.


# b) Korjaa 010-staff-only haavoittuvuus lähdekoodista. Osoita testillä, että ratkaisusi toimii.

# c) Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. Tämä auttaa 020-your-eyes-only ratkaisemisessa.

Olin tehnyt kyseisen tehtävän Tunkeutumistestaus kurssilla. Tehtäväni löytyy B osiosta: 

https://github.com/SakuKarp/Tunkeutumistestaus/blob/main/h3%20Fuff%20faster.md


# d) Murtaudu 020-your-eyes-only. Ks. Karvinen 2024: Hack'n Fix

Aloitin tehtävän pistämällä servun päälle käyttäen ohjeita : https://terokarvinen.com/hack-n-fix/ 020 - Your Eyes Only

Servu päällä: 
![image](https://github.com/user-attachments/assets/6176cdcc-da5c-4797-b71c-3fa8b1ebfe90)

Aloitin tutkimalla mitä kaikkea sivustolla on löysin rekisteröinnin, kirjautumisen, personal data ja admin dashboardin. Tehtävän tarkoitus oli päästä järjestelmänvalvojan consoli osioon. Olen jo aiemmin tunkeutumistestauksessä käyttänyt Ffuffia ja aloitin Ffuffaamalla kohde sivustoa:

Aloitin asentamalla Ffuffin (käytin tähän ohjetta https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/):
Käytin myös valmista seclistiä by: DanielMiessler linkki lähteissä.

     wget https://github.com/ffuf/ffuf/releases/download/v2.0.0/ffuf_2.0.0_linux_amd64.tar.gz #asentaa
     tar -xf ffuf_2.0.0_linux_amd64.tar.gz #purkaa
     wget https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/common.txt #luo dictionaren

Sitten päästäänkin fuzzaamaan.

    ./ffuf -w common.txt -u http://127.0.0.1:8000/FUZZ # -W eli worlist ja -u eli kohde url

![image](https://github.com/user-attachments/assets/c14b5204-bdd9-43cb-a92a-4e92680d691f)

Sieltä löytyi admin-console eli meidän haluttu kohde sivusto.

Koitin mennä suoraan 127.0.0.1:8000/admin-console/ mutta se ei päästänyt minua admin-consoleen.

Testailin muutaman kerran että olinko missanut jotain mutta sitten kun menin  127.0.0.1:8000/admin-console/ se vei sivustolle jossa kirjaudutaan sisään. Rekisteröidyin sivuston kautta ja kirjauduin sisään. Kun olin kirjautunut sisään fuzzazin uudestaan ja se näytti uudestaan admin-consolen joten testasin vielä 127.0.0.1:8000/admin-console/ sivua ja sieltä löytyi:

![image](https://github.com/user-attachments/assets/9adac45b-5847-41eb-b760-2ece00694e02)

Eli jonkinlainen käyttäjänoikeuksiin liittyvä vika tässä on.



# e) Korjaa 020-your-eyes-only haavoittuvuus. Osoita testillä, että ratkaisusi toimii.

# g) & h)

Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data"
Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability allowing login bypass"

Teimme nämä jo tunnilla:

![image](https://github.com/user-attachments/assets/4485f7c8-4731-4e73-9098-74d1d35f1210)



# References

https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/

https://terokarvinen.com/application-hacking/#kertauspaketti

https://owasp.org/Top10/A01_2021-Broken_Access_Control/

https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/

https://portswigger.net/web-security/access-control

https://terokarvinen.com/2006/raportin-kirjoittaminen-4/

https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/common.txt

https://portswigger.net/web-security/all-labs
