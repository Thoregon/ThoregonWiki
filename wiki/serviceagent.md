Service Agent
=============

- my resources
- migrations
- enables bots
    - on behalf of me


## Basic structure of an agent (service agent)

- agent
- agent.current
    - services          ... standalone services on behalf of the identity
    - mesh              ... mesh of services working together

enable circles over agent boundaries

## service configuration on a standalone agent

load it 

````javascript
serviceid: {
  app: <appid>,
  instance: <instanceid>,
  producer: <ProducerClass>,
  settings: {
      // service specific settings
  }
}

future: cron    : "0 * * ? * *",        // see https://github.com/node-cron/node-cron, https://www.freeformatter.com/cron-expression-generator-quartz.html
````

## service configuration with SSI

integrated component of the thatsme app with UI.

API 

## service configuration for apps

the descriptor of an app contains also the services belonging to the app.
the servcie descriptior is simmilar to the servicie configuration of an agent.
the appinstance is automatically determined.
the descriptor gives hints where to install an app service
- can it run on any device e.g. also on the UI side (browser)
- does it need web access (which the browser prevents)
- should it always be available (no local running app the user may quit) 

## service implementation

provide an implementation for a service. the implementation itself will become the producer 

the service will be accessible by the consumer, which is a facade to the service producer.
it supplies the API of the producer

### lifecycle

- install
- attach to an app instance
- activate
- deactivate
- uninstall

there is a hook for each phase. the methods may be implemented on the producer.
no error will rise if one is missing.

install:      async init(settings) {}   
- the settings specified in the configuration, service can add a listener to react on modifications
- will be called only once after the service is installed

attach app:   async attach(appinstance) {}
- hand over the app instance to the service 
- in case of install init() will be called be4 attach()
- will be called only once at all
- there is no 'detach' from app instance! uninstall an reinstall with another app instance

activate:     async activate() {}
- will be called every time the service is activated

deactivate:     async deactivate() {}
- will be called every time the service is activated

uninstall:      async quit() {}
- deactivate() will be called first be4 quit()
- will be called only once before the service is uninstalled

in the config, the hooks can be overridden with own functions. 
the parameter service is the 'consumer'. all method invokations and property sets will be forwarded to the producer.

````javascript
serviceid: {
  // ... app instane and other control information
  hooks   : {
    oninstall   : async (service, settings) => {} ,
    onattach    : async (service, appinstance) => {},
    onactivate  : async (service) => {},
    ondeactivate: async (service) => {},
    onuninstall : async (service) => {}
  },
}
````

## service mesh

a service mesh defines services working together.
the consumers of the specified will be collected and
passed to the producer by invoking the 'inject' method with the consumers as parameters.

````javascript
serviceid: {
  // ... app instane and other control information
  mesh    : {
    consumers: [ 'serviceid1', 'serviceid1', 'serviceid1' ],
    inject   : 'useServices'
  }
}
````

### connect services 

- declaration: declare to mesh by specifying the required other services for a service
- directory lookup: use the API to lookup the required other services

