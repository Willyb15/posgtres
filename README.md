# posgtres
Postgre Configuration Walkthrough
//Install PostGre
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
 
sudo apt-get install pgadmin3
 
//Switch to the Postgres Role
sudo -i -u postgres
 
//Access Postgres Prompt
psql
 
//Exit out of Postgres
postgres=# \q
 
//Create a New Database
create database cc_hist;
 
/*
To log in with ident based authentication, you'll need a Linux user with the same name as your Postgres role and database. If you don't have a matching Linux user available, you can create one with the adduser command. You will have to do this from an account with sudo priveleges (not logged in as the postgres user):
*/
//From outside of postgres
sudo -u postgres createuser -s <<username>>
 
//Give the user privileges to everything. Log in as the postgres role, then do:
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO <<username>>;
 
Once you have the appropriate account available, you can either switch over and connect to the database by typing:
sudo -i -u <<username>>
You will be logged in automatically assuming that all the components have been properly configured
 
//List Databases
\l or \list
 
//List of Tables
 
\dt
//Connect to a database:
\connect cc_hist;
 
//Determine the current database:
select current_database();
 
//Create a table
CREATE TABLE article (
    article_id bigserial primary key,
    article_name varchar(20) NOT NULL,
    article_desc text NOT NULL,
    date_added timestamp default NULL
);
