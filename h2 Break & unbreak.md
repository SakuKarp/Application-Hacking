x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

OWASP: OWASP Top 10: A01 Broken Access Control
- Haavoittuvuudet jotka sisältävät luvattoman pääsyn, URL manipulointi, tilitietojen väärinkäyttö ja eri API-kutsujen puutteelliset suojat.
- Haavoittuvuuden ennalta ehkäisy. Pääsynhallintaa kannattaa käyttää vain palvelinpuolella, estää pääsy oletuksena, käyttää yhtenäöiosiä pääsynhallintamekanismeja, seurata epäonnistuneet yritykset ja varmistaa tunnisteiden turvallisuus.

Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf
- Avoimen lähdekoodintyökalu jonka on tehnyt joohoi.
- Brute force etsintään käytettävä
- Tehokas fuzzaus työkalu

PortSwigger: Access control vulnerabilities and privilege escalation
-Käyttöoikeuksien muuttaminen (esim. roolit)
-Pääsynhallinan estäminen

## Karvinen 2006: Raportin kirjoittaminen

- raportissa kerrotaan miten raportin pitää olla toistettava ja täsmällinen. Raportin pitää olla helpostiluettava ja selkeä rakenteeltaan.
- Lähteisiin pitää muistaa viitata.
- Pahoja mokia on esim. tekijänoikeuksien rikkominen.


# a) Murtaudu 010-staff-only. Ks. Karvinen 2024: Hack'n Fix

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
