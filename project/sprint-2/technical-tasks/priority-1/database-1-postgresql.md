# PostgreSQL Database

Currently every version of the application uses H2 as a database.

This should change to the following:

* The development environment backend uses H2
* The integration tests backend run on H2
* The production environment backend uses a production schema in a dedicated PostgreSQL database

Vercel offers one free PostgreSQL database on the Hobby plan.

- Go to your project on Vercel, and go to the "Storage" tab
- Choose "Postgres" and click "Create"
- Choose a database name and set the region to "Frankfurt, Germany"
- Click "Connect"
- You'll get a snippet that starts with `psql`. The part between quotes looks like:
  ```
  postgres://default:PASSWORD@SUBDOMAIN.eu-central-1.aws.neon.tech:5432/verceldb?sslmode=require
  ```
  This means you can connect to the database using:
  - username: `default`
  - password: `PASSWORD`
  - hostname: `SUBDOMAIN.eu-central-1.aws.neon.tech`
  - port: `5432`
  - database name: `verceldb`
