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




# b) Korjaa 010-staff-only haavoittuvuus lähdekoodista. Osoita testillä, että ratkaisusi toimii.

# c) Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. Tämä auttaa 020-your-eyes-only ratkaisemisessa.

# d) Murtaudu 020-your-eyes-only. Ks. Karvinen 2024: Hack'n Fix

# e) Korjaa 020-your-eyes-only haavoittuvuus. Osoita testillä, että ratkaisusi toimii.

g) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data".

h) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability allowing login bypass"

# References
https://terokarvinen.com/application-hacking/#kertauspaketti
https://owasp.org/Top10/A01_2021-Broken_Access_Control/
https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
https://portswigger.net/web-security/access-control
https://terokarvinen.com/2006/raportin-kirjoittaminen-4/
