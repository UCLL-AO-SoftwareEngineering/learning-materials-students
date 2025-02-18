# PostgreSQL Database

Currently every version of the application uses H2 as a database.

This should change to the following:

* The development environment backend uses H2
* The integration tests backend run on H2
* The production environment backend uses a production schema in a dedicated PostgreSQL database

Vercel offers one free PostgreSQL database on the Hobby plan.

- Go to your project on Vercel, and go to the "Storage" tab
- Click "Create" next to the "Neon" option
- Set the region to "Frankfurt, Germany" and installation plan to "Free"
- Choose a name and click "Create"
- Under "Quickstart", you'll now see that `.env.local` is selected. Click "Show secret".
- In the snippet you'll see a line:
  ```
  DATABASE_URL=postgres://neondb_owner:PASSWORD@SUBDOMAIN.eu-central-1.aws.neon.tech:5432/neondb?sslmode=require
  ```
  This means you can connect to the database using:
  - username: `neondb_owner`
  - password: `PASSWORD`
  - hostname: `SUBDOMAIN.eu-central-1.aws.neon.tech`
  - port: `5432`
  - database name: `neondb`
