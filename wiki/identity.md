Self Sovereign Identities
=========================

Every SSI founds its personal cloud. It acts now in a network, not on a platform anymore.

see also [SSI](./ssi.md)

To access content in the universe, the SSI needs a claim for each content or content collection.
Content is not just a data structure anymore, it comes with behavior. 

Kinds of identity
- hosted
    - siloed (centralized, account for each provider)
    - federated (third-party like facebook, google, ...)
    - get credentials from backend
- guest identity
    - user defines credentials on local device
- ghost identity
- self-sovereign

Define Protocols for attests
- data (class) -> verifiyable claims
- behavior (like contract on blockchain)

Elements of a DID
- DID (for self-description)
- Set of public keys (for verification)
- Set of auth methods (for authentitication)
- Set of service endpoints (for interactions)
- timestamp (for audit history)
- signature (for integrity)

resolving DID to DID Document
    did:ipid:Qme5bsBSdt8FDbv7AJan5GDTwTWAzhdmn8vLcDfhrNgerc
    did:thoregon:neuland:GXud1pe6IudFFUodE737wrW4JhNl5mZ8
     ^    ^       ^        ^
     |    |       |        |
  scheme method network identifier

Add thoregon resolver to https://dev.uniresolver.io/ -> https://github.com/decentralized-identity/universal-resolver/
Each driver in a (docker) container, enables independent implementations

see also 
- DID Universal Resolver Driver Configuration
- https://github.com/jolocom/jolo-did-method

Service Agent - duplicate self (friend harvey)
! Fellow
- Companion
- Orbiter
- Seconder


- https://www.heise.de/hintergrund/Auslegungssache-37-Anonymitaet-Der-heilige-Gral-der-DSGVO-6024895.html

## Securtiy

best would be to use an SE (Secure Element) and 2FA (two factor authentication)

support strong anti-correlation to avoid tracking 

--> https://www.w3.org/TR/vc-data-model/#privacy-considerations

- use one-time bearer tokens

## Basic structure of an identity (SSI)

- me
    - credentials : certificates/attests/claims/menberships received
        - own credentials for all private galaxies
        - hierarchical for context/app
    - contacts    : all associated contacts, communities are memberships in claims
    - agents      : known service agents
    - devices     : connected devices to the SSI, see evolux.equipment
    - repositories: taped repositories the the SSI, each device can extend by tapping additional repos
    - aliases  (TDB)
    - device      : current device
    - properties, personal data    
    
    queries/views on credentials
    - friends     : committed contacts with credential 
    - grants      : certificates/attests/claims issued to others
    - galaxies    : persistent objects
    - apps        : can be device specific
    
### Structure of (persistent) data

Identity Instance
- me.instance
- me.instance.credentials
- me.

Root for an App:
- me.app.<appname> 
Instances:
- me.app.<appname>.<instance>   for apps supporting multiple instances
- me.app.<appname>.sole         if only one instance exists 
Credentials:
- me.app.<appname>.credentials
- me.app.<appname>.<instance>.credentials
Persistence:
- me.app.<appname>.root
- me.app.<appname>.<instance>.root
Setup (Settings):
- me.app.<appname>.setup
- me.app.<appname>.<instance>.setup
- me.device.app.<appname>.setup
- me.device.app.<appname>.<instance>.setup

fallback: first ask device setup, then instance setup, then app setup
design decision from app developer if device settings - or parts -  exists 

const approot = me.app.BG.POCS.root

Shotrcut for current app

universe.app (= approot)

Idle detection: https://web.dev/idle-detection/

### Thatsme private identity directory

the thatsme private directory stores hash entries of SSI's.
a hash for each verification of a user is built: salt + verification + password

--> see verifications

Recovery system with security questions like 'what was your first car' ...
for each verification a hash entry will be stored again: salt + verifcation + answer 

## Alias

a separated user profile with own settings (and keys).
- own properties

there is always a 'default' alias profile.

## Credentials (Claims)

- has metadata
- is a set of claims and proofs
- contract between exactly two particpants
- verifiable attributes from both sides
- one issuer
- extended claim 
    - allowed usage (DSGVO)

- hierarchy of proofs
    - issuer needs a certain credential to be authorized to issue the claims
    --> 'ewings' chain of proofs from authorities

When a SSI is created, or a thoregon identity with an external SSI,
it will get claims (invitations) for all 'global' collections e.g. the dorifer repository.

- user can add onw properties to (aside) the credential to add relevant information

Provide multiple views (virtual lists) on credential of the SSI
- contacts/friends/relations, also company
- access permissions/memberships
    - apps/widgets/components
- communication channels


### Issuing Credentials


- Credentials can only be 'decrypted' by the issuer and holder!

- the holder requests a credential from the issuer
    - holder creates a placeholder (address) in its 'credentials'
    - issuer writes the credential to the placeholder
    - credential tracks its state

## Identity Verifications

Will be expressed as credentials.

Access verifications: Verifies only access to a certain communication/access capabilities, not authenticity.

- phone
- email
- address

-> https://www.heise.de/hintergrund/Messenger-IDs-Warum-Messenger-nach-Ihrer-Telefonnummer-fragen-5066901.html?seite=all

Qualified verifications: Verifies the identity 

- person
    - qualified electronic signature (e.g. handysignatur)
    - identity service provider (e.g. banks, specialized services, authorities, government, ...)
    - EUid   https://www.heise.de/news/EUid-Online-Ausweise-kommen-EU-weit-Facebook-Co-muessen-sie-anerkennen-6061860.html 

Contracts
    
- sign documents to accept and participate
    - Thoregon Constitution
        - civil law, inheritance law
    - UNCITRAL (UN-Kaufrecht) https://de.wikipedia.org/wiki/UNCITRAL

## Request Queue

Every SSI, can also be a service, has a request queue to receive inquiries.
This can be request for invitations, e.g. to a channel.
The request must contain a queue (reference) where to send the answer.
A request can contain an invitation, the recipient decides whether to accept it. 


## DID Auth
- [What is DID-Auth and how does it work?](https://medium.com/@sethisaab/what-is-did-auth-and-how-does-it-works-1e4884383a53)

Sources & Links
- [A Guide To Self-Sovereign Identity: A Deep Dive by Ontology](https://medium.com/ontologynetwork/a-guide-to-self-sovereign-identity-a-deep-dive-by-ontology-3fe0f12c3be2)
- [SSI Meetup](https://www.youtube.com/channel/UCSqSTlKdbbCM1muGOhDa3Og/videos)
    - [Decentralized identifiers (DIDs) fundamentals and deep dive](https://www.youtube.com/watch?v=SHuRRaOBMz4)
    - [Decentralized Identifiers (DIDs) - The Fundamental Building Block of Self Sovereign Identity](https://www.youtube.com/watch?v=Jcfy9wd5bZI)
    - [Machine Identity - DIDs & Verifiable Credentials for trust & interoperability in IoT](https://www.youtube.com/watch?v=TJQ8Pt4lfuA)
    - [Self-Sovereign Identity: Ideology and Architecture with Christopher Allen](https://www.youtube.com/watch?v=MGYOWqCMLKg)
    - [Verifiable Credentials 101 for SSI with Tyler Ruff - Decentralized Digital Identity](https://www.youtube.com/watch?v=6O_iJnhIh5o)
    - [DID Resolution - Given a DID how do I retrieve its document? Markus Sabadello](https://youtube.com/watch?v=gf2g4O3yqCc)


## Identity & Authentication Systems

- https://www.heise.de/ratgeber/Webanwendungen-schuetzen-mit-Authelia-6202838.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser

## Risks

- https://www.heise.de/news/Digitaler-Fuehrerschein-hatte-keinen-Schutz-vor-Identitaetsdiebstahl-6204574.html
