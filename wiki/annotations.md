Annotations
===========

annotations are used to declare information and also behavior.

## Webhooks

### Class Annotations

### Method Annotations

### Attribute Annotations


## Services

### Class Annotations

### Method Annotations

@OnMessage

condition params: (evt, handle, appinstance, home)

### Attribute Annotations


## Future - runntime Annotations:

Instance creation Annotations
new /*@abc*/ Class()

Type cast Annotations
x = /*@NotNull String*/ y;

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
