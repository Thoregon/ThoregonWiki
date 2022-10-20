WebService
==========

Expose services from Thoregon as web services. 

Thoregon supports REST and Mail API's.

This feature requires a real server to exec the service,
it can't run just with IPFS or on a (local) machine which
is not accessible from the WEB.

## Create the dispatcher for the endpoints

vani͛llaT provides three methods to define webservices.

### API

Create a class representing the webservice

register a webroot at the server instance you run the webservice

index.mjs
````js
    // specify your config. this object will simply be passed 
    // to the connect method of the webservice
    const config = {};
    export const mywebservice = new MyWebService()
                                        // first param is the root path, second is the config
                                        .addTerminalRoot('api', config)
                                        // start() registers the webservice,
                                        // can also be called later. 
                                        // mywebservice.connect() will be called 
                                        // when the webservice routing is running 
                                        .start();
````
Now implement your webservice

mywebservice.mjs
````js 
import { RestFull }          from "/evolux.web";

class MyWebService extends RestFull {
    /**
     * implement the connect() method to setup the endpoints.
     * 
     * wwwroot is a Router (/evolux.web/lib/router.mjs) 
     * and provides methods to define endpoints.
     * however, it is up to you to setup and handle the endpoints 
     * all handers can be async as well as sync.
     * errors thrown will be handled.   
     * @param {Router} wwwroot - router to define endpoints
     * @param {Object} config - the config you specified at addTerminalRoot()
     */
     connect(wwwroot, config) {
        // check authorization for all request 
        wwwroot.isAuthorized = ({ auth, url, params, query, content }) => authcheck();  

        /** @param {Request} req - request as known for express */
        /** @param {Response} res - response as known for express */
        /** @param {params, query, content} data - convenience, provides already extracted data from the request */
        /** @param {ResponseUtils} utils - easier responding  (/evolux.web/lib/responseutils.mjs) */
        // for each method an authorization check can be provided. overrules auth check from above
        wwwroot.post('postendpoint', async (req, res, data, utils) => { your.code.here() }, ({ auth, url, params, query, content }) => authcheck());
        wwwroot.put('putendpoint', async (req, res, data, utils) => { your.code.here() });
        wwwroot.get('getendpoint', async (req, res, data, utils) => { your.code.here() });
        wwwroot.patch('patchendpoint', async (req, res, data, utils) => { your.code.here() });
        wwwroot.delete('deleteendpoint', async (req, res, data, utils) => { your.code.here() });

     }
}
````

### Annotations



````js
````


### Config
simply specify a webservice

index.mjs
````js
    import { WebService }          from "/evolux.web";
    // specify your config. this object will simply be passed 
    // to the connect method of the webservice
    export const mywebservice = new WebService({
        'api' : {
            'endpoint' : { method: 'get', do: async (req, res, data, utils) => { your.code.here() }},
            'endpoint2' : { method: 'put', do: async (req, res, data, utils) => { your.code.here() }}
        },
        'api2' : {
            ...
        }    
    });
````

### Convention
This is the easiest way to define a web service. Names will setup the webservice.

directory ws/<wsrootname>
    setup.mjs
    cleanup.mjs
    
    put.<endpointname>.mjs

## OpenAPI & AsyncAPI

To provide a [OpenAPI](https://www.openapis.org/) and a [AsyncAPI](https://www.asyncapi.com/) 
add specific information for params and entities by using evolux.schema 

## GraphQL

TBD ... not supported right now

## Create the commands

