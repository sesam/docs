---
title: CANCEL JOB
summary: The CANCEL JOB statement lists all currently active schema changes and backup/restore jobs.
toc: false
---

<span class="version-tag">New in v1.1</span> The `CANCEL JOB` [statement](sql-statements.html) lets you stop a long-running jobs, which include:

- Schema changes through `ALTER TABLE`
- Enterprise [`BACKUP`](backup.html), [`RESTORE`](restore.html), and `IMPORT`

<div id="toc"></div>

## Required Privileges

By default, only the `root` user can cancel a job.

## Synopsis

{% include sql/{{ page.version.version }}/diagrams/cancel_job.html %}

## Parameters

Parameter | Description
----------|------------
`job_id` | The ID of the job you want to cancel, which can be found with [`SHOW JOBS`](show-jobs.html).

## Examples

### Cancel a Restore

~~~ sql
> SHOW JOBS;
~~~
~~~
+----------------+---------+-------------------------------------------+...
|       id       |  type   |               description                 |...
+----------------+---------+-------------------------------------------+...
| 27536791415282 | RESTORE | RESTORE db.* FROM 'azure://backup/db/tbl' |...
+----------------+---------+-------------------------------------------+...
~~~
~~~ sql
> CANCEL JOB 27536791415282;
~~~

## See Also

