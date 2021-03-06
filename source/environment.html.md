---
title: Useful Environment Variables
icon: file-text
summary: 'Plume uses environment variable to configure instances. You can use them
to configure the database, or the HTTP interface for instance.'
---

Plume relies on some environment variables for some configuration options. You can either set them before
starting the app with `cargo run` or write them in a `.env` file to have automatically loaded.

Here are the variables that Plume uses:

- `BASE_URL`: the domain name, or IP and port on which Plume is listening. It is used in all federation-related code.
- `DATABASE_URL`: the URL of the PostgreSQL database, used by Plume (`postgres://plume:plume@localhost/plume` by default with PostgreSQL, `plume.db` with SQlite).
- `MIGRATION_DIRECTORY`: The folder that stores the migration files for the database, migrations/postgres for PostgreSQL database or migrations/sqlite for SQlite database.
- `USE_HTTPS`: if it is `0`, federation and medias will be using HTTP by default (`1` by default).
- `ROCKET_ADDRESS`: the adress on which Plume should listen (`0.0.0.0` by default).
- `ROCKET_PORT`: the port on which Plume should listen ([`7878` by default](https://twitter.com/ag_dubs/status/852559264510070784))
- `ROCKET_SECRET_KEY`: key used to sign private cookies and for CSRF protection. If it is not set, it will be regenerated everytime you restart Plume,
meaning that all your users will get disconnected. You can generate one with `openssl rand -base64 32`.

The SMTP server to send mails can be configured with:

- `MAIL_SERVER`: the SMTP server to connect to.
- `MAIL_USER`: the username of the user that sends emails.
- `MAIL_PASSWORD`: its password.
- `MAIL_HELO_NAME`: the name sent during EHLO/HELO.

## Diesel

Diesel, the tool we use to run migrations may be configured with the `DATABASE_URL` which should contain the URL of the
PostgreSQL database. Otherwise, you can specify `--database-url YOUR-URL` everytime you run a `diesel` command.
