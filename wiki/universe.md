Universe
========

'universe' is the global variable allowing access 

Each participant has his own view of the universe. The claims, which the participant owns, define the visibility of the universe.

Global objects:

- universe  runtime environment
- thoregon  fundamental information and behavior about the runtime environment.
- dorifer   the [repository](dorifer.md) providing behavior.
- me        the current [identity](identity.md). see the document for more information.


## universe

Runtime environment. Normalizes 'node' and 'browser' globals.

Structure:
- universe
    - dorifer   also available as global
    - me        also available as global 
    - device    the current device
    - galaxies  same as me.galaxies
    
## galaxies
persitent data is stored in galaxies (imagine like a DB)

You always have a personal view to the universe. you see a part of the universe, the visible universe.

data from others can only be seen - will be mapped to your universe - when you get invited and
you accept the invitation. a claim is added to your identity.

there is also a process to ask for invitation. in this case you
don't need to accept the invitation.

there are some galaxies provided by thoregon which you get a claim automatically.
the galaxy 'ammandul'

app/components can also add galaxies to your visible universe. you get claims according the
rules defined by the app. 

to access the galaxies from an app, always use a namespace, which is actually the name of the publisher and the app.
e.g.: universe.galaxies.thatsme.mywebsties

namespaces must be registered by the publisher. this is done by publishing the app via the
thatsme app directory
 
apps can request access to other galxies, however this must be accepted by the user and 
is revocable.
app must (should) also work without access to the requested galaxies. apps use feature/asset detection
to adjust their functionality.

dev mode supports:
- im memory DB; keep in mind, performance may be much better while testing
- map appname to another dev galaxy
- modify strangeness; other universe  

subunits of galaxies are:
- starclusters   a collection of stars
- stars          an entity
 
