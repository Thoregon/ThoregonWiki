Thoregon Packager
=================

## Entrypoint

package containing the PULS (like a kernel) to start Thoregon in a browser.
inkludes only minimal code, just to start and load the Thoregon system
from IPFS.

Contains: 
- gun, sea  to to find the system package in IPFS
    - read CID from gun
    - verify
    - load from ipfs
- ipfs
    - minimal client to load the thoregon package
    - unzip to local cache
- puls
    - service worker
    
Two flavors:
- with dev loader
- w/o dev loader -> public available in IPFS
    
## Environments

create basic thoregon system packages for fast system load and startup.
this is manly for browser environments, node or electron envoronments
typically comes with all requirements to start the system. 

build separate packages for 
- node/electron environments
    - with or w/o express to support 
        - initial load from a client
        - provide REST/GraphQL webservices
    - w/o UI packages 
- browser environments
    - with UI packages
        - evulux.ui
        - thoregon.aurora

Two flavors of the packages
    - with and w/o thoregon system package 

Contains:
- shared workers 
    - gun
    - ipfs
- puls

        
### Excludes

- files starting with '.'
- *.md, *.txt
- direcorties
    - test, tests
    - doc

### ES6 Wrapper

some modules will be packaged - and minified - e.g. with webpack, browserify or others.
those packagers will create packages to be imported with 'require', 'amd' ...
but with ES6 import. 

The wrapper will add code to be able to load the module with 'import'  

### Worker importScript() wrapper

opposite of the ES6 wrapper. Makes .mjs modules importable with importScript() 
in Workers. Caution: mapps the exports to the global context!
The name of the module is the namespace, the default is available with 'name'.default


## Docker

prepackaged docker container are available.
pass credentials on install/start.
[docker image](https://hub.docker.com/_/alpine) based on [alpine](https://alpinelinux.org/) 

## Repository

all packages will be stored in IPFS. there is a signed root entry
in universe matter containing the CID of the packages (versioned)

the public key for verification is included in the service worker
first requiring the thoregon package.

gun firewall will reject changes with wrong signature.

todo: enable multiple signatures, update of allowed sig keys

caution: someone could publish an entrypoint with its own service worker
to a malware thoregon system! The system must authorize itself to the apps
it loads.  

## Links

- https://www.heise.de/hintergrund/JavaScript-Bundler-Turbopack-Mit-den-Erfahrungen-aus-zehn-Jahren-Webpack-7337331.html

