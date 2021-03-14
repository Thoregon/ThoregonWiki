Pioneers of change summit 2021
==============================

## BOM

Minimal spec for summit

- Query
    x existing items
    - modifications

- CollaborationComments
    x channelquery
        - modificaitons
    - reactions query
    - replies query
    - reaction action
        - add
        - remove
    - reply action
    - AuroraComment
        - queries for reactions and replies
    
    - admin drop message
    - admin release message


- Cache control
    x simple
    - use 'no-cache' with 'Last-Modified' or 'ETag'
        -> https://web.dev/http-cache/#:~:text=ETag%20.,Last%2DModified%20.
        -> https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag
        -> https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Last-Modified
        
- Widget 
    - height

- Comment Channel 
    - Widget
    - Ghost Id
        x joinAsGhost()
        x firewall
            x vulnerability
            x is spam
            - save IP für blocking  -> not really feasable in browser
        x nickname in Browser
            x If missing in localstore, ask user with a popup
    x No Guest ID 
    x SecretCollection (SecretObject with addSecretItem)
        - partitions
            - fn()     -> partitionid
            - fn(item) -> partitionid
        x items as SecretObjects
    x CollaborationChannel as subclass of SecretObject
- Shadow channel
    - Suspicious

Later

- Server
    - setup 2nd server
        - gun signaling: matter2.thoregon.io
        - thoregon component server
    - review cache settings
    - include heroku gun

- Set POC21
    - create manually (or fake in overview app)
    - Each speaker is a channel

- Service API's
    - create/update/delete set -> currently only one POC21
        - !currently only one set is allowed, 
            - just activate/deactivate channel
            - add/remove from single set
    - create channel
        - in set
        - with ghost
        - grant write to ghost
    - update/deactivate channel
        - update reactivates channel
    
- Overview App
    - Set with all channels in drawer
    - Shadow channel
    - Login for admin
    - later for public
   
