## ud_fullstack_p5
### The IP address and SSH port so your server
#### IP
52.89.23.250
#### SSH PORT
2200
### Complete URL to application
http://52.89.23.250
### A summary of software you installed and configuration changes made
#### What I've done:
1. added new user grader, created file `/etc/sudoers.d/grader` with necessary permissions. Like so: `adduser grader` File `/etc/sudoers.d/grader` has `grader ALL=(ALL) NOPASSWD:ALL` inside
2. `sudo apt-get update` - to retrive new package list
3. `sudo apt-get upgrade` - to update software, based on the list from previous command
4. Make changes in `/etc/ssh/sshd_config`, set `Port 2200` and `PasswordAuthentication no`
5. Configired ufw using `ufw`:

  ```{r tidy=FALSE}
sudo ufw status
ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2200
sudo ufw allow www
sudo ufw allow ntp
ufw enable
```
6. Configure the local timezone to UTC: `dpkg-reconfigure tzdata`, choose `etc` at the bottom of the list, then `UTC`.
7. Install (like [here][id1]) and configure Apache to serve a Python mod_wsgi application. Added configs based on [this][id5] to `/etc/apache2/sites-enabled/000-default.conf` at the ending of `</VirtualHost>` block. Created `/var/www/html/myapp.wsgi` file.
8. Install and configure PostgreSQL like [here][id2]:
  - Deinied remote connections, set `listen_addresses = 'localhost'` in file<br> `/etc/postgresql/9.3/main/postgresql.conf`
  - Created user `catalog` like [here][id2] and set permissions (only ability to login) like [here][id3] and [here][id4]. Set password for `catalog` role: `sudo -i -u postgres`, then <br> `ALTER ROLE catalog WITH PASSWORD '123123';`
9. Install git `sudo apt-get install git`, clone my `ud_fullstack_p3` repo and setup my Catalog App project like [here][id5]
10. Install pip (`apt-get install python-pip`), sqlalchemy (`pip install SQLAlchemy`), utils (`pip install sqlalchemy-utils`), psycopg2 (`sudo apt-get install python-psycopg2`). Finally run `python database_setup.py` to create db tables.
11. Configure apache2 like [here][id6] and in [official falsk docs][id5]
12. Installing Flask `sudo pip install Flask`, `apt-get install python-oauth2client`

### List of third-party resources
* https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
* https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04
* https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2
* http://www.postgresql.org/docs/9.0/static/sql-alterrole.html
* http://superuser.com
* http://markdowntutorial.com
* http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
* http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/
* http://askubuntu.com/questions/122330/unable-to-restart-apache-getting-error-apache2-bad-user-name-apache-run-use
* https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
[id1]: https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
[id2]: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04
[id3]: https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2
[id4]: http://www.postgresql.org/docs/9.0/static/sql-alterrole.html
[id5]: http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/
[id6]: https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
