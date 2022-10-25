WebService
==========

Expose services from Thoregon as web services. 

Thoregon supports REST and Mail API's.

This feature requires a real server to exec the service,  
it can't run just with IPFS or on a (local) machine which  
is not accessible from the WEB.

## Create the dispatcher for the endpoints

the class representing the service must be installed as service in a service agent.

### Annotations

annotate classes to become REST services:  
import the required annotations before use

Class level declarations
#### @Restfull
declare this class as a REST full service and define the entrypoints  
it can be installed as a service on a service agent

#### @Path
used on class level to specify the base path to the service
parameters 

Method level declarations. Function parameters for Get, Put ...

{ auth, params, query, content }
- auth: reference to the SSI if authenticated
- params: named path parameters
- query: query parameters from url
- content: body from request

#### @Get
declare a GET method with path and path parameters.
e.g. @Get("greet/{name}")

#### @Put
declare a PUT method with path and path parameters.

#### @Post
declare a POST method with path and path parameters.

#### @Patch
declare a PATCH method with path and path parameters.

#### @Delete
declare a DELETE method with path and path parameters.

#### @Head
declare a HEAD method with path and path parameters.

#### @Auth
declare if this method can only be invoked when authenticated.

#### @Consumes
specify the content type this methods can handle.

#### @Produces
specify headers what this method produces

Example:  
https://'host'/helloworld/greet/Charlie

````js
import { Restfull, Path, Auth, Get, Produces } from "/evolux.web";

"@Restfull"
"@Path('helloworld')"
export default class HelloWorld {

    "@Auth(false)"
    "@Get('greet/{name}')"
    "@Produces({ 'Content-Type': 'text/html' })"
    greet({ auth, params, query, content } = {}) {
        return `<html><body><p>Hello ${this.myfunction()} ${params.name ?? 'Stranger'}!</p></body></html>`
    }
}

HelloWorld.checkIn(import.meta);
````

#### Extensions to be made

Param Specification. Assign request params to function params
- @PathParam
- @QueryParam
- @Body

Add HATEOAS
- @HATEOAS
- @HATEOASMethod

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

## OpenAPI & AsyncAPI

To provide a [OpenAPI](https://www.openapis.org/) and a [AsyncAPI](https://www.asyncapi.com/) 
add specific information for params and entities by using evolux.schema 

## GraphQL

TBD ... not supported right now

