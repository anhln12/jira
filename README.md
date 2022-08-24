# jira
# Sử dụng môi trường docker
```
docker volume create --name jiraVolume
docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira" -d -p 8080:8080 atlassian/jira-software

hoặc
sudo docker run --detach --publish 8080:8080 --link jiradb-postgres:postgres --name jira7 cptactionhank/atlassian-jira-software:latest
```

# Tạo container Postgres

```
docker run --name postgres -e POSTGRES_PASSWORD=123456 -d -p 5432:5432 postgres:alpine
```

# Truy cập container Postgres, tạo database kết nối Jira
```
// Truy cập container
docker exec -it postgres /bin/sh
su postgres
createuser --interactive -P jirauser
psql
```

```
// Tạo database
CREATE DATABASE jiradb WITH ENCODING 'UNICODE' LC_COLLATE 'C' LC_CTYPE 'C' TEMPLATE template0;
```

# Gán quyền truy cập database
```
// GRANT ALL PRIVILEGES ON DATABASE <Database Name> TO <Role Name>
GRANT ALL PRIVILEGES ON DATABASE jiradb TO jirauser;
```

# Truy cập localhost:8080
<img src=https://i.imgur.com/C7Zv5jN.png>

# Cấu hình database
<img src=https://i.imgur.com/ej58j2S.png>

# Tạo Trial key
<img src=https://i.imgur.com/LIUT8NX.png>

# Nhập License key
<img src=https://i.imgur.com/yVw0LCK.png>

# Cấu hình account administrator
<img src=https://i.imgur.com/EZflJkM.png>

# Thành công
<img src=https://i.imgur.com/YQoXTSP.png>
