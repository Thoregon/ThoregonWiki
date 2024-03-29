Blockchain Integration
======================

## Articles

- https://www.heise.de/news/US-Regierung-fordert-Gesetz-zur-Regulierung-von-Stablecoins-6245165.html    
- https://t3n.de/news/oracles-off-chain-daten-smart-contract-1465490/
- https://www.computerwoche.de/a/das-proof-of-abc,3612715
- https://www.computerwoche.de/a/crypto-wallets-zukunft-der-identitaet,3612775
- ! https://www.diepresse.com/13435075/forscher-entwickeln-einfaches-tauschprotokoll-fuer-kryptowaehrungen


## Considerations & Pitfalls  

- https://www.heise.de/hintergrund/Kryptowaehrungsmixer-Sanktionen-gegen-Tornado-Cash-schaffen-Praezedenzfall-7337784.html?seite=all

- Moxie's Web3 first impressions: https://moxie.org/2022/01/07/web3-first-impressions.html
- Abstract: https://cryptoslate.com/moxie-marlinspike-heres-whats-wrong-with-web3/
- Opinion: https://www.coindesk.com/layer2/2022/01/10/is-moxie-marlinspike-right-about-web-3/
- Vitalik's critisism: https://www.reddit.com/r/ethereum/comments/ryk3it/my_first_impressions_of_web3/hrrz15r/
- https://www.computerwoche.de/a/ein-ueberwachungssystem-das-nutzer-auspluendert,3612836

- https://t3n.de/news/eip-4844-ethereum-erfinder-otherside-1470443/
- https://www.heise.de/meinung/Web3-Im-vollen-Galopp-vor-die-Wand-ein-Kommentar-6537611.html?seite=all
- https://www.heise.de/hintergrund/Entwicklung-des-Web3-eine-Bestandsaufnahme-6537074.html?seite=all
- https://www.golem.de/news/beanstalk-hacker-erbeuten-kryptogeld-mit-mehrheitsentscheidung-2204-164677.html

- https://www.heise.de/news/Offener-Brief-Bruce-Schneier-warnt-US-Politik-vor-Kryptowaehrungs-Lobbyismus-7129230.html

- https://www.heise.de/news/Ethereum-Kontroverse-um-neues-Konzept-fuer-umkehrbare-Transaktionen-7279559.html
- https://www.heise.de/ratgeber/Smart-Contracts-Diese-rechtlichen-Fallstricke-gibt-es-7255732.html
- https://www.heise.de/hintergrund/Vor-und-Nachteile-der-Blockchain-in-Logistik-und-Handel-7222587.html

- Proof-of-Reserves https://t3n.de/news/proof-of-reserves-binance-chef-cz-arbeitet-mit-ethereum-erfinder-vitalik-buterin-an-krypto-transparenzprotokoll-1513349/


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

## Offline Private Side Chain

- Move and amount to a (new) private side chain
  - only on one device
- amount on the side chain can now be used offline
- receiver references to original on chain tx
  - adds a withdrawal tx 
- secure a full offline tx with zero knowledge proofs

--> check with lightning network

## Dev 

- https://infura.io/
- https://www.alchemy.com/
- https://www.web3.university/
- https://t3n.de/news/web3-entwicklung-solidity-blockchain-lernen-1454211/

## DeFi (decentralized finance)

- https://basicattentiontoken.org/de/  !!

- https://interledger.org/
- https://sundaeswap.finance/
- https://parachains.info/
- https://solana.com/wormhole
- https://fixedfloat.com/de/    Token Exchange

## Oracles

- [Binance Oracle](https://oracle.binance.com/docs)
  - [Binance Oracle: Konkurrenz zu Chainlink](https://t3n.de/news/binance-oracle-konkurrenz-zu-chainlink-1508858/)
- [Chainlink](https://chain.link/)

Articles
- https://www.btc-echo.de/academy/bibliothek/defi/
- https://de.cointelegraph.com/news/sectors-realizing-the-full-potential-of-defi-protocols-in-2020
- https://de.beincrypto.com/lernen/die-11-besten-defi-tools-zur-maximierung-deiner-defi-investitionen/
- https://computerwelt.at/news/central-bank-digital-currency-was-sie-ueber-cbdc-wissen-muessen-3/
- https://t3n.de/news/cardanos-sundaeswap-erreicht-1451449/
- https://t3n.de/news/avalanche-potential-smart-contract-chain-1435738/
- https://www.diepresse.com/14399569/ist-bitcoin-gut-fuer-die-umwelt-die-stimmung-schlaegt-um


## Coins

- bitcoin
- Monero
- Zcash

### bitcoin
- https://www.google.com/search?q=brc-20&rlz=1C9BKJA_enAT726AT726&oq=brc-2&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyBggBEEUYOTIJCAIQABgKGIAEMgkIAxAAGAoYgAQyBwgEEAAYgAQyCQgFEAAYChiABDIJCAYQABgKGIAEMgkIBxAAGAoYgAQyCQgIEAAYChiABDIJCAkQABgKGIAE0gEIOTc4NmowajeoAgCwAgA&hl=de&sourceid=chrome-mobile&ie=UTF-8

## Interledger/Bridge/Sidechain

- https://de.wikipedia.org/wiki/Lightning-Netzwerk
- https://wormhole.com/
- https://interledger.org/

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
