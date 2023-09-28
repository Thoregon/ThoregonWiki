Neuland
=======

synonym for 'new gun'

## TL;DR

- neuland is a persistent CRDT (conflict free replicated data types) database
- offline first, in memory
- full encrypted
- verifiable credentials based 
- neuland does not implement consenus like in a blockchain, it implements collaboration
  - sync is done by utilizing a state, which basically is a point on a timeline
  - last write wins, based on the state. modifications in the future will apply only in the future
  - other CRDT's may implement other merge strategies 

consensus means one of the changes will be picked by the consensus protocol
collaboration means the changes will be merged to get convergence

## Automerge Links

[Automerge](https://automerge.org/docs/tsapi/index/)
[Slack](https://app.slack.com/client/T61MVPYP5/browse-channels)

Examples
- https://snyk.io/advisor/npm-package/automerge/example


## entities

- entities keep track of their sync state
  - the automerge syncstate is stored along with the entity
    - keep syncstate of each connectd node in memory 
    - need sync state for each peer?
  - 'unsynchronous' until local changes are synced with other peers
    - can be displayed to the user
- security contexts: an entity can be comprised of multiple automerge docs
  - a context 
  - design entities with multiple permisson contexts
    - properties within a context needs a permission 
    - e.g. Product
      - context "pub", properties: name, description, price, ...
      - context "vendor", properties: purchase price, supplier, supplierid ... 
      - context "supplier", properties: vendorid, supplierid, ...
  - collections can also be comprised of multiple contexts
    - each context maintains its own collection
    - affiliation of item 
      - by select (filter function) during add
      - intentional by definition, add to a specific context
    - permissions for each context can be set
    - there is no more 'overall' sequence, the collection must be sorted
  
- store
  - async
  - after x changes
  - after n milliseconds
  - on exit -> [visibilitychange event](https://developer.mozilla.org/en-US/docs/Web/API/Document/visibilitychange_event)

## instances/peers

- each SSI has its own instance on each device/agent
- verifiable credentials for shared entities
- 'public' credentials for some collections will be provided 
  - directories like communication terminals (to a person or an organisation)
  - repositories for components
  - services for system interaction
- arbitrary collections with credentials can be added to the neuland instance

tech:
- node peer
  - introduce to relays with 'direct connect'
    - provide credentials: id, spub (pub key for signature), epub (pub key to generate a shared secret)
  - provide websocket for other peers
  - maintain MAX_PEERS (node) connections
    - watch the significance of the connected peers and disconnect some peers
    - keep peers sharing same 'soul'(s) connected  
    - disconnect spamming or leaching peers
- browser peer
  - introduce to relay with 'need relay'
    - provide credentials: id, spub (pub key for signature), epub (pub key to generate a shared secret)
  - maintain MAX_PEERS (browser) connections
    - watch the significance of the connected peers and disconnect some peers
    - disconnect spamming or leaching peers
    - disconnect inactive peers (after a timeout)
  - since they work with the same indexeddb
    - store an i (increment) with the data blob
    - before update read it again and compare it with the read i
      - if it is later, sync (merge) with automerge both local objects
    - store data blob with ++i 
- relay/signaling peer
  - if target peer is 'direct connect' respond 'redirect'
  - if target peer is 'need relay' pipe them together
  - when switching to WebRTC, the relay function changes to signaling
  - maintain a (part/shard) of the whole dataset
- heartbeat to check if known peers are alive

- peer discovery
  - a peer has in its config at least one known peer
  - the peer introduces itself to the known peers and maintains a socket connection
  - a peer may be a relay
    - a relay peer answers its know peers if they can be reached directly (node peer)
    - another peer can ask the relay for its known peers
    - relays handover peers with redirect, only one relay between two browser peers
    - ? if a new peer introduces itself to the relay, the relay notifies all other of its known peers about the new peer if it can be reached directly
- if a peer connects, the sync negotiation is done
  - ?

- peers
  - NetworkAdapter
    - PeerJS
    - Browser communication 
      - peers from the same origin
        - use postMessage and BroadcastChannel (https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API)
````js
// on all windows/tabs/iframes in he same context (same origin) the broadcast channel can be used
let bc = new BroadcastChannel("test_channel");
bc.onmessage = console.log
bc.postMessage("This is a test message.");
````
  - each peer knows some (!) others
  - a peer queries an entity with its 'soul'
    - if found locally, use it
      - ThoregonDecorator.from() does just a local lookup
    - if not in local db
      - if the ressource should exist because we have a resource id create it
        - caution: deleted references must be recognized! just mark them as deleted
      - create the resource and asks known peers to sync -> peer creates an entity
    - only the first sync request will be repeated from the receiving peers
      - request contains { discover: true }
      - the request is signed, if it needs a permission, its also encrypted
        - the receiving peer can only handle the request if it has the right credential
        - broadcasts with reqid, signatur, soul (encrypt) changes encrypted with credential sync ke
        - broadcast contains an encrypted challenge
     - peer has an entity for the 'soul'
      - when the connection was not established already, connect to the requester
      - otherwise the receiving peer asks all its known nodes, except the requesting node
        - it does not wait for an answer, the peer which can decrypt directly connects to the requester
      - request has a unique id and a repeated count to avoid loops
        - when a peer get the same request it stops spreading
        - each peer dispatching the request increments the repeated count
        - when the repeated count > MAX_QUERY_REPEATS the dispatching stops 
      - speed this up by using a DHT like routing
        - for each credential?
    - NO: this is not reliable -> requests have a timeout of 150ms, then requesting peer then assumes entity does not exist 
  - a peer creates an entity
    - peer sends to its know peers 'create' entity
    - peers which waiting for this 'soul' connects
    - peers which owns the credential replicates it to its local db 
  - a peer modifies an entity
    - peer sends to its know peers 'change' entity
    - peers which does not have the 'soul' in the local db discard (ignores) it
- only broadcasts are extra secured with encryption and signature
  - direct p2p communication is secured by the transport layer
  - only peers which are in possession of the correct verifiable credential can decrypt and process the request

- Sync Handler
  - commands
  - monitor 'loaded' entities
    - track last access (localtime)
    - after MAX_INACTIVE reomve from memory
    - disconnect peers when possible: last shared entity with this peer 
    - keep track of peer/doc tuples when conn is closed
      - if the connection is needed again try to reopen with same peerid
      - if this fails, try find with broadcast

- broadcast request
  - what
    - entity
    - command
      - get
      - create
      - change
    - mq
    - command
      - queue
      - topic
  - credential type
    - public
    - owner
    - verifiable credential
  - soul

- entities
  - wrapped with a thoregon decorator
    - decorator handles the automerge object
  - each automerge entity comes with metadata in the property '_'
  - use metaclass if it exists
    - embedded: store object(s) in property as part of the parent entity
      - attribute descriptor 'embedded' = false and property content is an Object embed it anyways 
      - no attribute descriptor:
        - property content is an Object treat it as 'embedded'
        - property content is a ThoregonEntity treat is as 'referenced' (not embedded) 
  - consider private properties 
    - starting or ending with '$' of '_'
    - defined as private in the attribute descriptor
  - assume defaults for missing information in the metaclass, or if the metaclass is missing
    - there is no attribute descriptor

- DHT (Distributed Hash Tables)
  - node impls
    - https://github.com/bushidocodes/chord-grpc
    - https://github.com/khaosdoctor/node-dht
  - https://www.tutorialspoint.com/distributed-hash-tables-dhts
  - https://en.wikipedia.org/wiki/Distributed_hash_table
  - https://en.wikipedia.org/wiki/Chord_(peer-to-peer)
  - https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf
  - https://www.youtube.com/watch?v=rhch2dZFcdM

- libp2p2
  - https://libp2p.io/implementations/
  - https://github.com/libp2p/js-libp2p-delegated-peer-routing
  - https://ldej.nl/post/building-an-echo-application-with-libp2p/

- noiseprotocol
  - https://noiseprotocol.org/


### Safety & Security

- Trustless vs. Zero Trust
  - The main difference seen now being Zero Trust is focused on device integrity, checking every time and at every level, as well as definitive statements whenever possible while Trustless would focus on mathematical proofs underlying the security and safety points of the system.
  - https://www.nananke.com/single-post/2018/08/07/zero-trust-vs-trustless-systems
  - [Trustless](https://www.trustlesscomputing.org/paradigms)
  - [Zero Trust](https://www.paloaltonetworks.com/cyberpedia/what-is-a-zero-trust-architecture)

- Encryption & Signatures

- Verifiable Claims


### instance meta data

- an instance is dedicated to a verifiable credential (from an SSI)


## local data

there are none synchronized entities to store local data 
for the device.

e.g. current UI settings for restart

## message queue

- to support service agents  
- address a service, not a location!  
- add only CRDT Set

## request of a SSI root

the request must have a signature, otherwise the peer will not answer the request

## state (time) sync between all peers


## request for device coupling

the request must have a signature, otherwise the peer will not answer the request

## optimize sync

1) get an entity

- when do I have to query for sync
  - everytime it is first fetched from an app?

2) sync after restart

- send the last 'state' to the other peers
- other peers (which are permitted) send (continously) the state (changes)

## monitoring

- syncs 
  - low quality or slow networks
  - retries
  - offline first

## performance measuring

instrumentation of methods for performance measuring 

--> https://nodejs.org/api/perf_hooks.html#performance-measurement-apis

## denial, deadlock & endless loop detection

- limit size of sync messages
- limit size of indexeddb entries (later!)
- watchdogs 
- recursion counters


## local DB in service worker

- target: run in service worker (needs type: module)
- communication
  - [SharedArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer)
    - see also [PartyTown](https://partytown.builder.io/)

# links & resources

## CRDT 

- https://www.heise.de/hintergrund/Agiles-Arbeiten-bei-der-Allianz-3944421.html?seite=all
- https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type
- https://crdt.tech/
- https://redis.com/blog/diving-into-crdts/

- https://martin.kleppmann.com/
- https://www.youtube.com/watch?v=B5NULPSiOGw   !
  - https://www.youtube.com/watch?v=x7drE24geUw !
  - https://www.youtube.com/watch?v=yCcWpzY8dIA

Projects
- https://github.com/automerge/automerge
  - https://github.com/automerge/automerge-connection
  - https://github.com/automerge/sync-server
  - Slack: https://app.slack.com/client/T61MVPYP5/C61RJCM9S
  - WASM
    - https://developer.mozilla.org/en-US/docs/WebAssembly/Using_the_JavaScript_API
    - 
- automerge used
  - https://github.com/pvh/automerge-repo
  - https://github.com/cmars/authmerge
    - https://www.openpolicyagent.org/
  - https://github.com/sammccord/perge
- demo apps 
  - https://github.com/pvh/automerge-demo/tree/main/src
  - https://github.com/okdistribute/automerge-chat-demo

- https://github.com/local-first-web

- https://github.com/automerge/hypermerge
- https://github.com/automerge/mpl
- https://github.com/automerge/trellis
- https://dat-ecosystem.org/ (prev: https://datproject.org/)
  - https://github.com/dat-ecosystem
  - https://docs.holepunch.to/   (hypercore)
  - https://github.com/RangerMauve/hyper-sdk
  - https://awesome.datproject.org/webrtc-swarm
- https://localforage.github.io/localForage/#settings-api-setdriver

see also: https://dataintensive.net/

- https://www.youtube.com/watch?app=desktop&v=M8-WFTjZoA0
- https://www.youtube.com/watch?app=desktop&v=ZLjl_55um4I
- https://www.youtube.com/watch?app=desktop&v=CD_0u03EdcA

# later

## conflict resolution

- don't use state to merge
- automerge strings
- like git (pull/merge)
- make suggestions to others
- one user selects correct data

## better p2p

currently the relays (relay & routing peers) are in a config file.  
allow peer network detection.

- https://github.com/libp2p/js-libp2p
- https://peerjs.com/

## client/worker communication

communication between client and (service) woker is currently made with 'postMessage'.  
for performance rebuild communication with SharedArrayBuffer/Atomics

## routing & relaying

- anonymous
  - like TOR or JAP
  - other possibilities?

- get rid of addresses (pointer to entity)
  - use non interactive zero knowledge proofs instead

## data partitions

if the data blob get to large, partition it 

## single db entries for entities

introduce a storage engine which stores each entity in a single record
- indexeddb 
- webdb
- filesystem

