# Prisma Isolated Testing Example

This example demonstrates how to set up integration tests with Prisma, so that
each test suite will run on a separate Postgres database instance.

We accomplish this by first creating and running migrations against a single
`test` database. Then, for each test suite, we create a new database with
`CREATE DATABASE <random_db_name> WITH TEMPLATE test`.

This allows each test suite to run in parallel, without sharing any global
state, and without running migrations (which can be slow) for each instance.
