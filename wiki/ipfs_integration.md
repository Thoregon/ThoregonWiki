Integration of IPFS
===================

JS IPFS
- Node
    - https://github.com/ipfs/js-ipfs
- Browser
    - https://js.ipfs.io/    
    - !! https://github.com/ipfs-examples/js-ipfs-examples/tree/master/examples

Deploy Websites to IPFS
- https://developers.cloudflare.com/distributed-web/ipfs-gateway
    - https://developers.cloudflare.com/distributed-web/ipfs-gateway/connecting-website
- https://dev.to/agentofuser/the-complete-beginner-s-guide-to-deploying-your-first-static-website-to-ipfs-33po

Pinning
- https://github.com/ipfs-shipyard/ipfs-deploy/tree/master/src/pinners
    - https://decentralify.runfission.com/
- https://docs.ipfs.io/how-to/websites-on-ipfs/single-page-website/#pinning-files
- https://docs.ipfs.io/how-to/work-with-pinning-services/#create-your-own-pinning-service

Pinning Services
    - https://sourceforge.net/software/product/Pinata/alternatives
- https://www.pinata.cloud/
    - https://docs.pinata.cloud/api-pinning/pinning-services-api
- https://temporal.cloud/temporal/
(Web3)
- https://filecoin.io/
- https://crust.network/
- https://infura.io/


Streaming
- https://stackoverflow.com/questions/29671771/how-can-i-stream-a-video-from-a-serviceworker
- https://developers.google.com/web/updates/2016/06/sw-readablestreams
- https://jakearchibald.github.io/streaming-html/server-render.html?
- https://pusher.com/sessions/meetup/milton-keynes-geek-night/service-worker-and-streams

Integration
- https://docs.ipfs.io/how-to/browser-tools-frameworks/

## Docu & Tutorials

- https://proto.school/tutorials?course=ipfs
- https://github.com/ipfs/js-ipfs/tree/master/docs/core-api
  https://docs.libp2p.io/concepts/fundamentals/peers/
- 
## Other Components/Systems

- https://docs.textile.io/
    - https://github.com/textileio/js-textile
    
- https://github.com/ipfs-search/ipfs-search 
- https://www.jsdelivr.com/package/npm/js-ipfs-fetch

### DNS Link

- https://developers.cloudflare.com/web3/ipfs-gateway/concepts/dnslink/
- https://docs.ipfs.tech/concepts/dnslink/
- https://dnslink.dev/#step-2-set-the-dnslink-value-on-a-txt-record

## Testing 

Playground/www/ipfs.html

Browser
- http://localhost:7777/thoregon.html

- http://localhost:7777/ipfs/QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/about
- http://localhost:7777/ipfs/QmRguchncQtxtyCRy3UjnkmhSboTBnaGizT1Xib523NeTM/blwelcome.txt
- http://localhost:7777/ipfs/Qmbs9MSm9iW5HpE9LM5Fvw2xRfZDevw4UK27wKsFuJ9Wtp/Gabi_IMG_2410.mp4

- http://localhost:7777/matter/root1
- http://localhost:7777/matter/root1/b

added QmepXSPVhFhFb5YkvaDufZMpFkGsxJrsZNeBvbrbEWyhmF video/Gabi_IMG_2410.mp4
added Qmbs9MSm9iW5HpE9LM5Fvw2xRfZDevw4UK27wKsFuJ9Wtp video


Enter on console

    > for await (const chunk of blipfs.ipfs.cat('QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG/quick-start')) { console.log(new TextDecoder().decode(chunk)) }
    > for await (const chunk of blipfs.ipfs.cat('QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc/readme')) { console.log(new TextDecoder().decode(chunk)) }
    
    > for await (const chunk of blipfs.ipfs.cat('QmRguchncQtxtyCRy3UjnkmhSboTBnaGizT1Xib523NeTM/blwelcome.txt')) { console.log(new TextDecoder().decode(chunk)) }
    > for await (const chunk of blipfs.ipfs.cat('QmXBiwfoavQWyz7Jg5KR1ruFM94tUjoytGJj3Xmq51vCMw')) { console.log(new TextDecoder().decode(chunk)) }

    > ipfs cat Qme5bsBSdt8FDbv7AJan5GDTwTWAzhdmn8vLcDfhrNgerc

