ToDo
====

## Aurora

- AuroraElement
    - provide each element basic information about
        - app
        - appelement
        - parent aurora element
        - parent view model
        - parent model

## Dorifer

- restart only app which is referenced
- split definition and runtime settings for apps

## SecretObject

- counter for number of properties (elements)
    - full hierarchy below, caution: cycle refs

- Queues with invitation

## Gun/Everblack

move completely to a shared worker, shield access from app js

matter (GUN) interface 
- access shared worker with messages
- not existing nodes
    - create all parents on write
    - enable listeners, connect once the node exists

same for heavymatter (IPFS)

## Process Contexts

separate contexts for each app (component)
not valid for 'import', check what you import!

- proxy 
    - context switch when calling other component
    - separate matter, heavymatter & eth nodes which are 'joined'
