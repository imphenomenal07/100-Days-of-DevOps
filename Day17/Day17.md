# Day17: Install and Configure PostgreSQL

1. Login into DB server:
# $ ssh user@server

2. Now check status of PostgreSQL, also enable and restart:
# $ sudo systemctl enable postgresql; sudo systemctl restart postgresql; sudo systemctl status postgresql

3. Now login into DB:
# $ sudo -i -u postgres; psql

4. Now create user:
# # CREATE USER user_name WITH PASSWORD 'password';

5. Create Database:
# # CREATE DATABASE db_name;

6. Grant full permission to user on databse:
# # GRANT ALL PRIVILEGES ON DATABASE db_name TO user_name;

7. Run below commands to check list of users and databases:
# \du  #list users
# \l  #list databases
