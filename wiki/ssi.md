Self Sovereign Identities
=========================

see also [identity](./identity.md)

## Types of SSI's

### Individual
This is the typical SSI for a Person and will be issued on the registration website from Thatsme.plus
It will hold attributes of the owner as well as all the claims.

### Individual - hosted
This is a hosted identity and will be issued by a service.agent if the user does not have an SSI. 
This ID is not sovereign as it belongs to the service.agent ( service provider ). 
the SSIs will be stored e.g. in the database of wordpress.

### Individual - guest
created by a service.agent and will exist within the Browser only  ( as Key pair ).
    - anonymous
    - personalized e.g. for example if the user wants to reply to a comment.
    - TODO: prevent that guest IDs can takeover the control of another guest as they share the same key pair. ( Hint: generate a key-pair in the browser for signature ) 

### Ghost Identity
A Pseudo SSI will always exist in the system internal and is there to simplify the protocol. It is only used if no other ID is signed on.

### Organization
owned by individuals. It will allow describing and organization. Act on behalf of the owners.

[Guidance for decentralized identity and verifiable claims (2020)](https://finema.co/2020-guidance-for-decentralized-identity-and-verifiable-claims/)

## User Settings

- i18n
    - dateformat, numberformat
    - language
-a11y
    - reading aids
- ui settings
    - theme ...

## User Stories

- New SSI

- Connect Device

## Recovery

all options can be used together 

1 PBKDF2 encrypt ServiceAgent and SSI address 
    a generate QR code (later: generate 5 QR codes, need min 3 to recover)
    b vault file to store on an USB stick or other portable storage
    
2 Thatsme recovery service with URL 

3 SSI Wallet
    a Native App
    b Browser Extension (see MetaMask)

4 2FA Hardware Tokens


