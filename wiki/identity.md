Self Sovereign Identities
=========================

Kinds of identity
- siloed (centralized, account for each provider)
- federated (third-party like facebook, google, ...)
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
    did:thor:neuland:GXud1pe6IudFFUodE737wrW4JhNl5mZ8
     ^    ^       ^        ^
     |    |       |        |
  scheme method network identifier

Add thoregon resolver to https://dev.uniresolver.io/ -> https://github.com/decentralized-identity/universal-resolver/
Each driver in a (docker) container, enables independent implementations

see also 
- DID Universal Resolver Driver Configuration
- https://github.com/jolocom/jolo-did-method

duplicate self (friend harvey)
! Fellow
- Companion
- Orbiter
- Seconder

  
DID Auth
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
