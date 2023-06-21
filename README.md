# docker oracle database express edition
Oracle linux database

* https://github.com/mrajaonson/compose-oracle-linux.git

## Requirements

* oracle account
* https://profile.oracle.com/myprofile/account/create-account.jspx

## Installation

```bash
# 1. login to registry oracle
docker login container-registry.oracle.com

# 2. pull docker oracle express 21
docker pull container-registry.oracle.com/database/express:21.3.0-xe

# 3. run docker
docker run --name oracle21 -p 1521:1521 -p 5500:5500 container-registry.oracle.com/database/express:21.3.0-xe

# 4. run sqlplus
docker exec -it oracle21 sqlplus / as sysdba
```

## Create user

```bash
alter session set "_ORACLE_SCRIPT"=true;

CREATE USER user1 IDENTIFIED BY user1;

grant create session to user1;

grant connect to user1;

GRANT ALL PRIVILEGES TO user1;
GRANT DBA TO user1;

connect user1;
```