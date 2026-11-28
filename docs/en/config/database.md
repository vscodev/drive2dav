# Database

Corresponds to the `database` section of the configuration file.

| Field                | Type   | Default              | Description                                                              |
|----------------------|--------|----------------------|--------------------------------------------------------------------------|
| `driver`             | string | `"sqlite3"`          | Database driver. Supports `sqlite3`, `mysql` and `postgres`.              |
| `data_source`        | string | SQLite file DSN      | Data source connection string. Its format depends on the driver, see below. |
| `max_open_conns`     | int    | `4`                  | Maximum number of open connections. Driver-specific defaults apply when `<= 0`. |
| `max_idle_conns`     | int    | `4`                  | Maximum number of idle connections. Driver-specific defaults apply when `<= 0`. |
| `conn_max_life_time` | int64  | `0`                  | Maximum lifetime of a connection, **in seconds**. Driver-specific defaults apply when `<= 0`. |
| `conn_max_idle_time` | int64  | `0`                  | Maximum idle time of a connection, **in seconds**. Driver-specific defaults apply when `<= 0`. |

Values used automatically when `max_open_conns` / `max_idle_conns` / `conn_max_life_time` / `conn_max_idle_time` are passed as `0`:

| driver     | max_open_conns | max_idle_conns | conn_max_life_time | conn_max_idle_time |
|------------|----------------|----------------|--------------------|--------------------|
| `sqlite3`  | `4`            | `4`            | unlimited          | unlimited          |
| `mysql`    | `10`           | `10`           | 30 minutes         | 5 minutes          |
| `postgres` | `10`           | `10`           | 30 minutes         | 5 minutes          |

## SQLite (default, zero dependencies)

```
file:<data directory>/drive2dav.db?mode=rwc&_busy_timeout=5000&_txlock=immediate&_journal_mode=WAL&_foreign_keys=true
```

Meaning of each parameter:

- `mode=rwc`: create the file if it does not exist
- `_busy_timeout=5000`: wait up to 5 seconds for a lock
- `_txlock=immediate`: take the write lock as soon as a transaction starts, avoiding deadlocks while the lock is upgraded
- `_journal_mode=WAL`: WAL mode, which gives better concurrent reads and writes
- `_foreign_keys=true`: enable foreign key constraints

**Do not put a SQLite database on a network file system (NFS / SMB / a Synology WebDAV mount)**: WAL relies on reliable shared
memory and file locks, so a network drive can easily corrupt the database. Media files can live on a network drive, but the
database must stay on a local disk.

## MySQL

Example:

```json
{
  "driver": "mysql",
  "data_source": "user:password@tcp(127.0.0.1:3306)/drive2dav?charset=utf8mb4&parseTime=true&loc=Local"
}
```

## PostgreSQL

Example:

```json
{
  "driver": "postgres",
  "data_source": "postgres://postgres:postgres@127.0.0.1:5432/drive2dav?sslmode=disable"
}
```

## Notes

- When using MySQL or PostgreSQL, **the database must be created in advance**. Drive2dav only creates tables and indexes and
  migrates the schema automatically; it does not create the database itself.
