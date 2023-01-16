new gun
=======

Name: neuland

neuland is a persistent CRDT (conflict free replicated data types) database.

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

## performance measuring

instrumentation of methods for performance measuring 

--> https://nodejs.org/api/perf_hooks.html#performance-measurement-apis

## denial, deadlock & endless loop detection

- limit size of sync messages
- limit size of indexeddb entries (later!)
- watchdogs 
- recursion counters


# links & resources

- 

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
