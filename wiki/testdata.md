Test Data
=========

define test data as collection of item or a single object for a path.

the path is relative to the app instances home

export it as module default 

````javascript
import { $ser, $ref } from "/evolux.util/lib/testutil.mjs";

export default {
    home: 'myobjects',
    $: '/thoregon.archetim/lib/directory.mjs',  // class of the collection to use; default is Collection (/thoregon.archetim/lib/collection.mjs)
    items: [
        {}, {}, {} // ...
    ]
}
````
````javascript
import { $ser, $ref } from "/evolux.util/lib/testutil.mjs";

export default {
    home: 'myobjects',
    $: '/mymodule/lib/myclass.mjs', // class of the entity
    entity: {}
}
````

if a directory is used
````javascript
export default {
    // ...
    items: [
        {}, {}, {} // ...
    ],
    indexes: [
        { name: 'idx1', properties: ['propA', 'propB'] },
        { name: 'idx2', property: 'propA' },
    ]
}
````

## define entities

define soul/id.
entities using symbolic references can only be loaded 
together!
they will get a random soul which is unkown to the 
maker of the testdata.

Define class of the entity with '$'

Define test data wide symbolic reference (id) with '_'

````javascript
    // entity or item
{
    $: '/mymodule/lib/myclass.mjs:Class',     // class of the entity
    _: 'ENTITY123456'                         // test data wide symbolic reference 
}
````

if a collection with keys ist used, e.g. a Directory, then
the property which is used as key must end with '#'.

the '#' at the end will be removed from the property name. 

````javascript
    // entity or item
{
    $: '/mymodule/lib/myclass.mjs:Class',     // class of the entity
    'name#' : 'NAME123'                     // key to be used for the directory 
}
````

## references between entities

reference from another entity by soul:
````javascript
    // entity or item
{
    // ... 
    other: $ref('ENTITY123456')
}
````

reference from another entity using index:
````javascript
    // entity or item
{
    // ... 
    other: $ref('idx:idx1/ABCD')
}
````
