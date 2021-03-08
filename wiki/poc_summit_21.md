Pioneers of change summit 2021
==============================

## BOM

Minimal spec for summit

- Comment Channel 
    - Widget
    - Ghost Id
        - Nickname in Browser
            - If missing in localstore, ask user with a popup
    - No Guest ID 

- Set POC21
    - create manually (or fake in overview app)
    - Each speaker is a channel
- Shadow channel
    - Suspicious

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

- Server
    - setup 2nd server
        - gun signaling: matter2.thoregon.io
        - thoregon component server
    - review cache settings
    - include heroku gun
   
