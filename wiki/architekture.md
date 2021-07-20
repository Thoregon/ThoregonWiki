Thore͛gon Architecture
=====================

## Environments

### Node 

### Browser

- Service Worker
    - https://serviceworke.rs/

- PWA
    - https://www.heise.de/ratgeber/Progressive-Web-Apps-Write-once-run-anywhere-4839505.html
- https://www.heise.de/news/Apple-oeffnet-iPhone-und-iPad-fuer-Browser-Erweiterungen-6068084.html

## Interfaces

easy integrate legacy systems 
- run container with universe (service agent)
- activate REST API

[OpenAPIS](https://www.openapis.org/)
[AsyncAPI](https://www.asyncapi.com/)

[ERC165](https://medium.com/coinmonks/ethereum-standard-erc165-explained-63b54ca0d273)

## Elements

### Component

- provides a specific functionality
- without UI
    - may (should) publish an API 
    - implements 'business' features of an app
- with UI
    - needs a frame (app, start screen)
        - has no 'app' blueprint
        - resizes into the target (where it is referenced)
    - apps can publish widgets

### App

- always has a UI
    - provides a main layout (blueprint)
- can be embedded in another app
- should use business components
- apps can publish widgets

### Widget

- published in am app or component
- to be integrated in an existing website
    - not to be used inside a thoregon app
    - definition of   
        - custom tag name
        - which component/app (in dorifer, allow other repos th be referenced)
        - rules & permissions, e.g. website descriptor
- provides the referenced component/app
- allows styles 
- permissions
    - bind to domain (URL)
    - SSI

## Repository

### Descriptors

#### Schemas

- component
- entity
- view

- actions
    - boundaries
        - must be defined (programmed or defined)
        - some fields must not be empty
        - some fields must be valid
    - params
        - link ui elems with params

### Directory Layout

- <component-name>
    - lib
        - commands
        - i18n
        - queries
    - ui (if needed implement own aurora elements)
        - i18n
        - assets
            - images
            - audio
            - video
            - ...
        - views
            - blueprint (main layout for the app)
    - test ... test data
    - index.mjs
    - component.mjs
    - README.md
    - LICENCE

## Entities

- can always be stored in an invalid state

## Commands & Actions

- action  -> UX
- command -> service (backend), typically creates, modifies or removes one or more persistent entities
- resource oriented
    - owner e.g. when create -> current SSI

- is available: is the action/command available for the current identity
- is executable: is the available action/command executable now

firewall rules applies also to is available

## Errorhandling

- avoid that the user can make mistakes
    - e.g. with selectable options, switches ...
- but explain why these options are available
    - show also options disabled and explain why they are disabled

- wenn disabled, anzeigen warum
- wenn disabled oder fehler, hinweise wie zu beheben
e.g. kredit nicht bewilligt weil einkommen zu niedrig, wenn einkommen > X wird kredit bewilligt

## Automations

## Firewalls

- signatures
    - multi sigs -> TBD
- FW rules
    - allow/reject modifications
- proliferation
    - only valid entities will be replicated to the local DB 
    

## Networks

- multiple networks (also mesh)
    - MESH WLAN
    - [Thread](https://www.heise.de/hintergrund/Smart-Home-Das-Funkprotokoll-Thread-im-ersten-Praxistest-6049222.html)


## Exchange of secret information
e.g. between SSI and Service Agent (SA)

- there is no direct communication 
- request queue (soul)
    - DH secret between both paricipants
- write to Q, encrypted and signed
- read from Q, verify and decrypt
- remove Q entry

## Information Roots

### Universe

the root for all information

### Dorifer

root for all repositories

shortcut for universe.dorifer

### Me

shortcut for universe.identity

## Public direcories

since the network DB has no root and cannot be searched, every
public information must be published via trustable public directories.

another possibility is to publish special datastructures in IPFS, which is
hierarchical and can be searched.
