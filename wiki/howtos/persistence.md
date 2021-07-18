Persistence
===========

Where are my data stored?

The root for all persistent objects is

    universe.galaxies


Every developer has to register at least one namespace where
the data of the app or component will be stored

    universe.galaxies.thatsme

## Universe

the universe is an extended cloud where every participant can
store and organise its data.

create folders like in a filesystem and store whatever you want.

Objects will be stored in matter, large BLOBs e.g. video and audio
will be stored in heavymatter

## Identity

SSI's have claims to access the data. 
every SSI 

## Galaxy

to access a certain galaxy we need a claim containing the key. 

### Matter

### Heavy Matter

distributed file storage 

## Index

define properties to be used to create an index.
the persistence layer will maintain all indexes.

## Usage

## Invitations

to access persistent data someone else has created,
you need a claim containing metadata and the key

### Ask for invitation

You need to know the queue of the SSI (or the service) 

### Invite

## Metadata

Each object stored also has its metadata stored.
In case of same metadata, e.g. the class definition,
the object will be referenced, not copied.

## Modifications

! view handling: only the collection or the creator must select the new created entity and show the details 

we distinguish between create of 
- independent entities which will be added to a collection
- embedded object in a parent entity

Create a new entity in a collection

    let mywebsties = universe.galaxies.thatsme.mywebsties;
    
1
    
    let newwebsite = await mywebsties.create({});
    
2 

    let newwebsite = await dorifer.create(ServiceAgentWebsiteDescriptor);
    await mywebsites.add(mywebsite)
    
Create an object as attribute of an object

    let images = await mywebsites.images.create();
    
Modify the entity
    
    newwebsite.shortname = "xyz";
    newwebsite.domain = "xyz";
    
