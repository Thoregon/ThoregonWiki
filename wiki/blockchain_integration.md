Blockchain Integration
======================

## CRDT - Blockchain w/o Blockchain

- CRDT instead of bockchain
- Firewalls for distributed DB must ensure fulfill/reject of transaction
    - signatures
    - contracts
- Transaction validity
    - 3rd party verifiers, tx fees, must be online
    - self contained tx, may be free of fees, can be peer to peer
    - -> see [Proof of Propagation & scalable blockchains w/ GunDB!](https://www.youtube.com/watch?v=EHZyaupYjYo&feature=emb_imp_woyt)

        ! wenn kein Konsens über die Gültigkeit einer SSI durchgeführt wird,
          wie können wir diese feststellen
          -> Gültigkeit von SSI Einträgen welche ich von einem andern Peer bekomme! 
             Third Party Singature (ThatsMe)? -> Yes but enable other identity providers also
             This is subject to DDNS! Must be a homomorphic encryption procedure running locally
          -> root block chain only for special root entities?
          -> another block chain for special root entities?
          -> another CRDT consent? 
            - root entry with a signature
            - publish the pubkey for verification on other channels
                - IPFS  -> content id can't change
                - Bitcoin, Ethereum, ...
                - github, gitlab, ...
                - websites, ...
            - use a hash from this signature as pepper (or salt) for ALL PoW hashes
            - provide browser plugin for security check 

## Ethereum
- https://developers.cloudflare.com/distributed-web/ethereum-gateway
Identities
- ERC725: https://erc725alliance.org/

Tokens
- ERC20: https://ethereum.org/en/developers/docs/standards/tokens/erc-20/
- ERC23: https://github.com/iam-dev/ERC23
- https://sharpcode.pro/difference-between-erc20-erc721-erc23-and-erc223-tokens/

NFT
s- ERC721: https://ethereum.org/en/developers/docs/standards/tokens/erc-721/
- EIP1155: https://eips.ethereum.org/EIPS/eip-1155

## Cardano
- https://cardano.org/

## Chainlink
- https://chain.link/

## Uniswap
- https://uniswap.org/

## Polkadot


