# cyanite-remover

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/cybem/whisper2cyanite/master/LICENSE)
[![Build Status](https://travis-ci.org/cybem/cyanite-remover.svg?branch=master)](https://travis-ci.org/cybem/cyanite-remover)
[![Dependencies Status](http://jarkeeper.com/cybem/cyanite-remover/status.svg)](http://jarkeeper.com/cybem/cyanite-remover)

cyanite-remover is a [Cyanite](https://github.com/pyr/cyanite) data removal
tool.

## Table of Contents

* [Building](#building)
  * [Dependencies](#dependencies)
  * [Building a Standalone JAR-file](#building-a-standalone-jar-file)
  * [Building a Deb-package](#building-a-deb-package)

## Building

### Dependencies

cyanite-remover is a [Clojure](http://clojure.org/) application and uses
[Leiningen](http://leiningen.org/) as build tool. Building cyanite-remover
needs a working Leiningen installation, as well as JDK.

### Building a Standalone JAR-file

```bash
lein uberjar
```

Built JAR-file will be placed in the `target/uberjar` directory. You can launch
the tool by running `./cyanite-remover` command.

### Building a Deb-package

Building cyanite-remover deb-package needs installed `dpkg-dev` and `fakeroot`
packages.

```bash
lein fatdeb
```

Built package will be placed in the `target` directory.

## Usage

### Quick Help

    cyanite-remover [options] remove-metrics <tenant> <rollup:period,...> <path,...> <cassandra_host,...> <elasticsearch_url>
    cyanite-remover [options] remove-paths <tenant> <path,...> <elasticsearch_url>
    cyanite-remover [options] list-metrics <tenant> <rollup:period,...> <path,...> <cassandra_host,...> <elasticsearch_url>
    cyanite-remover [options] list-paths <tenant> <path,...> <elasticsearch_url>
    cyanite-remover help

For more information see [commands](#commands), [arguments](#arguments) and
[options](#options).

### Commands

### Arguments

### Options

Options in alphabet order:

* [cassandra-batch-rate](#cassandra-batch-rate)
* [cassandra-batch-size](#cassandra-batch-size)
* [cassandra-channel-size](#cassandra-channel-size)
* [cassandra-keyspace](#cassandra-keyspace)
* [cassandra-options](#cassandra-options)
* [disable-progress](#disable-progress)
* [elasticsearch-index](#elasticsearch-index)
* [from](#from)
* [help](#help)
* [jobs](#jobs)
* [log-file](#log-file)
* [log-level](#log-level)
* [run](#run)
* [stop-on-error](#stop-on-error)
* [to](#to)

#### `cassandra-batch-rate`

`--cassandra-batch-rate` `RATE`

Set the Cassandra batch rate (batches per second, 1-100).

Throttling is not used by default.

#### `cassandra-batch-size`

`--cassandra-batch-size` `SIZE`

Set the Cassandra batch size.

Default: `1000`

#### `cassandra-channel-size`

`--cassandra-channel-size` `SIZE`

Set the Cassandra channel size.

Default: `10000`

#### `cassandra-keyspace`

`--cassandra-keyspace` `KEYSPACE`

Set the Cassandra keyspace.

Default: `metric`

#### `cassandra-options`

`-O`, `--cassandra-options` `OPTIONS`

Set Cassandra options.

Example: "{:compression :lz4}"

#### `disable-progress`

`-P`, `--disable-progress`

Disable the progress bar.

#### `elasticsearch-index`

`--elasticsearch-index` `INDEX`

Set the Elasticsearch index.

Default: `cyanite_paths`

#### `from`

`-f`, `--from` `FROM`

Set from time in the
[Unix (POSIX, epoch) time](https://en.wikipedia.org/wiki/Unix_time) format.

Example: 1420070400

#### `jobs`

`-j`, `--jobs` `JOBS`

Set the number of jobs to run simultaneously.

#### `log-file`

`-l`, `--log-file` `FILE`

Set the log file.

Default: `whisper2cyanite.log`

#### `log-level`

`-L`, `--log-level` `LEVEL`

Set the Log level.

Available log levels: `all`, `trace`, `debug`, `info`, `warn`, `error`,
`fatal`, `off`.

Default: `info`

#### `run`

`-r`, `--run`

Force a normal run. **Dry run using on default**.

#### `to`

`-t`, `--to` `TO`

Set until time in the
[Unix (POSIX, epoch) time](https://en.wikipedia.org/wiki/Unix_time) format.

Example: 1421280000

#### `stop-on-error`

`-S`, `--stop-on-error`

Stop on the first non-fatal error.
