# PostgreSQL docs

Object-relational Database

**ACID compliant**

ref: [ACID](https://en.wikipedia.org/wiki/ACID)

- **A: Atomicity**

  - All operations inside a transaction should be threaten as unique.

- **C: Consistency**

  - The database state should be unique, avoiding database invariants.

- **I: Isolation**

  - Transactions executed concurrently should leave database state as if they were executed in sequential mode.

- **D: Durability**
  - Data should be flush no non-volatile memory (like disk).

> _As of the version 16 release in September 2023, PostgreSQL conforms to at least 170 of the 179 mandatory features for SQL:2023 Core conformance. As of this writing, no relational database meets full conformance with this standard._ [About](https://www.postgresql.org/about/)

## Data Types

- **Primitives**: Integer, Numeric, String, Boolean
- **Structured**: Date/Time, Array, Range / Multirange, UUID
- **Document**: JSON/JSONB, XML, Key-value (Hstore)
- **Geometry**: Point, Line, Circle, Polygon
- **Customizations**: Composite, Custom Types

## Outstanding

- Indexing: B-tree, Multicolumn, Expressions, Partial
- Advanced Indexing: GiST, SP-Gist, KNN Gist, GIN, BRIN, Covering indexes, Bloom filters
- Parallelization of read queries and building B-tree indexes
- Table partitioning
- Just-in-time (JIT) compilation of expressions
- Replication: Asynchronous, Synchronous, Logical
- Point-in-time-recovery (PITR), active standbys
- Column and row-level security
- PostGIS
- Full-text search

## Architectural Fundamentals

> _The PostgreSQL server can handle multiple concurrent connections from clients. To achieve this it starts (“forks”) a new process for each connection. From that point on, the client and the new server process communicate without intervention by the original postgres process. Thus, the supervisor server process is always running, waiting for client connections, whereas client and associated server processes come and go._ [Architectural Fundamentals](https://www.postgresql.org/docs/16/tutorial-arch.html)

## CLI Operations

### Create Database

Create a database via CLI.

```bash
$> createdb <database_name>
```

> You can also create a database with your username name, don't pass <database_name> to `createdb` or other commands.

Drop the database via CLI.

```bash
$> dropdb <database_name>
```

### Accessing a Database

```bash
$> psql <database_name>
```

Once you're inside postgresql terminal interface you can write SQL commands.

```sql
#= select version();
#= select current_date;
#= select 2 + 2;
```

## SQL Language (Structured Query Language)

| **Definition**                       | **Commands**                        |
| ------------------------------------ | ----------------------------------- |
| **DDL** (Data Definition Language)   | CREATE, ALTER and DROP              |
| **DML** (Data Manipulation Language) | INSERT, UPDATE, DELETE              |
| **DQL** (Data Query Language)        | SELECT                              |
| **DTL** (Data Transaction Langyage)  | BEGIN TRANSACTION, COMMIT, ROLLBACK |
| **DCL** (Data Control Language)      | GRANT, REVOKE E DENY                |

### Creating a table

```sql
CREATE TABLE weather (
  city          VARCHAR(255),
  temp_low      int,
  temp_high     int,
  precipitation real,
  date          date
);
```
