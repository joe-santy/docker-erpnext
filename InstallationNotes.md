## Notes on ERPNext installation

Install Docker and Docker-Compose

Download ERPNext image from https://hub.docker.com/r/lukptr/erpnext7:

```
docker pull lukptr/erpnext7
```

Run container as daemon, exposing container port 80 to localhost port 80:
```
docker run -d --name erpnext  -p 80:80 lukptr/erpnext7
```

Enter ERPNext container:

```
docker exec -it erpnext bash
```

Update.  May need to used switch-to-branch to do so:

```
bench update
bench switch-to-branch 12
```

Migrate and backup:

```
bench migrate
bench backup
```

Look in site folder to find .sql.gz filename:

```
cd sites/site1.local/private/backups
ls
```

Go back to frappe-bench directory:

```
cd /home/frappe/frappe-bench
```

Use backup to restore DB:

```
bench --force restore sites/site1.local/private/backups/[FILENAME_FROM_ABOVE_ENDING-site1_local-database.sql.gz]
```

Go to localhost in web browser.
Login credentials:
```
Administrator
12345678
```

Setup your system, making sure to change the credentials of both the site login and database.  Good luck with your business!
