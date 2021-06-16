Component & App Structure
=========================

Thoregon supports a name convention to easy define components and apps

Directory structure
+ <meaningfull-app-name>
 + lib
    + views
    + commands
    + queries
 + ui
    + material
 - index.mjs        (optional)
 - component.tcd    (optional)
          

## Changing the convention

the name convention may be overruled - for whatever reason - using 
configuration or API 

### Configuration

Specify in 'component.tcd'

### API

Implement in 'index.mjs'

````js
let dorifer = universe.dorifer;

````


