# Periodic-Table-Database

For this project, I will create Bash a script to get information about chemical elements from a periodic table database.  

## Step 1: Create Docker-compose file

You will use docker compose to create a container docker for Postgres.  

Pls create a file `docker-compose.yaml` and a folder `atomic_mass_data`.    

File `docker-compose.yaml`    
```
services:
  pgdatabase:
    image: postgres:13
    environment:
      - POSTGRES_USER=root
      - POSTGRES_PASSWORD=root
      - POSTGRES_DB=periodic_table
    volumes:
      - "./atomic_mass_data:/var/lib/postgresql/data:rw"
    ports:
      - "5432:5432"
```

To start a postgres instance, run this command:  
`sudo docker-compose up -d`

**Note:** If you want to stop that docker compose, pls enter this command: `sudo docker-compose down`  

Ensure that the .pgpass file is properly set up to avoid any password prompts. If the .pgpass file doesn't exist, create it in your home directory and set the appropriate permissions:

```
touch ~/.pgpass
chmod 600 ~/.pgpass
```

Open the .pgpass file in a text editor and add the following line with the appropriate values for your PostgreSQL server:

```
localhost:5432:periodic_table:root:your_password_here
``` 

To log in to PostgreSQL with psql to create your database. Do that by entering this command in your terminal:

```
psql -h <hostname> -p <port> -U <username> -d <database>
```