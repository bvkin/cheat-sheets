# Postgresql Cheat Sheet

### Connection url format
`postgresql://[user[:password]@][netloc][:port][/dbname][?param1=value1&...]`

### Connect to postgres instance
`psql -h <host-url> <database> <user>`

### Connect to database
`\connect <dbname>` <br/>
`\c <dbname>` <br/>

### List databases
`\list` <br/>
`\l` <br/>

### List schemas
`\dn`

### List tables 
`\dt`
