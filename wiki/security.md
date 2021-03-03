Security
========

## Client

Browser Javascript is hostile to cryptography. The problem with running crypto code in Javascript is that
practically any function that the crypto depends on could be overridden silently by any piece of content 
used to build the hosting page!

A reference to the original 'crypto' will be established right at the beginning. 
Workers are not affected by exchanging the 'crypto' library. 

### Browser Key & Crypto handling
! https://blog.engelke.com/2014/09/19/saving-cryptographic-keys-in-the-browser/
! https://pomcor.com/2017/06/02/keys-in-browser/
Webworker for memory separation: https://auth0.com/blog/secure-browser-storage-the-facts/#Secure-Browser-Storage-in-Auth0-SDKs
https://github.com/infotechinc/key-storage-in-browser
https://www.ibiblio.org/hhalpin/homepage/presentations/webcrypto/Overview5.html
https://beaglesecurity.com/blog/article/how-to-store-and-secure-sensitive-data-in-web-applications.html
https://pragmaticwebsecurity.com/files/cheatsheets/browsersecrets.pdf

### CryptoConditions

https://github.com/bigchaindb/js-crypto-conditions

### Crendentials

https://pierreprinetti.github.io/credential-api-password/

### Issues

https://stackoverflow.com/questions/31241713/webcrypto-safari-cannot-exportkey-and-promise-seems-to-never-resolve-fail/41055016#41055016

### Specifications & Systems

https://globalplatform.org/

FIDO, U2F

## Service


## Blockchain

https://consensys.github.io/smart-contract-best-practices/known_attacks/
