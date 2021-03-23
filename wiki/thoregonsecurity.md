Security in Thoregon
====================

## Client

Browser Javascript is hostile to cryptography. The problem with running crypto code in Javascript is that
practically any function that the crypto depends on could be overridden silently by any piece of content 
used to build the hosting page!

A reference to the original 'crypto' will be established right at the beginning. 
Workers are not affected by exchanging the 'crypto' library. 

## Thoregon Crypto API

- on startup keep a reference to the original crypto API, it can be exchanged later by malicious code

- don't enclose 

- proxies with communication
    - postMessage
    - websocket
    - queue (SecretObject)

## Identites

An identiity can own multiple key pairs
All resources the identity can access are reachable
via a subnode 

### Ghost and Guest identites

- ghost identities can be published to enable everybody access to resources
    - can only read
- guest identities are more personalized, created for each participant
    - nevertheless anonymous
    - can write, chooses nickname and optionally an avatar image
    
## Permissions 

- Resource oriented
    - every identity has its allowed resources directly attached
    - for every resource, a new keypair is used
- ask for invitation
    - pass a node where permission can be stored

## Handshake

Request
- the one - e.g. a service - provides a QR code (or link or NFC token)
- or the one publishes a Q to receive invitation request
    - QR/Link includes a public key
    - creates a (temporarily) Q wating for invitation request  
- the other asks for invitation
    - creates a new keypair
    - creates a root node within its identity inviting the pubkey received 
    - create a invitation request with the new root node
- the one creates 
    - the attest
    - the entities
    - adds it the the others root node specified in the request
- both happy!

Invitation
- the other has published a node with a Q to receive invitation offers
    - there are also private directories e.g. for organisations
- the one create a invitation offer
    - contains the Q address for invitation requests
    - pushes it to the others Q
- the other asks for invitation     (same as above)
    - creates a new keypair
    - creates a root node within its identity inviting the pubkey received 
    - create a invitation request with the new root node
- the one creates 
    - the attest
    - the entities
    - adds it the the others root node specified in the request
- both happy!

todo: define firewall rules to reduce spam  

! enable sending requests and invitations by other secure messengers like signal
  

## Sandboxes

Since loading code from IPFS instead of a server disables all browser same origin security features
we need to recover security to be able to run several apps within the same origin. 

- Each Component - can be an App - lives in its separate context (sandbox) -> jailed
- Basic thoregon workers, having their own environment 

- ! secure access to localStore etc. because of the same origin !
    - the device key(s) are stored securely in indexDB
    - avoid others to delete these entries
    - exchange several API from window -> proxies with message passing 
        - localStore
        - indexDB
        - ...

- Specialized Sandboxes 
    - https://github.com/ysmood/nisp

- documents
    - https://www.html5rocks.com/en/tutorials/security/sandboxed-iframes/
    - https://blog.logrocket.com/a-complete-guide-to-threads-in-node-js-4fa3898fe74f/
    
## Library of Babel

- https://libraryofbabel.info/theory.html
    - Explanation: https://gist.github.com/bwhitman/3185350
- https://github.com/cakenggt/Library-Of-Pybel      JS implementaiton
    - Demo https://cakenggt.github.io/Library-Of-Pybel/
- https://github.com/aneopsy/LibraryOfBabel         Python implementation 
