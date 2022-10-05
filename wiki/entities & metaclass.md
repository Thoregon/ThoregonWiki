Entities
========

define classes and metaclasses for entities

To register the entity class to the system

    Class.checkin(import.meta, MetaClass);


## MetaClass

metaclasses defines the system behavior of the entity

### Attributes



````javascript
class MyMetaClass extends MetaClass {
    initiateInstance() {
        this.name = "MyMetaClass";  // give it a name
        // ...
        this.text('propertyName');
    }
}
````


### Events

with the metaclass additional events for the entity can be defined

the function will be evaluated after every modification of the entity.
if it answers true, the event will be sent to all listeners of
- the entity
- the metaclass of the entity

the 'detail' of the event will contain the entity.
if a 'detail function' is provided, 'detail' of the event will contain the result of this function.

make sure that you don't pass an arrow - function () => {...} - because this
would bind 'this' to the metaclass!

use standard javascript functions - function () { return ... }
in this case 'this' will be the entity

````javascript
class MyMetaclass extends MetaClass {
    initiateInstance() {
        // ...
        this.event("candance",  function () { return this.hasLegs() });
    }
}
````

````javascript
this.event("candance",  function () { return this.hasLegs() }, function() { return { numOfLegs: this.numOfLegs }});
````
