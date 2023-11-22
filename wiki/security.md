Security
========

General Security requirements

## General

- [Sicher kommunizieren](https://www.heise.de/hintergrund/Sicher-kommunizieren-Wie-moderne-Kommunikationsverschluesselung-funktioniert-5023121.html)
- [7 Cryptography Concepts EVERY Developer Should Know](https://www.youtube.com/watch?v=NuyzuNBFWxQ)
- https://www.heise.de/hintergrund/Cyberangriffe-Gefahr-durch-Hackbacks-6007526.html?seite=all
- https://www.it-daily.net/shortnews/33692-welche-phishing-mails-verleiten-mitarbeiter-besonders-zum-klicken
- https://www.heise.de/news/c-t-3003-Die-gefaehrlichste-Malware-aller-Zeiten-8661099.html
- https://futurezone.at/digital-life/hacker-salzburg-nfc-tesla-smartphone-it-sicherheit-security-forschung/402095128
- 
## Tracking
https://www.heise.de/news/Browser-Fingerprinting-Installierte-Apps-als-Tracking-Komplizen-6071347.html
--> see https://schemeflood.com/
--> https://github.com/fingerprintjs/external-protocol-flooding
https://www.heise.de/hintergrund/Sichere-Kommunikation-Wie-Messenger-versuchen-Metadaten-zu-vermeiden-5995307.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser

## MFA 2FA

- https://www.heise.de/news/Gehackt-trotz-2-Faktor-Login-Wie-man-sich-dagegen-schuetzt-c-t-uplink-48-2c-8970929.html
- https://www.heise.de/ratgeber/IT-Security-Wie-Angreifer-die-Zwei-Faktor-Authentifizierung-aushebeln-8973846.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser
- https://www.heise.de/ratgeber/2FA-absichern-So-schuetzen-Sie-sich-vor-Angriffen-auf-den-zweiten-Faktor-8977133.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser
- https://www.heise.de/ratgeber/Wie-Telefonbetrueger-die-Zwei-Faktor-Autorisierung-aushebeln-9061644.html?seite=all
- https://www.heise.de/ratgeber/FAQ-Einloggen-mit-Passkeys-statt-Passwoertern-9067746.html

## Crypto

- https://www.heise.de/tests/Anbieter-Uebersicht-Kryptocoins-mit-Hardware-Wallets-sichern-8969077.html

### Browser Key & Crypto handling
https://www.heise.de/hintergrund/Sicher-kommunizieren-Wie-moderne-Kommunikationsverschluesselung-funktioniert-5023121.html
https://www.heise.de/developer/artikel/Was-man-ueber-Kryptografie-wissen-sollte-5001908.html

https://www.heise.de/news/Google-veroeffentlicht-erste-Quantencomputer-resistente-Fido2-Implementierung-9283078.html

! https://blog.engelke.com/2014/09/19/saving-cryptographic-keys-in-the-browser/
! https://pomcor.com/2017/06/02/keys-in-browser/
Webworker for memory separation: https://auth0.com/blog/secure-browser-storage-the-facts/#Secure-Browser-Storage-in-Auth0-SDKs
https://github.com/infotechinc/key-storage-in-browser
https://www.ibiblio.org/hhalpin/homepage/presentations/webcrypto/Overview5.html
https://beaglesecurity.com/blog/article/how-to-store-and-secure-sensitive-data-in-web-applications.html
https://pragmaticwebsecurity.com/files/cheatsheets/browsersecrets.pdf
https://www.heise.de/news/Datenschutz-Google-stellt-Tools-fuer-homomorphe-Verschluesselung-quelloffen-parat-6071618.html
https://www.heise.de/hintergrund/Was-Sie-ueber-Kryptografie-wissen-muessen-5074699.html

https://code.google.com/archive/p/crypto-js/

https://github.com/ipfs-shipyard/js-human-crypto-keys

Add interface to https://docs.metamask.io/guide/

### Post Quantum Cryptography

https://www.heise.de/hintergrund/Quantencomputing-Was-Post-Quanten-Verschluesselung-leisten-muss-6130476.html?seite=all
https://www.heise.de/hintergrund/Verschluesselungssysteme-Kryptoagil-gegen-hackende-Quantencomputer-6135175.html?seite=all
https://www.heise.de/news/US-Geheimdienst-NSA-nimmt-Stellung-zu-Post-Quanten-Kryptographie-6191190.html

- Use curve P-384 for ECDSA and ECDH and SHA-384 for hashes.
- Always use key length equal or larger than 3072 bit (= 384 byte)

This should be sufficient until post quantum cryptographic encryption methods are mature

### Indistinguishability Obfuscation & Homomorphic Encryption

https://en.m.wikipedia.org/wiki/Indistinguishability_obfuscation

### CryptoConditions

https://github.com/bigchaindb/js-crypto-conditions

### Crendentials

! check: may not work proper at 'localhost'
https://pierreprinetti.github.io/credential-api-password/

### Issues

https://stackoverflow.com/questions/31241713/webcrypto-safari-cannot-exportkey-and-promise-seems-to-never-resolve-fail/41055016#41055016

### Specifications & Systems

https://globalplatform.org/

FIDO, U2F

--> MFA Bombing: https://www.golem.de/news/lapsus-hackergruppe-umgeht-2fa-mit-einfachem-trick-2203-164236.html

## Service


## Blockchain

Ethereum    https://consensys.github.io/smart-contract-best-practices/known_attacks/

## Products

- [Velid](https://www.heise.de/news/Hackerkollektiv-cDc-kuendigt-quelloffenes-Verschluesselungsframework-an-9240518.html)
  - https://gitlab.com/veilid/veilid
  - https://www.heise.de/news/Hackerkollektiv-Cult-of-the-Dead-Cow-veroeffentlicht-Privacy-Framework-9304796.html
- [eye Security](https://www.eye.security/de/)
  - https://www.computerwoche.de/a/ex-geheimdienst-experten-bauen-security-loesung-fuer-den-mittelstand,3615466

https://www.schlager-news.at/markt-kommerzielle-verschlusselungssoftware-kapazitaten/

@see also
https://www.heise.de/hintergrund/Unabhaengig-aber-sicher-Serverless-Security-6326609.html
