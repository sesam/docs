---
title: Release Notes
toc: false
---

## Apr 7, 2016: `beta-20160407`

### Backwards-incompatible Changes

* Any databases using the `DECIMAL` type will need to be deleted and
  created from scratch. Columns of this type were encoded incorrectly
  by `beta-20160330`.
  [#5820](https://github.com/cockroachdb/cockroach/pull/5820)
* `SELECT` statements must now specify specify one or more columns or
  expressions. Previously statements such as `SELECT FROM t` were
  allowed but the results would confuse many clients.
  [#5859](https://github.com/cockroachdb/cockroach/pull/5859)
* It is now an error to insert a value that is too large into a column
  with a type of limited length such as `VARCHAR(n)`.
  [#5750](https://github.com/cockroachdb/cockroach/pull/5750)

### Compatibility

* Added support for the "flush" message in the PostgreSQL network
  protocol, which improves compatibility with the node.js driver.
  [#5740](https://github.com/cockroachdb/cockroach/pull/5740)
* Fixed a panic when handling certain queries sent by the PHP PDO
  library. [#5783](https://github.com/cockroachdb/cockroach/pull/5783)
* Improved parsing of timestamps for compatibility with the Go
  `lib/pq` client library.
  [#5877](https://github.com/cockroachdb/cockroach/pull/5877)

### New Features

* Index hints: `SELECT FROM tbl@idx` or `SELECT FROM
  tbl@{FORCE_INDEX=idx}` instructs the query planner to use the given
  index. [#5785](https://github.com/cockroachdb/cockroach/pull/5785)
  and [#5806](https://github.com/cockroachdb/cockroach/pull/5806)
* The `cockroach` command-line client now accepts environment
  variables as default values for many command-line flags. See
  `--help` for details.
  [#5430](https://github.com/cockroachdb/cockroach/pull/5430)
* Added SQL `version()` function.
  [#5763](https://github.com/cockroachdb/cockroach/pull/5763)
* Added compiler and platform information to `cockroach version`
  output. [#5766](https://github.com/cockroachdb/cockroach/pull/5766)
* Debugging tools show fractional seconds in timestamps.
  [#5736](https://github.com/cockroachdb/cockroach/pull/5736)
* In secure mode, plain HTTP requests to the `http-port` used by the
  admin UI are now redirected to HTTPS.
  [#5746](https://github.com/cockroachdb/cockroach/pull/5746)
* Links to debugging pages are available on the HTTP port at
  `/debug/`.
  [#5795](https://github.com/cockroachdb/cockroach/pull/5795)
* The `cockroach zone set` command now echos the new configuration.
  [#5829](https://github.com/cockroachdb/cockroach/pull/5829)

### Bug Fixes

* Improved flow control for raft snapshots, fixing an issue that could
  lead to nodes running out of memory.
  [#5721](https://github.com/cockroachdb/cockroach/pull/5721)
* Fixed a deadlock scenario in which two conflicting transactions
  would both be unable to make progress.
  [#5710](https://github.com/cockroachdb/cockroach/pull/5710)
* Fixed a panic while executing certain `DELETE` statements.
  [#5840](https://github.com/cockroachdb/cockroach/pull/5840)

### Internal Changes

* Clock offsets are now measured continuously.
  [#5512](https://github.com/cockroachdb/cockroach/pull/5512)
* Improved caching to avoid redundant range descriptor lookups.
  [#5627](https://github.com/cockroachdb/cockroach/pull/5627)
* Reduced log spam when nodes are down.
  [#5883](https://github.com/cockroachdb/cockroach/pull/5883)

### Contributors

This release includes 77 merged PRs by 18 authors. We would like to
thank the following contributors from the CockroachDB community,
especially
[first-time contributor Seif Lotfy](https://github.com/cockroachdb/cockroach/pull/5747).

* Kenji Kaneda
* Seif Lotfy