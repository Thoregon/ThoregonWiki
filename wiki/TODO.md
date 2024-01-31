ToDo
====

## Thoregon

- Multiverse
  - gateway between universes
    - transform/recode entity as a reflection/image of the original 
    - strangeness for entities from another universe

### Apps

- enable views on app.root 
  - see GraphQL and supergraph (https://www.apollographql.com/blog/the-supergraph-a-new-way-to-think-about-graphql)

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

## Neuland DB

move completely to a shared worker, shield access from app js

matter interface 
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
