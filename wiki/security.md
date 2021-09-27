Security
========

General Security requirements

## General

- [Sicher kommunizieren](https://www.heise.de/hintergrund/Sicher-kommunizieren-Wie-moderne-Kommunikationsverschluesselung-funktioniert-5023121.html)
- https://www.heise.de/hintergrund/Cyberangriffe-Gefahr-durch-Hackbacks-6007526.html?seite=all

## Tracking
https://www.heise.de/news/Browser-Fingerprinting-Installierte-Apps-als-Tracking-Komplizen-6071347.html
--> see https://schemeflood.com/
--> https://github.com/fingerprintjs/external-protocol-flooding

## Crypto

### Browser Key & Crypto handling
! https://blog.engelke.com/2014/09/19/saving-cryptographic-keys-in-the-browser/
! https://pomcor.com/2017/06/02/keys-in-browser/
Webworker for memory separation: https://auth0.com/blog/secure-browser-storage-the-facts/#Secure-Browser-Storage-in-Auth0-SDKs
https://github.com/infotechinc/key-storage-in-browser
https://www.ibiblio.org/hhalpin/homepage/presentations/webcrypto/Overview5.html
https://beaglesecurity.com/blog/article/how-to-store-and-secure-sensitive-data-in-web-applications.html
https://pragmaticwebsecurity.com/files/cheatsheets/browsersecrets.pdf

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

## Service


## Blockchain

Ethereum    https://consensys.github.io/smart-contract-best-practices/known_attacks/
