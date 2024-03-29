Annotations
===========

annotations are used to declare information and also behavior.

## Webhook

### Class Annotations

### Method Annotations

### Attribute Annotations


## Service

### Class Annotations

### Method Annotations

## AutomationService

### Class Annotations

@AutomationService
  params: { callLimit: <int>, interval: <String> }
    call limit per interval
    values for interval: 'S', 'second', 'M', 'minute', 'H', 'hour', 'D', 'day'
  e.g. @AutomationService({ callLimit: 5, interval: 'minute' }) -> max 5 calls per minute

### Method Annotations

@OnMessage
  params: channel, eventtype, conditionfn, conditionfn2, ... 

condition params: (evt, handle, appinstance, home)

### Attribute Annotations


## Future - runntime Annotations:

Method/function param annotations:
print(/*@NotNull(ignore) @Is(String)*/ text) { ... }

Instance creation Annotations
new /*@abc*/ Class()

Type cast Annotations
x = /*@NotNull @Is(String)*/ y;

Exception Annotations
throw /*@Critical*/ Error();

ToDo:
- create real decorators with proxies or insert super class in prototype chain
- add static 'create' factory methods to wrap the object
- introduce reflection for annotations
- allow multiple decorators
    - get create method of next annotation decorator (reflection)

do not: insert a prototype in class hierarchy


## Links

- https://www.heise.de/blog/Features-von-uebermorgen-ES7-Decorators-2633730.html
- https://docs.oracle.com/javase/tutorial/java/IandI/index.html
- https://gist.github.com/SerafimArts/f802c544d8e9d15f5eece1dfb2664929
- https://stackoverflow.com/questions/17065949/javascript-annotations
- https://github.com/cmartin81/decorator-wrap
- https://github.com/wycats/javascript-decorators

REST Annotations
- https://www.juniper.net/documentation/en_US/junos-space-sdk/18.1/apiref/com.juniper.junos_space.sdk.help/html/reference/spaceannoREST.html#:~:text=Annotations%20are%20like%20meta%2Dtags,fields%2C%20parameters%2C%20and%20variables.
