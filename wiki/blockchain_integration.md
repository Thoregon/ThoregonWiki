Blockchain Integration
======================

## Articles

- https://www.heise.de/news/US-Regierung-fordert-Gesetz-zur-Regulierung-von-Stablecoins-6245165.html    

## CRDT - Blockchain w/o Blockchain

- CRDT instead of bockchain
    - network not chain
    - @see: offchain transactions, payment channels
        - https://de.wikipedia.org/wiki/Lightning-Netzwerk
        - https://t3n.de/news/ethereum-layer-2-optimism-hacker-1451825/
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

## DeFi (decentralized finance)

- https://interledger.org/
- https://sundaeswap.finance/
- https://parachains.info/
- https://solana.com/wormhole
- https://fixedfloat.com/de/    Token Exchange

Articles
- https://www.btc-echo.de/academy/bibliothek/defi/
- https://de.cointelegraph.com/news/sectors-realizing-the-full-potential-of-defi-protocols-in-2020
- https://de.beincrypto.com/lernen/die-11-besten-defi-tools-zur-maximierung-deiner-defi-investitionen/
- https://computerwelt.at/news/central-bank-digital-currency-was-sie-ueber-cbdc-wissen-muessen-3/
- https://t3n.de/news/cardanos-sundaeswap-erreicht-1451449/
- https://t3n.de/news/avalanche-potential-smart-contract-chain-1435738/

## Coins

- bitcoin
- Monero
- Zcash

## Blockchains

### Ethereum
- https://developers.cloudflare.com/distributed-web/ethereum-gateway
Identities
- ERC725: https://erc725alliance.org/

Tokens
- ERC20: https://ethereum.org/en/developers/docs/standards/tokens/erc-20/
- ERC23: https://github.com/iam-dev/ERC23
- https://sharpcode.pro/difference-between-erc20-erc721-erc23-and-erc223-tokens/
- https://intersoft.co/blog/difference-between-erc20-erc721-erc23-and-erc223-tokens/

NFT
s- ERC721: https://ethereum.org/en/developers/docs/standards/tokens/erc-721/
- EIP1155: https://eips.ethereum.org/EIPS/eip-1155

### Filecoin
https://www.heise.de/news/Filecoin-Neue-Anreize-fuer-die-Blockchain-als-verteilter-Speicher-im-Internet-5050727.html

### Cardano
- https://cardano.org/

### Chainlink
- https://chain.link/

### Uniswap
- https://uniswap.org/

### Polkadot
- 

### Solana
- https://solana.com/de

### Avalance
- https://www.avax.network/
- https://t3n.de/news/avalanche-potential-smart-contract-chain-1435738/

### EOS
- https://eos.io/

### Tezos
- https://tezos.com/
- https://tezoscommons.org/
