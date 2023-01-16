new gun
=======

Name: neuland

## TL;DR

neuland is a persistent CRDT (conflict free replicated data types) database.  
sync is done by utilizing a state, which basically is a point on a timeline.  

## instances

- each SSI has its own instance on each device/agent
- verifiable credentials for shared entities

## local data

there are none synchronized entities to store local data 
for the device.

e.g. current UI settings for restart

## message queue

to support service agents  
address a service, not a location!  

## request of a SSI root

the request must have a signature, otherwise the peer will not answer the request

## request for device coupling

the request must have a signature, otherwise the peer will not answer the request

## optimize sync

1) get an entity

- when do I have to query for sync
  - everytime it is first fetched from an app?

2) sync after restart

- send the last 'state' to the other peers
- other peers (which are permitted) send (continously) the state (changes)

## performance measuring

instrumentation of methods for performance measuring 

--> https://nodejs.org/api/perf_hooks.html#performance-measurement-apis

## denial, deadlock & endless loop detection

- limit size of sync messages
- limit size of indexeddb entries (later!)
- watchdogs 
- recursion counters


# links & resources

## CRDT 

- https://www.heise.de/hintergrund/Agiles-Arbeiten-bei-der-Allianz-3944421.html?seite=all
- https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type
- https://crdt.tech/
- https://redis.com/blog/diving-into-crdts/

- https://www.youtube.com/watch?v=B5NULPSiOGw
- https://www.youtube.com/watch?app=desktop&v=M8-WFTjZoA0
- https://www.youtube.com/watch?app=desktop&v=ZLjl_55um4I
- https://www.youtube.com/watch?app=desktop&v=CD_0u03EdcA

# later

## local DB in a worker

- target: run in service worker (needs type: module)
- communication 
  - [SharedArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer) 
    - see also [PartyTown](https://partytown.builder.io/)


## routing of requests

- anonymous
  - like TOR or JAP
  - other possibilities?

- get rid of addresses (pointer to entity)
  - use async zero knowlede proofs instead

## data partitions

## single db entries for entities
