# Setup Mysql


## Setup Mysql 8 on Docker Desktop and DBeaver
### Docker desktop
- name: `mysql-container`
- port: `3307`
- variables:
  - `MYSQL_ROOT_USER` : `root`
  - `MYSQL_ROOT_PASSWORD` : `password`
- Reference: https://youtu.be/vNH3aOTDjsw?si=6DOy4Epj3aLuR1hg

###  DBeaver
- Add Connection 
- Choose Connect By URL:
  - `jdbc:mysql://localhost:3307?useSSL=false&serverTimezone=UTC`
- Username : `root`
- Password ; `password`
- In Driver properties:
  - `allowPublicKeyRetrieval` : `true`
  - `useSSL` : `false`