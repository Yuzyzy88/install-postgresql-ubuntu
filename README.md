# Install Postgresql Ubuntu

## 1. [Install Postgress](https://www.postgresql.org/download/linux/ubuntu/)

I use manual installation because we can choose the version to install. To manually configure the apt repository, follow these steps.

Import the repository signing key:
```
sudo apt install curl ca-certificates
sudo install -d /usr/share/postgresql-common/pgdg
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
```

Create the repository configuration file:
```
sudo sh -c 'echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
```

Update the package lists:
```
sudo apt update
```

Install the latest version of PostgreSQL.
If you want a specific version, use 'postgresql-16' or similar instead of 'postgresql':
```
sudo apt -y install postgresql
```

## 2. Set Password for Postgres User

Go to root user:
```
sudo su
```

Swith to postgres user:
```
su postgres
```

Run 'psql' to use postgres shell:
```
psql
```

Change postgres password:
```
ALTER USER postgres PASSWORD 'new_password';
```

Then exit:
```
\q
```

## Connect to a Postgres Database

It is used to connect to a PostgreSQL database using the psql command-line client.  Replace 'localhost' with the actual hostname or IP address if the server is on a different machine:
```
psql -U postgres -h localhost
```

Create database:
```
CREATE DATABASE databasename;
```


## Database connection URL

```
DATABASE_URL="postgres://postgres:postgres@postgres/postgres"
```

- postgres://: This specifies the database type, in this case, PostgreSQL.
- postgres:postgres: This username and password used to connect to the database.
- @postgres: This is the hostname or IP address where the PostgreSQL database server is located.
- /postgres: This part specifies the default database name to connect to within the PostgreSQL server.

