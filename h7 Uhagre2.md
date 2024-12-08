# h7 Uhagre2 

## x) Lue/katso/kuuntele ja tiivistä.

€ Schneier 2015: Applied Cryptography, 20ed: Chapter 1: Foundations:

1.1 Terminology ("Historical Terms" loppuun)

- Kryptografiassa käytetään monia erityistermejä ja käsitteitä
- Koodit ja salakirjoitukset
- Salakirjoitukset
- Authentication, Integrity, Nonrepudiation
- Plaintext, Ciphertext
- Encryption, Decryption

1.4 Simple XOR

- Salaustekniikka
- XOR on operaattiori
- XOR perusteet
- Yksinkertainen XOR-algoritmi on Vigenèren polyalfabeettinen salakirjoitus
- Yksinkertaisen XOR-algoritmin murtaminen

1.7 Large Numbers

- Tekstissä kerrotaa siitä, että kirjassa käytetään useita suuria lukuja kryptografian eri asioiden kuvaamiseen.

Karvinen 2024: Python Basics for Hackers

- Ohjeet miten päästä alkuun pythonilla.


## a) 1. Convert hex to base64.

Aloitin tehtävän tekemisen ja huomasin, että tehtävä oli liian vaikea. Siksi lähdin tutkimaan Teron antamia vinkkejä, jotka auttoivat pääsemään alkuun tehtävässä. Huomasin, että siinä voidaan käyttää binascii -kirjastoa ja base64-kirjastoa. binascii-kirjastossa on funktio unhexlify, joka auttaa dekoodaamaan heksadesimaalimuotoisen merkkijonon binäärimuotoon. base64-kirjasto mahdollistaa binääridatan koodaamisen base64-muotoon. Jouduin käyttämään apuna Copilotia, joka auttoi joissakin kohdissa koodin luomisessa.

koodi:

![image](https://github.com/user-attachments/assets/7e8a25d0-dd18-40af-8d5d-854719c9b3ec)

muunnettu tuloste:
![image](https://github.com/user-attachments/assets/e4a04780-c33b-4768-840a-0beb23c83a79)

## b) 2. Fixed XOR.



## c) 3. Single-byte XOR cipher.

## d) 4. Detect single-character XOR.

# References

https://terokarvinen.com/application-hacking/

https://terokarvinen.com/python-for-hackers/

https://docs.python.org/3/library/binascii.html

https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01-sec005 (1.1, 1.4, 1.7)


