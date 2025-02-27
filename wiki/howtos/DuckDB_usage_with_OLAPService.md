Use OLAP Service
================

Back DB use is [DuckDB](https://duckdb.org/).

Find [reference and documentation](https://duckdb.org/docs/) here.

## Get the Service

get the DuckDB Wrapper:

```
// get OLAP service
const olap = app.current.home.olap;

const tables = await olap.getTables();
```

all functions are **async** and throws on errors

## SQL

### Exec

execute a SQL statement:

```
try {
    const result = await olap.exec(sql, params = [], types)
    ...
} catch (dberror) {
}
```

### Query

do a full query, returns **all** rows:

```
try {
    // returns an object with columnNames and rows
    const { columnNames, rows } = await olap.query('SELECT * FROM testtable WHERE id=?', [25]);
    ...
} catch (dberror) {
}
```

(todo) get a reader on a statement result:

```
try {
    // returns an object with columnNames and rows
    const { columnNames, rows } = await olap.read('SELECT * FROM testtable WHERE id=?', [25]);
    ...
} catch (dberror) {
}
```

### Insert

insert a record into a table. supply values as:
- Array: values must be in the order of the fields of the table ['a', 1, ...]
- Map (Object): property names must match table field names { field1: 'A', field2: 2 }

```
try {
    const values = { field1: 'A', field2: 2 };
    await olap.insert('testtable', values);
    ...
} catch (dberror) {
}
```


### Update

update a record in a table. supply keys and values as maps (objects)

```
try {
    const keys = { id: 15 };
    const values = { field1: 'A', field2: 2 };
    await olap.update('testtable', keys, values);
    ...
} catch (dberror) {
}
```

