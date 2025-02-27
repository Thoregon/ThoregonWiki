SQL DB Migration
================

Applies for SQL Databases defined with OlapService (thoregon.neuland)

Back DB use is [DuckDB](https://duckdb.org/).

Find [reference and documentation](https://duckdb.org/docs/) here. 

# Use OLAP Service

add in agent config (etc/agent_0.config.mjs)
```
import OLAPService             from "/thoregon.neuland/src/olap/olapservice.mjs";
```
```
services: {

    ...
    
    olap: {
        producer: OLAPService,
        settings: {
            db: 'dbname',
            version: 1,
            upcmds: [],
            downcmds: [],
            migration: {
                1 : [...],
            }
        }
    }

    ...
    
}
```

current DB version is stored etc/olap.mjs
```
export default { version: 1 }
```

# Define DB

The settings from the OLAP service definition will be used o define the database.
A [migration](#Migration) procedure supports changes in DB definition.

| Param     | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| db        | name of the DB in the 'main' catalog, will be created if missing            |
| version   | version of this definition                                                  |
| upcmds    | an array of SQL commands which will be executed when the agent starts       |
| downcmds  | an array of SQL commands which will be executed before the agent stops      |
| migration | an ordered sequence of migration steps. see section [migration](#Migration) |

future extensions:
- dblocation: location of the DB (files)
- catalog: name of the catalog (create if missing)

# Migration

The migration procedure executes all migration steps from the current DB version
to the required version defined in the **version** parameter of the DB definion.

A migration can contain a list of steps. the steps will be performed in the order 
they are defined. The initial creation of the DB should be done in migration step 1.

```
version: 2,
...
migration: {
    1: [
        { migration step 1.1 }
        { migration step 1.2 }
    ],
    2: [
        { migration step 2.1 }
        { migration step 2.2 }
    ],
}
```
There are different migration steps to be used:
- SQL command
- JS (JavaScript) command
- Define table
- Insert command
- Update command

define table, insert and update express commands SQL independent, but they can also
be imlemented as SQL commands.

## SQL Command
Simple SQL command which will be executed. the result will **not** be passed to the next 
migration step. 
When createing or altering tables and other DB objects keep in mind to use 'IF EXISTS' respectively 'IF NOT EXISTS'
to avoid error messages in the log. 
A failed migration step does not stop the migration.

```
{ sql: 'CREATE SEQUENCE IF NOT EXISTS txid START 1;' }
```

## JS command
pass a JS function to handle the migration step. 
params for the function:
- connection: DB connection object, execute SQL 
- params: arbitrary params which will just be passed to the function
- home: app home to enable more sophisticated migrations

the returned result will be printed in the log.
here is a useless example
```
{ js: async (connection, params, home) => {
        try { 
            const result = await connection.run('SELECT * FROM information_schema.tables');
            const chunks = await result.fetchAllChunks();
            chunks.forEach(chunk => console.log("DB Table: ", JSON.stringify(chunk.getRows())));
        } catch(dberror) {
            return `DB Error: ${dberror}`; 
        }
        return `Migration JS: ${params.a}, ${params.b}`; 
    }, 
    params: { a: 'A', b: 2} 
}
```

## Define table

```
{
    table: 'testtable', columns: [
        { name: 'id', def: "INTEGER DEFAULT nextval('txid')" },
        { name: 'field_a', def: 'INTEGER NOT NULL' },
        { name: 'field_b', def: 'VARCHAR' },

        { def: 'PRIMARY KEY (id)' },

        { cmd: 'CREATE INDEX IF NOT EXISTS idx_a ON testtable (field_a)' },
        { cmd: 'CREATE INDEX IF NOT EXISTS idx_b ON testtable (field_b)' },
    ]
}
```

## Insert command
SQL independent insert command

Specify field values in 'insert:' and the table name. omit auto generated keys. 
```
{ insert: { field_a: 1, field_b: 'A' }, table: 'testtable' },
```

## Update command
SQL independent insert command

Specify key values in 'update:', field values in 'set:' and the table name.
```
{ update: { field_a: 1 }, set: { field_b: 'B' }, table: 'testtable' },
```


future extensions for all migration steps:
- add 'onError:' for migration steps. if error handler returns true resume migration, otherwise stop it

